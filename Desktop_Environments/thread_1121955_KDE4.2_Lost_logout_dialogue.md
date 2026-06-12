---
title: "KDE4.2 Lost logout dialogue"
date: 2009-04-10
forum: Desktop Environments
---

### Post by beermad on 2009-04-10
For some unaccountable reason, I have lost the logout dialogue from my user under KDE4.2.

When I right-click on the desktop and click "leave", the background slowly fades to greyscale as normal, but no dialogue allowing me to choose what to do appears.

It seems to be something specific to my userid - creating a dummy one and using it, the same actions show the expected dialogue. Strange thing is, if I enable compositing (either Compiz or KDE's own) the dialogue appears when expected.

The correct boxes are checked in systemsettings (Session Manager, Confirm logout and Offer shutdown options).

Any ideas?

---

### Post by inobe on 2009-04-10
> Any ideas? 


what happens when you change the theme to aya or slim glow .

i haven't encountered what you are experiencing but i remember changing the theme once and back again to fix some rendering issues in 4.1'

---

### Post by beermad on 2009-04-10
> **inobe said:**
> what happens when you change the theme to aya or slim glow .

i haven't encountered what you are experiencing but i remember changing the theme once and back again to fix some rendering issues in 4.1'

No difference, unfortunately. A theme problem HAD occurred to me earlier, but none of the themes I tried made any difference.

---

### Post by inobe on 2009-04-10
i remember deleting a file that resets the kde desktop, i can't remember the path, give me a minute

edit: [http://www.kde-forum.org/artikel/18452/kde-4-reset-to-default.html](http://www.kde-forum.org/artikel/18452/kde-4-reset-to-default.html)

be careful with that, if you are unsure search google for reseting kde desktop.

in the past i needed to do that several times because i broke something on the desktop, it did reset the desktop.

when you restart the default theme will be applied' even the default wallpaper .

---

### Post by inobe on 2009-04-10
heres some more info

[http://www.google.com/search?q=rm+~%2F.kde4%2Fshare%2Fconfig%2Fplasma*&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=rm+~%2F.kde4%2Fshare%2Fconfig%2Fplasma*&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

that seems to be for opensuse

this one from kubuntu forums [http://kubuntuforums.net/forums/index.php?action=printpage;topic=3102117.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3102117.0)

---

### Post by beermad on 2009-04-14
> **inobe said:**
> heres some more info

this one from kubuntu forums [http://kubuntuforums.net/forums/index.php?action=printpage;topic=3102117.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3102117.0)

That did it. Thanks. Deleting ~/.kde/share/config/plasmarc restored the dialogue with only the minor side-effect of reverting the theme to default.

---

