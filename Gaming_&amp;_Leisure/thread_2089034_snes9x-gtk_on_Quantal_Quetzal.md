---
title: "snes9x-gtk on Quantal Quetzal"
date: 2012-11-28
forum: Gaming &amp; Leisure
---

### Post by viperdvman on 2012-11-28
Last year when Ubuntu 11.10 was released, **snes9x-gtk** was dropped from the Ubuntu repositories. However, a PPA came out that allowed people to install the latest (or close to) snes9x-gtk for Ubuntu 11.10, 12.04, and earlier Ubuntus.

Link to Bearoso's snes9x-gtk PPA:
[https://launchpad.net/~bearoso/+archive/ppa]("https://launchpad.net/~bearoso/+archive/ppa")

However, click on that link and we see that there is no package for Ubuntu 12.10. That means that any distro based on Ubuntu 12.10 can no longer install snes9x-gtk even from the PPA.

One would have to go to this website here (**[link]("http://snes9x.ipherswipsite.com/")**) to download it, and then either run it as a straight execute (Linux 32-bit & 64-bit), or compile it from source.

[COLOR="Navy"]Has anyone had any success compiling snes9x-gtk from source in (K)(X)(L)Ubuntu 12.10?[/COLOR] I certainly haven't. And I really **don't** want to have to use the inferior _zsnes_ nor the "tough to get roms running" _bsnes_ which requires me to manually change all my roms.

note: *I have made a couple attempts to try and compile it from source when I was running Kubuntu 12.10 (before I went back to Precise). But I may not have had the right required packages to successfully compile it and make install.*

---

### Post by WorLord on 2012-11-28
> **viperdvman said:**
> Link to Bearoso's snes9x-gtk PPA:
[https://launchpad.net/~bearoso/+archive/ppa]("https://launchpad.net/~bearoso/+archive/ppa")

However, click on that link and we see that there is no package for Ubuntu 12.10. That means that any distro based on Ubuntu 12.10 can no longer install snes9x-gtk even from the PPA.[/I]

Easiest thing to do: use the Precise PPA version of the app.  Works 100 percent.  

Add the PPA in the usual way, and then go back and change "quantal" to "precise" and reload your sources.  Should be good to go.

---

### Post by viperdvman on 2012-11-28
I will have to test that next time I run Quantal in a live environment. If the Precise package works, then I could always just download the .deb package and install that :)

If it does work like you're saying it does, then who needs to compile? :D

---

### Post by viperdvman on 2012-11-29
> **viperdvman said:**
> I will have to test that next time I run Quantal in a live environment. If the Precise package works, [COLOR=Red]**then I could always just download the .deb package and install that **[/COLOR]:)

If it does work like you're saying it does, then who needs to compile? :D

I tested the suggestion out and ran a test in a LiveUSB session of Kubuntu 12.10. I downloaded the correct .deb file *(in this case, the precise-amd64 file)*, made sure I had all the dependencies, and installed the .deb file directly. snes9x-gtk ran very well on Quantal.

So there ya have it. Instead of adding Bearoso's PPA, you could always go to [https://launchpad.net/~bearoso/+archive/ppa](https://launchpad.net/~bearoso/+archive/ppa) and grab the precise .deb package yourself.

---

