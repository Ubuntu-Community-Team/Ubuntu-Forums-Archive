---
title: "Hi, My first post. Screen resolution problem."
date: 2005-11-19
forum: Desktop Environments
---

### Post by cjm5229 on 2005-11-19
I have the Ubuntu 5.04, Kubuntu 5.04, and I am writing this from the live CD of Kubuntu 5.10, I don't have any versions installed in my computer because of resolution problem with my Monitor. It will only go as high as 640x480. I can't even get to the apply buttons in system settings because I can only see about 1/4 of the window can't get anywhere near the bottom of the window. I do have Linspire installed with WinXP on this computer. emachines W3050, AMD 3000+ 80 Gig HDD 512MB mem. Nvideo Motherboard, emachines 17" CRT monitor. Would really like to use Ubuntu or Kubuntu 5.10 but it is just impossible with this screen resolution. Any ideas? 
Thanks, Carl

---

### Post by aysiu on 2005-11-19
I have an eMachines and Kubuntu/Ubuntu also does not recognize my native screen resolution. I learned how to add two lines to the /etc/X11/xorg.conf file, and it's perfectly fine now.

Take a look here:
[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

It's not as scary as it may sound.

---

### Post by cjm5229 on 2005-11-22
Hi, Sorry I took so long to respond, I couldn't find my post after I sent it. I just got Kubuntu installed. I tried your solution and when I ran the backup it said timestamp to far in the future. I am trying to reset the system time but I need root access and I can't get to the button because of the screen resolution. I will keep working on this and let you know when I get it solved. Thanks for the information. Carl

---

### Post by HermanAB on 2005-11-22
Ctrl-Alt-F1 till F6 will open a text console.  The broken GUI is on Ctrl-Alt-F7 if you want to go back.

The file to play with is /etc/X11/xorg.conf

Restart X with Ctrl-Alt-Backspace after changing this file.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by cjm5229 on 2005-11-28
Hi, Time for an update. I have been going through the posts and tried everything I could find, including howto's. Everything I tried fails. Sometimes it just won't let me make the change, it says something like "no such command" or " program not found" etc. Other times I get the changes made and then can't reboot into Kubuntu. I get as far as the battery check and it stops. Then I have to reinstall it to get it go any further. I have tried several other Distros and none have had a problem with screen resolution. Most can't find my network controller, which Kubuntu had no problem with. But it is a lot easier to change a NIC card than switch Monitors. I guess I will try again with the next update, seems like an awful lot of people have problems with this, so maybe it will get fixed in the future.  Thanks for the help. Carl

---

### Post by cjm5229 on 2005-12-03
OK, One more update. I installed a new video card. Geforce FX 5200. Resolution problem solved. Still nvidia graphics, but it worked. Now I have to get the sound system working and I'll be in good shape. Thanks for having such a great forum, I have found a lot of useful information just browsing around.
In no time at all I should be able to progress from Noob to someone that might actually know what I'm doing. 
Thanks, Carl

---

