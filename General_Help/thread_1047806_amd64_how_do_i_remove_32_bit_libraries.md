---
title: "amd64: how do i remove 32 bit libraries?"
date: 2009-01-22
forum: General Help
---

### Post by Miles_Prower on 2009-01-22
I have an amd64 system, and recently installed psx on it. It needed some 32 bit libraries, so I let getlibs handle it. getlibs installed gvfs, and now pSX works great. However, nautilus is now totally fubar-ed. I can no longer:
view samba shares
browse the network
browse the... trashcan?!?
I've got pSX up and running on my secondary machine (32 bit), so now I just want gvfs to leave my amd64 alone. Can I just go to the lib32 directory and delete everything that's gvfs-related? That seems really dirty...

---

### Post by Miles_Prower on 2009-01-22
no one seems to know how to do this. Or everyone here hates me because I keep asking how. I don't know, but my OS has been rendered next to worthless. Can I get some help?

---

### Post by Yashiro on 2009-01-22
Open synaptic, file, history and find which stuff you installed. Then remove it.

---

### Post by Miles_Prower on 2009-01-22
not sure if getlibs uses synaptic, but synaptic didn't seem to know anything about the install. I just un/reinstalled ubuntu-desktop and now it seems better. samba's still kind of broken, but it's always been kind of finicky to me.

---

