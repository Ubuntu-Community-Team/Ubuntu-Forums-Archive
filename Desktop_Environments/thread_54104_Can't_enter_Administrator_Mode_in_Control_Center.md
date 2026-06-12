---
title: "Can't enter Administrator Mode in Control Center"
date: 2005-08-03
forum: Desktop Environments
---

### Post by Douglas on 2005-08-03
Hi,

I have the above problem.

I try: <sudo kcontrol> as suggested in Unofficial Documenetion. But not worked.

Would anyone have any suggestions?

Douglas

---

### Post by adwait on 2005-08-03
Are you in the sudoers list? What does it say when you try that?

---

### Post by cwaldbieser on 2005-08-03
Try:
```

$ sudo kdesu kcontrol
```

---

### Post by Rob400 on 2005-08-11
I am having the same problem. I am trying to set up my smaba and file sharing using Kde control but when I enter the admin password I get the blue splash about page. sudo kdesu kcontrol  command gave me errors. Im at work right now and cannot post them but will if needed.  I donot understand the comment regarding are you in the sudoers list. KDE is upgraded to 3.4.2. Admin control didnt work prior to update either. Another point is I installed Kubuntu from an ubuntu install. Any help would be greatly appreciated.
PS
I am currently running PcLinux and decided to try kubuntu. Great distro with the exception of not being able to access admin functions in kde.
thanks

---

### Post by Joe on 2005-08-11
This has been a problem since Kubuntu came out for me.  I stopped using it for a while and started using it again a couple weeks ago.  Anyway, since I'm not used to using sudo, I got rid of it by doing the sudo passwd command that you can find posted somewhere around here on the forums or on the ubuntuguide page.  Then whenever I need to access the administrative functions in the control center, I just go to run command and type kdesu kcontrol, it will ask you for your password and then everything should work fine.  It is annoying however that I have to run kdesu kcontrol every time I need to access admin functions.  You can probably do something like edit the menu so that everytime you access the control center, it comes up automatically w/admin priveleges but I have not looked into this.

---

### Post by jshein on 2005-08-29
I installed from a Ubuntu cd, then added all KDE packages through apt, and this situation does not happen. Kcontrol works perfectly.

Every time I have installed from the Kubuntu CD I got the same problem.

---

### Post by raveman7 on 2005-09-03
what is the command for installing the kde component? 

apt-get install kde ?

---

### Post by jshein on 2005-09-05
apt-get install kubuntu-desktop will get you most of what you will need ( a running kde desktop )

---

