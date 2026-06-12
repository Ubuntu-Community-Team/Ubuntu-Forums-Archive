---
title: "Cannot suspend or hibernate"
date: 2009-04-28
forum: General Help
---

### Post by Happy_Man on 2009-04-28
Hello, everybody.

I'm on a Dell Dimension 8250 tower running Jaunty, and I cannot for the life of me get the computer to return from a hibernate or standby mode. It will go into hibernate or standby with no problems (as least as far as I can tell), but it will not recover, and I'm clueless as to why or as to how to find out why. 

I've got:
Pentium 4 2.4 GHz
1 GB RDRAM
128 MB Nvidia Geforce FX 5200

Any help with this would be greatly appreciated.

---

### Post by ubockto on 2009-04-28
Probably need a bios update, don't quote me though

---

### Post by Happy_Man on 2009-04-30
Updating to the latest BIOS didn't help. Any other ideas, guys?

---

### Post by ubockto on 2009-05-01
Did this work with other versions of Ubuntu?

---

### Post by kerry_s on 2009-05-01
make sure your bios power setting is set to s3 not s1.

---

### Post by Happy_Man on 2009-05-01
> **kerry_s said:**
> make sure your bios power setting is set to s3 not s1.
Well, I could suspend and hibernate in Windows. Does Windows ignore this setting?

---

### Post by Yashiro on 2009-05-01
Hibernate and standby on desktop systems in Linux is broken and has been broken for years. It's a combination of many things. 
Kernel issues, bios, drivers, bad init scripts and daemons and so on.

If the machine can't Hibernate after a clean install with no 3rd party drivers installed then chances are it never will. With alot of forum scanning and googling you may find the answer but most people just assume it's a lost cause.

---

### Post by Happy_Man on 2009-05-01
> **Yashiro said:**
> Hibernate and standby on desktop systems in Linux is broken and has been broken for years. It's a combination of many things. 
Kernel issues, bios, drivers, bad init scripts and daemons and so on.

If the machine can't Hibernate after a clean install with no 3rd party drivers installed then chances are it never will. With alot of forum scanning and googling you may find the answer but most people just assume it's a lost cause.
Then how come Windows can do it with no problems at all? I'm not being petulant here, I'm genuinely curious.

---

### Post by kerry_s on 2009-05-01
> **Yashiro said:**
> Hibernate and standby on desktop systems in Linux is broken and has been broken for years. It's a combination of many things. 
Kernel issues, bios, drivers, bad init scripts and daemons and so on.

If the machine can't Hibernate after a clean install with no 3rd party drivers installed then chances are it never will. With alot of forum scanning and googling you may find the answer but most people just assume it's a lost cause.

that's just bull, there are 3 desktop computers in my house and we always suspend, there never shutdown, and there set to power button wakeup. when you hit the power button it looks like a instant on system.

Happy_Man, most of the time it's a bios setup, linux try's to use the bios if it can. you also need to be running the proper display drivers for your vid card.

---

### Post by Yashiro on 2009-05-01
> that's just bull, there are 3 desktop computers in my house and we always suspend, there never shutdown, and there set to power button wakeup. when you hit the power button it looks like a instant on system. And I have about 10 machines all of varying specs that do not work 100%. (from a hibernate perspective) 
Like I said, it can work, but if it doesn't out of the box then you are usually stuffed.

---

### Post by kerry_s on 2009-05-01
> **Yashiro said:**
> And I have about 10 machines all of varying specs that do not work 100%. (from a hibernate perspective) 
Like I said, it can work, but if it doesn't out of the box then you are usually stuffed.

sometimes you just got to work at it. :lolflag:
for example: this desktop i'm on now has been a pain, but it's cobbled together from spare parts, doesn't even have a proper power button, i'm using a diy momentary switch. :)
it took me days to figure out how to get it to suspend right, biggest problem was the wake up would not turn on the display, i finally turned off the vga setting in the bios and bingo, it lives. also i've changed to using uswsusp(s2ram) which is faster and more dependable. i disabled the standard suspend/hibernate and created a launcher. suspend works 99% of the time, every once in a while it won't wake up.

i don't use hibernate it's to slow.

---

### Post by Happy_Man on 2009-05-01
You have hit on my problem exactly! I can hear everything start up, it's just that my monitor never comes on. 

So I went into my BIOS and tried to find a VGA setting. No dice. It simply wasn't there. 

Also, my setting is at S3, so that's not it.

Ummm... what else... oh, yeah, my display drivers are the recommended for my card. 

Any other things I should check?

EDIT: I found [http://en.opensuse.org/S2ram#s2ram_-_Getting_suspend_to_RAM_to_work_out_of_the_box](http://en.opensuse.org/S2ram#s2ram_-_Getting_suspend_to_RAM_to_work_out_of_the_box), which seems to be a pretty comprehensive guide. And, more importantly, it tells me to pass vga=0 to the kernel. How exactly do I go about passing that?

EDIT 2: Found a package called hibernate that installed uswsusp along with it. Will muck around with it, see if it helps.

---

### Post by TiredBird on 2009-05-09
> **kerry_s said:**
> make sure your bios power setting is set to s3 not s1.
I did that but nothing changed that I could detect. CLI 'pm-suspend' and 'pm-hibernate' work fine and the resume from suspended or hibernated states seems okay. However, my GUI is not giving me the option to suspend or hibernate. Also, when I do get it to work by using the CLI, I can't resume by mouse movement or keystroke, although that does bring it back to life from a full shutdown.

---

### Post by AndThenWhat on 2009-05-09
[http://ubuntuforums.org/showthread.php?t=533924](http://ubuntuforums.org/showthread.php?t=533924)

^^ that talks about passing parameters to the kernel. hope it helps.

---

### Post by unutbu on 2009-05-09
TiredBird, to enable hibernate/suspend from the GUI, run

```

gconf-editor

```

Enable /apps/gnome-power-manager/general/can_hibernate
Enable /apps/gnome-power-manager/general/can_suspend

Logout, then log back in.

The option to hibernate and suspend should be available when you click the icon in the
upper right-hand corner of the gnome panel.

---

### Post by TiredBird on 2009-05-09
> **unutbu said:**
> e
The option to hibernate and suspend should be available when you click the icon in the
upper right-hand corner of the gnome panel.

I did not have to change the referenced settings as they were already checked. I did however, do a complete shutdown and restart just to make sure I hadn't overlooked something. Alas, no joy. It still didn't work.

My desktop environment is heavily modified from the install version. Among other things I am using the 'Main Menu' applet and the 'Shut Down' applet. Both *usually* give me choices of 'Shut Down' and 'Restart'. I say *usually* because sometimes the menu does show the hibernate and suspend options. Unfortunately, I can't figure out why it works occassionally but not always.

One bit of progress that I have made is that I can now resume from a mouse movement or key stroke, (assuming I was able to suspend or hibernate in the first place.) ```
echo PS2K > /proc/apci/wakeup
``` The preceding, which I learned about in another thread, fixes that problem for the current login. I am adding that line to one of my startup scripts to make it persistent.

Thanks for your efforts!

---

### Post by TiredBird on 2009-05-10
My problems related to suspend and hibernate have been solved thanks to the posts in these threads: [http://ubuntuforums.org/showthread.php?t=1144999]("http://ubuntuforums.org/showthread.php?t=1144999.") and [http://ubuntuforums.org/showthread.php?t=814939]("http://ubuntuforums.org/showthread.php?t=814939").

---

