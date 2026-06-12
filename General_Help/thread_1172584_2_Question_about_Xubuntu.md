---
title: "2 Question about Xubuntu"
date: 2009-05-28
forum: General Help
---

### Post by Gadgetboy on 2009-05-28
1. I have an ATI radeon x800 graphics card. Is there a way to install this graphics card without reinstalling xubuntu?

2. How do I setup a static ip in Xubuntu? I can find guides for Ubuntu but they don't work for Xubuntu.

---

### Post by Gadgetboy on 2009-05-28
Bump

---

### Post by Gadgetboy on 2009-05-28
bump

---

### Post by kerry_s on 2009-05-28
> **Gadgetboy said:**
> 1. I have an ATI radeon x800 graphics card. Is there a way to install this graphics card without reinstalling xubuntu?

2. How do I setup a static ip in Xubuntu? I can find guides for Ubuntu but they don't work for Xubuntu.

1.) just pop it in, xorg will auto load the driver.

2.) i think you can edit /etc/network/interfaces with something like this:

```

allow-hotplug eth0
iface eth0 inet static
address x.x.x.x
network x.x.x.x
gateway x.x.x.x
broadcast x.x.x.x
netmask x.x.x.x

```

replace "x" with you actual numbers.

---

### Post by Gadgetboy on 2009-05-28
All that file say right now is 
```

auto lo
iface lo inet loopback

```

If I replace it with what you suggested would it work, or would it mess it up?

---

### Post by kerry_s on 2009-05-29
> **Gadgetboy said:**
> All that file say right now is 
```

auto lo
iface lo inet loopback

```

If I replace it with what you suggested would it work, or would it mess it up?

no it go's under it. leave a space between. you need that for the loop back.

---

