---
title: "Network config in Enlightenment"
date: 2007-01-08
forum: Desktop Environments
---

### Post by tigerpants on 2007-01-08
Currently using E17 and loving it, despite the odd bug and glitch :) 

The one problem I do have is network configuration... I need to switch between my wireless config (DHCP) and wired (static IP) and I need to change the values. However, I cant find a way to do this in enlightenment. Any ideas?

Thanks

---

### Post by tcrroadie on 2007-01-08
I'm sorry, but I am at work at the moment, but I believe I may be able to lean you in the correct direction.  I believe your answer may lie in the terminal command ifconfig.  I personally have never had to manually set my network settings from the command line but I am sure someone could elaborate or correct me if I am wrong. 

Read the man page for ifconfig.

```
man ifconfig
```

Check for network command line tools using apropos.

```
apropos network
```

Sorry I could not be more helpfull at the moment.

---

### Post by tcrroadie on 2007-01-08
I feel like an idiot.  Bring up Enlightenments main menu by left clicking on the desktop.  Left click run from the menu.  In the blank dialog that comes up enter gnome-network-settings.  I may be a little off.  This is purely from memory at the moment.  In the run field you can also just type gnome- and page up and down the list until you find Gnome's graphical network tool.

Hope this helps out some more and answers your question.

---

### Post by tigerpants on 2007-01-08
Thanks man. Wasn't sure about using gnome settings as it sometimes bugs enlightenment out for me. I'll give that a go.

---

### Post by tcrroadie on 2007-01-08
> **tigerpants said:**
> Thanks man. Wasn't sure about using gnome settings as it sometimes bugs enlightenment out for me. I'll give that a go.

Just out of curiosity, what version of E17 are you using and what method did you use to install it?  I installed E17 on my desktop pc at home using the repositories located at edevelop.org for ubuntu edgy, and E17 has been nothing but bliss for me.  E has not crash once on me, yet at least.  

I also use Elive from time to time (have it installed on an extra partition on my machine) and E17 will crash sometimes on Elive, but mainly because the Elive developers are using an older version of E17.  Hopefully the Elive team will move to a more recent DR17 release in the near future since the current development stage of E17 has so much more to offer. 

Glad to hear I was able to help.

---

### Post by tigerpants on 2007-01-09
I'm using the same version of E17 as yourself.  I really love it, I think its by far the most interesting desktop environment available on any platform, and certainly has a great deal of potential. I think I'm going to do a clean ubuntu install on a spare drive, and try re-installing. I get some weird bugs and errors and I'm positive its down to some conflict or other.

I'd actually like to get some kind of dedicated ubuntu enlightenment forum or chat channel going (if there isn't already one) so that we can alla share tips and expriences. That would be cool.

---

### Post by tcrroadie on 2007-01-09
I'm glad to here that you are having a good a time using Enlightenment E17 as I am.  My E17 install on my Edgy system has worked flawlessly for me so far.  My Edgy system is pure vanilla with the exception of installing extra apps and codecs (cough) using automatix, and E17 using the repositories located at edevelop.org.  Buy the way I am also using the beta Nvidia driver for my Geforce 6800GT video card.  No source installs and hacking.

Hopefully who will have a better experience with E17 on a clean install.  As far as a forum dedicated to Enlightenment goes, I would expect one to start as soon as Elbuntu gets off the ground and gets some releases out.  Just a matter of time.

---

### Post by john_spiral on 2007-01-15
I've got E17 running under dapper and it's not too stable, but  then again I've been going mad with every tweek I can lay my hands on via the gui. 

The animated flames at the bottom of the screen are lovely combined with a desktop of Gandalf seeing off Balrog!

---

### Post by Guranic on 2007-02-09
Great to hear other users to have good experiences with E17. I have 1,5 ghz mobile celeron laptop with 512 mb memory and I'm running Enlightenment on top of Kubuntu Edgy. I found howto about installing E17 from edevelop repos and I've been using it one week now. The laptop is working REALLY great, E is so quick, smooth and memory saving.. I've been thinking if I'll try fresh install of Ubuntu (with some K-applications I like) and E17 on top of it.. But because it is working really well now I will wait stable Feisty before I'll do it. For this kind of laptop (or other low resource pc) E17 seems to be unbeaten choice, on the other hand pc with newest hardware would go fine with Kubuntu if the goal is to have good looking, functional and stable OS.

---

