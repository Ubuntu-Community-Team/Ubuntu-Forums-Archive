---
title: "Change The TTY Font Size"
date: 2006-01-28
forum: Desktop Environments
---

### Post by navilon on 2006-01-28
Is it possible to change the size of the font when you are in console mode? (not x)

---

### Post by nrwilk on 2006-01-28
I'm pretty sure that it isn't possible.

---

### Post by steve.horsley on 2006-01-29
I think you can set it at boot-up by appending a vga setting to the kernel definition line in grub, like this:

kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda6 ro quiet splash vga=771

However, I can't remember the proper numbers for the vga modes, and I'm not even sure if 771 in the example above is valid.

---

### Post by simosx on 2006-01-29
I think that vga=list will prompt you at boot time to choose from a list.
If you install the linux kernel source, there is documentation on this under
/usr/src/linux/Documentation/

---

### Post by navilon on 2006-02-02
Thanks ill give it a try.

> I'm pretty sure that it isn't possible.

If you pop in a knoppix live CD you'll see that it is possible. When linux is booting up the text is much smaller.;)

---

### Post by jchau on 2006-02-24
> I think that vga=list will prompt you at boot time to choose from a list.
If you install the linux kernel source, there is documentation on this under
/usr/src/linux/Documentation/

I have that folder, but I'm having trouble finding the doc.  Can you give a specific filename?

---

### Post by 5-HT on 2006-02-24
[QUOTE=jchau]I have that folder, but I'm having trouble finding the doc.  Can you give a specific filename?[/QUOTE]

Hi, I'm not sure if these are what you're looking for, but the Gentoo Wiki mentions these files:
/usr/src/linux/Documentation/fb/vesafb.txt
/usr/src/linux/Documentation/svga.txt 

It it's not in these, maybe they reference what you're looking for?

Here's a table for some of the modes though:
```
      |640x480|800x600|1024x768|1280x1024|1600x1200|
------|-------|-------|--------|---------|---------|
 8 bit|  769  |  771  |  773   |  775    |  796    |
15 bit|  784  |  787  |  790   |  793    |  797    |
16 bit|  785  |  788  |  791   |  794    |  798    |
24 bit|  786  |  789  |  792   |  795    |  799    |
 
```

Hope that helps.

---

### Post by staack2 on 2007-02-14
try this:

```
consolechars -f default8x9
```

---

### Post by hearty on 2007-09-12
```
root@hertz:/usr/share/consolefonts# consolechars -d
Cannot find a default font file.

```

---

### Post by RedSquirrel on 2007-09-12
steve.horsley's suggestion above works with **vga=791**.

---

### Post by jw5801 on 2007-10-01
I know this thread is a couple of weeks old, but oh well! The tty font size setting is what I was looking for. A similar question, is there a way to add a background image to tty1? I know there is because I ran an OpenSuse LiveCD the other day, and the default has an OpenSuse type background on tty1 (not on 2-6 though), which made me curious about how it would be done. It does make running through boot scripts with no splash image look mighty fancy though.

---

### Post by Odin25 on 2007-11-21
First of thanks you already discussed this thing and it got me started

> 
Here's a table for some of the modes though:
```
      |640x480|800x600|1024x768|1280x1024|1600x1200|
------|-------|-------|--------|---------|---------|
 8 bit|  769  |  771  |  773   |  775    |  796    |
15 bit|  784  |  787  |  790   |  793    |  797    |
16 bit|  785  |  788  |  791   |  794    |  798    |
24 bit|  786  |  789  |  792   |  795    |  799    |
 
```


In my case those codes didn't work: I found out by passing "vga=790" in grub, then while booting it complained, but I got the chance to type "scan" 
so I found out that my monitor supports 132x50 with the code 0x164 so I typed "vga=0x164" in the grub script and it worked for the first line of booting and 
than it switched back to 132x25.

so I had to change the fonts also.

How could I make this permanent (where to put the command "consolefont -f ..."
And where can I find a font 9 or 10  high I have 8,14,16 and is there a description what the font-names mean I now just took LAT2-VGA8 

BTW: it seems I dont have a framebuffer (maybe because I use a server setup without Xwin

Have a nice Day

---

