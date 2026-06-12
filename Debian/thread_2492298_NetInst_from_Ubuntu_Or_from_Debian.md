---
title: "NetInst from Ubuntu? Or from Debian?"
date: 2023-11-06
forum: Debian
---

### Post by ruwolf on 2023-11-06
I want to install Ubuntu + Debian blend.
Mostly pure Ubuntu, only snap packages from Debian (from regular deb repositories).
Can I use [Debian netinst]("https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/") for start?
I am asking, because I have not found any netinst for Ubuntu.

---

### Post by Tadaen_Sylvermane on 2023-11-07
While it may work somewhat it will ultimately fail. Debian and Ubuntu are not always binary compatible. You can build sources from debian on ubuntu usually, and vice versa. But installing packaged binaries via apt from both distros will only result in a mess at best, and a paperweight of an installation at worst.

---

### Post by SeijiSensei on 2023-11-07
Does Debian even have snap packages? I'm running Debian 12 on most machines these days, and all my software was (thankfully) packaged as debs.

---

### Post by Rubi1200 on 2023-11-07
Why would Debian have snap packages?

Snap packages are developed and maintained by Canonical.

If you are looking for a Debian/Ubuntu hybrid there are probably easier ways to go about it than what you propose.

Take a look on Distrowatch, there is probably something there that would suit your needs.

---

### Post by ruwolf on 2023-11-07
Of course, I know [DistroWatch Search]("https://distrowatch.com/search.php") and its ability to find distributions based on Ubuntu. 
Sadly, I cannot find option in it for distributions with Chromium browser and without Snap packaging...

---

### Post by Rubi1200 on 2023-11-07
I'm not sure I understand what you want.

Does it have to be Ubuntu based?

Perhaps this website can help you decide what you are looking for:
[https://distrochooser.de/](https://distrochooser.de/)

---

### Post by #&amp;thj^% on 2023-11-07
If I understand you correctly these are good choices IMHO:
EDIT: These listed below are snap free, but can very well use them if desired.
[https://www.linuxliteos.com/](https://www.linuxliteos.com/)

[https://linuxmint.com/](https://linuxmint.com/)

[https://pop.system76.com/](https://pop.system76.com/)

And of Debian, if that's to slow for you you can always add Testing sources.

---

### Post by SeijiSensei on 2023-11-07
> **ruwolf said:**
> Sadly, I cannot find option in it for distributions with Chromium browser and without Snap packaging...
Let me make the case for Debian 12. It has no snaps, and you can install Chromium on it with
```

apt update
apt install chromium

```
Debian doesn't use sudo like Ubuntu does. You create a root password during installation and become root with the traditional "su" command.

---

### Post by #&amp;thj^% on 2023-11-07
I second the above case use, and while I can't speak for SeijiSensei, the testing sources have been real stable for me

---

### Post by SeijiSensei on 2023-11-07
I just have a vanilla repository setup (except for the choice of server):
```

Hit:1 http://debian.csail.mit.edu/debian bookworm InRelease
Get:2 http://debian.csail.mit.edu/debian bookworm-updates InRelease [52.1 kB]
Hit:3 http://security.debian.org/debian-security bookworm-security InRelease

```
So far none of the packages I routinely use have been unavailable.

I'm using KDE Plasma as my desktop, just as I did with Kubuntu.

---

### Post by ruwolf on 2023-11-07
Debian is great, but stable packages can be in quite obsolete versions.
I will try Ubuntu with Debian stable and testing repositories (only for those, which are in Ubuntu exclusively by Snap).
 By pinning I will prefer stable before testing.

---

### Post by ian-weisser on 2023-11-07
> **ruwolf said:**
> Mostly pure Ubuntu, only snap packages from Debian (from regular deb repositories).

Seems like an ordinary Ubuntu system.

If you can find "snap packages from Debian," they should run just fine on Ubuntu. Broad cross-platform and cross-version compatibility is a key feature of snap packages.

> **ruwolf said:**
> I will try Ubuntu with Debian stable and testing repositories (only for those, which are in Ubuntu exclusively by Snap).

Well, that seems less wise. Mixing Ubuntu and Debian apt sources and deb packages creates a Frankensystem, the #1 practice to avoid on [Don't Break Debian]("https://wiki.debian.org/DontBreakDebian#Don.27t_make_a_FrankenDebian").

---

### Post by SeijiSensei on 2023-11-08
Unless there are features in newer software releases that you need, or security holes have been fixed, I see little reason to stay abreast of the latest-and-greatest versions of most software. 

On Ubuntu, I always rely on releases with long-term support like 22.04. By your standards, that software is probably very dated. Since it does what I need, I don't care.

Once again, there are no snap packages for Debian.

---

### Post by ruwolf on 2023-11-08
> **ian-weisser said:**
> Well, that seems less wise. Mixing Ubuntu and Debian apt sources and deb packages creates a Frankensystem, the #1 practice to avoid on [Don't Break Debian]("https://wiki.debian.org/DontBreakDebian#Don.27t_make_a_FrankenDebian").
Thank you for your warning, I know it.
I have used mixes like Debian stable + testing or PureOS + Debian without serious issues. I have ported Debian to Ubuntu without reistall or vice versa. too.
(In "snap packages from Debian," I have meant packages, which are in Ubuntu only in snap package, I will install ordinary deb from Debian.)

---

