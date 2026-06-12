---
title: "Ubuntu 9.04 causing Overheating"
date: 2009-04-28
forum: General Help
---

### Post by Johnnyftw on 2009-04-28
I was wondering why this is happening, I have Windows Vista and Windows 7 and they both do not make my computer overheat.

I have a ATI x1950 Pro AGP, It seems when I use Compiz it runs for a short bit and then locks up. I put my hand upto my Videocard and it's piping hot! It doesnt do this in Vista or Windows 7, or when gaming.

---

### Post by Johnnyftw on 2009-04-28
No one knows?

---

### Post by jako on 2009-04-30
Had similar problem with a HP nc8430, ati graphics (X1600) with xserver radeon driver, i.e. open source. Put option "DynamicClocks" "on" in my xorg.conf, solved problem. With the propietary driver I'd always used aticonfig to throttle things, but of course that's not possible now.

---

