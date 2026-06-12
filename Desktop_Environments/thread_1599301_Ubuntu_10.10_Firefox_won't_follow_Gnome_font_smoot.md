---
title: "Ubuntu 10.10 Firefox won't follow Gnome font smoothing settings."
date: 2010-10-17
forum: Desktop Environments
---

### Post by Tynach on 2010-10-17
Now, in 10.04 and before (I believe), Firefox's font smoothing would always follow the font anti-aliasing settings I choose in Gnome's Appearance settings... I prefer to turn hinting to Full, basically. Whenever I would download Minefield or Firefox from any other source, it would use different font smoothing.. And it kinda bugged me, but I would always just go ahead and use Ubuntu's Firefox for most things, and it worked fine for me.

Now, in 10.10, Firefox has completely gone to it's own smoothing settigns, which HAPPEN to be the smoothing settings that Ubuntu uses by default... Which I don't like. I change them, and in EVERY SINGLE PROGRAM, it's fixed... EXCEPT in Firefox.

How do I get Firefox to obey my font smoothing settings? Even if it requires recompiling from source, I'm willing to do so.

---

### Post by Tynach on 2010-10-17
Any suggestions? Even anywhere else I can ask?

---

### Post by phaed on 2010-11-08
You have to fiddle with your font settings.  Your situation might be different, but here's what worked for me:

I went to System -> Preferences -> Appearance and clicked on the Fonts tab.  I checked "Subpixel smoothing (LCDs)" and then clicked the "Details..." button.  Then I changed it from Slight to **Medium** hinting.

Then in a terminal, type the following command:

**sudo dpkg-reconfigure fontconfig**

And restart Firefox.  If that doesn't get the fonts the way you want them, fiddle with the hinting settings and make sure you re-run that dpkg-reconfigure command before checking it in Firefox.

---

### Post by bimaljr on 2010-12-17
You need to run two commands:

```
sudo rm /etc/fonts/conf.d/10*
```
```
sudo dpkg-reconfigure fontconfig
```

---

### Post by Izziedee on 2011-08-25
This fixed an issue I was having with Firefox and some pdf files on Ubuntu 10.10 Gnome desktop. Thanks!

---

