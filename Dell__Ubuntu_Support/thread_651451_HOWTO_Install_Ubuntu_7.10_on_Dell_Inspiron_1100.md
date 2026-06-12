---
title: "HOWTO: Install Ubuntu 7.10 on Dell Inspiron 1100"
date: 2007-12-27
forum: Dell  Ubuntu Support
---

### Post by LennoxRock on 2007-12-27
I know that installing Ubuntu on this Dell has been a headache ever since I first installed edgy. In mucking around with it, I have gotten a pretty simple, quick method that seems to work well.

First off, I highly recommend using the alternate desktop cd, as you will be able to install without having to deal with the display issues until later. I'm not going to get into the actual installation process, as this guide assumes you are able to actually get the OS installed with the alternate CD.  Also, before doing this, ensure you've upgraded your BIOS, and changed the video memory to 8MB in the BIOS settings (accessed by hitting F2 when you first turn it on).

Once you've installed Ubuntu and you reboot, press Escape at the GRUB loader (it's the screen right after your bios initializes). Select the recovery mode (should be the second option).

This should take you to the command prompt as root. From here type in

```
# dpkg-reconfigure xserver-xorg
```

This takes you to a series of setup questions regarding your keyboard, mouse, and video settings.

1. Answer NO to autodetect video hardware

2. Select i810 from the list of drivers.

3. Hit enter for the default identifier

4. Make sure the Video card's bus identifier reads "PCI:0:2:0" (without the quotes). This should already be the default.

5. Leave the memory question blank and hit enter.

6. Select NO on the kernel framebuffer interface question.

7. Answer the keyboard and mouse questions (use your common sense here) =p

8. Select YES on the question about writing the default Files section to configuration file.

9. Select NO to autodetect monitor.

10. Hit enter for the default identifier.

11. Select 1024x768, 800x600, and 640x480

12. Select ADVANCED method for selecting monitor characteristics.

13. Enter "31.5-48.5" (without the quotes) for the horizontal sync.

14. Enter "59.0-75.0" (again, without the quotes) for the vertical refresh.

15. Answer YES to the next question.

16. Select 24 for default color depth.


And you're DONE!!!

After this type

```
# reboot
```

And you should reboot into your nice, working Ubuntu installation. Enjoy!

(I had posted this under Installation and Upgrades, but I guess this is where it's supposed to go...)

---

### Post by barryaa on 2007-12-28
you are a genius, thank you.

---

### Post by strollerdude on 2007-12-29
I still have a problem with my Inspiron 1100. I managed to install gutsy on 28/12/07 by changing "vesa" to "i810" in xorg.conf using the safe graphics mode of the live cd as noted in another post [http://ubuntuforums.org/showthread.php?t=608481](http://ubuntuforums.org/showthread.php?t=608481) . Everything went very well. My network cable was connected during the installation and I assume main security updates were installed as a part of this. I rebooted and all was fine.

The next day, after enabling universe and multiverse repositories and downloading programs from these,  I booted up but a blank screen came up instead of the log on screen. I ran dpkg-reconfigure xserver-xorg as per the post, but it did not fix the problem.  I have reinstalled (still a valid option for me) twice, both with and without the network cable connected, and still get the blank screen instead of the log on screen. 

Any suggestions would be appreciated. I am about to try xubuntu, followed by the alternate cd.

---

### Post by LennoxRock on 2007-12-29
I get that problem occasionally as well, and have yet to solve it.  All I do is hold the power button until it cuts off, and then turn it back on.  9 times out of ten it boots up just fine the next time, but every so often I have to turn it off and back on several times to get the logon screen.  It's a pain, but it's all I've been able to do so far.  Hopefully someone out there might have some suggestions as to the cause of this.  I've been having this problem since Feisty came out.

---

### Post by strollerdude on 2007-12-30
Thank you LennoxRock. I tried xubuntu and had the same problem. I booted into recovery mode and typed "startx". X started fine as root. When I rebooted, all was good. I don't know if this was just random, or if I had achieved something. I thought I would reinstall ubuntu to see if it would fix the problem there (I haven't done much else today) however, after installing, things worked without me doing anything.

---

### Post by strollerdude on 2007-12-30
Problem happened again, and using startx from the recovery boot did help get things working. I have a feeling it has something to do with the .Xauthority file that I know nothing about. I will see what I can find.

---

### Post by strollerdude on 2007-12-31
Problem solved. Just needed to remove splash from /boot/grub/menu.lst as per the post [http://ubuntuforums.org/showthread.php?t=453277&page=2](http://ubuntuforums.org/showthread.php?t=453277&page=2). Now I can enjoy that empty feeling of having spent three days on a problem that was finally solved by deleting one word (not my worst problem solving effort either).

---

### Post by briguy367 on 2008-01-09
Great walkthrough.  The step-by-step got me up and running.  Thanks much.

---

### Post by JOBUME on 2008-02-27
I am experiencing similar problems with my Ubuntu 7.10 on Dell Inspiron 1100. I got it working by using dpkg-reconfigure command and following LennoxRocks step-by-step. It still booted to a black screen. I booted in recovery mode and tried editing the menu.lst file. I could not use gedit, it only said: cannot open display, so I tried using vi, which let me open the file. I removed the "splash" from the file and rebooted and it worked like a charm. Rebooted the comp a couple of times and everything seemed to be working. Now, just a few minutes ago, I ran into the same black screen. Rebooted, but got the black screen again. I opened menu.lst again and the "splash" was back. I deleted it, rebooted, and still got the black screen. I am very confused right now. As you can all guess, I am a total newb at Linux and at computers in general. I don't have the slightest idea what LennoxRocks step-by-step or the "splash" deleting really does, I am just following orders. Can someone explain what's going on?

---

### Post by aijack on 2008-03-08
I wanted to thank LennoxRock and strollerdude for the above posts. 

I was installing 7.10 on an old Inspiron 1100 that I had sitting in my closet for my 7 year old daughter. I figured the installation would be easy, and except for the display issues, it was. The posts in this thread saved me countless hours of work.

After messing around for hours experimenting with editing the xorg.conf file, I found this post, did a fresh install from the alternate ISO, and went right into recovery mode.

I followed LennoxRock's thread for configuring xserver, then strollerdude's post on removing the splash line from menu.lst (a note about this: if you CAN'T get into the GUI to use gedit, which I couldn't, you need to boot into recovery mode and edit from there using vi). Once the OS boots and you get to the prompt, type:
```

# sudo vi /boot/grub/menu.lst

```
Type "G" (CAP, no quotes) to get to the end of the file, "j" to move up to the line you need to edit, then hit "l" to move to the end of the 3rd line after the # # # # End of Default Options # # # # section as [noted in this post referred to by strollerdude]("http://ubuntuforums.org/showthread.php?t=453277&page=2"). Position  your cursor within the word "splash" and type "dw" to remove the word. Once the word "splash" has been removed, hit the ESC key, then ":wq" to save the file. Now type reboot at the command prompt.

Here's a link to basic vi commands for those not used to it:
[http://www.cs.rit.edu/~cslab/vi.html](http://www.cs.rit.edu/~cslab/vi.html)

. After those two steps it's been working wonderful, and my daughter is ecstatic to have her first laptop.

Great community, great post! Thank you!
:guitar:

---

### Post by mengel on 2008-03-17
Just installed gutsy kubuntu on my 1100 and followed your howto to fix display issue--it worked a treat! thank you, thank you, thank you!!!!

---

### Post by Threnners on 2008-03-19
Note: These instructions also worked for the Inspiron 1150 (but I don't know if it's because I'm using an LCD from an 1100), however, I did have to reboot in recovery mode and launch startx before the screen came up.  Once I rebooted, it came up normally and all has been peachy.

---

### Post by thecrambler on 2008-03-22
> **LennoxRock said:**
> I know that installing Ubuntu on this Dell has been a headache ever since I first installed edgy. In mucking around with it, I have gotten a pretty simple, quick method that seems to work well.

First off, I highly recommend using the alternate desktop cd, as you will be able to install without having to deal with the display issues until later. I'm not going to get into the actual installation process, as this guide assumes you are able to actually get the OS installed with the alternate CD.  Also, before doing this, ensure you've upgraded your BIOS, and changed the video memory to 8MB in the BIOS settings (accessed by hitting F2 when you first turn it on).


Hey Lennox! Thank you for the VERY informative post! I am having a problem with the alternate text based install. After I answer the questions regarding my keyboard layout, the installation fails to mount the cd-rom and nothing I do seems to make it work. It loads the module 'floppy' for 'Linux Floppy' but that's it. HELP!

---

### Post by mtnbike_rider on 2008-04-02
Hey Lennox, 
Just wanted to say thanks for taking the time to post this tutorial.
YOU ARE A LIFESAVER!!!
I read so many forum entries about similar black screen problems, but it never solved the problem.  The BIOS was the key to this one..


THANKS!!!!

:D

---

### Post by strollerdude on 2008-04-30
Hi Fellow Inspironers,
I recently upgraded to Ubuntu 8.04 and it went very smoothly from the livecd. I did remove splash from /boot/grub/menu.lst as discussed earlier. Seems like there is no need in 8.04 to change from vesa to i810.

I do get a blank screen after suspend and rarely on boot up. Sometimes this is fixed by one or more pressings of ctrl-alt-backspace - I am currently not using suspend unless my 5 year old does it out of habit.

I do have 768MB of ram - the live install suggests a minimum of 384MB - so this might be an issue if you still have 256MB.

---

