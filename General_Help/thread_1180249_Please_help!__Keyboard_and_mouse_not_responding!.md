---
title: "Please help!  Keyboard and mouse not responding!"
date: 2009-06-06
forum: General Help
---

### Post by lariosa42 on 2009-06-06
Hello,

After copying a large number of files to a backup drive using [FONT="Courier New"]rsync[/FONT] (while working in root), I rebooted my computer. The splash screen displayed with no problem, but my computer would not recognize any input from the mouse, keyboard, or touchpad, so I could not log in!

I rebooted in recovery mode, and I was able to use the keyboard. I ran fsck, clean and a few other utilities, but to no avail. Next, I tried booting off the live CD (by using [FONT="Courier New"]startx[/FONT] from the recovery mode root login), but I get the same problem (which seemed strange). I don't think I deleted anything while in root, and I even checked a few .log files for possible overflow, but I don't know what would have caused this.

Please help!  My computer is basically locked up, and I need to run Matlab this weekend for finals week!  Thanks in advance.

---

### Post by ajgreeny on 2009-06-06
> Next, I tried booting off the live CD (by using [FONT=Courier New]startx[/FONT] from the recovery mode root login), but I get the same problem (which seemed strange).I don't understand what you mean by this.  I can see why you might use startx from recovery mode to get a gui, but I do not see what that has to do with a live CD, which runs from the CD itself and does not touch your hard disk, and should also go straight to a gnome desktop with no input from you.

Your problem sounds rather like a hardware problem to me, perhaps could be the motherboard as both periferalls went wrong together.

---

### Post by joezamboni on 2009-06-06
try winbloze

---

### Post by lariosa42 on 2009-06-06
Hello, thanks for the replies. I should mention that I am using a laptop (Dell), and both the keyboard and touchpad are built-in.  The mouse is USB.  None of them work.

I used [FONT="Courier New"]startx[/FONT] to boot the live CD because simply rebooting with the live CD in the drive would send me straight to the installed version.

Obviously the mouse and keyboard are connected: as I mentioned, I can type just fine by pressing [FONT="Courier New"]ESC[/FONT] while the system boots and using the CLI.  This leads me to believe that it is not a hardware problem.

The live CD does not seem to be entirely independent of the hard drive.  As evidence of this, when I boot from the CD, I get some of the same error messages that I usually get when I boot up (for example, I get an error message from the Tomboy that hasn't been working for a month or so, and I haven't gotten around to fixing).

So no luck yet, but I appreciate everyone's help so far!

---

### Post by ajgreeny on 2009-06-06
> **lariosa42 said:**
> Hello, thanks for the replies. I should mention that I am using a laptop (Dell), and both the keyboard and touchpad are built-in.  The mouse is USB.  None of them work.

I used [FONT=Courier New]startx[/FONT] to boot the live CD because simply rebooting with the live CD in the drive would send me straight to the installed version.

Obviously the mouse and keyboard are connected: as I mentioned, I can type just fine by pressing [FONT=Courier New]ESC[/FONT] while the system boots and using the CLI.  This leads me to believe that it is not a hardware problem.

The live CD does not seem to be entirely independent of the hard drive.  As evidence of this, when I boot from the CD, I get some of the same error messages that I usually get when I boot up (for example, I get an error message from the Tomboy that hasn't been working for a month or so, and I haven't gotten around to fixing).

So no luck yet, but I appreciate everyone's help so far!
I still think you are confusing the live CD and the installed version of ubuntu, and I certainly don't understand your comment about startx letting you boot to the live CD.

---

### Post by lariosa42 on 2009-06-06
OK, I don't think the live CD is really the pertinent issue here, but...

When I reboot *without* the live CD in the drive, I get my usual splash-screen, but I can't login due to not being able to type.  When I reboot *with* the live CD in the drive, exactly the same thing happens.  However, when I reboot with the live CD in the drive *and* I hit [FONT="Courier New"]ESC[/FONT] and load recover mode, then open a root terminal, and enter [FONT="Courier New"]startx[/FONT], I do not get a splash screen.  Instead I am presented with a desktop which looks like a fresh boot.  I assumed this meant it was running off the live CD, but maybe it is not.  On this new desktop, I still cannot type or move the mouse.

Regardless, there should be a way to get Ubuntu to recognize input.  Perhaps it doesn't know how to run the devices (i.e., a file needs to be restored), or there is something which is blocking input (such as an overflow somewhere).  

While it would be nice to get the live CD working, I don't think it would really solve the problem, since I already have full access to the CLI (unless my only option is a full system reinstall, which I would like to avoid).

Thanks in advance for any help!

---

### Post by lariosa42 on 2009-06-07
Well, it's been two days, and my computer is still completely stuck.  It would be nice if I didn't have my programming assignment on there that's due next week.

Anyway, I realized that it is not booting off the live CD at all.  [FONT="Courier New"]startx[/FONT] was just booting out of root, which is why it looked different, but behaved the same.  Sorry to give incorrect information on the problem.  Regardless, it seems like a problem with X, not a hardware problem.

That leaves me still stuck: I can't use the keyboard or mouse with X, and I can't boot the live CD (unless there is a CLI way to do this).  This leaves me with trying to find a solution in the terminal.  No luck on that front so far.

---

### Post by ajgreeny on 2009-06-07
If it's a problem with X try booting to recovery mode from the grub menu, which may need you to hit ESC to see, and then when the small menu appears choose xfix, if you can, of course.  That should re-detect the hardware again as is done at installation of the system, and may just allow you to start using your laptop again.

I accept that this may still not be possible if your keyboard will not let you boot to recovery, but I think from your comments that you can use the keyboard in the grub menu, and again in the cli of recovery mode, so I'm hopeful.  If it does not work, I have no idea where you can go from here, other than a re-installation of the system, having first backed up all your personal files using the live CD if necessary.

---

### Post by lariosa42 on 2009-06-07
Thank you for the help.  Unfortunately, [FONT="Courier New"]xfix[/FONT] was one of the first things I tried, and it didn't fix the problem.  I'll keep working on it, but it may be hopeless.

Thanks again for your efforts.

---

