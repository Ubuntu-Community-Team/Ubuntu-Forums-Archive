---
title: "HELP!! No GUI or Functionality on my Ubuntu!!"
date: 2006-10-01
forum: Desktop Environments
---

### Post by tybrenis on 2006-10-01
Hello everyone, I'm new to these forums. I've poked about but haven't been able to find anything about this issue that has worked.

I just installed Ubuntu desktop onto my system, and all went well. I had it all configured and I used it for a few hours. I then installed a new program on the machine, and it told me to reboot to finish everything off. I restarted, and it seemed to be going fine.

It went through the normal procedures, everything was okay except for my Network Interface, which it locked up on because I have wireless. So I just typed Ctrl + C to skip that step.

All went well, and the GUI came up asking me for my username and password. I type them in, and when the desktop should be coming up, the screen goes almost black with my mouse in the middle. I can move around the cursor no problem, but there is nothing but a blank screen.

What the heck!! How do I start up my Ubuntu?

I appreciate your replies.

P.S. I should mention that I am a COMPLETE linux newbie, this is my first install so you'll really have to walk me through this stuff.

---

### Post by tybrenis on 2006-10-01
Also, I can press Ctrl + Alt + F1 and I can go into the command line. It appears that everything but the GUI has booted up. When I shut down the computer, it goes through all of the shutdowns and lists everything that it is turning off etc. and it would appear that everything is functional except for the gui. My question is how the heck do I get it to work?

This is fairly urgent, responses are greatly appreciated.

---

### Post by Ocxic on 2006-10-01
go into one of those command line screens, login with you username and pass

then type, "sudo dpkg-reconfigure xserver-xorg" the password it ask's for is yours, when it askes you to chose the screen size, use the "simple" method. hopfully this will help.

---

### Post by tybrenis on 2006-10-01
> **Ocxic said:**
> go into one of those command line screens, login with you username and pass

then type, "sudo dpkg-reconfigure xserver-xorg" the password it ask's for is yours, when it askes you to chose the screen size, use the "simple" method. hopfully this will help.

Hello, 

Thanks for the tip. However, it didn't work for me.

I typed in the code, and just received a flashing underscore and nothing happened.

This is what I get:

"user@user-desktop:~$ sudo dpkg-reconfigure xserver-xorg
HERE is where I just get a flashing underscore and nothing happens and I have to reboot"

Replies appreciated.

---

### Post by tybrenis on 2006-10-01
> **Ocxic said:**
> go into one of those command line screens, login with you username and pass

then type, "sudo dpkg-reconfigure xserver-xorg" the password it ask's for is yours, when it askes you to chose the screen size, use the "simple" method. hopfully this will help.


Okay, I returned to my first booth screen where I select what version/operating system I wanted to start up. This time I selected one that said "magma". I went in, and it gave me errors about the X server, and then told me that it would be disabled until I fixed and restarted it. 

I typed in the code you gave me and went through set up, and I switched it to the "simple" method. I booted back in after doing this and got the same exact problem.

What can I do!?

Please help!

---

### Post by sarhento_lobo on 2006-10-01
> **tybrenis said:**
> Hello everyone, I'm new to these forums. I've poked about but haven't been able to find anything about this issue that has worked.

I just installed Ubuntu desktop onto my system, and all went well. I had it all configured and I used it for a few hours. I then installed a new program on the machine, and it told me to reboot to finish everything off. I restarted, and it seemed to be going fine.

It went through the normal procedures, everything was okay except for my Network Interface, which it locked up on because I have wireless. So I just typed Ctrl + C to skip that step.

All went well, and the GUI came up asking me for my username and password. I type them in, and when the desktop should be coming up, the screen goes almost black with my mouse in the middle. I can move around the cursor no problem, but there is nothing but a blank screen.

What exactly did you install, and how did you go about the installation process?

---

### Post by tybrenis on 2006-10-01
I downloaded Ubuntu 6.06 off of this website:

[http://www.linuxcnc.org/index.php?option=com_content&task=view&id=21&Itemid=4&lang=en](http://www.linuxcnc.org/index.php?option=com_content&task=view&id=21&Itemid=4&lang=en)

I installed it onto my hard disk and all was well. I downloaded breezy-install off of the link I provided above. I installed it and it told me to re-boot Ubuntu, and I shut it down, and when it came back up I've had the same problem since then. 

Please help. I appreciate your response.

---

### Post by Fass on 2006-10-01
> **tybrenis said:**
> I downloaded Ubuntu 6.06 off of this website:

[http://www.linuxcnc.org/index.php?option=com_content&task=view&id=21&Itemid=4&lang=en](http://www.linuxcnc.org/index.php?option=com_content&task=view&id=21&Itemid=4&lang=en)

I installed it onto my hard disk and all was well. I downloaded breezy-install off of the link I provided above. I installed it and it told me to re-boot Ubuntu, and I shut it down, and when it came back up I've had the same problem since then. 

Please help. I appreciate your response.

Breezy is the old version of Ubuntu. You installed dapper and then you ran some sort of installer script for breezy which seems to [install a breezy kernel](http://www.linuxcnc.org/emc2/dists/breezy/emc2/binary-i386/) and a bunch of other stuff that is not compatible with dapper. One could liken it to you installing Windows XP and then installing the inner most parts of the Windows 98 OS. You can imagine what sort of a mess that makes...
 
I suggest wiping the partition and reinstalling dapper and then staying away from anything called breezy. You want the dapper install script for emc2.

---

### Post by tybrenis on 2006-10-01
> **Fass said:**
> Breezy is the old version of Ubuntu. You installed dapper and then you ran some sort of installer script for breezy which seems to [install a breezy kernel](http://www.linuxcnc.org/emc2/dists/breezy/emc2/binary-i386/) and a bunch of other stuff that is not compatible with dapper. One could liken it to you installing Windows XP and then installing the inner most parts of the Windows 98 OS. You can imagine what sort of a mess that makes...
 
I suggest wiping the partition and reinstalling dapper and then staying away from anything called breezy. You want the dapper install script for emc2.

Ahh, thanks a bunch! I just found the pre-configured version of EMC, so I'm just going to wipe that partition and install the newest version of EMC onto it, I am downloading the ISO right now.

Thanks again!

---

