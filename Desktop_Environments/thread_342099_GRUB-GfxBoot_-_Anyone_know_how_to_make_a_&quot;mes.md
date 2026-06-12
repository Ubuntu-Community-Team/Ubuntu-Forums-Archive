---
title: "GRUB-GfxBoot - Anyone know how to make a &quot;message.&lt;&gt;&quot; file?"
date: 2007-01-19
forum: Desktop Environments
---

### Post by t_anjan on 2007-01-19
I have got Grub-GfxBoot installed and working properly. 

But, I can't seem to find any kind of info as to how to use GfxBoot to make my own themes. Actually, I don't want to make a theme from scratch, I just want to edit an existing boot graphics message.<> file. The original message file uses a "pcx" image. I want it to use a "jpg" file (as the "pcx" is too big).

I have the original message file's source, but I don't know how to compile it to produce a new message file.

I managed to find a guide in German, but Google's Translate wasn't of much help......
[http://www.andreas-loibl.de/content/linux/tutorials/grub-gfxboot/index.html](http://www.andreas-loibl.de/content/linux/tutorials/grub-gfxboot/index.html)

Can anyone help?

---

### Post by unluckyluke on 2007-07-10
It's very easy: simply open gnome-terminal or konsole, or whatever is your preferred terminal application and then give the following commands:

cd the_directory_containing_your_boot_splash_files/
ls .|cpio -o > message.new

.
You'll find the CPIO archive in the_directory_containing_your_boot_splash_files.

Bye!

---

### Post by Morton's Red Stapler on 2008-01-03
> **unluckyluke said:**
> It's very easy: simply open gnome-terminal or konsole, or whatever is your preferred terminal application and then give the following commands:

cd the_directory_containing_your_boot_splash_files/
ls .|cpio -o > message.new

.
You'll find the CPIO archive in the_directory_containing_your_boot_splash_files.

Bye!

wow, that was no help at all

---

### Post by chewearn on 2008-01-03
There is one method:

1. take existing message.suse
2. extract it using cpio -i
3. replace the background file
4. then archive it again using cpio -o

Instructions are buried inside this very long thread:
[http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)

Or maybe there are better instruction somewhere else; I'm still looking...

---

