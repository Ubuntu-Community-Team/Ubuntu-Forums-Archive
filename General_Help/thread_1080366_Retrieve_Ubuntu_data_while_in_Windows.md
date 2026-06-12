---
title: "Retrieve Ubuntu data while in Windows"
date: 2009-02-25
forum: General Help
---

### Post by BillPgh on 2009-02-25
My son had a hard drive and/or boot problem, and received a new HD from Dell. I have his old HD installed in a machine, and want to retrieve his data, but of course Windows does not recognize the partition. 

Any hints as to how I can do that? I would rather not install Ubuntu on the machine, mainly because I don't have the time to install/uninstall, fix mbr on theis brand new machine that I want to put in production at my company tomorrow.

Thanks

---

### Post by wolfen69 on 2009-02-25
use a live cd and copy the files over to a flash drive.

---

### Post by sedawk on 2009-02-25
First choice really is to use the LiveCD.

Second choice is to install a driver on Windows that
can read ext2/ext3 partitions.
I've installed one on XP that seems to work.
I think it is this one:
[http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by BillPgh on 2009-02-25
Thanks for the quick replies! The "Live CD"---How do I get it? And will it allow me to read, transfer files, etc, without installing Ubuntu?

---

### Post by BillPgh on 2009-02-25
Hey, that was dumb of me--I am downloading it now, but what will the process  consist of, if all I want is to recover those files?

---

### Post by jaminux on 2009-02-25
1) Write the live iso to cd. In Ubuntu just right click and select write to disc. In Windows download the program ISO recorder (google it), install it and choose some option like write to disc (forgot the exact name).

2) Once the cd is written, go into the bios (menu when you start the computer, get it by pressing esc or f1 or some other key) and make sure that the live cd is the first device to boot (i.e. boot order).

3) Restart, shove the cd and wait for it to load. Choose Try Ubuntu without making any changes to your computer

4) this loads up the desktop in a minute or two

5) Press alt+f2 on the desktop and type nautilus

6) In the pane on the left side of the screen are some devices and locations. Pick the one for your ubuntu partition and click on it. Browse to your son's files... probably /home/son's name. 

7) Open a new tab in nautilus (file menu)

8) Plug in your removable media and wait for it to appear in the pane on the left side of the screen and open it.

9) Copy the files from the first tab into the second tab. Make sure you only copy the visible ones as there can sometimes be a huge amount of data that is hidden and unnecessary.

10) Shut off the computer, everything should now be on the removable media.

---

### Post by kahlil88 on 2009-02-25
You could also copy the files to the Windows partition from the Live CD if you don't have a thumb drive, or if there are very large files. Both partitions should appear in the Places menu. You said that Dell sent your son a new hard drive.....I hope the old one isn't dead?

---

### Post by BillPgh on 2009-02-25
First, that was an excellent decription of the process. Thank you ver much.

I chose to download the drivers, before that reply came across, and have moved most of the files across. I had to drill down quite a bit, since he had colons in some names that Windows didn't care for, and move those folders move surgically. 

I am a network admin for a medium-large business, and hate to come across as a newbie, but I didn't want to go too far down a blind path. I wasn't sure if it would require a "within Windows" install that might not see the partition anyway. I will be able to set up a method for him to access the files from my servers now.

Again, I really appreciate the help.

---

