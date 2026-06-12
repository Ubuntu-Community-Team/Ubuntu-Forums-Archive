---
title: "Adjusting Watcom Parameters"
date: 2005-04-22
forum: Desktop Environments
---

### Post by Johank on 2005-04-22
I hope this is the right forum...here goes:
My watcom tablet is working on 5.04, just needs tweaking. Is there any way to adjust the various parameters from the device manager or anywhere? For example, the mouse is acting more like a pen (cursor does not stay when you lift the mouse and put it elsewhere). Linux knows it is a watcom tablet - I see it listed as one of the devices but can't (don't know how/what) to edit anything there.

---

### Post by alastair on 2005-04-22
Ahh ... you mean "Wacom" tablet - ofcourse. I had thoughts of old Canadian C compilers going through my head there!

This is an X configuration issue probably i.e. 

The tablet (as an "input" device for X) is set up, like your mouse etc., via the X config file:

/etc/X11/xorg.conf

For the Wacom X module "wacom" - see the manual page i.e.

man wacom

If you change the xorg.conf file to experiment, take a BACKUP copy first.

If you experiment, edit the file, save your changes and .... (with nothing else opened/unsaved) ... restart X e.g. CTRL+ALT+BACKSPACE.

---

### Post by Johank on 2005-04-22
Thanks Alastair. You seem to be ever present on the forum! Yup, I too recall the Watcom compiler and have always confused the wacom when typing - must be getting old!

On the subject - can one use the Live CD to 'try' these things and thus avoid damaging your actual install?

---

### Post by alastair on 2005-04-22
It's a while since I used the LiveCD - but I think you could try it out with that. You don't need to reboot or anything, and should be able to experiment with the xorg.conf file and restart X to test.

P.S. I'm "ever present" only because I don't reboot my computer ever, or quit the browser! But I might be in bed (or at work occasionally).

---

