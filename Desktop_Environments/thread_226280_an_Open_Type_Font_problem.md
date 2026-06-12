---
title: "an Open Type Font problem"
date: 2006-07-31
forum: Desktop Environments
---

### Post by AV1611 on 2006-07-31
Greeting to all!
What do I have:
an amd64 comp, debian 3.1r1, ubuntu 6.06 amd64 installed off of the desktop-cd & alternate cd (to separate partitions, sure), openoffice 2.0.2 (ubuntu's/debian's one and generic one - both at ubuntu and debian), openoffice 2.0.3 (the same way: distro native's one and generic one), an Open Type (Cyrillic) Font - 3 OTF files: Bold, Italic, Underlined. 
Our task is to get linux ooo working with this font.
Our steps (were done at each one of the linuxes):
1. adding our font through KDE Control Center -> Font installer.
2. Copying OTF font to the coresponding dirs at /usr/share/fonts with "mkfontdir && mkfontscale && fc-cache" commands following.
3. installling utilities & libs for open type fonts work: libotf0, libotf-bin, libotf-dev, lcd-typetools, libffreetype6, fondu.
After performing step no. 3  my font showed up correctly at Debian openoffice 2.0.2 font's list (generic one only - an TGZ archive extracted to a dir). All the others ones (Ubuntu; and also generic debian's native 2.0.2, 2.0.3 and debian's generic openoffice_2.0.3) didn't give me a positive answer ;)
Generally, openoffice can't work with OTF (and that's a known bug; and you can't solve it with manual copying your font to /usr/share/fonts etc, as you can with the other types of fonts), but I could get debian's ooo to work with it (displaying more or less correctly), but it's strange thing: WHY ubuntu can't do the same?

---

