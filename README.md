
## How to create and use remote ssh public key

Generate the key on your home (client) machine.  Follow the prompts
```
#ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/root/.ssh/id_rsa): /root/.ssh/root_rsa
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /root/.ssh/root_rsa.
Your public key has been saved in /root/.ssh/root_rsa.pub.
The key fingerprint is:
SHA256:0KdnNoDWsomeLongSequenceOfRandomThings root@aap01.example.com
The key's randomart image is:
+---[RSA 3072]----+
|       .o o      |
|Blah, blah, blah |
|   o  + O B o    |
|Blah, blah, blah |
|*.+o .= S =      |
|Blah, blah, blah |
|o  o=.o .        |
|Blah, blah, blah |
| .+o+            |
+----[SHA256]-----+
```
Next copy the key to the remote server
```
# ssh-copy-id -i /root/.ssh/root_rsa.pub root@10.1.10.150
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/root/.ssh/root_rsa.pub"
The authenticity of host '10.1.10.150 (10.1.10.150)' can't be established.
ECDSA key fingerprint is SSHA256:0KdnNoDWsomeLongSequenceOfRandomThings.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
root@10.1.10.150's password: 

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'root@10.1.10.150'"
and check to make sure that only the key(s) you wanted were added.
```
Now back on the home server (client), add to...
```
# ssh-agent bash
# ssh-add /home/admin/.ssh/admin_rsa
```

And now you are good to go.
