---
title: "Advice on changing from NVidia to ATi to make update to 8.10 practicable"
date: 2008-10-22
forum: Desktop Environments
---

### Post by eurgain on 2008-10-22
Hi

There is a well-known problem with using OpenOffice (and some others including Eclipse) under KDE4.x and NVidia 3D drivers.  This combination causes major display corruption, and is well-known.  The bug seems to reside in X, but at present only the 3D Nvidia drivers seem to trigger it. The bug is not cured by X7.4, KDE4.1.2, by OOo 3, nor by any combination of the above.

Since OOo is, for me, the number one application, this effectively blocks an upgrade to 8.10, which is a shame because it has features that I want.  My conclusion is that I need to move away from NVidia.

The Intel i910 card in my latptop suits me just fine, but there is no equivalent PCIE card, which is a shame because it is ideal for my needs.

I know nothing about ATi cards, and I am finding it difficult to discover which cards are well supported.  On researching the matter seems to have uncovered a schism between those who think ATi cards are a Good Think and those that hate them.  There are so many different numbers and versions, I am now totally confused.

Can anyone recommend a well-supported ATi card that will do compositing for desktop effects, will not be used for gaming, and which installs easily under Kubuntu?  I must have a silent card - that is, with no fan.

A

---

### Post by krazyd on 2008-10-22
R500 and earlier chips are fully supported by the open source driver. That is, they will play video well, compositing works well and 3D is working, if not quite up to the same speed as the closed source driver. This includes all X1xxx cards (eg. I have an X1600 that works out-of-the-box with 8.10).

Newer cards than this, including the HD 2xxx, HD 3xxx and HD 4xxx cards are not fully supported by the open source driver. Video accelleration and 3D do NOT work with these cards.

The closed source driver (fglrx) is faster (for 3D) than the open source drivers but it is quite buggy, and exhibits 'tearing' on video playback.

See [here]("http://en.wikipedia.org/wiki/Radeon") for an explanation of the ATI card versions, and [here]("http://wiki.x.org/wiki/radeon") (currently seems to be down, try [this]("http://72.14.235.104/search?q=cache:D94KzrGdqhQJ:www.x.org/wiki/radeon+http://wiki.x.org/wiki/radeon&hl=en&client=firefox-a&gl=au&strip=1") mirror) for more info on the open source driver. A detailed feature matrix for the open source driver is [here]("http://www.x.org/wiki/RadeonFeature") ([mirror]("http://72.14.235.104/search?q=cache:vkPE4hX_vhsJ:wiki.x.org/wiki/RadeonFeature+http://www.x.org/wiki/RadeonFeature&hl=en&client=firefox-a&gl=au&strip=1")).

Note: though fglrx is apparently faster for 3D than the open source driver, nexuiz still runs great on my card! :)

---

### Post by eurgain on 2008-10-22
> **krazyd said:**
> R500 and earlier chips are fully supported by the open source driver. That is, they will play video well, compositing works well and 3D is working, if not quite up to the same speed as the closed source driver. This includes all X1xxx cards (eg. I have an X1600 that works out-of-the-box with 8.10).

Newer cards than this, including the HD 2xxx, HD 3xxx and HD 4xxx cards are not fully supported by the open source driver. Video accelleration and 3D do NOT work with these cards.

The closed source driver (fglrx) is faster (for 3D) than the open source drivers but it is quite buggy, and exhibits 'tearing' on video playback.

See [here]("http://en.wikipedia.org/wiki/Radeon") for an explanation of the ATI card versions, and [here]("http://wiki.x.org/wiki/radeon") (currently seems to be down, try [this]("http://72.14.235.104/search?q=cache:D94KzrGdqhQJ:www.x.org/wiki/radeon+http://wiki.x.org/wiki/radeon&hl=en&client=firefox-a&gl=au&strip=1") mirror) for more info on the open source driver. A detailed feature matrix for the open source driver is [here]("http://www.x.org/wiki/RadeonFeature") ([mirror]("http://72.14.235.104/search?q=cache:vkPE4hX_vhsJ:wiki.x.org/wiki/RadeonFeature+http://www.x.org/wiki/RadeonFeature&hl=en&client=firefox-a&gl=au&strip=1")).

Note: though fglrx is apparently faster for 3D than the open source driver, nexuiz still runs great on my card! :)
Thanks for your thorough response.  The numbering is far from simple, as I thought!

Now, the next challenge is to find a fanless card.

Regards
Alistair

---

### Post by krazyd on 2008-10-22
Whoops, re-reading my post - it's a little unclear. The latest cards *are* supported by the proprietary fglrx driver from AMD/ATI. Just not by the open source driver.

---

### Post by eurgain on 2008-10-23
> **krazyd said:**
> Whoops, re-reading my post - it's a little unclear. The latest cards *are* supported by the proprietary fglrx driver from AMD/ATI. Just not by the open source driver.

That opens up my choice a bit!  Thanks, A.

---

