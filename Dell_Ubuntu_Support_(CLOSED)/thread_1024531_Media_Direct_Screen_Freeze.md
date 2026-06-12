---
title: "Media Direct Screen Freeze"
date: 2008-12-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mikull on 2008-12-29
okay, i went ahead and installed linux and wanted the usual media direct button to load linux and power button to boot vista.

did enough of re-search on these forums to get to know how to do it. 

here how my PT looks like.

1. recovery
2.vista(c:)
3.d: on vista(ntfs)
4.linux partition.

installed GRUB on linux partition(hd0,4)
rmbr 2 4
booted thru vista cd and did a bootrec /fixmbr and /fixboot.

after that when i pressed the power button,vista booted.
shut it down.
pressed the media direct button. the splash screen of media direct button came up and it was hung there. no key worked.waited for a while thinking that the GRUB timeout has to countdown to 0 and waited for like 10 min..nothing happend. same frozen screen. had 2 force it to shutdown by pressing the power button for 5sec. again i tried media direct,samething,hung..
i was like,let me try vista again. it worked. shut it,tried media direct button again and guess what,vista booted.
i had to putin the live cd and restore my grub (setup(hd0)) and that is how is it right now. could someone guide me on how to make my linux partition boot from the media center button now.
BTW i have media center 3.5
cheers

---

### Post by mikull on 2008-12-29
now even the media direct button is loading vista. WZF?!?!?

---

