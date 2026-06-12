---
title: "Bits missing from cheese in KDE?"
date: 2009-04-08
forum: General Help
---

### Post by IanB2 on 2009-04-08
I'm experimenting with KDE 3.5 and would like to run some gnome applications.

I've installed cheese. Cheese appears to be fine however I cannot take pictures. The count down runs but no picture thumbnail is shown in the lower panel. I guess there is a package missing?

Here is the output from xsession-errors which might mean something???
Any help would be much appreciated!


** (cheese:6112): WARNING **: Couldn't load icon: Icon 'image-loading' not present in theme

** (cheese:6112): WARNING **: Throbber animation not found

** (cheese:6112): WARNING **: Throbber fallback animation not found either

** (cheese:6112): WARNING **: Couldn't load icon: Icon 'image-loading' not present in theme
X Error: BadWindow (invalid Window parameter) 3
Major opcode: 19
Minor opcode: 0
Resource id: 0x3000003

---

### Post by IanB2 on 2009-04-08
> **IanB2 said:**
> I'm experimenting with KDE 3.5 and would like to run some gnome applications.

I've installed cheese. Cheese appears to be fine however I cannot take pictures. The count down runs but no picture thumbnail is shown in the lower panel. I guess there is a package missing?

Here is the output from xsession-errors which might mean something???
Any help would be much appreciated!


** (cheese:6112): WARNING **: Couldn't load icon: Icon 'image-loading' not present in theme

** (cheese:6112): WARNING **: Throbber animation not found

** (cheese:6112): WARNING **: Throbber fallback animation not found either

** (cheese:6112): WARNING **: Couldn't load icon: Icon 'image-loading' not present in theme
X Error: BadWindow (invalid Window parameter) 3
Major opcode: 19
Minor opcode: 0
Resource id: 0x3000003

The pictures were actually been taken and saved in ~/.gnome2/cheese/media
The solution appears to be to install gnome-icon-theme

Hope this helps someone

---

### Post by indeed on 2009-09-02
Thanks, this was puzzling me. And what a daft dependency!

---

### Post by kbm on 2009-10-04
Thanks for posting the solution, worked for me as well.  Seems an easy enough thing to fix though.  Is this something to log as a defect?  I guess it's a bit off since it is a gnome tool in a kde desktop, but I don't run into other apps with issues like this.

---

