---
title: "Font antialiasing problem :("
date: 2008-08-16
forum: Desktop Environments
---

### Post by [CPR]-AL.exe on 2008-08-16
Hello. 

Got a very huge problem with fonts. I tried to install mac fonts, using the manual [http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23) and found out, that they have no cyrillic support. So, I tried to revert to ubuntu's original Sans and Serif fonts... but they don't have any antialiasing now :( 

Please, help me to do something with that. Other fonts do have antiailising enabled.

---

### Post by benerivo on 2008-08-17
You could try```
sudo dpkg-reconfigure fontconfig
```then log out, press Ctrl+Alt+Backspace, then log back in.

---

### Post by [CPR]-AL.exe on 2008-08-17
Unfortunately, that didn't help...

Though, this command geneated some errors, i can post them here:

```

alexe@mainframe:~$ sudo dpkg-reconfigure fontconfig
Cleaning up font configuration of fontconfig...
Cleaning up category cid..
Cleaning up category truetype..
aCleaning up category type1..
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-indic-fonts-core /usr/share/fonts/truetype/thai /usr/share/fonts/truetype/ttf-bitstream-vera /usr/share/fonts/truetype/ttf-lao /usr/share/fonts/truetype/unfonts /usr/share/fonts/truetype/ttf-arabeyes /usr/share/fonts/truetype/ttf-dejavu /usr/share/fonts/truetype/freefont /usr/share/fonts/truetype/arphic /usr/share/fonts/truetype/ttf-malayalam-fonts /usr/share/fonts/truetype/kochi /usr/share/fonts/type1/gsfonts /usr/share/fonts/truetype/msttcorefonts
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
Fontconfig warning: "local.conf", line 586: saw number, expected matrix
Fontconfig warning: "local.conf", line 586: saw number, expected matrix
Fontconfig warning: "local.conf", line 586: saw number, expected matrix
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
Fontconfig warning: "local.conf", line 586: saw number, expected matrix
Fontconfig warning: "local.conf", line 586: saw number, expected matrix
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-indic-fonts-core /usr/share/fonts/truetype/thai /usr/share/fonts/truetype/ttf-bitstream-vera /usr/share/fonts/truetype/ttf-lao /usr/share/fonts/truetype/unfonts /usr/share/fonts/truetype/ttf-arabeyes /usr/share/fonts/truetype/ttf-dejavu /usr/share/fonts/truetype/freefont /usr/share/fonts/truetype/arphic /usr/share/fonts/truetype/ttf-malayalam-fonts /usr/share/fonts/truetype/kochi /usr/share/fonts/type1/gsfonts /usr/share/fonts/truetype/msttcorefonts
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
Fontconfig warning: "local.conf", line 586: saw number, expected matrix
Fontconfig warning: "local.conf", line 586: saw number, expected matrix
Fontconfig warning: "local.conf", line 586: saw number, expected matrix
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
Fontconfig warning: "local.conf", line 586: saw number, expected matrix
Fontconfig warning: "local.conf", line 586: saw number, expected matrix
Updating font configuration of fontconfig...
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category type1..
Updating category type1..
Updating category truetype..
Updating category cid..
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-indic-fonts-core /usr/share/fonts/truetype/thai /usr/share/fonts/truetype/ttf-bitstream-vera /usr/share/fonts/truetype/ttf-lao /usr/share/fonts/truetype/unfonts /usr/share/fonts/truetype/ttf-arabeyes /usr/share/fonts/truetype/ttf-dejavu /usr/share/fonts/truetype/freefont /usr/share/fonts/truetype/arphic /usr/share/fonts/truetype/ttf-malayalam-fonts /usr/share/fonts/truetype/kochi /usr/share/fonts/type1/gsfonts /usr/share/fonts/truetype/msttcorefonts
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
Fontconfig warning: "local.conf", line 586: saw number, expected matrix
Fontconfig warning: "local.conf", line 586: saw number, expected matrix
Fontconfig warning: "local.conf", line 586: saw number, expected matrix
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
Fontconfig warning: "local.conf", line 586: saw number, expected matrix
Fontconfig warning: "local.conf", line 586: saw number, expected matrix
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-indic-fonts-core /usr/share/fonts/truetype/thai /usr/share/fonts/truetype/ttf-bitstream-vera /usr/share/fonts/truetype/ttf-lao /usr/share/fonts/truetype/unfonts /usr/share/fonts/truetype/ttf-arabeyes /usr/share/fonts/truetype/ttf-dejavu /usr/share/fonts/truetype/freefont /usr/share/fonts/truetype/arphic /usr/share/fonts/truetype/ttf-malayalam-fonts /usr/share/fonts/truetype/kochi /usr/share/fonts/type1/gsfonts /usr/share/fonts/truetype/msttcorefonts
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
Fontconfig warning: "local.conf", line 586: saw number, expected matrix
Fontconfig warning: "local.conf", line 586: saw number, expected matrix
Fontconfig warning: "local.conf", line 586: saw number, expected matrix
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
Fontconfig warning: "local.conf", line 586: saw number, expected matrix
Fontconfig warning: "local.conf", line 586: saw number, expected matrix
Regenerating fonts cache... done.

```

**~/.fonts.conf**:

```
<?xml version="1.0&#8243; ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
<edit name="autohint" mode="assign">
<bool>true</bool>
</edit>
</match>
</fontconfig>
```

---

### Post by [CPR]-AL.exe on 2008-08-17
I don't want to re-install the ubuntu :( Maybe, someone could share his local.conf and fonts.conf file with the original ubuntu settings?

---

### Post by benerivo on 2008-08-17
This is the only line in my ~/.fonts.conf```
rgb     true     hintfull     true
```but it will very probably not be the 'ubuntu default'. I can't find a local.conf file. Try loading a live cd if you have one and copy the files from the live cd session.

---

### Post by [CPR]-AL.exe on 2008-08-17
local.conf is in /etc/fonts/

> Try loading a live cd if you have one and copy the files from the live cd session.

Nice idea! Thanks, i'll try that :)

---

### Post by [CPR]-AL.exe on 2008-08-28
How could i make symbolic links for **sans**, **serif** and **monotype** fonts?.. Antialiasing is bak, but the symbolic links are not :(

---

### Post by [CPR]-AL.exe on 2008-08-31
For real?.. Noone knows? :((

---

### Post by jstalnak on 2009-05-09
Sorry no one replied on how to make a symbolic link -- I know it's been quite some months, but in case you never found out:

#> ln -s <path-to-original-file> <path-to-link>

e.g.,

#> ln -s /usr/share/fonts/X11/100dpi/courO10-ISO8859-1.pcf.gz /usr/share/fonts/link-name

You may need to use sudo privileges if the source location is owned by root.

Regards

---

