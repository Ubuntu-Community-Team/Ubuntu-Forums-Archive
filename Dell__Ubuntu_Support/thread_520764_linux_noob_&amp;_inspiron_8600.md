---
title: "linux noob &amp; inspiron 8600"
date: 2007-08-08
forum: Dell  Ubuntu Support
---

### Post by greenjeddak on 2007-08-08
Hi,

I looked through other posts that might have matched the title of this one, but they were more about installations. So here goes ...

I just dual boot installed Ubuntu Fiesty and XP SP2 on my Inspiron 8600 ...

1. Can someone please educate me on how to get all resolutions available, esp. 1680x1050, to work with my ati mobility radeon 9600? I tried following some directions on the Web and here in the forums, but I just don't know my way around linux. I'm trying to learn and asking questions is the best way imo!

2. I also need to turn off the synaptics touchpad feature. I can barely use my touchpad without it picking up a window or clicking something.

I think those are my main two hassles ... if some kind hearted person would take it upon themself to educate me I would be in their debt.

Thank you!

---

### Post by ManFromMars on 2007-08-08
Hello,

I am in exactly the same position as you - just installed Ubuntu 7.04 on my Inspiron 8600, dual booting with XP SP2.

Resolutions wise, I believe some kind of graphics drivers would be in order (though I have yet to do this myself!): [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) - have you had a look at that?

EDIT: After following these instructions, sx66gns's advice allowed 1650x1050 to be selected :-)

I have yet to experiment with the touchpad settings, as I've been busy trying to get the internet working. Can you connect to the internet? If so, how do you connect, and did you have to do anything special to get it working? My wireless card appears to be connected to my wireless network and sending and receiving data, but Firefox can't access any pages...

EDIT: Fixed internet problems, was an ipv6 issue :-)

EDIT: Touchpad information from sx66gns was useful (thank you very much!)

---

### Post by Wiebelhaus on 2007-08-08
Run this in the terminal:

> sudo dpkg-reconfigure -phigh xserver-xorg


select the resolutions you want with the spacebar then hit tab to select ok hit enter , restart and set your resolution.


[Touchpad]("http://ubuntuforums.org/showthread.php?t=493758")

---

### Post by greenjeddak on 2007-08-08
I was able to get the internet working by using the text installer version of the OS

It prompted me through a portion where it found my wireless and ethernet modems and then had me log on to the network from there. 

... btw thanks sx66gns. I will boot in to Ubuntu and see if that works.

---

### Post by greenjeddak on 2007-08-08
Hi:

I ran the command and I got the option for the 1680x1050 resolution, however, when I select it -- it's all borked and I can't even use the screen. Any thoughts? I really appreciate the hand holding. Thanks!

EDIT: I tracked it down to this thread:
[http://ubuntuforums.org/showthread.php?t=502723&highlight=9600&page=3](http://ubuntuforums.org/showthread.php?t=502723&highlight=9600&page=3)

 >> Originally Posted by mcduck:
After installing fglrx you need to run 'sudo aticonfig --initial' so the driver configures your xorg.conf to work correctly. Check the sticky thread about Ati cards for more info.

---

### Post by ManFromMars on 2007-08-09
Strange, I didn't have any problems with changing the resolution straight off... is your problem solved by the way, then? Thanks for the net tips, I am now posting here from Firefox in Ubuntu, huzzah!

---

### Post by Spiffster on 2007-08-09
To fix my touchpad i used the recipy given in this website: [URL="http://ubuntu.wordpress.com/2005/11/15/fixing-my-alps-touchpad-with-the-synaptics-driver/"][COLOR="Blue"]Fixing my Alps Touchpad with the Synaptics Driver[/COLOR]
[/URL]
Cheers,

Spiffster

---

### Post by greenjeddak on 2007-08-09
Problem solved ... I really just stumbled my way through it. I don't remember exactly everything I did, but when I ran that command above it fixed the problem.

---

### Post by Chepe on 2007-08-16
I'm so happy I found this thread! I'm a novice user of linux (and ubuntu) and I've been struggeling to get the right resolution on my inspiron, but following these instructions it worked perfectly! Thanks!

However, I have an additional question: How do I get my wireless card working? I have tried to follow some online guides, but I've gotten nowhere... I have tried ndiswrapper, but can't seem to manage to install the correct drivers? How did you guys get your wireless card working? I would appreciate easy instructions, I'm really not familiar with the linux-way of doing things... :)

---

### Post by pmoseley on 2007-09-23
I'm using my Inspiron 8600 / Precision M60 and in order to get the right resolution on my notebook I had to edit /etc/X11/xorg.conf...

I removed all resolutions that were there and only inserted:

24bit 1680x1050

I believe this forces X Windows to use that resolution and after a reboot all worked great!

---

