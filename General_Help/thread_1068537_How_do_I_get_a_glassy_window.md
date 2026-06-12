---
title: "How do I get a glassy window"
date: 2009-02-13
forum: General Help
---

### Post by Burnasty on 2009-02-13
I have been searching for what seems like everywhere to find how people are making their windows that are open glassy.  I have compiz with emerald right now.

---

### Post by ilioscio on 2009-02-13
Can you be a little more specific? Perhaps link to a screenshot of what you're looking for?

---

### Post by binarypill on 2009-02-13
If you are referring to window themes, you might want to check out [gnome-look]("http://www.gnome-look.org")

If you want transparency effects on your open windows, use CCSM (CompizConfig Settings Manager) and enable the "Opacity, Brightness and Saturation" accessibility feature. Also, you can press Alt + Scroll Down/Scroll Up to adjust the current window's transparency.

---

### Post by dj722000 on 2009-02-14
Well if you have emerald, open it and go to Edit Themes. You will have to click on one of the themes to see a listing. I personally like the truglass. All the setting are in there. If not you may have to search for the one you like and put it in there.
Now what nobodys tells anybody is that you need this command to make it work right. emerald --replace
Hit alt f2 and put it in the text area and hit run.. This will start it.
Now on reboot it will not come back up. To fix this you can go to SYSTEM -> Preferences -> Sessions. Click ADD. A box will come up and you have to input the info.

Name: Auto Start Emerald
Command: emerald --replace
Comment: whatever you want.
Click on SAVE. This will restart Emerald on reboot or a restart.

You also may need to install the Compiz Fusion Icon. It will go in Applications -> System Tools. Click on it, it will go up to the panel bar and you get a little control over emerald. 
You can go here and get more Emerald themes and other stuff.
[http://www.compiz-themes.org/]("http://www.compiz-themes.org/")

Hope this helps.:popcorn:

---

### Post by UbuntuNerd on 2009-02-14
check out this link it should give you an idea 
[http://my.opera.com/ubuntunerd1/blog/make-ubuntu-look-like-windows-vista]("http://my.opera.com/ubuntunerd1/blog/make-ubuntu-look-like-windows-vista")

---

### Post by blur xc on 2009-06-17
I think this setup is beautiful- just need to figure out how do do something like it on my system...

[http://ubuntuforums.org/showpost.php?p=7378818&postcount=12](http://ubuntuforums.org/showpost.php?p=7378818&postcount=12)

BM

---

### Post by cmost on 2009-06-17
Personally, I think the best result is achieved by patching the sources for nautilus and recompiling with rgba support enabled.  Now, any Murrine themes with rgba enabled will display with cool semi-transparent glasslike appeal.  See My screenshot attached.  I'd be happy to post a howto if there is interest.

---

### Post by ametalguitarist on 2009-06-17
I would like to know how to do the bottom panel you have on that one, with the icons above the black and the reflections.

---

### Post by dewmanstl on 2009-06-17
> **ametalguitarist said:**
> I would like to know how to do the bottom panel you have on that one, with the icons above the black and the reflections.

Looks like OSX...;)

---

