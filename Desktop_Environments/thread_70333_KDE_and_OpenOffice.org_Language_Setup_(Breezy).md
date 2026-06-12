---
title: "KDE and OpenOffice.org Language Setup (Breezy)"
date: 2005-09-29
forum: Desktop Environments
---

### Post by audax321 on 2005-09-29
Hello,

       I'm trying out Kubuntu Breezy and it's working great. However I have two questions regarding languages:

1. How do I setup KDE with both the United States-Basic and United State-International keyboard layouts and switch between them using a key combination. When I go to add the keyboard layouts it seems I can only add one or the other and not both.

2. How do I install spelling and hypenation dictionaries in OpenOffice.org Beta2?

I've been using Gnome for the past year so I haven't been keeping up with changes in KDE and am completely new to OpenOffice in Linux. I know how to edit the dictionary.lst file and add languages in Windows, but have no idea where these are located in Kubuntu.

Thanks.

---

### Post by mlomker on 2005-09-29
Go into the Control Panel under Regional & Accessibility, Keyboard Layout.  Check the *Enable keyboard layouts* box and add the second keyboard layout.  Go to the Switching options tab and check the *Show indicator for single layout*.  Now you should have a keyboard indicator in the icon area on your task bar.  You can just click on that icon to change the keyboard layout.  I am not sure how to make a hotkey work for that.

---

### Post by audax321 on 2005-09-29
That's what I thought too, but it doesn't work. After I add the "U.S. English (us)" keyboard it is removed from the list on the left and added to the right with its 'basic' layout variant selected by default. I can manually change this to 'intl' but I want to add both variants to the list so I can select between them using the icon on the taskbar. However, since that keyboard layout is no longer in the list I can't do this.

I've tried doing this in both Gnome and Windows. In Windows it automatically sets up the Cntrl+Shift hotkey. In Gnome it works as well, but if I press its hotkey (Alt+Alt) it only switches once and doesn't switch back. But even in Gnome I can select the other variant through an applet on the panel.

I'm pretty sure that this used to work back when I used KDE 3.2 with SuSE 9.1. I'm not quite sure why it doesn't work anymore.

---

### Post by mlomker on 2005-09-29
I see what you're saying.  I was thinking you wanted to also add en_US.

---

### Post by Knome_fan on 2005-09-30
Hm, about the keyboard layout, I just tested it here (hoary+3.5beta, so maybe this makes a difference) and as far as I can tell it works fine.

I do have us, us_intl and en_US layouts on the left and can select them. They now appear on the right and I can select them as mlomaker described.
(Keep in mind, I'm on my first coffee, so maybe I misunderstood your problem).

About OO2 and languages:
I'm pretty sure simply installing the language-pack and language-support for the languages you want to have available should do the trick.

If this doesn't work (there used to be a bug, but I think it's solved now), there's always this great tool:
[http://ftp.services.openoffice.org/pub/OpenOffice.org/contrib/dictionaries/dicooo/DicOOo.sxw](http://ftp.services.openoffice.org/pub/OpenOffice.org/contrib/dictionaries/dicooo/DicOOo.sxw)

Just open the file with OO2, agree to run makros and off you go.

Have fun!

---

### Post by audax321 on 2005-09-30
[QUOTE=Knome_fan]Hm, about the keyboard layout, I just tested it here (hoary+3.5beta, so maybe this makes a difference) and as far as I can tell it works fine.
I do have us, us_intl and en_US layouts on the left and can select them. They now appear on the right and I can select them as mlomaker described.
(Keep in mind, I'm on my first coffee, so maybe I misunderstood your problem).
About OO2 and languages:
I'm pretty sure simply installing the language-pack and language-support for the languages you want to have available should do the trick.
If this doesn't work (there used to be a bug, but I think it's solved now), there's always this great tool:
[http://ftp.services.openoffice.org/pub/OpenOffice.org/contrib/dictionaries/dicooo/DicOOo.sxw](http://ftp.services.openoffice.org/pub/OpenOffice.org/contrib/dictionaries/dicooo/DicOOo.sxw)
Just open the file with OO2, agree to run makros and off you go.
Have fun![/QUOTE]

Well, I'm using KDE 3.4.2 on breezy... maybe the support for the different keyboard layouts hasn't been fully implemented yet?

Oh and as far as OO2 goes, it appears that spell check dictionaries not working on breezy preview installs is a bug. I found a work around here:

[http://ubuntuforums.org/showthread.php?t=62884&page=2](http://ubuntuforums.org/showthread.php?t=62884&page=2)

then all you have to do is install the myspell-<language> package for the dictionaries you want. I'm going to try it out later today...I'm in Windows right now and feeling too lazy to reboot. :)

---

### Post by audax321 on 2005-09-30
Yup, just had to do this to get the OpenOffice spell check working:

sudo ln -s /etc/openoffice/dictionary.lst /usr/lib/openoffice2/share/dict/ooo/dictionary.lst

Now, hopefully the extra keyboard layouts will start working as development on breezy progresses.

---

