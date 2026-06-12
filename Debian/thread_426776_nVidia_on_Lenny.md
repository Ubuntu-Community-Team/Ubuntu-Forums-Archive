---
title: "nVidia on Lenny"
date: 2007-04-28
forum: Debian
---

### Post by CocoAUS on 2007-04-28
I recently switched from Ubuntu to Debian (which is EFFING AWESOME), but the guides that I've found for installing the proprietary nVidia driver are all weak and outdated, always presenting me with steps that give me errors.  Is there an easy, sure-fire way to install the nVidia driver on Lenny (besides the official binary)?

Also, Beryl runs slowly on Lenny, but ran fine on Sid.  Is there an option to speed it up?  I could go without a 3D desktop, but Beryl really does increase productivity, especially when there are tons of windows open on the desktop.

Thanks ahead of time!

---

### Post by bwhite82 on 2007-04-28
You will find the Debian community to be more tight-lipped about non-free/proprietary software and drivers. It is mainly because Debian prides itself on being completely free. With that said, most of the Ubuntu guides on any given subject will easily apply to Debian as well. As far as Beryl being slow in Lenny, after you install your driver, you will find that the slowness will be gone.

If you need help, feel free to post here or on the Debian forums, [http://forums.debian.net](http://forums.debian.net)

---

### Post by Pobega on 2007-04-28
> **Soldierboy said:**
> http://forums.debian.net[/url]

Or email [email]debian-user@lists.debian.org[/email] if you have other problems. Although generally, simpler questions are more suited for the forums than the mailing list.

---

### Post by CocoAUS on 2007-04-28
Thanks for the responses.

I actually ran Beryl on my last Lenny install (which I broke) after I installed the nVidia driver, so the driver wasn't the answer.  As far as installing the driver as in Ubuntu, it seems that there's some mix-match between the kernel and the driver?  Simply installing nvidia-glx doesn't work.

---

### Post by bwhite82 on 2007-04-28
> **CocoAUS said:**
> Thanks for the responses.

I actually ran Beryl on my last Lenny install (which I broke) after I installed the nVidia driver, so the driver wasn't the answer..

It more than likely *is* the problem if you used the driver from Debian's non-free repository because it's an older version. What you need to do is find a guide on the Ubuntu wiki for compiling the latest Nvidia driver from nvidia.com and give that a whirl. If that is not the problem, then I would head for either a mailing list or IRC.

EDIT: Try here: [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Or here (Debian-specific):[ http://wiki.serios.net/wiki/Debian_NVIDIA_proprietary_display_driver_installation_using_NVIDIA's_installer]("http://wiki.serios.net/wiki/Debian_NVIDIA_proprietary_display_driver_installation_using_NVIDIA's_installer")

---

### Post by CocoAUS on 2007-04-28
Thanks for the info.  I guess I should've realized the testing repo's would have an older version.  Thanks again for the help.

---

### Post by plb on 2007-04-29
[http://wiki.debian.org/NvidiaGraphicsDrivers](http://wiki.debian.org/NvidiaGraphicsDrivers)

---

