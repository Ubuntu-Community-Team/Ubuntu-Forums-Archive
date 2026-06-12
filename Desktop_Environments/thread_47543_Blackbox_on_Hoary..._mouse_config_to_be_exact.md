---
title: "Blackbox on Hoary... mouse config to be exact"
date: 2005-07-09
forum: Desktop Environments
---

### Post by MkIII_Supra on 2005-07-09
I am a lefty and I can set the mouse to left handed in Gnome, KDE and XFCE but I am not sure how to do it in Blackbox. Can someone clue me in please? Thanks!

Also I am trying to use bbconf but I am getting this error:

```

john@jtop:~$ bbconf
Could not open config file: /home/john/.bbconf/config
Using internal defaults for plugin.
Segmentation fault
john@jtop:~$

```

 :roll:  ](*,)

---

### Post by MkIII_Supra on 2005-07-09
Rubber baby buggy bumpers... move it on up!

---

### Post by MkIII_Supra on 2005-07-11
Okay no answer on that one... no prob... I am putting Blackbox on the back burner for a while.

Now I am having some problems with apt and trying to install some apps I want and need to set my laptop up. First I know Gnome is the default for Ubuntu... I prefer KDE. I have been using is since 1999 and see no reason to change. Next, I am trying to install KDE and it's various components with both Synaptic and apt-get and I am getting this:

```

john@jltop:~$ sudo apt-get install akregator
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  akregator
0 upgraded, 1 newly installed, 0 to remove and 29 not upgraded.
Need to get 356kB of archives.
After unpacking 1245kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hoary/main akregator 4:3.4.0-0ubuntu10 [356kB]
Fetched 356kB in 3s (98.0kB/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/akregator_3.4.0-0ubuntu10_i386.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
john@jltop:~$

```

I have tried running apt-get update --fix-missing and that didn't correct it either. So until I figure this out, I am stuck. Any ideas? ](*,)

---

### Post by bluevoodoo1 on 2006-02-02
[QUOTE=MkIII_Supra]I am a lefty and I can set the mouse to left handed in Gnome, KDE and XFCE but I am not sure how to do it in Blackbox. Can someone clue me in please? Thanks!

Also I am trying to use bbconf but I am getting this error:

```

john@jtop:~$ bbconf
Could not open config file: /home/john/.bbconf/config
Using internal defaults for plugin.
Segmentation fault
john@jtop:~$

```

 :roll:  ](*,)[/QUOTE]

This is pretty old, have you solved it??

Here are my ideas...

Do you have the bbconf config file? If not, make one in the .bbconf folder. Here's the contents of my .bbconf/config file...

```

! bbconf Configuration file

bbconf.style:	Default
```

Not much to it eh? If that doesn't work, how about complete removal and another install of bbconf?


Try typing 'gnome-settings-daemon' in a terminal. See if that helps with the mouse. I know it will turn on gnome-themes, multimedia meyboard, screensaver. Perhaps mouse too?

---

