---
title: "Top panel customization"
date: 2012-07-06
forum: Desktop Environments
---

### Post by sophiesperner on 2012-07-06
Good day the community,


I have installed ubuntu 12.04 64 bit amd version for my AMD Sempron LE 1100 processor. Works nice. I have updated and installed additional software.

I would like to ask please:

[LIST=1]
[*]I applied non-English translation to the whole system and want to change names of some folders in Places menu on the top panel (title bar), how could I do that?
[*]I have found how to remove messages indicator from the top panel (title bar), I was wondering how could I remove the My name user account indicator (icon) from the top panel as well?
[/LIST]


Best wishes and thank you for reply!


Sophie.

---

### Post by Frogs Hair on 2012-07-06
Hello and Welcome

2.The following works for Unity. Open the software center and install dconf editor. Open the application from dash, select apps > indicator-session and remove the check from show real name on panel. Logout and back in or restart.

---

### Post by sophiesperner on 2012-07-07
Good day!

I have dconf editor, but I have Gnome classic without effects, and there is no option indicator-session under apps selection.. Maybe I can login under Unity and check it, then logout and login under Gnome classic again?

Thank you. Would be nice if anybody could advise what to do with the Places menu items translation too. I have programs for reading .mo and .po files, but have no idea where is the file to translate the Places menu.

Have a nice day!

---

### Post by kansasnoob on 2012-07-07
It sounds like you're using the Gnome classic session, is that correct?

I'm making that assumption since you say:

> I applied non-English translation to the whole system and want to change names of some **folders in Places menu on the top panel** (title bar), how could I do that?

I think to rename folders in the Places menu you simply have to open Nautilus and rename the corresponding folder there. Like in this example I renamed Pictures to Photos and it shows up that way in the menu:

[ATTACH]220802[/ATTACH]

[ATTACH]220803[/ATTACH]

And to rename an application you go to System Tools > Preferences > Main Menu. Then if you highlight an app it can be renamed in Properties:

[ATTACH]220804[/ATTACH]

> I have found how to remove messages indicator from the top panel (title bar), I was wondering how could I remove the My name user account indicator (icon) from the top panel as well?

I use the standard "indicator-applet" along with the standard clock applet instead of "indicator-applet-complete". Please look at step #2 here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

And also a comparison of the applets here:

[http://ubuntuforums.org/showpost.php?p=11900657&postcount=12](http://ubuntuforums.org/showpost.php?p=11900657&postcount=12)

---

### Post by kansasnoob on 2012-07-07
> Would be nice if anybody could advise what to do with the Places menu items translation too. I have programs for reading .mo and .po files, but have no idea where is the file to translate the Places menu.


I'm not at all familiar with those file suffixes, but one thing! I highly recommend backing things up to a separate device before playing too much!

A few years ago I renamed a slew of photos, messed up, and it took me weeks to get it straightened out :(

---

### Post by sophiesperner on 2012-07-07
Dear Kansasnoob,

> I'm not at all familiar with those file suffixes, but one thing! I  highly recommend backing things up to a separate device before playing  too much!
No worries because all my files have a copy on external hard drive.

About your previous post,

> It sounds like you're using the Gnome classic session, is that correct?
Correct.

> I think to rename folders in the Places menu you simply have to open  Nautilus and rename the corresponding folder there. Like in this example  I renamed Pictures to Photos and it shows up that way in the menu:
Maybe with default English folders it is fine, but what I did:

[LIST=1]
[*]installed English system with all needed software;
[*]translated English Ubuntu 12.04 into my language;
[*]Found that if I rename Desktop just as you showed, it has no effect on the Places
menu item, which should be the renamed version of Desktop, instead it is something else, which is wrong translation, so I want to find the appropriate file to edit the existing translation.
[/LIST]
Unfortunately my Gnome classic without effects can not afford to make screenshots with opened Places menu to compare with the folders in the home directory (so hope you understand my text).

> And to rename an application you go to System Tools > Preferences  > Main Menu. Then if you highlight an app it can be renamed in  Properties:
True, that is easy. I was wondering about the Places menu items only.

> I use the standard "indicator-applet" along with the standard clock  applet instead of "indicator-applet-complete". Please look at step #2  here:
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

I've read the post and installed both:
```
sudo apt-get install indicator-applet indicator-applet-session
```
Now I have indicator-messages again on the panel :) I'm going to remove it by using simple command in the terminal, but still have no idea how to remove the My account switcher.

Thank you anyway.

---

### Post by sophiesperner on 2012-07-07
Dear all,

I have found the answer on my first question and few more nice things:

[LIST]
[*][URL="http://ubuntuforums.org/showthread.php?t=1535033"]Disable User Switcher indicator on the top panel
[/URL]
[*][URL="http://ubuntuforums.org/showthread.php?t=1477500"]Disable Suspend and Hibernate options
[/URL]
[*][Disable guest account]("http://ubuntuforums.org/showthread.php?p=11889879")
[/LIST]
I'm still coping with translation issues, especially with my second question - how to edit the Places menu items translation. I found the translation files directory:
/usr/share/locale-langpack/fr/LC_MESSAGES

It contains .mo files, I have the software to read and edit those files. The only thing I do not know - which file should I edit :)

Please help!

---

