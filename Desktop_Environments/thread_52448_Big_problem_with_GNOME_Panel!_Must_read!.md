---
title: "Big problem with GNOME Panel! Must read!"
date: 2005-07-27
forum: Desktop Environments
---

### Post by leslie on 2005-07-27
Hello everyone,

Thanks for taking the time out to read this post. Right what am I on about well after installing Ubuntu 5.04 (Hoary Hedgehog) x86 from the install disk I was of course presented with that lovely brown interface.

After playing with a few of the appearance setting, I mean it’s only the very strange who prefer the brown, I went to install the updates.

Nothing strange there you say well, I doubled clicked the updates icon (about 32 to install) and I changed user and stated them all. They all downloaded and installed fine (well apart from a very trivial error message at the end, can’t quite remember just what it was intended to portray). 

It all looked splendid, nice blues and greys with all the updates. I rebooted and logged in. Everything looked fine till I came to use the GNOME Panel!!!

To my surprise everything from the desktop icon to the calendar was working, but even though visible I could not access the applications, actions etc panel buttons nor could I right-click on the panel. Nothing, it was dead, but strangely enough the rest of the desktop was working fine. 

I right clicked and opened the terminal to try and resolve the problem (with a little help from the web) but alas it was gone.

So my question is what I should do. Go back to my windows heritage and do a fresh install or is there some fix to this problem. 

Please find the time to help a fellow Ubuntu user in need.

Kindest Regards

Leslow

---

### Post by Velvet Elvis on 2005-07-27
There is probably an easier way to do this.

Open an  x-term (gnome terminal) and run top (type "top" (no quotes) at the shell prompt).  Find the process number that corresponds to "gnome-panel." Make note of it.  Hit Q to leave top.  while still in the x-term, type "kill processnumberhere." This should kill the hung gnome-panel process.  Gnome will ask ask you if you want to restart the process.  Say yes.

Ctl-alt-backspace will kick you back to the login screen btw.

---

### Post by charlieg on 2005-07-27
Or just 'killall gnome-panel' or, in top, press k then type the process number (listed against gnome-panel).  Also gnome-panel might not be listed in top (might be too many processes) so use 'ps uwx'.  Um, yeah, that's about it.

---

### Post by leslie on 2005-07-28
Thank you for your help people, you have enlightened on the path to becoming a Linux guru myself

---

### Post by leslie on 2005-07-28
I have restarted the gnome panel and now i have lost the clock and speaker as well as the buttons being hung! Help

---

