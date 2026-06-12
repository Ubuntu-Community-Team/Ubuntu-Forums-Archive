---
title: "[SOLVED] Subpixel rendering is broken?"
date: 2007-11-11
forum: Desktop Effects &amp; Customization
---

### Post by Noisedsn on 2007-11-11
After font rendering adjusting, or maybe xgl uninstalling I cant enable subpixel font rendering... I switch the radiobutton in Font Settings to "Subpixel Antialiasing", but everything still looks like greyscale.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=49917&stc=1&d=1194822223[/IMG]

Tried to reinstall the original version of libraries:

```
sudo aptitude install libfreetype6/gutsy libcairo2/gutsy libxft2/gutsy
```

It's still broken. Subpixel AA is enabled in .fonts.conf also:

```
<match target="font">
 <test qual="all" name="rgba"><const>unknown</const></test>
 <edit name="rgba" mode="assign"><const>rgb</const></edit>
</match>
```

Maybe someone know how to fix it?

Update: Java applications still anti-aliased with subpixel method.

---

### Post by Jouke74 on 2007-11-12
Are you sure that your screen is still selected as being a LCD? > Edit: never mind. I guess so.

---

### Post by Noisedsn on 2007-11-12
Yes, at the screen properties my LCD Samsung 215tw is selected. And at the font settings "Subpixel Antialiasing" is selected (screenshot is Russian, but options are at the same place as in English ubuntu). But i think that subpixel antialiasing must work even at CRT monitors...

---

### Post by Noisedsn on 2007-11-12
Maybe there are some config files, where subpixel antialiasing can be disabled?

---

### Post by hugmenot on 2007-11-13
Have you tried "sudo dpkg-reconfigure fontconfig-config"?
This softlinks some config files in /etc/fonts for system-wide settings.

---

### Post by Noisedsn on 2007-11-13
Of course I have tried it. I even verify links in /etc/fonts manually - everything seems to be ok, but don't work..

---

### Post by hugmenot on 2007-11-13
But something must be overriding the setting. Any other stray config around? ~/.fonts.conf maybe?

EDIT: deleting the .fonts.conf entirely? What happens? Also, Java has it&#8217;s own method, unrelated to freetype.

---

### Post by Noisedsn on 2007-11-14
Here is my .fonts.conf:
```

	<fontconfig>
	<match target="font">
	<test qual="all" name="rgba">
<const>unknown</const>
</test>
	<edit name="rgba" mode="assign">
<const>rgb</const>
</edit>
</match>
	<match target="font">
	<edit name="autohint" mode="assign">
<bool>true</bool>
</edit>
</match>
	<match target="font">
	<edit name="hinting">
<bool>true</bool>
</edit>
</match>
	<match target="font">
	<edit name="hintstyle">
<const>hintslight</const>
</edit>
</match>
	<match target="font">
	<edit name="antialias">
<bool>true</bool>
</edit>
</match>
	<!--
 If the font is bold, turn off autohinting
         <match target="font">
                  <test name="weight"
compare="more"><const>medium</const></test>
                   <edit mode="assign"
name="autohint"><bool>true</bool></edit>
           </match>
-->
</fontconfig>
```

Deleting has no effect.

---

### Post by hugmenot on 2007-11-14
And what does 
```
apt-cache policy libfreetype6 libcairo2 libxft2
```
tell you?

---

### Post by Noisedsn on 2007-11-14
Finally, I've found where the problem was. I was trying to tune the font rendering by compiling freetype-2.3.5 from source code. But in the sources ```
#define FT_CONFIG_OPTION_SUBPIXEL_RENDERING
``` option is disabled by default.

Thanks all for the help.
P.S. sorry for my poor english.

---

### Post by hugmenot on 2007-11-14
Okay :popcorn:.
Your OP tells otherwise ...

---

