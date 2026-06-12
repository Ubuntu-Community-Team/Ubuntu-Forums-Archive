---
title: "X-Plane with open source ATI drivers on 9.04?"
date: 2009-05-17
forum: General Help
---

### Post by akos.maroy on 2009-05-17
As I upgraded to 9.04, I can no longer use the fglrx drivers for my ATI card, as the new drivers don't support my card anymore (Mobility FireGL V5200 - interesting, this is only a 2 year old laptop). So I'm stuck with the open source driver.

I'm trying to make X-Plane work - it was OK with the old drivers on the same laptop. But now, with the open source driver, it's like 2 seconds / frame (not kidding).

interestingly, compiz, ioquake, other 3D applications seem to work fine. (of course, I'm turning off compiz when starting X-Plane or ioquake)

Has anyone had luck making X-Plane work with the open source video driver?

---

### Post by Legace on 2009-05-17
> **akos.maroy said:**
> Has anyone had luck making X-Plane work with the open source video driver?

Nope, you can't. The open source drivers lack support for 3D acceleration for newer cards. You'll either have to wait for that support to arrive or downgrade to 8.10..

---

### Post by akos.maroy on 2009-05-17
> **Legace said:**
> Nope, you can't. The open source drivers lack support for 3D acceleration for newer cards. You'll either have to wait for that support to arrive or downgrade to 8.10..

you say newer cards - but then, these cards are not supported by the binary driver, as they seem to be too for them?

I'm a bit confused :(

---

### Post by Legace on 2009-05-17
> **akos.maroy said:**
> you say newer cards - but then, these cards are not supported by the binary driver, as they seem to be too for them?

I'm a bit confused :(

ATi dropped support for cards prior to the HD2000 series, even though cards like X1650 (your card is based on the X1600 series)  are relatively new.

---

### Post by akos.maroy on 2009-05-17
I see..

how do I downgrade Ubuntu 9.04 to 8.10?

---

