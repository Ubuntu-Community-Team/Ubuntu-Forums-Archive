---
title: "Minor problems with Kubuntu"
date: 2005-09-03
forum: Desktop Environments
---

### Post by HolyShnikes on 2005-09-03
Hey, I have been using Kubuntu for just a few days now.  I have worked in other linux OS before but I liked the live CD of this on so much I got rid of Xandros (my previous OS) and installed Kubuntu.  I had some problems with video card stuff (NVIDIA) and I soon found the answer to the problems here and fixed it on my own, so I do look for the answers before I post.  but here are some of the problems I am having so far with this OS:

1: Sounds work on the computer but no CD Player sounds work.  I have looked into media codecs and some other solutions but I have came up empty handed.  If you need more info on this certain problem I will let you know (keep in mind I just installed this OS 3 days ago).

2:  This could help a few of my questions, but when I type "gedit" in the terminal it comes up as not found 
```
nathan@ubuntu:~$ sudo killall esd
esd: no process killed
nathan@ubuntu:~$ sudo cp /etc/esound/esd.conf /etc/esound/esd.conf_backup
nathan@ubuntu:~$ sudo gedit /etc/esound/esd.conf
sudo: gedit: command not found
``` 

3:  I have tried several different ways to get Firefox installed on my computer but I cant seem to get it.  apt-get install firefox works but when it is time to install there is an error ```
nathan@ubuntu:~$ sudo apt-get install Firefox
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package Firefox
``` 

I think  those are the problems that I am experiencing so far.  I dont know if you guys need more info but if you do I would glady let you know.  Thanks for reading :-)

---

### Post by GeneralZod on 2005-09-03
"gedit" is a text-editor that is most commonly used under GNOME.  You can use it under KDE by simply installing it via synaptic, but I'd recommend using "kwrite" instead - simply replace "gedit" with "kwrite" (minus the quotes, of course :)).

Re: installing Firefox - I would first install synaptic (mentioned above) :

```

sudo apt-get install synaptic

```

and then open it (it should appear as "Synaptic Package Manager" in the "System" part of the K-Menu).  Then just search for any packages you want and install via the nice GUI :)

---

### Post by HolyShnikes on 2005-09-03
Ok I have got the synaptic package manager installed, that was pretty easy and thank you for the information on that.  With that I could install my NVIDIA-Settings, Firefox, and Gaim.  I am still however, having a problem with my sound.  I have been working on it for a little while now and I still cant seem to get it.  The system sounds work fine, and when I play a music file located on my computer it works fine too.  The problem is when I try to play a CD/DVD.  (I just noticed the DVD, its the first time I tried it).  So if anyone has some suggestions on fixing it, I would appreciate it.  There is no sound at all.

Oh one more thing...I am experiencing some trouble with my keyboard.  I am using the Microsoft wireless elite set (mouse and keyboard set) and the mouse is fine, but the keyboard will every once in a while add extra letters like llllllllllllllllllllllllllllll or eeeeeeeeeeeeeeee.  It gets stuck for some reason, it does it when I backspace also (deleting some things that I dont want to delete).  It has never done that in windows, and I remember it doing it in Xandros, I dont know if anyone knows what to do but I am open to suggestions.  Thanks for reading again.  :)

---

### Post by eljay on 2005-09-04
Hi, I am very new to anything other than windows so I hope this works for you. I had the same problem and got my sound to work somehow. Try double-clicking the volume control icon (next to the clock) and that should open up KMix. Now right-click on each option to see if any are muted.

This is what I remember doing. LOL. So I hope it will work for you.
 :)

---

### Post by mlomker on 2005-09-04
I'd agree that it's probably muted in Kmix.  Some applications have the ability to have their own sound devices selected, so you should look through the options to double-check what it is set to.  For example, you could configure Skype to use only a headset and everything else goes to your speakers.  It's up to the application whether or not it uses the default sound card.

---

### Post by HolyShnikes on 2005-09-04
LOL, good suggestion but Im not that new to Linux.  I made another topic specifically for this problem because it was giving me so much trouble.  [http://ubuntuforums.org/showthread.php?t=62255](http://ubuntuforums.org/showthread.php?t=62255) 

I get this error message when I log on and try to test for sound.  So I am still open to suggestions.  Thanks for the previous ones though :-)

---

