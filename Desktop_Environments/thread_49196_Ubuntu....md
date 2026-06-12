---
title: "Ubuntu..."
date: 2005-07-15
forum: Desktop Environments
---

### Post by SKLP on 2005-07-15
Hi!

I've been using Ubuntu since last November and i really like it. However there are a few small issues (easily fixed probably)  i don't like (both ubuntu and gnome "bugs"):

-- The GtkFileChooser shows folders before other files even though i configured Nautilus to not do that. Now i know the GtkFileChooser isn't nautilus but some consistency would be nice :)
---------------------------EDIT----------------------------------
Same bug also applies for file-roller (gnome's archive manager) :(
Should I create a bugzilla page?
--------------------------------------------------------------------
-- Totem's keyboard shortcuts for jumping forward and backward (the left and right arrows) jump 5 sec backward if i push the left button and 15 sec forward if i push the right one. This is really odd and i think it would be more logical if the offset was the same regardless of the direction. I actually wrote a simple patch that fixes this and changes a few other hotkeys in Totem...

-- Ubuntu "SPATIAL": This SUCKS! It's not even really spatial. To make it somewhat spatial they should make folder windows close when you open a file from them. But i would really prefer if ubuntu reversed this decision... This SUCKS! (I know it can be disabled and i did it right away...) 
---------------------------EDIT----------------------------------
Upstream spatial is now the default spatial mode but browser mode is now default
So i guess you could say this is fixed :)
--------------------------------------------------------------------

-- I don't like that the letters in menu bars and buttons that can be used with the alt key to click a button or open a menu, is marked with an "_". IMHO this looks UGLY, is there any way to disable this without patching gtk?

-- Firefox: In hoary pre-release the toolbar icons was using icons from the current gnome theme. This was reversed before the release, why? (I've switched to Epiphany for now...)

-- Muine: The packages from ubuntu is currently compiled with MPEG-4 file format (mp4ff) support disabled. This makes it impossible to play most AACs even if you installed gstreamer0.8-faad from some repository (for example backports).
(I've had to compile muine manually for no good reason)
---------------------------EDIT----------------------------------
This is apperently getting [fixed](http://ubuntuforums.org/showpost.php?p=246546&postcount=5).
--------------------------------------------------------------------
Thx in advance...

---

### Post by SKLP on 2005-07-16
*bump*

---

### Post by angkor on 2005-07-16
Erm, you're not really asking any questions. :)

Except for the " "-thingie which I don't get...

---

### Post by SKLP on 2005-07-19
[QUOTE=angkor]Erm, you're not really asking any questions. :)[/QUOTE]Yeah, I might have been a bit unclear  ](*,) 
Sorry.
Well, I guess I wanted to know if other ubuntu users also dislike these things...
[QUOTE=angkor]Except for the " "-thingie which I don't get...[/QUOTE]Let me put it this  way: In the menu bars of GTK+-applications the letters that can be used for keyboard shortcuts (f.e. the "F" in "File") are marked with an underline. IMHO this looks dirty and I'm wondering if there's an option to disable it (without patching the gtk+ source code preferably).

---

### Post by SKLP on 2005-07-26
Ubuntu spatial is no longer default :)

---

### Post by basse1989 on 2005-07-26
I agree with everything, except I don't see the problem with the "_"s.

---

### Post by SKLP on 2005-07-26
[QUOTE=basse1989]I agree with everything, except I don't see the problem with the "_"s.[/QUOTE]But you do agree that you should be able to disable them if you want?

---

### Post by basse1989 on 2005-07-26
Naaah, maybe. But only in gconf.

---

### Post by SKLP on 2005-07-26
[QUOTE=basse1989]Naaah, maybe. But only in gconf.[/QUOTE]Fine with me, however i would prefer them to be disabled by default :)

Another thing, i also think the "focus lines" should behave like after applying the patch from [here](http://bugzilla.gnome.org/show_bug.cgi?id=162023).

---

### Post by basse1989 on 2005-07-26
Indeed.

---

### Post by stwog on 2005-07-26
Yeah, I don't mind the underlining of the letters either. That's the way its always been. Not just with Gnome, but pretty much every desktop I've used including Windows. I'm not too sure, but I seem to recall OS X doing this as well.... Maybe it is the font that you are using that makes these undelines stand out.

---

### Post by SKLP on 2005-07-26
[QUOTE=stwog]Yeah, I don't mind the underlining of the letters either. That's the way its always been. Not just with Gnome, but pretty much every desktop I've used including Windows. I'm not too sure, but I seem to recall OS X doing this as well.... Maybe it is the font that you are using that makes these undelines stand out.[/QUOTE]The Mac OS (including X) does not have this.

I don't really mind it being the default, I just want an option to disable it.

---

### Post by SKLP on 2005-07-26
IIRC, it can be disabled in Windows.

---

### Post by basse1989 on 2005-07-30
But when you think about it, the underlines are really not that great.
I never use that kind of keyboard shortcut and it's a lot slower than just clicking on, for exaple, _F_ile than pressing <Alt>f. And the few times I've tried to use the shortcuts it just made me confused because I didn't know which button + _*_ to press. So yeah, away with them. :)

---

