---
title: "Changing Ubuntu boot graphic"
date: 2006-07-21
forum: Desktop Environments
---

### Post by mjpatey on 2006-07-21
Hello, Group-

The Beginner Forum didn't seem to have an answer for this, so I thought I'd try here...

I'm trying to change the graphic that comes up at the very beginning of the Ubuntu boot process.  It's the graphic that has the logo with the word "ubuntu" in brownish-orange, and its reflection below it, on a black screen.  The boot text scrolls by beneath this graphic.

Does anyone know how to change that to a graphic I specify?

Thanks for any help you may have!

-Mark

---

### Post by PhrankDaChickenGeek on 2006-07-21
See this thread: [http://ubuntuforums.org/showthread.php?t=82835](http://ubuntuforums.org/showthread.php?t=82835)

---

### Post by mjpatey on 2006-07-21
Whoah, that looks too complicated for me at this point.  Thanks for the link!  Suddenly I like pixellated, over-compressed graphics more than I ever knew.  :-)

-Mark

---

### Post by ovistanciu on 2006-07-21
hey, it isn't that hard, you just have to follow the steps described there. if something goes wrong, your computer will not be harmed (you'll boot without the splash screen - worst case scenario).

good luck!

---

### Post by Thund3rstruck on 2006-07-21
I've never been able to get that to work. Perhaps I'm not using the correct type of boot screens. I downloaded several from [Gnome-Look.org/splash]("http://www.gnome-look.org/index.php?xcontentmode=160&PHPSESSID=493043b6a9dc17c3d75d01ea7e6c1fa6")
but none of them installed with the method in the howto

---

### Post by bulldog on 2006-07-21
Try this one!
Is very easy to do and it's real nice.
The only thing is that when you get a new kernel,you have to do it again.
But what I said,it's easy and quick to do.

[http://doc.gwos.org/index.php/Serengeti_Usplash_for_Dapper](http://doc.gwos.org/index.php/Serengeti_Usplash_for_Dapper)

---

### Post by Thund3rstruck on 2006-07-22
> Try this one!

I will.. thanks for that

---

### Post by mjpatey on 2006-07-22
I did try the Serengeti bootsplash install, but I can't get it working, and here's why (I think)...

Where it tells you to add "VGA = ___" (insert the number that corresponds to your screen resolution, 794 in my case), it never tells exactly where to insert that line.  Here's the text that confuses me:


[B]5. Add vga= to grub menu.lst file. The script loads menu.lst using gedit and the boot kernel line is toward the end (line 113 on my computer).

vga = 785 for standard vga
vga = 788 for 800x600
vga = 791 for 1024x768 *
vga = 794 for 1280x1024 [/B]

I have no experience doing this, so I ended up putting the exact words "vga = 794" in several places, but none of them worked.

Does anyone know where to put that line?

-Mark

---

### Post by mjpatey on 2006-07-22
By the way, just a secondary question... when adding the "VGA" line to menu.lst, I saved the original version of the file as "menu.lst.20060721" (or something like that) so I'd have a backup.

After not being able to make the process work, I opened the original file and re-saved it as "menu.lst" (to replace the changed version with the original) and on reboot, for some reason my system didn't revert to the original boot graphic.

I'm just curious why reverting to the original menu.lst wouldn't restore the old boot graphic?

---

### Post by PhrankDaChickenGeek on 2006-07-22
> **mjpatey said:**
> By the way, just a secondary question... when adding the "VGA" line to menu.lst, I saved the original version of the file as "menu.lst.20060721" (or something like that) so I'd have a backup.

After not being able to make the process work, I opened the original file and re-saved it as "menu.lst" (to replace the changed version with the original) and on reboot, for some reason my system didn't revert to the original boot graphic.

I'm just curious why reverting to the original menu.lst wouldn't restore the old boot graphic?

Menu.lst file only holds infromation for booting operating systems, not the splash image location. Find the line that looks something simaliar to this and add the vga= here:

```

title		Ubuntu, kernel 2.6.15-26-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/sda2 ro quiet splash **vga=794**

```

---

### Post by mjpatey on 2006-07-22
Thanks, Phrank!  I'll check that out.

Regarding my previous post (not knowing where to put the "vga=794" line), I finally found it in the post's example.  Sometimes I just need a good whack upside the head :-)

However, when I put "vga=974" in the proper place, on reboot, I got a message on screen that said "Analog1: Cannot display this video mode."  (I assume this was a message from my monitor.)

So, on a hunch, I changed it to "vga=791" (not my native resolution, but worth a try).  I got the Serengeti bootsplash!  And then I got a message that my "xorg.conf" file was bad, and it eventually dumped out to shell mode.

So 794 causes my monitor to go poopy, and 791 ruins my chances of having a GUI.

Does this mean I have some weird situation in which the Serengeti Bootsplash just won't work?

-Mark

---

### Post by bulldog on 2006-07-22
> **mjpatey said:**
> I did try the Serengeti bootsplash install, but I can't get it working, and here's why (I think)...

Where it tells you to add "VGA = ___" (insert the number that corresponds to your screen resolution, 794 in my case), it never tells exactly where to insert that line.  Here's the text that confuses me:


[B]5. Add vga= to grub menu.lst file. The script loads menu.lst using gedit and the boot kernel line is toward the end (line 113 on my computer).

vga = 785 for standard vga
vga = 788 for 800x600
vga = 791 for 1024x768 *
vga = 794 for 1280x1024 [/B]

I have no experience doing this, so I ended up putting the exact words "vga = 794" in several places, but none of them worked.

Does anyone know where to put that line?

-Mark

It's not so hard to find out where to put vga=794.
Type in console uname -r and see which kernel you use.
Find in your grub menu.lst the line with the same number [not the recovery] and put at the and of the line vga=794.
That should do the tric.
Should also tell you that all the lines with # before it in your grub menu.lst,not been displayed on your screen.
The line you are looking for has no # in front of it and is usual near the end of your list.

About your 794 error,try 792.

---

### Post by PhrankDaChickenGeek on 2006-07-22
> **mjpatey said:**
> Thanks, Phrank!  I'll check that out.

Regarding my previous post (not knowing where to put the "vga=794" line), I finally found it in the post's example.  Sometimes I just need a good whack upside the head :-)

However, when I put "vga=974" in the proper place, on reboot, I got a message on screen that said "Analog1: Cannot display this video mode."  (I assume this was a message from my monitor.)

So, on a hunch, I changed it to "vga=791" (not my native resolution, but worth a try).  I got the Serengeti bootsplash!  And then I got a message that my "xorg.conf" file was bad, and it eventually dumped out to shell mode.

So 794 causes my monitor to go poopy, and 791 ruins my chances of having a GUI.

Does this mean I have some weird situation in which the Serengeti Bootsplash just won't work?

-Mark

No, it the Serengeti Bootsplash should work on any screen. 
The "vga=" option sets the resolution for the bootup splash only. Try setting it to "vga=785", as this should work on any monitor.

As for your borked xorg.conf file, try running this command to reconfigure it:
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by mjpatey on 2006-07-22
Phrank-

I just tried vga=785, and it caused the same xorg.conf error.  I think I'll try your suggestion to reconfigure xorg.conf.  Will all my settings be overwritten when I do that?

By the way, in order to revert to my previous menu.lst file, I've been doing:

sudo cp menu.lst.20060722 menu.lst

...is that the best way to do it?

Thanks for all the incredibly helpful info!

-Mark

---

### Post by PhrankDaChickenGeek on 2006-07-22
> **mjpatey said:**
> Phrank-

I just tried vga=785, and it caused the same xorg.conf error.  I think I'll try your suggestion to reconfigure xorg.conf.  Will all my settings be overwritten when I do that?

By the way, in order to revert to my previous menu.lst file, I've been doing:

sudo cp menu.lst.20060722 menu.lst

...is that the best way to do it?

Thanks for all the incredibly helpful info!

-Mark

Yes, the reconfigure will overwrite your xorg.conf. You can always make a backup of your xorg.conf file:
```

sudo cp /etc/X11/xorg.conf xorg.conf.20060722

```

As seen from the above command, I'd say that you're backing up the menu.lst just fine! :)

---

### Post by autocrosser on 2006-07-23
Also to change back to the original bootsplash, just rerun the 
inst.serengeti.sh & select option #1.

It would be possible to have another bootsplash (in .so format) & have the script install it--you just need to change every instance of "serengeti" to the splash you want to use.

---

