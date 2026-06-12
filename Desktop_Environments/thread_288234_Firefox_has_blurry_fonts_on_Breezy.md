---
title: "Firefox has blurry fonts on Breezy"
date: 2006-10-29
forum: Desktop Environments
---

### Post by msmeyer on 2006-10-29
Hi,

since I upgraded from Dapper to Breezy, Firefox has blurry fonts in both the UI and the web pages. See the following link for an example (left is the menu from Firefox and right is Thunderbird):

[http://www.mesw.de/support/firefox_thunderbird.png](http://www.mesw.de/support/firefox_thunderbird.png)

Before the upgrade to Breezy, Firefox and Thunderbird looked exactly the same. It seems that though the same font and font sizes are used as before, the new Firefox 2.0 uses different anti-aliasing routines than the rest of the system.

Is this a bug or do people really think it's a good idea when Firefox looks different to all other programs? How can I get my normal anti-aliasing back?


Markus

---

### Post by .t. on 2006-10-29
Do you mean upgraded to Edgy? It'd be interesting to **downgrade** to Breezy.

Post your ~/.fonts.conf

If you're feeling brave (I mean it), you could try this repository for new font rendering packages:```
deb http://www.elisanet.fi/mlind/ubuntu edgy fonts
deb-src http://www.elisanet.fi/mlind/ubuntu edgy fonts
```

---

### Post by msmeyer on 2006-10-29
Yeah, of course I mean Edgy, sorry ;)

I don't have a ~/.fonts.conf:

markus@markus:~$ ls -l  ~/.fonts*
-rw-r--r-- 1 markus markus 0 2006-10-27 09:54 /home/markus/.fonts.cache-1
markus@markus:~$ 

Why would I need new packages for font rendering? Fonts render just fine on my system, it's just that Firefox 2.0 seems to have a problem here. Did you look at the screenshot? Is there a name for what it is that Firefox 2.0 does different than Firefox 1.5?

---

### Post by .t. on 2006-10-30
You shouldn't need new packages; it's just that it's fine for me.

Here's me ~/.fonts.conf (you can always delete it if it doesn't work):```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

I guess it was set by gnome-font-properties...

---

### Post by ReadWrite on 2006-11-06
msmeyer, this worked for me:
[http://ubuntuforums.org/showthread.php?t=292729](http://ubuntuforums.org/showthread.php?t=292729)

But it is only a part of my problem: I installed msttcorefonts to get some regular fonts in OpenOffice. However, it changed look and feel of firefox - now Gmail displays in ugly Arial font instead of a gnome sans serif. Don't have an idea how to prevent firefox from using msttcorefonts

---

