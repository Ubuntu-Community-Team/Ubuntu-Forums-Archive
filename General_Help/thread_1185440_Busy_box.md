---
title: "Busy box"
date: 2009-06-12
forum: General Help
---

### Post by Rifai on 2009-06-12
During fresh install of ubuntu 8.10 everything moves fine upto partition. After that it gets reboot and falls to Busy Box command. Nothing gets work.
  "BusyBox v1.1.2 (Debian 1:1.1.2-6ubuntu3) Built-in shell (ash)"
  "Enter 'help' for a list of built-in commands"
   
  While installing inside windows, gets installed fully. On reboot asking username and password then hangs with a orange sceen. I got that compiz is not able to start in my syst through the forums. So removed compiz using the command
  sudo apt-get remove compiz
  sudo apt-get remove compiz-core
   
  Now everything seems ok. But not able to copy any datas from cd or dvd. Showing i/o error while copying. In windows i solved it by changing the tranfer mode from ultra dma to Pio only mode. How to do it in ubuntu?
   
  Don’t want to have dual boot? Need only ubuntu. How to install it without getting busybox command? How to make compiz get working?
   
   
  Note: I’m a newbie to linux world. So explain it in detail. Any help will be accepted with thanks. English may be not so good. Please forgive me for it.

---

### Post by PreviousN on 2009-06-12
I think I'm having trouble understanding your question. But, let me adlib: 

One of my computers sometimes falls to busybox on boot. Why? Something about emask, etc. I looked it up and apparently that is a message associated with a failing hard drive. Well, I didn't want to replace this hard drive because I'm poor/broke so the way to escape from that busybox shell is to type:

```
exit
```

and it continues the boot process. So, try typing exit. It might allow your computer to continue doing whatever it was doing before it dropped to busybox. If it does (continue booting/whatever you were doing), open a terminal and type: ```
 dmesg | tail 
```That'll get you the system log.

Upon further reading, it looks like your problem is happening DURING install? So you have a working live cd install session, and when it gets to partitioning it drops to busybox? That may indicate a problem with your hard drive (since when you partition you are modifying your harddrive's partition table). If that is the case, you can try several things: command line tools to format the hard drive before ubuntu gets to that part in the installation dialog, using gui tools to partition manually before ubuntu does, etc. 

But, still, try typing "exit" into busybox, then hit enter. It may continue doing what it was doing...

---

### Post by Rifai on 2009-06-12
> **PreviousN said:**
> I think I'm having trouble understanding your question. But, let me adlib: 

One of my computers sometimes falls to busybox on boot. Why? Something about emask, etc. I looked it up and apparently that is a message associated with a failing hard drive. Well, I didn't want to replace this hard drive because I'm poor/broke so the way to escape from that busybox shell is to type:

```
exit
```and it continues the boot process. So, try typing exit. It might allow your computer to continue doing whatever it was doing before it dropped to busybox. If it does (continue booting/whatever you were doing), open a terminal and type: ```
 dmesg | tail 
```That'll get you the system log.

Thanks for your reply PreviousN. I tried that also, but no use. It went execute some codes then falls on same busybox command. If i tried again it results in black scree.

My syst: P4 2.4ghz, 512mb, 40 gb HDD(IDE), Intel 845 chipset.

---

### Post by PreviousN on 2009-06-12
What did you have installed on this computer before ubuntu? Did you notice odd behavior on it before hand? Since you seem to be using the live install cd (which copies its data to RAM, and doesn't touch the hard drive before you click install), your problem indicates that you have a dying hard drive. 

But, if you want to force install, you could try an alternate install cd. When you're installing via the live cd, you can still use the computer, right? You might try opening a terminal (go to applications --> accessories --> terminal), and typing "dmesg". You can add the tail part if you want. Tail just gives you the end of dmesg.

If you have windows on the computer, you could try installing using wubi.

---

### Post by Rifai on 2009-06-12
windows xp get installed before ubuntu..

Live cd without install moves upto ubuntu logo and then hangs.


When installed inside windows, compiz not allowing me to log in. so removed compiz and now its ok without compiz.

Now showing i/o error while copying datas from cd/dvd. How to rectify?.

I rectified it in windows by changed the data transfer mode from ultra dma to pio only mode.

---

### Post by PreviousN on 2009-06-12
I/O errors are consistant with my hard drive dying theory. If windows works fine, however, then that is inconsistant with my theory. So, the live cd "hangs" on boot? And when you install via windows, compiz prevents you from logging in? 

Sidenote: I've never heard of compiz preventing people from logging in until now. If I recall correctly, compiz doesn't even run until you log in, since it loads user settings after the user has typed them in. For example, if you have two users, it won't know which config to load until one user logs in. So you may have uninstalled compiz, which may have uninstalled a component which was preventing you from logging in.

Anyways...

Your error with ultra dma is also associated with hard disk problems and IDE. Let's think outside the box here...

Your windows install is working, but when you try to load from a cd you are getting input/output errors. You had to change a mode setting on your cd drive when you were in windows. Hmmm...it sounds like you have a corrupted cdrom, or your cd drive may be going dead. You may try putting the ubuntu installation media onto a usb drive instead of a cd. Now that I think about it, this all could be that your cd drive is going bad.

**I now think it may be your burned cd or your cd drive because you're getting I/O errors (which is nothing to sneeze at) but your other operating system is running fine. Your only getting the I/O errors when trying to install (using a cd), and you had to change the way you use your cd drive in windows.**

Here is how to install from a usb drive: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
But... That link is complicated, so let me lay out easier steps for you. 

1. Boot into ubuntu using your wubi installation (the one that you said you could use after disabling compiz)
2. Open a terminal (Applications --> Accessories --> Terminal)
3. Type this: sudo apt-get install unetbootin
4. Open the program by typing in the same terminal (after it has installed) "sudo unetbootin"
5. Use either the "distribution" drop down to have unetbootin download the ISO from the internet, or the "image" drop down to use an iso that you've already downloaded. 
6. Backup your flash drive. This will delete everything from your flash drive.
7. Click "ok"
8. Wait
9. It will be done. 

Reboot, change your bios of your computer to allow booting from usb. Tell it that usb will have priority over hard drive boot. Then, boot into ubuntu from the flash drive. Then install. Tell me what happens...

---

### Post by Rifai on 2009-06-12
Thanks for your reply. Will try it after reaching home and reply you tomorrow. Thanks...

---

### Post by PreviousN on 2009-06-20
What was the verdict?

---

### Post by Rifai on 2009-06-27
Hi [PreviousN]("http://ubuntuforums.org/member.php?u=380660"),

Installation got finished successfully. Got the login screen. Typed username and password. It results in a black screen with mouse pointer. Keyboard become dead. I searched this forum and got that compiz+intel 82845 was the reason for this. So next time before typing username and password i chaged the session as "failsafe terminal" through options in the lower left end in the logon screen and entered the terminal mode. Then typed the command "sudo gedit /etc/x11/xorg.conf" then password. It opens an empty xorg.conf file in gedit. I closed it. Browse and open /etc/x11/xorg.conf in gedit and added the follwing line in the device section.
[FONT=&quot]
[/FONT]  [SIZE=1][FONT=&quot]Driver "intel"[/FONT][FONT=&quot]
[/FONT][FONT=&quot]Option "AccelMethod" "XAA"[/FONT]


Now my xorg.conf looks like

[/SIZE]Section "Device"
 Identifier "Configured Video Device"
 Driver "intel"
 Option "AccelMethod" "XAA"
EndSection

Section "Monitor"
 Identifier "Configured Monitor"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
EndSection
Then saved it and exit the terminal by typing exit.

Then login as normal.

Now my system working fine without any display problem.

Link "http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1128253"

But now the only problem is i/o error while copying anything from dvd rom. I think i have to change the tranfer mode from UDMA to PIO only to rectify this, as i did in XP. So please help me how to do it.


Thanks for your patience.

---

