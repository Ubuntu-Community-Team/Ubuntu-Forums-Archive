---
title: "Ibex mounting my USB Storage device as a picture CD?"
date: 2008-11-01
forum: Desktop Environments
---

### Post by SimbaSpirit on 2008-11-01
When I mount my NTFS non-system partition (on same drive as Vista and Intrepid) and open it using nautilus I get the little popdown saying "These Files are on a Picture CD [Open with F-Spot Photo Manager].

   How can I either rectify this or disable this checking?
Going to preferences and disabling everything relating to image handling (even in the dropdown "Picture CD") doesn't do anything (I also closed and re-opened the window, as well as just refreshing).


   One other small bit of functionality I'm not sure how to set up is using the media buttons on my mouse (forward, backward. Works in FF) in Nautilus. I don't see any bindings in the preferences nor under Keyboard Shortcuts (was worth a try...). Does anyone know where the proper binding setting would be?

Thanks,
-SS

---

### Post by Reg67 on 2008-11-04
This happens to me as well after upgrading to ibex when I mounted a remote drive with sshfs. It also seems to then set the free space to 0 bytes, despite the fact there are around 250 free gigs on the remote drive.

Any ideas?

---

### Post by ndale686738 on 2008-12-01
This happens when i access my permanently mounted data drive regardless of the folder i am in. it is very annoying. anyone know how to get rid of it?

---

### Post by elgreengeeto on 2008-12-04
I have the same thing happening in Intrepid with an s3fs mount.

I would love to learn how to turn all of these popdowns off!

---

### Post by rosj04 on 2008-12-04
Have the same problem. Quite annoying. All the folders are picture cd's it says.

---

### Post by Atzu on 2008-12-04
Any idea??? I have the same problem with my usb storage (Fat 32).

---

### Post by SamNSane on 2008-12-05
It appears that Intrepid Ibex will call any entity with a "Pictures" folder at its root a Picture CD. Change the name of the folder, the problem goes away.

Weird.

---

