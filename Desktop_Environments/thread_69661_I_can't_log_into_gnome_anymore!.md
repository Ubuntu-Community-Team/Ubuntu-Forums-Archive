---
title: "I can't log into gnome anymore!"
date: 2005-09-27
forum: Desktop Environments
---

### Post by scorpio2002 on 2005-09-27
Hi there!
I need help. I don't know why, but I can't login anymore. When I try to login I get this error:

"The gnome session has last less then 10 seconds" together with other error messages... and it gets back to the login screen...

What the hell is going on? plz help :|

---

### Post by brentoboy on 2005-09-27
more info

Was it working before?
when did it stop?
did it die from an "automatic update" or did you install a new package lately?
how long has it been since the last successful reboot?

---

### Post by mlomker on 2005-09-27
Not sure.  It looks like there are some logs in /var/log/gdm.

---

### Post by scorpio2002 on 2005-09-27
Here's the error log:
****************************
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "skorpio"
/etc/gdm/Xsession: Beginning session setup...

** (gnome-session:6936): WARNING **: Unable to read ICE authority file: /home/skorpio/.ICEauthority
*************************

This morning it just worked fine as it's done for the last 3 months. I didnt upgrade or install anything :|

---

### Post by mlomker on 2005-09-27
Look at [this post.]("http://www.ubuntuforums.org/showthread.php?t=69660&highlight=.ICEauthority")

---

### Post by scorpio2002 on 2005-09-27
Th you a lot! it worked and now everything seems back to normality. The only thing I can't understand is how it happened. I didn't change the owner of any file in my home dir...

---

### Post by connellr on 2005-09-27
Did you use K3b?   From what I understand, this is a problem with some KDELibs, and K3b tends to be something that causes the problem a lot ... especially if you launch k3b with the sudo command (sudo k3b) ... I guess if you need to run K3b with root privlidges you should use gksudo rather than sudo.

Sorry for such a jumble of thoughts above, Im still trying to figure this one out myself.

RJ

[QUOTE=scorpio2002]Th you a lot! it worked and now everything seems back to normality. The only thing I can't understand is how it happened. I didn't change the owner of any file in my home dir...[/QUOTE]

---

### Post by Brando569 on 2005-09-27
pretty much the same thing just happened to me! everything worked fine, i booted into windows for sumthin and i couldnt do it, i rebooted the computer and went to class. i came back 3 hours later and tried to login and couldnt, i said i didnt have r/w access to $home i was like wtf? how did this happen? somehow all of the files in my $home directory got changed to user/group root luckly i know enough about linux by now and did various things to change all of my files back to my ownership. this worked ofr 95% of the files, but .ICEauthority was still owned by root, so i rebooted created a new user, logged in as that then it said i was in the sudoers list, luckly i changed to root password from the default and could use the root acct to get past my problems. it was just very odd that this happened. it seems like KDE likes to changed permissions/passwords on you. i remember a little while ago it changed my password on me and wouldnt let me login!

---

### Post by yorick on 2005-10-03
Same thing happened to me a couple of times. The method described in the above post for resolving the problem is rather complicated, tho.

I just log with my username in a terminal and do a 
             
                   sudo rm .ICEauthority

Then I restart kde/gnome and it works.

Not sure why the problem happens either...

---

