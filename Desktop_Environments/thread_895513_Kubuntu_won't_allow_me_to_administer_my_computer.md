---
title: "Kubuntu won't allow me to administer my computer"
date: 2008-08-20
forum: Desktop Environments
---

### Post by sjmiller85 on 2008-08-20
Well it seems that Kubuntu/KDE, while it is my favorite desktop environment to choose from produces the most amount of hair pulling.  I have been using KDE desktop primarily over GNOME, and I am in a bit of a pickle this time around.  Normally when ever stuff starts to go FUBAR, I just back up all my data, and re-image my partition with another copy of KDE (already had to do this when my network capabilities "houdini'd" away).  But, my CD drive is now not managing to read CDs...

That aside, my current copy of Kubuntu has started to get real annoying.  I messed around with my network settings over the course of 2 or 3 days trying to get it to cooperate with an internet cafe while in route between 2 destinations, when all of a sudden, I can no longer administrate any of the System Settings.  It asks for the password, then it goes back to nothing.
Problem 2 comes when I try to access many programs that require administrator privileges.  I cannot install software, I cannot even change the time of the system, because every time it asks for a password, I enter it, the programs appear to start (hence the hourglass icon at the bottom bar where it shows what programs are currently running), but then it just quits without producing any windows are anything.  i have not screwed around with the accounts at all, so passwords definitely aren't a problem (especially since it registers it as not being incorrect therefor not producing said error).
I find this udderly annoying, since I cannot reload Kubuntu without a functioning CD drive, so is there anyone who either knows of a fix for this issue, or can point me in the right direction for how to re-install Kubuntu with any other means than a disk (thumb drive or external HDD would be optimal for me).  Thank you VERY much for all your help!!

-Scotty

---

### Post by sjmiller85 on 2008-08-21
Strategically Repositioning in the hopes for an answer.

Quick low-down and dirty of the situation.  Every time I am asked for a administrator password (except the shell w/ sudo), the program will not run.  It registers the password as being correct, and down in the Panel it shows the hour glass indicating that it is loading, yet I never see a window.

---

### Post by kuja on 2008-08-21
Try running things with kdesudo from a shell, that should give a hint as to why it doesn't want to work.

---

### Post by sjmiller85 on 2008-08-21
```
scotty@:~$ kdesudo qtparted
xauth: (argv):1:  bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0
/usr/bin/xauth: (argv):1:  bad display name ":0.0" in "add" command
sudo: unable to resolve host

passprompt


No protocol specified

qtparted: cannot connect to X server :0.0


```

Any idea what this means?

---

### Post by kuja on 2008-08-22
> **sjmiller85 said:**
> ```
scotty@:~$ kdesudo qtparted
xauth: (argv):1:  bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0
/usr/bin/xauth: (argv):1:  bad display name ":0.0" in "add" command
sudo: unable to resolve host

passprompt


No protocol specified

qtparted: cannot connect to X server :0.0


```

Any idea what this means?

I would check this first: [https://bugs.launchpad.net/ubuntu/+bug/203593](https://bugs.launchpad.net/ubuntu/+bug/203593)

---

### Post by fmartinez on 2008-08-22
Try running this command: 
```
cat /etc/group |grep admin
```
The output should tell you if you have admin rights. If not you may have messed up your permissions, and if you didn't install a default admin you may be out of luck.

---

### Post by sjmiller85 on 2008-08-22
Aha!  So I looked into the bug report, and here is what I have in my /etc/host file:

```
127.0.0.1 localhost
127.0.1.1 scotty-laptop
```

Ok, now when I type in 'hostname' in the shell, this is the output:

```

scotty@:~$ hostname

scotty@:~$

```

I take it that the output of nothing showing that I do not have a host name, is a bad thing, even more when it says every time that i try and use sudo via the command line:

```

sudo: unable to resolve host

```

So does this trigger any hints for how I need to go about fixing this little bugger?  Thanks for all the help!

P.S. And in reply to fmartinez:

```

scotty@:~$ cat /etc/group |grep admin
lpadmin:x:109:scotty
admin:x:114:scotty

```

---

