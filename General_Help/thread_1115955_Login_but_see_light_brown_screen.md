---
title: "Login but see light brown screen"
date: 2009-04-04
forum: General Help
---

### Post by s0babail on 2009-04-04
I have done the following:
1.  Installed Ubuntu 8.04 from the LiveCD.  Everything went fine with the install process.
2.  Reoboted the computer.
3.  At the login screen, entered the username and password.

Once I click Enter, the screen remains the light brown/tan color.  I can move the mouse fine but see no icons.  The keyboard appears disabled because the Num Lock and Caps Lock buttons do nothing.  I do know for a fact that the keyboard works as I am able to enter the BIOS.

The LiveCD worked when I booted and ran from it.  I even did a check of the CD and it came back fine.  

Some other info. . . 
This hard drive originally had Windows XP on it.  I installed Xubuntu (yesterday) on it from a LiveCD and it worked fine.  The only thing that did not work with Xubuntu was I could not change the subnet mask to 255.255.255.0.  It kept reverting back to 24 for some reason.  Instead of troubleshooting that issue, I decided to install Ubunutu on it since I know and really like this.  

The machine does meet the system requirements.  Else the LiveCD would not have worked.

I wish to make Ubuntu work since I feel this is a better choice than Windows.  Please keep in mind that my Linux experience is limited because I grew up on Windows.  I do hold an IT job so I am not a total newbie with computers, just with Linux.

Any ideas or suggestions would be most welcomed.

Thanks for your time,
Bryan

---

### Post by fabricator4 on 2009-04-04
If you press <ctrl><alt><F1> do you get a terminal screen?

It should have some text like "loading, please wait" and maybe some error message that will give a clue.

It may also be possible to log in to the terminal session and fix the problem as it sounds like Gnome has not installed correctly, maybe.  I'm  a rank noob at linux too, though my computer experience is definitely NOT small either.

If the keyboard isn't working at all, is it a USB keyboard, or PS2?


Chris

---

### Post by Peter09 on 2009-04-04
Boot into recovery mode - you do that by hitting the escape key as soon as you see the Grub prompt on boot. Use the arrow keys to move down by one line to the recovery option.

Once it has booted you should see a menu, choose the fix X server option - see how you get on...

---

### Post by s0babail on 2009-04-04
First off, I mispoke about the version.  it's 8.10 desktop.
I rebooted and went into the recovery mode.  I choose the xfix option and rebooted.  I am still having the same issue as described in the first post.

I could try re-installing but really want to troubleshoot this just for experience.

Thanks,
Bryan

---

### Post by Peter09 on 2009-04-04
OK - it does get a bit sticky from here - can you go into recovery mode again but select the 'drop into command line' option.

Once in command line type the following. (note that case matters)

```
lshw -C Display
```

and post the output.

After that try typing 
```
startx
```
in the command line

---

### Post by s0babail on 2009-04-04
The output:

*-display UNCLAIMED
     description: VGA compatible controller
     product: 82845G/GL [Brookdale-G]/GE Chipset Integrated Graphics Device
     vendor: Intel Corporation
     physical id: 2
     bus info: pci@0000:00:02.0
     version: 03
     width: 32 bits
     clock: 33MHz
     capabilities: pm cap_list
     configuration: latency=0

***
I typed startx and the screen displayed a page's worth of commands that I could not read because it went too fast.  Now the screen has alternating color vertical bars (dark tan and black).  The screen refreshing is very visible.

So the logic is to see if the video card can handle X?  Am I correct in that it appears my video card can't run the X-server?  I just want to know the why as well as the how.

Thanks for your help,
Bryan

---

### Post by Gaz... on 2009-04-04
Hello all,

Can I point out that I was having the exact same problem on a Dell Evo D310 Desktop machine. The live CD works 100% but as soon as it booted from the HD it got as far as the Pre desktop image/music intro then it would just freeze. I tried this using 3 different Hard Drives and the same problem every time. So I assumed it was the video card which is on board with shared memory. I tried various video setting in the BIOS but still nothing.

I tried the idea's listed above in previous posts, but still no luck...

I then found an old 32mb video card lying around so I put it in... and Hey Presto... every thing is as it should be...


Gaz...

---

### Post by Peter09 on 2009-04-04
See if the last post in this thread helps

[http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-install-trouble-with-intel-82845g-graphics-card-557840/](http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-install-trouble-with-intel-82845g-graphics-card-557840/)

---

### Post by abn91c on 2009-04-04
go to a terminal and  enter ```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
``` this will solve your issue

---

