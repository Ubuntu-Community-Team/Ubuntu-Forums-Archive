---
title: "My system seems all messed up, sudo not working..."
date: 2006-05-21
forum: Desktop Environments
---

### Post by seatea on 2006-05-21
My system seems to be all messed up. It started with  my usb flash drive disappearing from my desktop while I was working on  another file. I was able to remount  it by unplugging it and plugging it back in, but I can't write to it now. I can only read what is on it. Curiously, it let me drag a file onto it, but I can't remove it now that it is there. I have tried to chown and chmod many times in attempting to get it to function as before, but it refuses and gives back statement  ":Read-only file system". I noticed in media that there were two folders for the same drive, but the case in their respective file names was different. I do not have and have never had any line in fstab relating  to my usb drive.I tried to remove the one that was not being used because I thought it might be creating  confusion. The rmdir command appeared to work, but when I check with ls, ithe folder is still there. I thought it might help to run fsck, so I created a file /forcefsck and restarted. fsck ran and did not report any problems. Now, I cannot use sudo. I cannot open synaptic, etc. When I type sudo with acommand, I get this message: "sudo: /etc/sudoers is owned by uid 1000, should be 0". I presume that I am uid 1000 and  root is 0. Bizarrely, I can open the sudoers file to edit with gedit without sudo. Here is my sudoers file: 
"# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL".

Does anyone know what may have happened? How can I straighten out this mess?

---

### Post by aysiu on 2006-05-21
Reboot your computer.

Choose **recovery mode**. It's below your usual normal boot option and above "memtest."

You'll be logged in as root. Type ```
chown root:root /etc/sudoers
```

Reboot into normal mode.

---

### Post by seatea on 2006-05-21
Well, either my computer will not boot into recovery mode or I  don't know how to boot into  recovery. When I get to "boot:", I can press escape, I even tried pressing escape before I got to the boot prompt, but that didn't work either; I can type in "help", "rescue", or "recovery", and nothing happens. My computer boots into yaboot and it is supposed to at least give help when "help" is typed in, but all it says is something like "file not found". This has been  a disastrously frustrating week with my Ubuntu system. I am about ready to wipe it off my hard drive and call it quits for Linux. I suppose the next step, not today however, is to start up with a  live cd  and mount my system and chown that way?

Thanks for your input.

---

### Post by jones_jj on 2006-05-21
seatea, have you tried to put the install disk in, and restart your system?  When you do that, it will boot up and you will have the option to install, recovery and help I believe.  You should be able to get into recovery mode and then run the command that aysiu suggested.

Also with your sudoers file, did you add yourself as a user to use sudo?  Where it says:
**root ALL=(ALL) ALL**
add yourself to the sudoers list like:
**<username> ALL=(ALL) ALL**

Basically it kind of looks like you got removed from the sudoers list.

Do you have a Windows machine you could plug your flash drive into?  If so I would do that, and check to make sure you can still access your files.  After you find out it is going to work again, try plugging the flash drive back in your Ubuntu system and everything should work again.

---

### Post by seatea on 2006-05-21
I booted from the live cd because I have had trouble accessing the rescue mode with the  installer and was able to  "chown root:root /etc/sudoers" on my filesystem. I also unmounted my filesystem and ran fsck on it from the live cd and once again it  reported no problems. I am starting  to think  that the  reputation of Linux for stability  and  the value of journaling is something of  a myth. Thankfully,  sudo now works, I still have problems though that were not  there before I did  the reboot with  the /forcefsck file I made. I will not do that again. Besides having corrupted my  usb flash drive, I now have rendered my ability to open programs from System>Administration such as Synaptic or any of  the  other items in that sub-menu useless. When I try to access those programs, they either appear to try to load and then fail, or nothing at all happens after  clicking. I can start Synaptic from Terminal. Any ideas on  where the  problem  might be now?

I can  access a Windows 98SE system to plug my flash drive into. Is plugging it in under Windows, opening a file, then closing  the file, unmounting the drive, unplugging the drive,  and then plugging it back into ubuntu all I need to do to be able to write to the  drive  again?

---

### Post by jones_jj on 2006-05-21
The reason I'm having you check on a Windows machine is to see if the Flash drive is hosed or not.  Was there anything on the drive that was important?  If not and you are able to access it in Windows you may want to try and format the drive again and see if that will help.

What filesystem did you use when you installed Ubuntu?  Did you use ext2 or ext3?

It does sound like something fishy is going on when you plugged in your USB drive and it now messed up a lot of different things.  I'm not totally sure if there is a way to rebuild System->Administration or not.  I will have to look into that.  But you are now able to use sudo?

---

### Post by seatea on 2006-05-21
Yes, I can use sudo now. I can read my Flash Drive ok and I have not lost  any data. I haven't made it yet to plug it in to the  Windows system. I  was so frustrated with trying to fix things  and repeatedly  failing  that I had to take a breather  from working on my  system. I am using ext3 on my system. I tried reinstalling a bunch of core programs, including the  kernel, but that didn't help. It does seem that from the time  I did all those  updates on  Breezy about  3 weeks ago, my system has been troublesome. Which of those updates might have been the culprit, I couldn't  even guess.

---

### Post by seatea on 2006-05-22
I just now plugged  the usb drive into Windows. It has  all the files in it and I can write to it. There is some data loss from a test file on it that I had made under  Linux. I was able to drag the test file onto the  drive under  Linux, this was from my  previous attempts at figuring out my problems with the drive , but I could not remove it  later or edit it. Now the file is empty.

Should I go ahead and format the drive under Windows? Why couldn't the drive be formatted under LInux?

---

### Post by jones_jj on 2006-05-22
You could format it under Linux if you want.  If you are wanting to use it both with Windows and Linux, I would suggest formatting it using FAT/FAT32.  Linux should allow you to format that way.

Do you remember what updates you were installing when your issues were starting to happen?  I wonder if it was a core Ubuntu update, like a kernel update that may not have been stable or something similar to that?

---

### Post by seatea on 2006-05-22
There was a kernel patch (or update) and several library updates in early May. I can't remember them all and I haven't been able to find a log of the updates. I assumed everyone got the same updates. I am running  the powerppc version of Linux so maybe i386 users did not get the  same updates.

When I had the  usb drive connected  to Windows 98SE, I ran scandisk. It took three scans to get to the point where there were no errors on the usb drive. The drive sems to be  working ok  now. I can  read and  write to it. Why was I unable to fix the drive under LInux?

I tried adding a new menu bar, but it behaved the same way. I can access anything in the submenus, unless it is in the  Administration sub-menu. None  of those will start.

---

### Post by jones_jj on 2006-05-23
[QUOTE=seatea]There was a kernel patch (or update) and several library updates in early May. I can't remember them all and I haven't been able to find a log of the updates. I assumed everyone got the same updates. I am running  the powerppc version of Linux so maybe i386 users did not get the  same updates.
[/QUOTE]

That is probably where your problem lies, maybe something in the PPC update for Ubuntu there may have been an issue that you just some how found when you plugged in your USB drive and did something.  May be even a freak thing, who knows really.

> I tried adding a new menu bar, but it behaved the same way.  How is it behaving?  Is it behaving correctly, or is it behaving like System->Admin?

The reason you weren't able to fix the USB drive under Ubuntu may have had something to do with permissons.  Did you have full rights to the drive as a user or were the permissons pointing to root only?

---

### Post by seatea on 2006-05-23
It behaved the same. It listed the programs under System>Administration, but none of the programs would start when clicked. i don'teven get prompted for  a password. I can start synaptic from the  command line, but I do get this message in terminal.

"(synaptic:5646): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed"
 
Any thoughts?

---

