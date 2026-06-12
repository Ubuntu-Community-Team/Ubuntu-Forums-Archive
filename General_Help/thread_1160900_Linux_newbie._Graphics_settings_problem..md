---
title: "Linux newbie. Graphics settings problem."
date: 2009-05-16
forum: General Help
---

### Post by Sandalphon on 2009-05-16
First, off let me first say that I'm glad that Ubuntu has what appears to be a good forum with lots of help topics. It's nice to have somewhere to go to for a change. Secondly, I need to apologize for not properly searching for a relevant forum section for this problem, or searching if the problem already exists, which I know is a big forum taboo. The reason I haven't is because I'm booting from the demo of the Live CD for reasons I'll explain in  a minute and for some reason, my computer likes to make a habit of freezing when running in the demo, so I'm hoping to get this problem typed up and posted, before it freezes again :(

Anyway, I'll cut to the chase. I'm still new to this stuff and I know next to nothing about Linux, but I was slowly starting to learn. To make a long story short, I got brave/stupid and ended up accidentally changing something in my graphics settings (namely the /etc/X11/xorg.conf section) only to find that when I restarted the computer, everything was scrambled. 

So I decided to try and use the demo on the Live CD, which obviously worked, since I'm on this forum :P . So is there anyway I can reset the graphics settings so that they work, in the same way they do on the Live CD demo. I would reinstall Ubuntu, but I don't want ti lose everything that I've got stored on my PC. 

Failing a solution, is there a way to back up my files onto an external hard drive, since up to now I've not been able to access them since I can't boot Ubuntu outside of the Live CD demo.

Thanks for any help you guys can provide anyway. And sorry again for rushing to get this question posted. I hope it's not too annoying. Forgive my newb-ness.

---

### Post by chellrose on 2009-05-16
The easiest option is probably this: Try renaming that file (assuming you don't mind restarting with a default).  Boot in recovery mode, select the option "drop to root shell" (or something similar), and in the shell type

```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```

Then reboot into normal mode, which *should* restart your X server and generate a new version of that file.

If that doesn't work...

Do you remember what you changed in /etc/X11/xorg.conf?  If so, you can boot in recovery mode, select the option "drop to root shell", and edit the file:

```

pico /etc/X11/xorg.conf

```

(Ctrl+X to save the file and exit.)

You can then reboot by typing the command "reboot", and that should fix everything.

Alternatively, check here: [http://ubuntuforums.org/showthread.php?t=1140945&highlight=%2Fetc%2FX11%2Fxorg.conf](http://ubuntuforums.org/showthread.php?t=1140945&highlight=%2Fetc%2FX11%2Fxorg.conf)

---

### Post by CatKiller on 2009-05-16
Did you make a backup of your xorg.conf before you changed it? You should be able to restore your backup from the recovery mode that Sissy13 suggests with cp /etc/X11/xorg.conf.whatever-you-named-your-backup /etc/X11/xorg.conf. Some text editors automatically create a backup of an edited file by appending a ~ to the filename; in this case the backup would be xorg.conf~.

In recent versions of Ubuntu there is an option to "fix X" in a menu for the recovery mode. This will run dpkg-reconfigure xserver-xorg. That might help you if you don't have a backup and can't remember the changes you made to undo them.

Even when X doesn't display properly, you should still be able to use Ctrl-Alt-F1 to get into a virtual console which will let you log into a text-based session.

For your other question; it's certainly possible to use the live cd to back up your existing data, but you shouldn't need to in this case, and since you're having stability problems from the live cd it would probably be a bit frustrating anyway.

---

### Post by Sandalphon on 2009-05-16
I tried all these solutions, and none of them worked :( . Looks like it's time to resort to backing everything up. You say it can be done with the Live CD? So far I've been unable to access my hard drive and my external drive won't mount properly. I assume it's done outside of the demo?

---

### Post by XCan on 2009-05-16
> **Sissy13 said:**
> The easiest option is probably this: Try renaming that file (assuming you don't mind restarting with a default).  Boot in recovery mode, select the option "drop to root shell" (or something similar), and in the shell type

```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```

Then reboot into normal mode, which *should* restart your X server and generate a new version of that file.


If the purpose of this was to force X to create a fresh xorg shouldn't the command be
```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
``` ?

---

### Post by chellrose on 2009-05-16
XCan:  You're absolutely right!  I can't believe I did that.  ](*,)
It was late at night, you know?

Sandalphon:  As XCan mentioned, you should do this:

 Boot in recovery mode, select the option "drop to root shell" (or something similar), and in the shell type

```

mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```

Then reboot your machine.  THAT should cause X to create a new version of that file.  I apologize for the error the first time.

---

### Post by Legace on 2009-05-16
Or, you could boot into the Live CD, copy the xorg.conf from the Live CD file system (located in /etc/X11) and then move it into the Ubuntu filesystem.

---

### Post by Sandalphon on 2009-05-16
> **Sissy13 said:**
> XCan:  You're absolutely right!  I can't believe I did that.  ](*,)
It was late at night, you know?

Sandalphon:  As XCan mentioned, you should do this:

 Boot in recovery mode, select the option "drop to root shell" (or something similar), and in the shell type

```

mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```Then reboot your machine.  THAT should cause X to create a new version of that file.  I apologize for the error the first time.

Still didn't work. :( Thanks anyway though. 

[QUOTE=Legace]Or, you could boot into the Live CD, copy the xorg.conf from the Live CD file system (located in /etc/X11) and then move it into the Ubuntu filesystem.[/QUOTE]

Where is the 'Ubuntu filesystem' located. Sorry. :tongue:

---

### Post by chellrose on 2009-05-16
> **Sandalphon said:**
> Where is the 'Ubuntu filesystem' located. Sorry. :tongue:

The "Ubuntu filesystem" would be the file system on your local Ubuntu installation, i.e., the hard drive (not the live CD).

Do you have a USB stick, and does the computer recognize it in Live CD mode?  (It should).  If so, boot from the live CD and copy /etc/X11/xorg.conf from the live CD to your USB stick.  Unmount the stick but leave it plugged in.  Then, reboot into your local (hard drive) Ubuntu installation, in recovery mode.  Select "drop to root shell" again.  It should have recognized your USB stick on boot.  You can copy the file to the hard drive via

```
cp /media/disk/xorg.conf /etc/X11/xorg.conf
```

If that doesn't work... worst-case scenario you can print a hard copy of the file from the CD and enter it in by hand.

---

