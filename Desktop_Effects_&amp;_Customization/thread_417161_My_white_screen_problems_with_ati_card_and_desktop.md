---
title: "My white screen problems with ati card and desktop effects fixed"
date: 2007-04-21
forum: Desktop Effects &amp; Customization
---

### Post by trotur on 2007-04-21
I have a radeon 9800 card.

I got white screen because of the following bug: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684)

This is how I got things working:

1. Make sure you have open source "ati" drivers (howto: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver))

2. Do "lsmod | grep edac". If you get output containing i82875p_edac and edac_mc, blacklist them:
```
sudo gedit /etc/modprobe.d/blacklist
```
Add lines
```
blacklist i82875p_edac
blacklist edac_mc
```

3. Reboot and try desktop effects.

I also hadn't direct rendering working before doing this (not with "ati" nor with "fglrx" drivers). Hopefully this would resolve someone other's problems too.

---

### Post by ronocdh on 2007-04-21
> **trotur said:**
> I have a radeon 9800 card.

I got white screen because of the following bug: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684)

This is how I got things working:

1. Make sure you have open source "ati" drivers (howto: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver))

2. Do "lsmod | grep edac". If you get output containing i82875p_edac and edac_mc, blacklist them:
```
sudo gedit /etc/modprobe.d/blacklist
```
Add lines
```
blacklist i82875p_edac
blacklist edac_mc
```

3. Reboot and try desktop effects.

I also hadn't direct rendering working before doing this (not with "ati" nor with "fglrx" drivers). Hopefully this would resolve someone other's problems too.
Thank you for the post. This did not help me. I'm on a Radeon Mobility X1600 128MB; I still get the white screen of death every time I type "beryl-manager" in the terminal.

---

### Post by powder on 2007-04-23
> **trotur said:**
> 
This is how I got things working:

Thanks trotur.  I've got a Radeon 9550 and this solved my white screen problem.

---

### Post by trotur on 2007-04-23
> **ronocdh said:**
> Thank you for the post. This did not help me. I'm on a Radeon Mobility X1600 128MB; I still get the white screen of death every time I type "beryl-manager" in the terminal.

Maybe you should try to get effects working with fglrx driver and XGL since your card isn't supported by open source drivers. (I don't know how to do that but I have seen some howtos about the subject.)

---

### Post by schoene on 2007-05-03
I also have a Radeon  9800 Pro, and by using this method, I could enable direct rendering

thanks for the tip!

---

### Post by ThomThom on 2008-05-29
Does this apply to 8.04 as well?

I had desktop effects before I upgraded. Then I can't remember if it was the Ubuntu upgrade or something else I did that made the effects disappear.

Now I've finally managed to get the restricted ATI drivers to run, but as you, I get the white screen when I try to enable the effects. It returns to normal after about 20-30 seconds though.

I got an ATI Radeon 9800 card.

---

