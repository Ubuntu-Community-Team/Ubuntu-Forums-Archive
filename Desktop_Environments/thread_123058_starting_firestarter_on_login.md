---
title: "starting firestarter on login"
date: 2006-01-29
forum: Desktop Environments
---

### Post by louis_nichols on 2006-01-29
hi! I'd like to be able to have firestarter run on login. It has to be run with root privileges, so writing it as startup app in session manager won't do. I could try gksudo, but what I would like is for it to just start, no password.

I know there must be a way to do this, but don't know what that is. I would appreciate your help. Thanks.

---

### Post by tufkakf on 2006-01-29
[QUOTE=louis_nichols]hi! I'd like to be able to have firestarter run on login. It has to be run with root privileges, so writing it as startup app in session manager won't do. I could try gksudo, but what I would like is for it to just start, no password.

I know there must be a way to do this, but don't know what that is. I would appreciate your help. Thanks.[/QUOTE]
Hi, doing this isn't really a great idea imho.
Firestarter is just a frontend to iptables. It sets up your iptables rules and they should be run on bootup from now on. In other words, your firewall is running anyway, so there is no need to run the firestarter-gui just to get it running.

---

### Post by psomas on 2006-01-29
tufkakf is right...you dont have to do it...
but if you want perhaps to do this for another application(which has root privilleges) you can change it with the command chown ,and then write it as startup application...;)

---

### Post by tufkakf on 2006-01-29
[QUOTE=psomas]tufkakf is right...you dont have to do it...
but if you want perhaps to do this for another application(which has root privilleges) you can change it with the command chown ,and then write it as startup application...;)[/QUOTE]
I don't think that will work, as it has to run with root privileges.

What would work, I think, is to edit your /etc/sudoers file, so that the user is allowed to launch firestarter as root without giving a password.

However, this is of course a very bad idea security wise, so I'd recomend against doing this.

---

### Post by byen on 2006-01-29
If you are trying to install firestarter-gui during startup...this is what you do
Step1:
System>Preferences>Sessions>Startup Programs>Add
Startup Command: sudo firestarter --start-hidden 
Order: 20
(Notes: this is add firestarter to your start-up)

Step2:
Open terminal and type:
sudo gedit /etc/sudoers (this will open a file)
Add this to the bottom of that page 
username ALL=NOPASSWD:/usr/sbin/firestarter
(insert your login user name in place of the username)
(This would tell the computer not to ask for a password for the user specified)
save

thats it.. it should work. Let me know if you have any problems.
Goodluck! Hope that helps.

---

### Post by louis_nichols on 2006-01-29
Thanks for the answers, guys! I guess I'm a little confused now. I do know iptables is always there, but this makes me wonder what that command to stop firewall does in firestarter. I assumed that not having firestarter active somwhow resets the iptables rules it creates.

Anyway, it's good to know in case, as you said, I might later need to start another app with root privileges. So, thanks again!

---

