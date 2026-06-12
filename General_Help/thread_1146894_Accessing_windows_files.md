---
title: "Accessing windows files"
date: 2009-05-03
forum: General Help
---

### Post by logicalform on 2009-05-03
Hey guys,
I'm new to Linux and am loving Ubuntu. My question is about accessing the media files I have under Windows. I used Wubi to install Ubuntu 9.04. The Wubi faq says that I should be able to find my files in /host and /media, but what I want (my music files - 30gbs or so) doesn't seem to be there unless I'm just really dumb... What do I need to do to be able to retrieve my media?

Thanks in advance.

---

### Post by DeMus on 2009-05-03
> **logicalform said:**
> Hey guys,
I'm new to Linux and am loving Ubuntu. My question is about accessing the media files I have under Windows. I used Wubi to install Ubuntu 9.04. The Wubi faq says that I should be able to find my files in /host and /media, but there's nothing in those folders. What do I need to do to be able to play all of my media? Is it not possible?

Thanks in advance.

You have a double boot with some kind of Windows version?
If so, part of your disk is taken by Windows, or you have a separate disk for Windows and one for Linux.

Make sure no Windows disk is mounted already. If you have a disk mounted already right-click it and select unmount.

Open Synaptic package Manager in System - Administration, type your password, let it start completely and use search. Search for ntfs-config
Mark the little square box in front of it with your left mouse button and choose install, accept the other programs which need to be installed as well. Then use the Green Apply button on top.

When installed open it in System - Administration. Click the drives you want to mount and select OK, then check the tick-box which says it is okay to write on internal drives and select OK again.
You ow have your ntfs drive(s) mounted which mean they can be reached from with in Ubuntu. This will also stay like that the next time you reboot.

---

### Post by logicalform on 2009-05-03
Hey, DeMus, thanks for the quick reply. I'm not sure if the method you described will work in my case because I'm not exactly dual booting. I used Wubi to install Ubuntu within Windows (however that works...) which the Wubi website says should allow me to access my files automatically. Do you think that enabling NTFS partitions would help me?

---

### Post by DeMus on 2009-05-03
> **logicalform said:**
> Hey, DeMus, thanks for the quick reply. I'm not sure if the method you described will work in my case because I'm not exactly dual booting. I used Wubi to install Ubuntu within Windows (however that works...) which the Wubi website says should allow me to access my files automatically. Do you think that enabling NTFS partitions would help me?

I have no experiences with Wubi whatsoever and also don't know how this works. I hope somebody else who also uses it can help you. Sorry.

---

### Post by logicalform on 2009-05-03
NP, thanks for the info though. At least I know how to mount NTFS partitions now, haha.

---

### Post by sgtlange on 2009-05-05
I have a similiar question that i am hoping can be answered by demus. Not to steal a thread either. But i have installed a dual boot via dowloading the iso from the website and burning to a disk and the intalling and partitioning within the installer. My problem is the drive that i believe has windows files on it shows up empty in my /media/windows folder that was created for the mount. This drive cannot be unmounted due to it is the one ubuntu itself runs under. The only problem i had with the ntfs-config is my manager had a problem saying it could not be marked for installation because of unresolvable dependencies and said this:

ntfs-config:
 Depends: libdbus-1-2 (>=0.60) but it is not installable

I have libdbus -1 -2 installed but unsure what >=0.60 means.

Maybe using ntfs config will help?

---

### Post by XProflmfao on 2009-07-05
My problem's similiar to yours but a little bit more complicated than that. When I downloaded Ubuntu, I decided to only use Ubuntu and removed Windows from my PC. What I didn't know was that that removed all my old files, or that it hides it somewhere in my computer. I can't seem to find my old files, such as pictures, etc. Any help would be great, thanks.

---

### Post by merlinus on 2009-07-05
If you chose "use entire disk" during installation, then yes, everything is gone.

You might be able to use testdisk or photorec to recover some of the files, but it is unlikely.

---

