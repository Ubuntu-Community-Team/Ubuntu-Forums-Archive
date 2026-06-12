---
title: "Ati Radeon Xpress 200M SLOW UI"
date: 2008-12-26
forum: General Help
---

### Post by h377r1d3r on 2008-12-26
Hi;
System: Compaq Presario with ATI Xpress 200M
OS: Ubuntu 8.10
Drivers: Ati 8.12 fglrx latests.

Problem: Slow UI, no 2D acceleration.

What I did so far: different versions of fglrx, boot from live ubuntu CD (It uses radeon drivers to compare whether xorg radeon drivers would be faster) different configurations of xorg.conf. I'm using simplest UI, no compiz; Tried kubuntu, xubuntu - the same problem.

I have searched forums already for weeks, and so far I have not ide how to get it working, so that I don't have to wait three seconds from clicking to bookmarks to seeing them.
Whole system feels sluggish, all windows are rendering slowly.

Any help would be appreciated. I will do anything to get this sorted out.

---

### Post by ethann on 2009-03-22
I have been having exactly the same question..I have checked so many forum posts, but I am sorry, the answers given there all imply to me one thing:

"*Experiment with your precious laptop, and hopefully it will work. If not, try that other thing that may work or may not*"

Something more clear?:confused: Anybody? No answers?

---

### Post by mpsii on 2009-03-22
Did some googling:

Article concerning how the BIOS sets up the RAM for the video card for an ATI XPRESS 200M:
[http://www.ensode.net/ati_radeon_xpress_200m_linux.html](http://www.ensode.net/ati_radeon_xpress_200m_linux.html)

Release notes show the XPRESS 200 to be a "mobility" or "integrated" chipset and supported by the latest drivers:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

---

### Post by ethann on 2009-03-23
> **mpsii said:**
> Did some googling:

Article concerning how the BIOS sets up the RAM for the video card for an ATI XPRESS 200M:
[http://www.ensode.net/ati_radeon_xpress_200m_linux.html](http://www.ensode.net/ati_radeon_xpress_200m_linux.html)

Release notes show the XPRESS 200 to be a "mobility" or "integrated" chipset and supported by the latest drivers:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

Thanks for the good reply! I read on the first link from ensode.net that you provided, that this BIOS setting will solve the 3D acceleration issue. I was wondering, how about plain 2D issues, because the problem I am experiencing is exactly with plain simple things. Windows take too long to load, and it takes a looong time to open a menu panel such as "applications" or "places"; even with only metacityin its simplest settings!

Or maybe it is not an ATI Radeon Xpress 200 issue at all, and I am looking for a solution at the wrong direction?

---

