---
title: "cant install?no root??"
date: 2009-03-15
forum: General Help
---

### Post by blaker1994 on 2009-03-15
> No root file system is defined.

Please correct this from the partitioning menu.

I get that message. anyone know y?

---

### Post by taurus on 2009-03-15
Which option did you pick when you were at the partition screen (Step 4 of 7)?

---

### Post by blaker1994 on 2009-03-15
There is no options??

---

### Post by taurus on 2009-03-15
Are you trying to install it from windows (wubi) or are you trying to install it along side with windows, dual booting?  Post a screenshot of that screen.

---

### Post by blaker1994 on 2009-03-15
um, there is  operating system on the harddrive, at least i dont think so.

---

### Post by taurus on 2009-03-15
Can you explain a little more what you were doing when you got that error message with no root filesystem defined (_partitioning men_u)?

Are you trying to install Ubuntu right now or are you partitioning your harddrive?

---

### Post by blaker1994 on 2009-03-15
ok, i put the ubuntu cd into the laptop and selected "install" then i get to step 4 and the screen is blank, let me post a pic

---

### Post by blaker1994 on 2009-03-15
[IMG]http://i671.photobucket.com/albums/vv72/blaker1994_2009/beforeward.png[/IMG] (before i pushed forward)
[IMG]http://i671.photobucket.com/albums/vv72/blaker1994_2009/Screenshot.png[/IMG]

---

### Post by taurus on 2009-03-15
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by blaker1994 on 2009-03-15
nothing happens?

---

### Post by taurus on 2009-03-15
It means that Ubuntu does not detect your harddrive.  Until then, you can't install it because you cannot install Ubuntu into an imaginary drive (none).  Go into the BIOS and perhaps turn on AHCI for your harddrive.

---

### Post by blaker1994 on 2009-03-15
Thanks, but on my laptop the harddrive button lights up, hmm, ill do wat u say :D

---

### Post by blaker1994 on 2009-03-15
oh and how do i get to my bios?

I have a hp compaq nc6000

---

### Post by taurus on 2009-03-15
When you first turn on your laptop, you would see an HP logo and either on the upper right corner or bottom, you would see a quick message telling you what key to press to get into the Setup.  I believe you have to use F2.

---

### Post by blaker1994 on 2009-03-15
k, ill try it and ill let u know

---

### Post by blaker1994 on 2009-03-15
Nothing:( this means i need a new harddrive.. is it possible to run off of ubuntu's cd?

how much space is on the ubuntu live cd? an i make it more?

Sorry for so many ?s

---

### Post by taurus on 2009-03-15
You mean the BIOS doesns't detect your harddrive?

Yes, you can run Ubuntu off the LiveCD although it would be a little slow.  To do a normal install, you need at least 2.5GB and if you plan to install more apps later, you probably need something like 5GB.  If you have 10GB, that should be more than enough unless you plan to download a bunch stuff.

---

### Post by blaker1994 on 2009-03-15
well, i was wondering if i customize the ubuntu cd and only pick the stuff i needed and run it off of that. i could delete stuff that i dont need and use the empty space. how big is the ubuntu live cd?

---

### Post by blaker1994 on 2009-03-15
is it possiblle?

---

### Post by heulenwolf on 2009-04-08
I'm getting the same error.  Did anyone determine a solution?

Here's the sequence that got me here:
Downloaded Wubi (heard about it on the FLOSS Weekly podcast) on a ~5 year old Dell laptop running Windows XP
Defragged HD in Windows
Ran Wubi to install Ubuntu 8.10 as a virtual disk file
Rebooted
Selected Ubuntu from boot menu
Was brought to a grub> prompt, never saw Ubuntu
Rebooted back into Windows
Uninstalled Wubi/Ubuntu
Rebooted
Reinstalled Wubi/Ubuntu using backed up copy of Ubuntu 8.10 ISO
Rebooted
Chose Ubuntu from boot menu
Nifty desktop screen came up (leathery brown background), selected time zone, clicked Next
"Prepare partitions" dialog came up with no partitions shown and all buttons greyed out except for "Quit"
Finally gave up in clicked Quit
Ubuntu came up normally, though I'm logged in not with the account I created in Wubi but as a "Live session user" with username "ubuntu"
Logged out, was unable to log back in with my account settings from Wubi
System automagically logs me in as "ubuntu"

---

