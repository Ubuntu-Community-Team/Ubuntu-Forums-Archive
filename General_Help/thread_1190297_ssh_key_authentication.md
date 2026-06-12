---
title: "ssh key authentication"
date: 2009-06-17
forum: General Help
---

### Post by wpalmer on 2009-06-17
hello just curious as what the command to connect to a  reomte box 

i think its


your file.txt  followed by ssh connecting but im not very sure

any idea?

---

### Post by jonobr on 2009-06-17
Hello


Thats a bit of a strange title for the question you ask.

Im guessing you just want to access one machine from another.

in order to go from one ubuntu machine to another its simply

```
ssh myname@<myiporhostname>
```

where <myiporhostname> is the ip address of the target machine or host name.

This will ssh to your other box <myip>, where myip, could be the ip address or hostname of the remote machine and it will present the username <myname>.

when thats done you give your password and your placed into the home directory of the user you ssh as.

You must have openssh or some ssh daemon running on the machine your connecting to.
You can install open ssh from synaptic.
If your going from a windows machine to ubuntu, use, putty.exe,
you can find that by doing a google.
Same thing, just fill in the info required in the program and it should login.


If you wanted to copy files from the one client ubuntu box to another
eg, I want to copy the file named file from my machine here to the remote machine called larry and into the desktop.

You would use

```
scp file mylogin@larry:~/Desktop
```

If you wanted to copy that same file from larry to the current directory into your local machine then it would be


```
scp mylogin@larry:~/Desktop/file . 
```
Note the dot at the end to signify the copy to the current directory.

You could also use places-> connect to server to make your life easier from an ubuntu box

If your client is a windows box you could use winscp, a free windows scp utiltiy

Hopefully thats enough to keep you busy for a while

---

### Post by lovinglinux on 2009-06-17
[SSH](https://help.ubuntu.com/community/SSHHowto)
[SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
[SSHFS](https://help.ubuntu.com/community/SSHFS)

---

### Post by wpalmer on 2009-06-17
ok thanks for your help but im still getting issues doing those

i have the ssh key on desktop

but the command is what im not comprehending very well

---

### Post by lovinglinux on 2009-06-17
> **wpalmer said:**
> ok thanks for your help but im still getting issues doing those

i have the ssh key on desktop

but the command is what im not comprehending very well

Follow [this](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) to setup the keys. Once the keys are setup you don't need extra commands. To connect to the server simply run this command:

```
ssh user@serverip
```

---

