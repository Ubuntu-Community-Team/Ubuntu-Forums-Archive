---
title: "I think I found a bug in GNOME menu"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by flashman2006 on 2007-10-20
OS: Ubuntu 7.10 (Gutsy)

Intro: I was playing around with the GNOME 'Applications' menu and attempting to add 'Python (v2.5)' to the a sub menu under 'Applications' (which already had another application in it, 'Eclipse'), but it did not work. The sub menu 'Programming' was blank (no text or icons, but it looked like both applications there but invisible)

GNOME MENU
Applications
      Programming      <- sub menu
             Eclipse                    <- Invisible (no text/icon)
             Python (v2.5)            <- Invisible (no text/icon)

I then determined that it was the entry 'Python (v2.5)' that was causing the problem. But this only happens when there are exactly TWO entries in a sub menu (not more not less). So something is up with GNOME, or maybe it's just that my installation is missing like 4 lines of code or something. It's a small problem I know, but this could happen to others and I'm new to this whole bug thing so how should I contact the programmers about this?

'Python (v2.5)' entry variations that also cause the same problem:
'PaTaaa (v2.5)'
'Python (va.d)'

But these work for:
'PaTaib (v2.5)'
'PaTaij (v2.5)'
'Python(v2.5)'

It might just be the arrangement of certain characters that causes this.

---

