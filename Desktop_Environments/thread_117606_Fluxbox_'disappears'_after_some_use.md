---
title: "Fluxbox 'disappears' after some use??"
date: 2006-01-15
forum: Desktop Environments
---

### Post by happogiri on 2006-01-15
Hello,

I installed fluxbox from Ubunty breezy package (.deb from debian site) and everything works fine for sometime, but then the bar (from lower part of screen) disappears and menu doesn't work anymore (if I press right mouse button, I get the gnome desktop thingy). The programs that are open remain, backgroung stays etc... What could it be?

---

### Post by bonzodog on 2006-01-15
Are you by chance opening nautilus? That automatically knocks out the native desktop, and inserts it's own. It's VERY annoying..I try to avoid using it in windowmaker.

---

### Post by happogiri on 2006-01-15
Hey... that might be! I'm now on my desktop comp with windows I can't try but will open my laptop soon!

---

### Post by syklitengutt on 2006-01-15
when opening nautilus from terminal do this:
nautilus --no-desktop

---

### Post by happogiri on 2006-01-15
Thanks again, does it work if I put that also in my launcher bar icon?

---

### Post by syklitengutt on 2006-01-15
if you edit the starter to 
nautilus --no-desktop 
Im doing that.... works like a charm

---

