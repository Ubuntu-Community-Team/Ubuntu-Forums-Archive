---
title: "pen not working on my pc tablet"
date: 2009-03-01
forum: General Help
---

### Post by workshop1702 on 2009-03-01
hi just installed some updates and my tablet pc pen has stpped working again , someone did help me to get this working sometime ago doesnt seem to be in my list of posts anymore so i cannot see how to get it going again.
seem to remember it was to remove the stars before something in terminal.
just cannot remember how to do it. could someone help please.

---

### Post by Favux on 2009-03-01
Hi workshop1702,

Was it your xorg.conf?  And you removed "#"'s from in front of Wacom entries?

What version of Ubuntu are you on?  Do you know what the updates were?  What kind of tablet pc do you have?

---

### Post by workshop1702 on 2009-03-02
yes that sounds like it but how do i do it .i need step by step instructions as i have forgoten how to do it.

---

### Post by workshop1702 on 2009-03-02
sorry forgot using 8.04 my tablet is a tatung RTAB912

---

### Post by Favux on 2009-03-02
Hi workshop1702,

Ok, so you're using Hardy (8.04) and a tatung RTAB912.  I'm not familiar with it.  I'll have to google it.  You think it was the xorg.conf you worked with last time.

Did you make a backup of the xorg.conf last time?

Does it use the linuxwacom drivers or some other drivers?  

Do you know what version of the drivers you are using?

Is it usb or serial?

Do you remember what update broke it?

We'll have to look at you're xorg.conf.  It is in "/etc/X11/".  Please attach it to your next post.

Edit:  I saw another of your posts.  You have a pure tablet Tablet PC.  It docks to a keyboard.  That may complicate things, and be part of your problems.  Does the keyboard stand offer other things like usb ports, video ports, and DVD, etc.?  I can't tell from what I'm looking at.

It has a sylus with an eraser.  I can't tell if it has buttons on the stylus.  Does it?  How many?

Something that may help you.  In a terminal type:
```
lspci -v -nn
```
```
lsusb -v
```
You'll get two long outputs.  Save each in a separate text file.  That will help you see what Hardy sees of your system.  As you go along you can edit out parts that aren't relevant and shrink their size.  But they will be available to copy and paste into your forum posts when people ask for details.

---

