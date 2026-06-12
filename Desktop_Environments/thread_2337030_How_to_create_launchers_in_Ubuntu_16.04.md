---
title: "How to create launchers in Ubuntu 16.04"
date: 2016-09-13
forum: Desktop Environments
---

### Post by clymbon on 2016-09-13
Installed ubuntu 16.04. I think I'm using the "unity" desktop - not sure.  It's whatever the default was when I did the install.

I just installed google-chrome so I could watch Netflix.  I couldn't find it with the "Ubuntu Software", but I installed Synaptic, found it easily there, and installed it.  It works fine if I launch it from a terminal window, but I the install did not create a "launcher" for it, probably because Synaptic isn't fully integrated with the desktop environment I am using.  

Interestingly, I installed classicmenu-indicator, and after I did the google-chrome install with Synaptic it automagically shows up in the classic menus, right there under Internet where I would expect it.  It also runs fine from the command line.

A couple of questions:
1) How do I create launcher for new apps like this?
2) How do I get the classicmenu-indicator to show up on my desktop automatically after a reboot?

Also, a more general question.  I did some searching to find the answer to these questions, and I was surprised to see answers like: "you can't do that".  Almost felt like I was on an Apple website.  Of course with ubuntu I can do anything I want to - the whole thing is open source after all - so it's just a matter of how much effort I'm willing to put into it.  Can someone explain the philosophy here?  Is there a conscious attempt to discourage users from installing software by any means other than the "ubuntu software" tool?  Is that just a "Unity" think?  If so, that's fine, I can see how that might make sense for some users, but it's not for me.  What's the idea?

Thanks,

Duncan

---

### Post by CantankRus on 2016-09-13
Firstly let's determine what desktop you are running.

Install this small sysinfo script via terminal...
```
sudo apt install inxi
```
After install, post the terminal output of ...
```
inxi -S
```

google-chrome isn't available from the default repositories.
What you may have installed is the open source **chromium-browser**
What is your output from the below command(include the * when copying)...
```
apt policy chromium-browser google-chrome*
```


As to this...
> **clymbon said:**
> 

Also, a more general question.  I did some searching to find the answer to these questions, and I was surprised to see answers like: "you can't do that".  Almost felt like I was on an Apple website.  Of course with ubuntu I can do anything I want to - the whole thing is open source after all - so it's just a matter of how much effort I'm willing to put into it.  Can someone explain the philosophy here?  Is there a conscious attempt to discourage users from installing software by any means other than the "ubuntu software" tool?  Is that just a "Unity" think?  If so, that's fine, I can see how that might make sense for some users, but it's not for me.  What's the idea?

Thanks,

Duncan
You can do anything you like but heed warnings that tell you it may make your system unreliable or insecure.
The unity desktop (Ubuntu) is relatively inflexible but it is just a desktop environment and can be replaced while still running the core of ubuntu underneath....
 or install from an iso of Lubuntu, Kubuntu  Xubuntu or Gnome-ubuntu from the get go.

---

### Post by clymbon on 2016-09-14
Thanks for your response.  

Actually, the next time I logged onto the system (actually I think it was after a reboot) the launcher showed up.  Perhaps some kind of re-indexing of the installed application had to happen.  is that expected behavior?  

So my immediate problem is actually solved - without doing anything, but I'm still wondering about the design decision that prevents users from creating their own launchers. 

I'll keep messing around with Unity for a while, but I think I may abandon it and switch to something I'm a little more familiar with.  Not sure I understand the philosophy behind it.  As I said, it seems "Apple-like". 

Anyway, thanks for the pointer to inxi, very useful tool.  Just for completeness, here's what I'm running:

[INDENT]System:    Host: linuxbox Kernel: 4.4.0-36-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
[/INDENT]

I did install chromium-browser, but it does not provide the functionality I was looking for (the ability to play Netflix videos, which depend on Microsoft Silverlight). So I removed it.  I subsequently installed google-chrome (using Synaptic, not the "Ubuntu Software" tool).  It works fine.

Here's the output of the apt command:

[INDENT]$ apt policy chromium-browser google-chrome*
chromium-browser:
  Installed: (none)
  Candidate: 52.0.2743.116-0ubuntu0.16.04.1.1250
  Version table:
     52.0.2743.116-0ubuntu0.16.04.1.1250 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     49.0.2623.108-0ubuntu1.1233 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
google-chrome-stable:
  Installed: 53.0.2785.113-1
  Candidate: 53.0.2785.113-1
  Version table:
 *** 53.0.2785.113-1 100
        100 /var/lib/dpkg/status
[/INDENT]

---

### Post by CantankRus on 2016-09-14
Create a launcher...
[https://ubuntuforums.org/showthread.php?t=2272591&p=13260814#post13260814](https://ubuntuforums.org/showthread.php?t=2272591&p=13260814#post13260814)
There was a couple of apps to create launchers but it is just as easy to do it manually.

To make an application autostart, search in the dash for "start" and open "startup applications"
and add your application.

PS: Most who have gained some experience use synaptic.

---

### Post by ian-weisser on 2016-09-14
The Launcher (Shortcut Bar) should be showing up every time. No 'reindexing' should be needed. Perhaps you have a display issue?

Unity is neither Apple-like nor Windows-like. And not trying to. Unity is designed to be easy to use, easy to discover, and safe to use by unskilled users.
Happily, a plethora od Desktop Environments are easily available for you to try.

---

