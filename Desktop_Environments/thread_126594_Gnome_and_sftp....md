---
title: "Gnome and sftp..."
date: 2006-02-06
forum: Desktop Environments
---

### Post by jammet on 2006-02-06
I know in KDE it can use Lisa to access sftp similarly to a samba share, it can even find sftp servers on your network for you and let you loggin and such. I was hoping for something similar to Gnome. I tried the Places > Network Servers and the Places > Connect to Server > selecting SSH > inputing information and so on but it just does not work for me. I have tried many different configurations and such and all i get is the same error. It says:

Cannot display location 'sftp://admin@iris/home/admin'
Details: There are no default action associated with this location.

Am i just entering in something wrong? Or am i missing something in here? Cause im not seeing it and i have played with it for the past few days. I have searched over the board and found nothing as well, but i tend to not find what im looking for normally.

Any help would be apprechated, thanks.

---

### Post by jammet on 2006-02-10
I am really hoping for a little help on this from someone. Please?

---

### Post by ebash on 2006-02-10
Your problem seems quite strange as sftp is a supported protocol under Gnome VFS.
Try opening nautilus, do CTRL+L and paste you URL:
sftp://admin@iris/home/admin/

Is it working?

Also are you sure that you can connect to that remote host?
Can you do ?
ssh admin@iris

How about?
ssh -2 admin@iris

If I'm not mistaken sftp uses SSH version 2.

Try to use the command line version of gnome-vfs:
gnomevfs-info sftp://admin@iris/home/admin/
gnomevfs-ls sftp://admin@iris/home/admin/

Any luck?

---

### Post by jammet on 2006-02-10
I have tried those in the past few days, if i do a location try in nautilus all i get is the same error, over command line all i get is:

Error opening: Timeout reached.

the ssh -2 works just fine, im just trying to connect to a freebsd 6 machine that i ssh to all the time. Maybe there are some files im missing that are not installed or some service that gnome requires to be able to do this?

---

### Post by ebash on 2006-02-11
Is your key protected by a passphrase?

If so you will need the SSH agent, do you have the SSH agent running?
Run the command
env  | grep -i ssh

You should see the following environment variables, their values will differ:
SSH_AUTH_SOCK=/tmp/ssh-JnrUcZ4898/agent.4898
SSH_AGENT_PID=4943

Are you using a custom configuration file?
See if you have this file ~/.ssh/config, if you do rename it and try again. I used to have problems in the past because I enabled BatchMode through this file.

I'm starting to run out of ideas!

---

### Post by v79 on 2006-02-11
Hi
Don't know if this will help or not... I used to have the same problem, till one day I didn't specify a port number and it started to work just fine...

v79

---

### Post by jammet on 2006-02-13
Yup according to that ssh agent is running.

the config file is nonexistant in my home folder

v79 i have not specified a port number and i also have specified it as well.. nither work still...


These are good ideas .. Any more :)

---

