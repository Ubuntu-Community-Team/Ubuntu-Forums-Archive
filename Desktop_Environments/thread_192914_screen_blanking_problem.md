---
title: "screen blanking problem"
date: 2006-06-09
forum: Desktop Environments
---

### Post by wpshooter on 2006-06-09
Well, I thought I had this figured out, but the problem is still present.

Even though I have the power management parameters set to NEVER and I also have the screen saver disabled, after a period of inactivity (no mouse or keyboard) the screen/display goes BLANK.  It comes back on fine, if I move mouse, etc.

Is this a problem that is being caused by the graphics driver that is being installed by Dapper Drake Ubuntu.  If so, how to I go about getting & installing the correct driver for my ATI Radeon 7000 video card ?

Thanks.

---

### Post by an.echte.trilingue on 2006-06-09
Edit: I didn't see the last line of your post...

1.  Read [this wiki]("https://wiki.ubuntu.com/AddingRepositoriesHowto") and add the restricted repository.

2.  install the package xorg-driver-fglrx and linux-modules-restricted.

3.  In a terminal, run the command "sudo dpkg-reconfigure xserver-xorg".  On the first screen, be sure to select the fglrx driver.  Also, you need to know the resolutions you want and the refresh rate of your monitor.

4.  Restart the X server.

---

### Post by wpshooter on 2006-06-09
[QUOTE=an.echte.trilingue]This may be a driver problem, it might not.  To help us determine if it is one, can you please do three things:

1.  Tell us what graphics card you have

2.  Run the command lspci in a terminal (make sure you window is wide enough for it to be readable) and post the output here.

3.  Post the contents of the file /etc/X11/xorg.conf.[/QUOTE]

The card is a Power Color build of an ATI Radeon 7000.

I will do step 2 & 3 when I get home, if I can figure out how these are done.

Thanks.

---

### Post by an.echte.trilingue on 2006-06-09
Be sure to read the edit I was skimming your post and I missed the last line.  Sorry!

---

### Post by wpshooter on 2006-06-09
[QUOTE=an.echte.trilingue]Edit: I didn't see the last line of your post...

1.  Read [this wiki]("https://wiki.ubuntu.com/AddingRepositoriesHowto") and add the restricted repository.

2.  install the package xorg-driver-fglrx and linux-modules-restricted.

3.  In a terminal, run the command "sudo dpkg-reconfigure xserver-xorg".  On the first screen, be sure to select the fglrx driver.  Also, you need to know the resolutions you want and the refresh rate of your monitor.

4.  Restart the X server.[/QUOTE]

There are 3 packages I see that start with xorg.  Do I install all 3 or just the driver-fglrx.

Also, there are a number of linux-modules-restricted (of varying names) listed some of which are already marked and some that are NOT marked.  Which do I need to intall ?

Also what is restart the X server ?

Thanks.

P. S. - Is it possible to get an updated driver directly from the ATI website.  I see some Linux drivers on there, but none that is specifically listed as being for the Radeon 7000.

---

### Post by wpshooter on 2006-06-10
bump

---

### Post by an.echte.trilingue on 2006-06-12
1.  xorg-driver-fglrx is the only one that you need.  With a card that old, the driver called "ATI" and the one called "Radeon" might be worth a shot, but I doubt it.

2.  There are different modules for different kernels.  If you are running an intel-type system (includes AMD, I think, but not 64 bit or PPC), the stock Ubuntu kernel is for the i386 architecture (as an aside, you might get a nominal performance increase from the 686 kernel (or K7 for AMD), which you can install through synaptic).  You need the restricted modules that match your kernel (the one that ends in 386 if you are running a stock system).  If you are in doubt, you can open up a command line and type:  "uname -a"

3.  The X server is the program that runs most of your input and output, such as your screen and keyboard.  You can restart it by simply rebooting or hit CTRL+ALT+BACKSPACE, but be sure you have saved everything first.

4.  No.  ATI will not support older any cards older than the 8500 at all.  ATI's linux support trully blows.  The fglrx driver might not even work for you.  If it does not than your best bet is to run dpkg again and try to mess with the configuration while using the "ATI" driver.

---

### Post by thirsch on 2006-06-12
Maybe, [this link]("http://ubuntuforums.org/showthread.php?t=193838&highlight=power+management") contains a duplicate of this post.

I got the same problem with my NVidia card.
I recognized, that it appears after a system restart.

I switch the setting in the power management to off and the monitor does not get in standby mode. But after a system restart, the setting is at off, but the monitor will go in the standby mode.

Any suggestions:confused:

---

