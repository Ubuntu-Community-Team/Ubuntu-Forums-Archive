---
title: "Desktop Effects on Gutsy on ATI Radeon Xpress 200m"
date: 2007-10-12
forum: Desktop Effects &amp; Customization
---

### Post by jmusso on 2007-10-12
Hi. When I tried to enable the restricted video card driver to enable the desktop effects on Gutsy on a fresh install of the RC, it said that it couldn't find xorg-driver-fglrx. When I tried to do a sudo apt-get install of it, I got nothing. Ideas please?

---

### Post by gerardino on 2007-10-17
Hello. It's been 4 days since your post. Perhaps you've already solved it.
If you still haven't, it'd be like this:
1. Look for "Software Origins" ("Origenes de Software" in spanish) in tracker. 
2. Run it (yeah, it's an app)
3. Enter you super-user password
4. On the window, check the "restricted" stuff checkbox
5. Click "Close" and confirm to reload the sources list in the messagebox that appeared.

Try to enable the driver again. If that fails, try checking more unchecked checkboxes.

An alternative is to modify the sources.list file located somewhere near /etc/apt/ (must do as root)
Then look for the lines where the "restricted" word is used and uncomment them (remove all the # at the beginning of the line).
Save the file and run a
'sudo apt-get update'
in the terminal

---

### Post by hiddensphinx on 2007-10-18
I can only get the cube effect (press F1) to work using Gutsy Gibson and ATI 200M on my compaq laptop

Is there other effects i am missing out on with Gutsy Gibson?

---

