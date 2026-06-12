---
title: "ssh script automagically login help"
date: 2006-10-05
forum: Desktop Environments
---

### Post by ser1alsn1per on 2006-10-05
hi im a total nooob when it come to stuff like this 

currently im running 2 pc 1 pc with ubuntu with 2 screens + another pc runing osx86 using wireless keyboard + mouse + synergy to share them

synergy autostart on both pcs 

the problem being i hae the mac on all the time and its the client wich should be run after the server 

I need a terminal script to log in to my mac via ssh 

so 

##/bin/bash
ssh 192.168.1.64 



then thats all i have 

i would like it to enter the password for me automagically 

run 1 command 

sudo /Library/StartupItems/Synergy/Synergy start

then end 


can any1 help

---

### Post by chalex on 2006-10-05
You probably want to use something like "ssh -c" with an ssh key in place.  Look up "using ssh keys" in google.  

Alternatively, can't you configure synergy to just try to connect to the server every minute while it's not there?  There should be a config option for it somewhere.

---

### Post by ser1alsn1per on 2006-10-06
cheers any help is appreciated

---

### Post by TyphoonJoe on 2006-10-06
> **ser1alsn1per said:**
> cheers any help is appreciated

Run the following command to generate your a key:
```
ssh-keygen -t rsa -b 2048
Generating public/private rsa key pair.
Enter file in which to save the key (/home/user/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/user/.ssh/id_rsa.
Your public key has been saved in /home/user/.ssh/id_rsa.pub.
The key fingerprint is:
cb:23:01:33:fe:01:11:0a:36:34:4b:f0:22:11:ca:1a user@server.domain.com
```

The command prompts you for several things while it is running. Use the default file name and location for your key; this is where SSH will look for it. The pass-phrase is optional. Since you will be using this to automate sending commands to your server, you should leave the pass-phrase empty.

The ssh-keygen command creates 2 files. The file id_rsa is your local identification key file and should not be shared with any other user accounts and it should not be copied to other servers. The file id_rsa.pub is your public key file. The contents of this file need to be distributed to the servers you will be connecting  with. To securely copy this file to your the other server, type:
```
scp ~/.ssh/id_rsa.pub server1.domain.com:server_id_rsa.pub
```

After the public key has been copied to the remote server, connect to the remote server using SSH. Afterwards, copy the contents of the public key into the local .ssh/authorized_keys file. For example you can type:
```
cat server_id_rsa.pub >> ~/.ssh/authorized_keys
```

Be sure to use ">>" and not ">" to avoid overwriting any other keys that may be in the file. Also, check the file permissions on authorized_keys. It should be set to "644" so that only the owner can write to the file. 
Log off of the remote server and attempt to connect again. If everything was done correctly, you should be logged in without having to provide a password.

At this point you can use "ssh -c command" to execute a command on the remote server.

---

### Post by ser1alsn1per on 2006-10-07
cheers for the help 

but how is this done by a bash script    

ie i need the command to input the password automagically 

once again i have 

##/bin/bash
ssh 192.168.1.64

which runs the ssh   but asks for the password so i just need the code to do this for me

---

### Post by ser1alsn1per on 2006-10-12
so does any one know theese few simple comands in script please 



or at the terminal how do i log in to ssh input the password in 1 command 


please help



pleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleasepleaseplease

---

### Post by BatteryCell on 2006-11-09
Once you have the key generated and copied to the server (TyphoonJoe) all you have to do to login in a bash script is put the line:
```
ssh user@website.example
```
And it should automatically log you in.

---

