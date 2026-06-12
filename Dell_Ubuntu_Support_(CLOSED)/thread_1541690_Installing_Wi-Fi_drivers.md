---
title: "Installing Wi-Fi drivers"
date: 2010-07-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by javamaniac on 2010-07-29
Hi. I've got ubuntu-10.04-desktop-amd64 release and I'm trying to permanently replace currently installed windows 7 (no dual boot). I can easily install Ubuntu, but unfortunately I have access only to wireless network/internet connection, witch means that I can't use it unless there's an appropriate wi-fi driver installed.

So the question is: how to install wireless drivers on ubuntu 10.04 x64 if I'm running dell inspiron i14r-2265 and can't connect to internet after installation from ubuntu because of absence of wi-fi drivers?

Thanks in advance.

---

### Post by CoolJohnB on 2010-07-29
Try going to System>Administration>Hardware Drivers, the wireless driver should be listed there and will be installed automatically when you click on it.

Hope that works for you.

---

### Post by gamepanther on 2010-07-30
I had the same problem how i fixed it was connect in ubuntu using an ethernet cable and install all updates. then i clicked sytem,administration and then Hardware Drivers next still with the ethernet connected i installed the sta driver

---

### Post by ptn107 on 2010-07-31
I had to copy the following packages from the install CD to my desktop and then manually install them to get wireless working. The Hardware Drivers applet would not show anything because it complained about not having sources to get the drivers from:

/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_amd64.deb
/pool/main/d/dkms/dkms_2.1.1.2-2fakesync1_all.deb
/pool/main/p/patch/patch_2.6-2ubuntu1_amd64.deb

and from ~/Desktop/
```
sudo dpkg -i *.deb
```

I'm sure it may have been easier to just add my install CD to apt via apt-cdrom but this was faster for me.

*Note you will have to do the following [just this once] to make the driver load after a restart:
```
echo "wl" | sudo tee -a /etc/modules
```

**Keep in mind I'm running 64-bit.

---

### Post by ugm6hr on 2010-07-31
Just to check - it is sensible to confirm your wifi card with the output from:
```
lspci
lshw -class network
```

Obviously, any solution given is often specific to a driver, and any laptop is often sold with a number of different component options. Hence, by giving this output, you can confirm before installing any drivers.

---

### Post by stanz on 2010-10-08
Is this solved?
I also have only wireless, but when using the livecd--that driver manager came and offered the drivers.
So after install, and nothing from the hardware driver manager, I added the cd of 10.04 to synaptic package manager,
and soon after the wireless was working...and updates followed!
I loaded the same as *ptn107 *

---

### Post by jjkohl on 2010-10-15
[SOLVED]

So I followed this forum, and I got my wireless driver installed and it is active, but my wireless is still disabled and when i right click the connection button on the row on top, it says enable wireless, but its gray and It won't let me.

I ran that code two posts previous and it definitely says my wireless is disabled. Any ideas how to enable it?

product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation

---

### Post by gibbylinks on 2010-10-17
Have you tried the keyboard function keys ? On my Inspiron 1501 it's the "Fn" & "F2" keys at the same time The symbols on my keyboard are in blue.

The "F2" key has a little wireless symbol on it. The key combination turns my wireless card on and off, which cause my wireless card LED to go on and off.

Hope that helps.

---

