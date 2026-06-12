---
title: "desktop shrunk and I can't restore to full screen!!"
date: 2008-08-31
forum: Desktop Environments
---

### Post by apdc on 2008-08-31
Hello there. I am still learning Linux and while I was using my laptop with a 10" screen, my desktop shrunk about an inch on all four sides. I tried to play with the resolution but no help!!

Can someone tell me how top restore it...????

---

### Post by randcoop on 2008-08-31
When you right-click on the desktop, you'll get a menu that includes the Desktop Settings.  Select that.  In the window, you'll see image style and a pull-down menu for stretched, full, etc.  Play with those and you should get a full desktop screen.

---

### Post by apdc on 2008-09-01
Thanks very much for responding.  I tried your suggestion but there are no changes regardless of my choices. I have noticed that when I reboot, the very first image with "XUBUNTU" and the progress bar, it appears that is on full screen.

Any other suggestions??????

Thanks

---

### Post by randcoop on 2008-09-01
It sounds like you may have inadvertently altered your xorg.conf file, which is the configuration file for displays, monitors, mouse, keyboard, etc.  

You can try running a program that will walk you through reconfiguring your xorg.conf file.  Before you do, you should make a backup of your current file.  Use the command ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Now, you can run the command ```
sudo dpkg-reconfigure xserver-xorg
```

That will walk you through a reconfiguration that might restore you to the status quo ante. 

If for any reason the result is worse instead of better, you can simply copy the backup you made back to the original and re-start xserver.  To put the copy back, the command is ```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by apdc on 2008-09-01
Super thanks!!!!

I tried waht you suggested and went through the process well.  However, all the questions and prompts were about the keyboard layout and the not the screen or video layout.  So at the end of the porocess there is no change!

Is there a similar command for the video layout??

---

### Post by little cazy on 2008-09-01
At the beginning it should be all that junk, (it get's better as u go on) did u complete the whole thing?

---

### Post by apdc on 2008-09-01
I rebooted and it now is restored.  Super thanks, very much appreciated!!!

---

### Post by randcoop on 2008-09-01
Please mark this thread SOLVED.  Others who search with similar problems will more easily find the solutions to their problems.

---

