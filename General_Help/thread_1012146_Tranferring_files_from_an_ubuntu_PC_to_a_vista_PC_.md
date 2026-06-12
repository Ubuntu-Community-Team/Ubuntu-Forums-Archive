---
title: "Tranferring files from an ubuntu PC to a vista PC via direct Ethernet cable"
date: 2008-12-15
forum: General Help
---

### Post by SomedoodIV on 2008-12-15
I don't really know if this should go in the networking section, so ill put it here.
Does anyone know how to be able to move files from an ubuntu (v8.10) PC to a Vista PC using a directly connected ethernet cable, as in a cable connected from one port to the other? I've been trying to get some files from the ubuntu PC to the vista PC?

---

### Post by hikaricore on 2008-12-15
I've heard of something similar being done before with a "cross over cable".

But, wouldn't it just be simpler to use a router?

---

### Post by SomedoodIV on 2008-12-15
> **hikaricore said:**
> I've heard of something similar being done before,
but wouldn't it just be simpler to use a router?
Well, that's pretty much my situation right now, i need to transfer some files and i dont have aw working router. Unless i could transfer the files via eSata.

---

### Post by SomedoodIV on 2008-12-15
Nevermind, i found a crossover cable and got it to work, but it keeps giving me an error "unable to mount c$", but still lets me browse and use the c:, should i just ignore the errors?

---

### Post by Kain000 on 2008-12-15
> **SomedoodIV said:**
> Nevermind, i found a crossover cable and got it to work, but it keeps giving me an error "unable to mount c$", but still lets me browse and use the c:, should i just ignore the errors?

I guess that depends, can you transfer files?

---

### Post by HermanAB on 2008-12-15
The easiest way to transfer files between two machines is with FTP.  You could install FileZilla client and server for that.

---

### Post by editrix on 2008-12-18
I do this all the time with Kubuntu 8.04 & a Win98 box, so while my GUI would be different from yours, it's the same under the hood.

I've given both boxes static IP addresses. It's been a while, but I'm pretty sure Ubuntu comes with an FTP client and/or server. And, I think, so does Vista. Worst case scenario, for Ubuntu it would be proftpd.

I use Konqueror, where I can split the view, and use one pane to see the Linux box and the other for the Windows box, then drag and drop files.

Don't know what you'd use with Gnome, but I'm sure there's something. With Vista, there may be permissions issues. Make sure the client and/or server is set up to allow anyone full access.

---

