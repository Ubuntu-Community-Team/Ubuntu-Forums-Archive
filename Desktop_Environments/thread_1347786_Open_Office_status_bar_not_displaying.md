---
title: "Open Office status bar not displaying"
date: 2009-12-06
forum: Desktop Environments
---

### Post by alienjon on 2009-12-06
I'm running kubuntu 9.10 (although it may have occurred in an earlier version and I didn't notice it) and I just noticed that when I open up open office (any of the programs, but I'm specifically looking at OOWriter) the status bar exists (there's the gray area where it should be) but the only thing that displays in it is the 'file zoom' utility.  I like using the status bar for noting both the page number and the status information it should provide, but I can't seem to find out why they aren't displaying.  Google doesn't show anything and, as it displays fine in my Gentoo desktop, I'm guessing it's an install/configuration something somewhere.  I just updated (full-upgrade) and still have the issue.  Any ideas?

---

### Post by SteveMcQwark on 2009-12-16
It has to do with the KDE integration. I'm looking for an answer to this too. The buttons are still there,they just are invisible. If you click around on the bar, you'll see some of them show up. 

Edit:
here's how I solved it:
install the package: openoffice.org-gtk
add this line to .profile (in your home folder)

export OOO_FORCE_DESKTOP=gnome


(make sure there's a newline after it)
You have to relogin for it to take effect.

It should now look the same as Firefox and any other gtk apps you have. Because you still have openoffice.org-kde, you will still be using the kde file dialogue, which may or may not match your current theme, but will match the expected behaviour.

---

### Post by GroMmiT on 2010-02-22
Confirmed, works in LinuxMint KDE64.

Thanks Steve!!!

---

### Post by herophuong on 2010-08-17
Thanks very much. Worked perfect in kubuntu kde4 lucid

---

