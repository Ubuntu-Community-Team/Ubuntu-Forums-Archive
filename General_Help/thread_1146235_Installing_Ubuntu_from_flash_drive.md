---
title: "Installing Ubuntu from flash_drive"
date: 2009-05-02
forum: General Help
---

### Post by demontager on 2009-05-02
I have created USB startup disk with USB Startup disk creator, used Ubuntu 9.04 amd64, when i boot from flash receive: password requered, what i should to do?

---

### Post by codeseer on 2009-05-02
That's a boot disk, not an install disk.

Use this: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by delcypher on 2009-05-02
That's odd looks more like the BIOS requesting a password rather than the USB start up disc. Does your BIOS have any options on it that require a password to be entered if you try to boot off external media?

I've made a USB start up disk before and that's never happened.

Besides the possible BIOS issue, did you format the USB stick before using the "Create USB start up disc" first?

What .iso image did you use to make the USB start up disc?

---

### Post by demontager on 2009-05-02
> **delcypher said:**
> That's odd looks more like the BIOS requesting a password rather than the USB start up disc. Does your BIOS have any options on it that require a password to be entered if you try to boot off external media?

I've made a USB start up disk before and that's never happened.

Besides the possible BIOS issue, did you format the USB stick before using the "Create USB start up disc" first?

What .iso image did you use to make the USB start up disc?
I used Ubuntu 9.04 x86_64.iso. I used unetbootin as well, same issue. Before i boot from other usb media containing windowsXP and install it normally, this is not a problem with my Bios.

---

### Post by demontager on 2009-05-02
> **codeseer said:**
> That's a boot disk, not an install disk.

Use this: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
I done it before, same as with Usb Start up disk creator

---

### Post by codeseer on 2009-05-02
> **demontager said:**
> I done it before, same as with Usb Start up disk creator

Any of your drives encrypted?

---

### Post by demontager on 2009-05-02
> **codeseer said:**
> Any of your drives encrypted?
No, i never use such one

---

### Post by codeseer on 2009-05-02
> **demontager said:**
> No, i never use such one

Is your USB drive encrypted? Sometimes they have a little switch or something on the side of them.

What happens when you just enter a blank password?

What happens when you enter your password that is on the system you used to create the disk?

Do you have a BIOS password set? If so, what happens when you enter that?

---

