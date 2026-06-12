---
title: "How to turn off metacity transparency???"
date: 2008-11-26
forum: Desktop Environments
---

### Post by jrharvey on 2008-11-26
I just cant stand the transparent metacity any more. It only shows up on non focused windows and only when compiz is running but I cannot figure out how to disable it. Anyone know?

---

### Post by hambone79 on 2008-11-26
If you launch gconf-editor, you should be able to turn it off by going into apps->metacity->general and unchecking the "compositing_manager" option.

It may also help to use Emerald as your window decorator rather than the GTK Window Decorator. This always makes my windows behave better with Compiz.

---

### Post by jrharvey on 2008-11-26
Thank you kindly good sir

---

### Post by jrharvey on 2008-11-26
Ok so i tried this but the option is false by default and even unchecked it still goes transparent. Any other ideas? I dont want to use emerald so maybe there is another way.

---

### Post by hictio on 2008-11-26
> **jrharvey said:**
> Ok so i tried this but the option is false by default and even unchecked it still goes transparent. Any other ideas? I dont want to use emerald so maybe there is another way.

That's weird...

- Do you have the NVIDIA drivers installed?
(Assuming you have an NVIDIA card because of your signature ;) )

- Do you have the Desktop Effects enabled?

---

### Post by jrharvey on 2008-11-26
> **hictio said:**
> That's weird...

- Do you have the NVIDIA drivers installed?
(Assuming you have an NVIDIA card because of your signature ;) )

- Do you have the Desktop Effects enabled?

Yes compiz is enabled so Im guessing that it is overiding the metacity compositor settings. Yes I am using an Nvidia card but it is now 9800gx2 instead of 8800gt.

---

### Post by nikgare on 2008-11-26
If you have compiz installed ans running, then surely metacity won't be running - if I understand it correctly?

---

### Post by hictio on 2008-11-26
> **jrharvey said:**
> Yes compiz is enabled so Im guessing that it is overiding the metacity compositor settings. Yes I am using an Nvidia card but it is now 9800gx2 instead of 8800gt.

So, you must have the Desktop Effects enabled, thru Compiz for sure; but, you just want to get rid of the transparency on the window's borders, but retain all the other effects?

---

### Post by jrharvey on 2008-11-26
> **hictio said:**
> So, you must have the Desktop Effects enabled, thru Compiz for sure; but, you just want to get rid of the transparency on the window's borders, but retain all the other effects?

You hit the nail on the head. I have tried emerald before but cant stand it. Too shiny and takes more memory than usefull.

---

### Post by NTolerance on 2008-11-26
Try this:

[http://ubuntuforums.org/showpost.php?p=6122375&postcount=14](http://ubuntuforums.org/showpost.php?p=6122375&postcount=14)

---

### Post by hictio on 2008-11-26
What Emerald theme are you using? Have you searched thru the "System -> Preferences -> Emerald Theme Manager -> Edit Themes tab"?
I mean, to check if there is an option that you can change to make the inactive window border not transparent.
Or, perhaps, switch to another Emerald theme?

---

