---
title: "How to enter filename in file chooser dialog"
date: 2018-06-23
forum: Desktop Environments
---

### Post by fugue137 on 2018-06-23
Ubuntu 18.04:

When I ask, say, Chrome to upload a file, I get a dialog. I'm using the default GUI for this Ubuntu---GNOME modified by Ubuntu. I want to type the name of my file (actually cut and paste a long pathname from another application). However, all the dialog gives me is the option to click and scroll and click and scroll and click and scroll some more until I finally locate the file whose name is in my cut buffer. That gets tedious, since the file chooser is inferior to purpose-built applications for choosing certain file types (images in directories containing thousands of almost-identically-named images are the most accessible example, but there are others).

How do I enter the filename?

I've found many older answers to this question dating back 10 or more years. They involve using the commandline to set secret Gnome parameters, using the tweak tool to set options that no longer exist, even switching to other desktop environments... haven't tried the last since I'm still willing to give Ubuntu's Gnome another chance, but I haven't found recent discussions of it here or on the web at large. Apparently I am using the wrong search terms? Sorry for what must surely be a duplicate question, but any pointers to the answer would be nice.

Developers (if you're reading this): you make this really hard to figure out. It used to be easy (e.g. an editable filename box always visible), then it got harder (the secret way to enter a filename was to click somewhere, or to just start typing blindly), and now it's harder again (I've been running Linux since 1992 and I can't figure it out). How do you justify this change?

---

### Post by vanadium on 2018-06-23
It is simple, but you have to know. Press Ctrl+L. This shows the location path where you can paste your file name.

---

### Post by fugue137 on 2018-06-26
Thank you!

Is there any reliable way to have ^L not replace my cut-paste-buffer contents with its own?

Developers: what's the rationale behind making this feature so hard to find? Are you trying to force us to build community? ;)

---

### Post by coffeecat on 2018-06-26
> **fugue137 said:**
> Developers (if you're reading this)

No, they're not.

> **fugue137 said:**
> Developers: what's the rationale behind making this feature so hard to find?

We are all end-users just like you. Developers rarely if ever come here.

---

### Post by Holger_Gehrke on 2018-06-26
> **fugue137 said:**
> 
Developers: what's the rationale behind making this feature so hard to find?

You're not supposed to discover features. It's ART !!1!! You're supposed to take two steps back, admire it's beauty and simplicity, then log out and log into a session with a usable UI :grin:

Holger

---

