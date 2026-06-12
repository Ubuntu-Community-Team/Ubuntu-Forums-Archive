---
title: "Gnomebaker problems"
date: 2006-08-03
forum: Desktop Environments
---

### Post by akshaysrinivasan on 2006-08-03
Hi,i just installed the gnomebaker 0.5.1 and when i run it ,it gives me error 
message saying GThread can be initialized only once.what does that mean any remedies?it was working fine on breezy,so i don't suspect any hardware problem.

pluto@pluto-desktop:~$ gnomebaker

(gnomebaker:6315): Gdk-WARNING **: locale not supported by Xlib

(gnomebaker:6315): Gdk-WARNING **: cannot set locale modifiers
GTK Accessibility Module initialized

GThread-ERROR **: GThread system may only be initialized once.
aborting...
Aborted
pluto@pluto-desktop:~$

---

### Post by croak77 on 2006-08-03
That's a known bug. A solution was posted on the Mailing List.

"The problem is gnomebaker is not getting along with the accessibility
 module. If accessibility support is not a requirement for you, it can be
 disabled with the gconf-editor. The relevant key
 is /desktop/gnome/interface/accessibility. Uncheck the box and then
 restart your session."

Hope that helps.

---

### Post by akshaysrinivasan on 2006-08-04
Hurrah its back.thanks a lot.if it hadn't worked i would've had to download k3b and the kdelibs(which crash a lot).

---

