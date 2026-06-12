---
title: "Video card driver problem?"
date: 2006-04-15
forum: Desktop Environments
---

### Post by PsychoBee90 on 2006-04-15
Um.
So.
Yeah.
I have pretty much screwed my computer, it seems.

I used to have SuSE on my computer, and I decided to put newer drivers for my video card in. Everything worked fine, except for getting X to recognize them, or something like that. Then I accidentally did a command that messed things up. I think it was "sax2 -a -r". After that I was unable to get to any GUI, and was entirely stuck in command line.

I figured this problem would be fixed if I switched to Ubuntu (and I had been wanting to try Ubuntu anyway), so I installed it.

Everything was going dandy, it had installed all the packages, and then the computer tells me it is going to fire up the GUI, and WHAM! Black screen with a static underscore in the top left.

I have no idea what to do at this point. Any help would be greatly appreciated.

<3 Linux

---

### Post by encompass on 2006-04-15
Let's start with your hardware... what do you know about your computer...
the speed, the ram, the video card... Those are all a great start...

---

### Post by PsychoBee90 on 2006-04-15
666MHz
192 MB SDRAM
Something nVidia

I just thought of something while I was in BIOS checking this, and I switched my  primary video card to the onboard, and it works now!

But not this also reminded me of one more thing. Is there a default root password, or will I be asked to set one up soon, or what? Because it's like when I logged into command line I was automatically root, then I did a 'su' then I tried to 'su' back to root and I had no idea what the password was, it enver asked me.

---

### Post by Scunizi on 2006-04-15
When you first installed Ubuntu it asked for your user name and password.  The password you entered (the same one used to log into the system) is your root password.  I'm not sure about SUse but it probably has a su command and a terminal to give you root privlidges.  In Ubuntu you start the initial command you want to run with sudo followed by the command you want to enter.  After hitting enter it will ask for your password and execute the command.  Your root privlidges will last for apx 15 minutes.  Within that time period if it won't execute a command because you're not root preface it again with sudo.

---

### Post by maddog39 on 2006-04-15
Yeah, I was having the same problem with the nvidia driver, I was able to fix it by manually editing the config and setting it back to the Vesa driver and got it working again but it refuses to run the nvidia drivers.

---

### Post by taurus on 2006-04-15
[QUOTE=maddog39]Yeah, I was having the same problem with the nvidia driver, I was able to fix it by manually editing the config and setting it back to the Vesa driver and got it working again but it refuses to run the nvidia drivers.[/QUOTE]
Have you followed the steps in this post to install nvidia driver for your video card?  

[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

---

### Post by encompass on 2006-04-16
[QUOTE=Scunizi]When you first installed Ubuntu it asked for your user name and password.  The password you entered (the same one used to log into the system) is your root password.  I'm not sure about SUse but it probably has a su command and a terminal to give you root privlidges.  In Ubuntu you start the initial command you want to run with sudo followed by the command you want to enter.  After hitting enter it will ask for your password and execute the command.  Your root privlidges will last for apx 15 minutes.  Within that time period if it won't execute a command because you're not root preface it again with sudo.[/QUOTE]
ubuntu doesn't try to use a root account that you can use... instead it uses everything with the sudo so instead of su and then the commands... try sudo and use your current password....

---

