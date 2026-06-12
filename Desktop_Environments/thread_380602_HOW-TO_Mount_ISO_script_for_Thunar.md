---
title: "HOW-TO: Mount ISO script for Thunar"
date: 2007-03-09
forum: Desktop Environments
---

### Post by JasonValdron on 2007-03-09
Hi there,
I just wrote a simple script for Thunar, so that I can mount ISO easily.

First of, you need two dependencies, Xdialog and gksudo, but gksudo, if you are on Ubuntu or Xubuntu you'll have it for sure, not sure about Kubuntu, sorry.

To be sure to have those two dependencies (you probably don't have Xdialog) run this:
```

apt-get install xdialog gksudo

```

And to install the script, I've created an install script :)
```

cd
wget http://www.enter-the-darkness.uni.cc/Thunar/mountiso-0.1.tar.bz2
tar -xf mountiso-*.tar.bz2
cd mountiso-*
chmod +x install.sh
./install.sh
cd ..
rm mountiso-* -r

```

After this, if Thunar is running, close it and open it back, and then check if it works :) If you encounter any error, please let me know of them.

Please tell me your comments!! This is my first Bash script ever, so it won't be perfect ;) But, it works! :)

EDIT:
Wrong forums! Sorry can a moderator move this to Tutorials & Tips please?

---

### Post by aidanr on 2007-03-09
thanks, i was just looking for this very thing

it didn't work straight away, but i got it to work with a couple of changes to /usr/bin/mountiso

```
#!/bin/bash
if [ -d "/mnt/$2/" ]; then
	gksudo umount "/mnt/$2/"
	gksudo [COLOR="Red"]rmdir[/COLOR] "/mnt/$2/"
	Xdialog --title "MountISO" --msgbox "ISO file has been unmounted successfully" 5 60
else
	if [ -e "$1" ]; then
		gksudo mkdir "/mnt/$2/"
		gksudo [COLOR="Red"]"mount -o loop -t iso9660 "$1" "/mnt/$2/""[/COLOR]
		thunar "/mnt/$2/"
	else
		Xdialog --title "MountISO" --msgbox "ISO file '$1' doesn't exist" 5 60
	fi
fi
```

thanks:)

---

### Post by JasonValdron on 2007-03-09
> **aidanr said:**
> thanks, i was just looking for this very thing

it didn't work straight away, but i got it to work with a couple of changes to /usr/bin/mountiso



Thanks for letting me notice that! Because, you see, I run in root (I KNOW I KNOW! lol :P) and I don't use sudo, so I forgot to include it, and I included it at the last minute, and I didn't tested it eheheh. Well it's fixed now! So, if anyone was wondering if the bug is still there (yeahhh anyone :roll: eheheh) it's not :) Should work perfectly!

---

### Post by lapsey on 2007-03-27
great little program!

---

### Post by Ajd on 2007-09-03
Wow, that was painless. Good job.

---

### Post by Mammlouk on 2007-11-14
Thanks!  What a great solution.

---

