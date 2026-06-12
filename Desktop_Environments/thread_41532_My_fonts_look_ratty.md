---
title: "My fonts look ratty"
date: 2005-06-13
forum: Desktop Environments
---

### Post by Curlydave on 2005-06-13
My fonts in Linux look ratty. I can change the font, but they all look ratty. I want nice, clean, pristine fonts. How can I do this? Thanks! Even when I use MS fonts (eg Ariel) that I got from the setup script, they look ratty. What's up?

---

### Post by desdinova on 2005-06-13
try

sudo [size=-1]dpkg-**reconfigure** fontconfig

Myself I prefer Autohinting - but there's three options to try

a
[/size]

---

### Post by dudinatrix on 2005-06-13
Mine too.. I mean, the font's look *ok*, but they have that soft touch to it that actually kind of distorts it.  If I disable the smoothing/hinting.. it's too crisp and chunky.

I'm dual booting with WinXP.. and my fonts look super crisp and smooth in XP.  I just want my Ubunto to look like that! :)

---

### Post by tread on 2005-06-13
Make a backup of the .fonts.conf in your home and try putting this there instead:

```

<?xml version="1.0"?>
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

### Post by dudinatrix on 2005-06-13
[QUOTE=tread]Make a backup of the .fonts.conf in your home ...[/QUOTE]
What if I don't have a .fonts.conf?  (forgive me, I'm a day-old n00b!)

---

### Post by tread on 2005-06-13
Then create one :) The backup was just to make sure you don't lose any settings in case you don't like these.

---

### Post by dudinatrix on 2005-06-13
[QUOTE=tread]Then create one :) The backup was just to make sure you don't lose any settings in case you don't like these.[/QUOTE]
sounds good to me :)  do I need to point anything to it, or will it just work after I create the file?

---

### Post by bored2k on 2005-06-13
You could also try [http://www.ubuntuforums.org/showthread.php?t=23426&highlight=ubuntu-geek+fonts](http://www.ubuntuforums.org/showthread.php?t=23426&highlight=ubuntu-geek+fonts)

---

### Post by tread on 2005-06-13
Yup, just create the file in your home directory with the given contents.

---

### Post by Curlydave on 2005-06-14
Wow, that worked; Thanks!!!

---

### Post by Curlydave on 2005-06-15
Thank you very much! That fixed my Ubuntu fonts. Perfect. However, my font when viewing the Ubuntu forums is now worse... Weird!

---

### Post by beefsprocket on 2005-06-15
What font resolution are you using in Firefox? I have the option of choosing between 72dpi and 96dpi in the font dialog within Firefox. I had the same problem (KDE only) with ratty and extremely small fonts in Firefox until I changed the modeline in my xorg.conf and selected 96dpi in Firefox. Are you using KDE or Gnome?

If you aren't using 96, select it as your default option. If you don't have 96 at all, look into creating a mode line in xorg.conf (it worked for me).

Edit: Someone else linked to this indirectly through another posted link. It should make a difference in terms of modeline *if* you need it: 

[http://ubuntuforums.org/showthread.php?t=20976](http://ubuntuforums.org/showthread.php?t=20976)

---

### Post by Curlydave on 2005-06-15
[QUOTE=beefsprocket]What font resolution are you using in Firefox? I have the option of choosing between 72dpi and 96dpi in the font dialog within Firefox. I had the same problem (KDE only) with ratty and extremely small fonts in Firefox until I changed the modeline in my xorg.conf and selected 96dpi in Firefox. Are you using KDE or Gnome?

If you aren't using 96, select it as your default option. If you don't have 96 at all, look into creating a mode line in xorg.conf (it worked for me).

Edit: Someone else linked to this indirectly through another posted link. It should make a difference in terms of modeline *if* you need it: 

[http://ubuntuforums.org/showthread.php?t=20976](http://ubuntuforums.org/showthread.php?t=20976)[/QUOTE]


It defaults at 96.

---

