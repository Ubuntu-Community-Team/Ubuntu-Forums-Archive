---
title: "[SOLVED] Adobe Flash player upgrade problem??"
date: 2008-09-30
forum: Desktop Environments
---

### Post by brian77095 on 2008-09-30
I am using FF3.0 and when I goto a web site that uses Adobe flash player it redirects me to the adobe website and wants me to pick a file for upgrade if I pick one it starts to DL it.

My question is witch file should I pick and would do I do afterwards with the file?

thanks for the help!!

B

---

### Post by Paddis on 2008-10-01
I chose the .tar.gz (or something similar) and downloaded it. When it's on your desktop, rightclick and click on the ''Extract here''. When it's extracted you should find a new folder on your desktop. Doubleclick it, and you'll find two files, choose the one that opens Terminal (try both) and when it opens up in terminal, it should give you further directions on installing it. That's what I did and it works for me, still, I am really new to Ubuntu so...

---

### Post by brian77095 on 2008-10-03
ahh I it does not seem to support a 64bit proccesor...:(


:~/Desktop/install_flash_player_9_linux$ ./flashplayer-installer

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

oh well nice try..

---

### Post by brian77095 on 2008-10-08
so if you have a 64 bit system you cant use adobe flash????

---

### Post by Perfect Storm on 2008-10-08
Yes you can. In Ubuntu you use Synaptic Package Manager.

Or by command;

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by brian77095 on 2008-10-13
sudo apt-get install flashplugin-nonfree
[sudo] password f 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I did this but still cant seem to use the flash player..

It still says I need to

You will need to Install the latest Flash plugin to view this page properly.

??

---

### Post by Perfect Storm on 2008-10-13
Which version do the site ask for?

---

### Post by brian77095 on 2008-10-13
right..uhh hmm not sure...

here is the site...

[http://store.steampowered.com/](http://store.steampowered.com/)

and the flash is top center..

---

### Post by CJ56 on 2008-10-13
Well I'm running Ubuntu 8.04 64-bit & I got the page to work okay, so -

Have you checked out this:

[http://ubuntuforums.org/showthread.php?t=772490]("http://ubuntuforums.org/showthread.php?t=772490")

If you're running 8.04 Hardy, just do exactly what Kilz says & it should sort itself out...

---

### Post by brian77095 on 2008-10-14
Thanks Everyone!!!  I needed to uninstall something I must have installed earlier.  

On last question....I see that when people have question answered they change the title to 

Answered or Done .....something like that How do I do that for this thread??

---

### Post by Perfect Storm on 2008-10-14
> **brian77095 said:**
> Thanks Everyone!!!  I needed to uninstall something I must have installed earlier.  

On last question....I see that when people have question answered they change the title to 

Answered or Done .....something like that How do I do that for this thread??

Edit your fist post and go to advance edit, you can now select [SOLVED]

---

### Post by brian77095 on 2008-10-14
ok now I feel stupid I went to my first post and cant find advanced edit anywhere...

---

### Post by Perfect Storm on 2008-10-14
Hmm..must be because we're making some forum upgrades. I'll mark it for you then.

---

