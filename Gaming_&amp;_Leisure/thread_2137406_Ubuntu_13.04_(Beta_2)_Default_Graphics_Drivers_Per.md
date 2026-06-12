---
title: "Ubuntu 13.04 (Beta 2) Default Graphics Drivers Performance vs AMD (Read Inside)"
date: 2013-04-20
forum: Gaming &amp; Leisure
---

### Post by iTech278 on 2013-04-20
Hello!

I have used Ubuntu for a few years now, but am not able to access my Linux box at the moment, so I can't test this myself. I know that there have been improvements made to the out-of-the-box Linux drivers in Ubuntu 13.04, but has anyone tested to see how well these drivers handle gaming compared to the AMD Proprietary Drivers? If so, could you let me know which performed better? That would be great!

Thanks!

---

### Post by cRaZyBisCuiT on 2013-04-20
I can't test it myself but I read that the latest shipped radeon-drivers in combination with the 3.8 kernel are pretty much better then the ones in Ubuntu 12.04 & 12.10. Anyway, still the AMD proprietary driver is considered to be much faster. But that's just what phronix says. I have no source right now. And in addition: If you do use a AMD legacy card like the HD3000/HD4000 series, then the radeon shipped driver might be faster.

---

### Post by R33D3M33R on 2013-04-25
I'm using 13.04 with KDE and Radeon driver on an HD4670. Everything seems to work fine, but there seems to be a memory leak that hogs the system after few hours of inactivity. Tons of errors in dmesg and no other way than reset. I'm still looking into this issue and it also happened with 12.10. 

I'm also using 13.04 with KDE and fglrx from the AMD site on an HD7750. Everything works superb. Gaming performance and desktop responsiveness is amazing! I also didn't have issues installing it: just built the package, dpkg -i *.deb and sudo aticonfig --initial.

---

