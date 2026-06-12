---
title: "How to install on laptop having no DVD Drive"
date: 2009-01-07
forum: General Help
---

### Post by UranUtan on 2009-01-07
Hi,

How can I install Ubuntu on a laptop which doesn't have an optical drive?

HP Compaq nc4200 Notebook PC
[http://h18000.www1.hp.com/products/quickspecs/12137_na/12137_na.HTML](http://h18000.www1.hp.com/products/quickspecs/12137_na/12137_na.HTML)

Thanks in advance for any help.

---

### Post by dcstar on 2009-01-07
> **UranUtan said:**
> Hi,

How can I install Ubuntu on a laptop which doesn't have an optical drive?

HP Compaq nc4200 Notebook PC
[http://h18000.www1.hp.com/products/quickspecs/12137_na/12137_na.HTML](http://h18000.www1.hp.com/products/quickspecs/12137_na/12137_na.HTML)

Thanks in advance for any help.

Create a Live USB drive using the inbuilt tools (on another Ubuntu PC), and use that bootable USB for the install.

---

### Post by UranUtan on 2009-01-07
> **dcstar said:**
> Create a Live USB drive using the inbuilt tools (on another Ubuntu PC), and use that bootable USB for the install.

It's that simple? I plan to buy this laptop. Not having it in hands yet. So I assume I set the BIOS to boot on USB and the laptop could boot and install Ubuntu like from a CD?

---

### Post by dcstar on 2009-01-07
> **UranUtan said:**
> It's that simple? I plan to buy this laptop. Not having it in hands yet. So I assume I set the BIOS to boot on USB and the laptop could boot and install Ubuntu like from a CD?

Should be, the USB is basically a Live CD (but with persistence) and contains all the install files.

People do this on things like the eee-pc, as it has no CD drive.

---

### Post by theozzlives on 2009-01-07
> **UranUtan said:**
> It's that simple? I plan to buy this laptop. Not having it in hands yet. So I assume I set the BIOS to boot on USB and the laptop could boot and install Ubuntu like from a CD?

If the laptop can boot from USB.

---

### Post by CaesarLike on 2009-01-07
USB boot works for me on my Acer Aspire One :))

---

### Post by Drubie on 2009-01-07
> **dcstar said:**
> 
People do this on things like the eee-pc, as it has no CD drive.

And the dell inspiron 9 mini, but there is an option for ubuntu 8.04 preloaded

---

### Post by Drubie on 2009-01-07
> **dcstar said:**
> Create a Live USB drive using the inbuilt tools (on another Ubuntu PC), and use that bootable USB for the install.

btw, what are said inbuilt tools called/where can I access them?

---

### Post by Harii on 2009-01-07
Another way is--

Here is what i had to do:
An hard drive swap--i had a bad cd drive
then swap back and
> sudo dpkg-reconfigure xserver-xorg

just another way?

---

### Post by dcstar on 2009-01-07
> **Drubie said:**
> btw, what are said inbuilt tools called/where can I access them?

It is the USB creator in the 8.10 System menus.

---

### Post by compman25 on 2009-01-07
unetbootin is a real easy way to make a USB flashdrive bootdisk

---

### Post by Drubie on 2009-01-08
> **dcstar said:**
> It is the USB creator in the 8.10 System menus.

No wonder I couldnt find it - Im running 8.04.   duh...
that would be a really nifty thing to have - ooh I could play a really cruel practical joke on a friend... 
[color=white]blarg[/color]

---

