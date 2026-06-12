---
title: "Compiz Fusion, 3 sides to my 'cube' but a number of virual workstations on each."
date: 2007-08-31
forum: Desktop Effects &amp; Customization
---

### Post by jtreach on 2007-08-31
I have installed compiz fusion with a few hiccups all of which i have cleared up apart from one. My 'cube' has 3 sides and each side has 2 virtual desktops. My 'Desktop size' options in CompizConfig read as follows:

Horizontal Virtual Size: 3
Vertical Virtual Size: 1
Number of Desktops: 2

The obvious solution would be to reduce the number of desktops to 1 but when I do this the number forcibly jumps to 4 desktops.

Any ideas?

---

### Post by praet on 2007-08-31
Try this:

Horizontal Virtual Size: 4
Vertical Virtual Size: 1
Number of Desktops: 1

---

### Post by jtreach on 2007-08-31
I've already tried that as stated, but it just jumps to 4 desktops as soon as I do it.

---

### Post by Zenham on 2007-08-31
1. Make sure you're using the flat file backend.
2. Try to reset the options with the whisk-broom icon.

You really do want the settings to be 4,1,1.

---

### Post by jtreach on 2007-09-04
I've tried using the whisk-broom icon..... to no avail. :(

I'm not really sure what you mean by the flat file backend?

---

### Post by jtreach on 2007-09-04
Sorry I didn't mean to post that three times. :s

---

### Post by praet on 2007-09-04
What Zenham means is to check that your settings are being stored in a flat file (~/.config/compiz/) instead of a database configuration (gconf).
To check this, go to System > preferences > CompizConfig settings manager
In the main screen, choose Preferences from the left hand list, then on the Profile and backend tab, make sure the Backend option is set to "Flat-file Configuration Backend".

---

