---
title: "fstab and the magic invisible nfs mounts."
date: 2007-04-27
forum: Desktop Environments
---

### Post by rcrook on 2007-04-27
HI all...

Just a note on a peculiarity I found with fstab.

Two weeks ago I went to convert my network from Version 3 of nfs to Version 4. I don't have a big network here at home but I use nfs for file sharing in it. As I opened the fstab on the first machine I thought to myself *what a mess!*. So I proceeded to clean it up. format it into a easily readable file. Despite the use of the horrid UUIDs for devices I managed to get it looking pretty good. I then modified it to mount the new nfs4 shares off my other boxen.

Once I had that done I moved on to the other machines and in short order I manage to have them all running nfs4 and working well. 

UNTIL.... I rebooted my laptop. none of the new nfs4 mounts worked on boot. NO auto mount at boot. Manual mount? No problems, mount -a -t nfs4 worked a charm. I spent a few minutes sniffing about, then got sidetracked to mourn the loss of inittab in an appropriate manner. Then after 3 glasses of mourning wine lost interest.

Well today I decided to get back to the mystical non boot mounting file systems. After a bit of convoluted spaghetti script following and a number of dead ends I found where the nfs mounts are supposed to be done during boot. 

/etc/network/if-up.d/mountnfs  

I looked at if and at my fstab.. looked at them both again, and again, and again.... Then it clicked. 

SPACES...... It was the SPACES.

Sure enough when I cleaned my fstab files up I did as any good scripter is supposed to do, I used spaces to delimit the fields. Silly me, what was I thinking... why was I doing something that sysadmins have been doing for over 30 years now, using spaces in the fstab.. 

I changed the spaces in the fstab with tabs and reboot and sure enough all the nfs mounts where there when the system finished booting. 

Now I must admit, My style of scripting is fairly basic and in long form so when I go back to read it 12 months later I can actually understand what I wrote. But when I looked and the mountnfs script it took me a bit to figure out what the hell was going on.... Even then I am guessing. I really don't quite understand why tabs vs. spaces makes a difference with it. 

mount -a reads the fstab ok with spaces so does the other scripts that mount the local file systems. But for the life of me I don't know why mountnfs wont read it properly when I use spaced in the fstab.

If someone could possibly tell me why I am forced to use tabs instead of spaces I would be appreciative. 

Randall.

---

