---
title: "Consolas font looks bold?"
date: 2007-12-30
forum: Desktop Effects &amp; Customization
---

### Post by Sonja on 2007-12-30
The Consolas font looks too bold and ugly on Ubuntu. I really liked it in Vista. How do I make it look correctly on Ubuntu?

---

### Post by Forlong on 2007-12-30
Consolas is specifically designed to work with ClearType - which is Windows-only.

---

### Post by Sonja on 2007-12-30
How do I upgrade Ubuntu to ClearType then?

---

### Post by Forlong on 2007-12-30
ClearType is Microsft's software to provide anti-aliasing for fonts (subpixel rendering). It's proprietary (closed source) software. You can't use it on Linux.

---

### Post by whaley on 2008-03-19
Slightly OT:

I find using Inconsolata has an inverse effect.  It looks **wonderful** in OSX and Linux, but like bolded crap in Windows.  If you like Consolas, then Inconsolata might be a decent alternative for you in Linux.  It can be installed via synaptic/apt .

---

### Post by Kupari on 2008-05-01
This is a problem which I myself had been experiencing and trying to fix for quite a while. Thankfully, I found the solution (and by accident, I might add).

The problem lies in the Hinting; if you select Medium or Full, Consolas (as well as some other Vista ClearType fonts such as Candara, Constantia, and Segoe UI) will appear bolded. The solution for this is to change the hinting to *Slight*, which you can do by going to *System -> Preferences -> Appearance*, clicking on the *Fonts* tab and going to *Details...*. Change the Hinting to *Slight*. If you do not have *Subpixel (LCDs)* under **Smoothing** selected, be sure to do so as well.

This will fix Consolas as well as Candara, Constantia and Segoe UI. The downside to this is that some of the other fonts (most notably the Bitstream Vera family) will not look as good as it used to. I still haven't figured out what's wrong with Calibri and Cambria for me (and Corbel never looked bad anyway).

Hope this helped.

---

