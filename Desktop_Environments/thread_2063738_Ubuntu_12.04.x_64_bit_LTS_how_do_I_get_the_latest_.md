---
title: "Ubuntu 12.04.x 64 bit LTS: how do I get the latest GNOME?"
date: 2012-09-27
forum: Desktop Environments
---

### Post by Welly Wu on 2012-09-27
I added the GNOME3 PPA and I wanted to know how I can get the latest version of GNOME desktop environment for Ubuntu 12.04.1 64 bit LTS. I currently have GNOME 3.4.1. I want to get GNOME 3.6.0 or higher. How do I do this?

---

### Post by Frogs Hair on 2012-09-27
3.6 was released only yesterday so it may take a little time to update any PPAS. [http://news.gnome.org/](http://news.gnome.org/)

---

### Post by cariboo on 2012-09-27
There's a soon to be Ubuntu sponsored Gnome remix, that just went to beta, avaiable [here]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Beta"). I haven't updated yet, but I'm quite impressed with the alpha so far.

---

### Post by orange2k on 2012-09-28
What interests me is whether Ubuntu 12.04 will get updated Gnome 3.6 at all, or will it be up to the user to use an alternative PPA like Ricotz's PPA...

---

### Post by rai4shu2 on 2012-09-28
Have they ever upgraded Gnome in an LTS? That would be a tough way to maintain a distro, I would think (always having to upgrade the whole desktop every six months).

---

### Post by orange2k on 2012-09-28
Thats true, well, I'll just have to use another way...

---

### Post by kio_http on 2012-09-28
> **orange2k said:**
> Thats true, well, I'll just have to use another way...

Alternatively you could move to 12.10 which seems wiser. Also if you are using KDE, I would advice you to use the newest possible KDE release as the performance and stability is improving release after release. LTS is not a wise option when it comes to KDE, then you get people complaining about old KDE bugs and how KDE is bad when the current state is light years ahead of what they are using.

---

### Post by snowpine on 2012-09-28
> **orange2k said:**
> What interests me is whether Ubuntu 12.04 will get updated Gnome 3.6 at all, or will it be up to the user to use an alternative PPA like Ricotz's PPA...

That's never been Ubuntu's policy; the expectation is that users will upgrade to 13.04 in the spring if they need Gnome 3.6 (or whatever version is current at that time). I don't think it's even going to be in 12.10 since there simply isn't enough time to test it thoroughly for next month's release. Certainly it will never be updated retroactively to 12.04.

---

### Post by mips on 2012-09-28
> **Welly Wu said:**
> I added the GNOME3 PPA and I wanted to know how I can get the latest version of GNOME desktop environment for Ubuntu 12.04.1 64 bit LTS. I currently have GNOME 3.4.1. I want to get GNOME 3.6.0 or higher. How do I do this?

You can't expect stable and the latest 3.6 in the same breath seeing it was released a few hours ago, your expectations are unrealistic. Either move to 12.10 or a bleeding edge distro.

---

### Post by Welly Wu on 2012-09-29
I added Ubuntu-Tweak and I just added the GNOME-Shell Testing PPA. I now have GNOME-Shell version 3.5.4. I expect that this PPA will get updated to GNOME 3.6.0 some time soon. Hopefully, I will have GNOME 3.6.0 without having to upgrade to Ubuntu 12.10 64 bit.

---

### Post by Welly Wu on 2012-09-29
I also added the GNOME Staging PPA.

---

### Post by kio_http on 2012-09-29
> **Welly Wu said:**
> I also added the GNOME Staging PPA.

If their staging ppa is like most others e.g Kubuntu, DO NOT ADD THAT!

It is used by package maintainers to test archives and build before moving into the regular repository. It is nearly always broken and is not intended to be used as a source for installing gnome.

From the Kubuntu staging ppa

> PPA description

For the love of the blue gears, DO NOT USE.
This is where we build and stage the packages for final PPA releases, so this PPA will never have usable packages.

---

### Post by Welly Wu on 2012-09-29
I removed it.

---

