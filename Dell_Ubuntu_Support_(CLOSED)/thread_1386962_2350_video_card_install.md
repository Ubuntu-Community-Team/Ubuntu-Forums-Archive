---
title: "2350 video card install"
date: 2010-01-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by PartsMan on 2010-01-21
I got my video card last night but it is not working.
The computer is a Dell 2350 2.0 celeron.
The card is a Zotac GeForce FX 5200 256mb.[http://www.zotacusa.com/geforce-fx-5200-256mb-128-bit-ddr-250mhz-333mhz-zt-52fpc2n-hsl.html](http://www.zotacusa.com/geforce-fx-5200-256mb-128-bit-ddr-250mhz-333mhz-zt-52fpc2n-hsl.html)

When I turn the computer on the monitor doesn't even kick on if it is plugged into the card.
What's the problem?

---

### Post by lykwydchykyn on 2010-01-21
If you plug in to the onboard video does it come on?

It may be that you have to change a BIOS setting to get it to use the card.

---

### Post by PartsMan on 2010-01-21
Yes it still works on the integrated graphics. I can't find any graphics settings in the bios.
I saw a something online about updating the bios first. I tried that and can't get a floppy to boot.

---

### Post by lykwydchykyn on 2010-01-21
> **PartsMan said:**
> Yes it still works on the integrated graphics. I can't find any graphics settings in the bios.
I saw a something online about updating the bios first. I tried that and can't get a floppy to boot.

If you have Ubuntu installed you can upgrade a Dell BIOS without a floppy.

Since every howto I can find on this seems deficient in some way, I'll put brief instructions here:

 - Add these to your software sources:
```

deb http://linux.dell.com/repo cross-distro dell-firmware
deb http://linux.dell.com/repo karmic dell-software

```

 - refresh your repositories.

 - Open synaptic or your favorite package manager and search for the package "system-bios-<dell model>".  In your case it'd be dimension-2350.
Install the package and its dependencies.

 - At a command prompt, run this command:
```

sudo dellBiosUpdate

```

That's it.

---

### Post by PartsMan on 2010-01-21
=D>

You are awesome!

I am running Hardy now but need some of the features of 9.10.
I need the video for 9.10.

---

### Post by lykwydchykyn on 2010-01-21
> **PartsMan said:**
> =D>

You are awesome!

I am running Hardy now but need some of the features of 9.10.
I need the video for 9.10.

If you're running hardy just change the "karmic" in that line to "hardy".  You'll get the same bios update, it just means the bios flashing software will be compiled for hardy.

I'm not sure what you mean that you need some of the features of 9.10; are you planning to upgrade?

---

### Post by PartsMan on 2010-01-21
Before the video quit on my 2400 I ran x9.10.
My PCI wireless adapter worked immediately and the later version of OpenOffice are the two biggest for me.

I am sure that with enough trouble I could get both in hardy but why not upgrade?

Edit: By upgrade I mean fresh install. I think upgrades are a horrible idea.

---

### Post by afrodeity on 2010-03-01
> **lykwydchykyn said:**
> If you have Ubuntu installed you can upgrade a Dell BIOS without a floppy.

Since every howto I can find on this seems deficient in some way, I'll put brief instructions here:

 - Add these to your software sources:
```

deb http://linux.dell.com/repo cross-distro dell-firmware
deb http://linux.dell.com/repo karmic dell-software

```

 - refresh your repositories.

 - Open synaptic or your favorite package manager and search for the package "system-bios-<dell model>".  In your case it'd be dimension-2350.
Install the package and its dependencies.

 - At a command prompt, run this command:
```

sudo dellBiosUpdate

```

That's it.

How do I know if it upgraded? I have a Dell Inspiron 2650. After I did

sudo dellBiosUpdate, there was no further information. Is that it? What else happens?

---

### Post by lykwydchykyn on 2010-03-01
> **afrodeity said:**
> How do I know if it upgraded? I have a Dell Inspiron 2650. After I did

sudo dellBiosUpdate, there was no further information. Is that it? What else happens?

It's possible you were already up to date.  If you look at the version of the BIOS you installed through the repos, it should be A09.  When you boot the machine, on the first screen that comes up (the one with the Dell logo), there should be an "A09" somewhere on the screen.  If it's lower than A09, something's not right.

EDIT: You can also check with this command:
```

sudo dmidecode |grep Version

```

Though IF it upgraded you probably need to reboot first.

---

### Post by afrodeity on 2010-03-02
Bios version is A13 as far as I can tell. Which is a 2007 Bios.

---

### Post by lykwydchykyn on 2010-03-02
> **afrodeity said:**
> Bios version is A13 as far as I can tell. Which is a 2007 Bios.

A13 appears to be the most recent BIOS, according the support.dell.com.  They don't update them very often, especially after the product's been out a few years.

That doesn't tell me why the  version in the repository is A09, but no harm no foul.

---

### Post by afrodeity on 2010-03-03
Thanks, one can only hope. I have Karmic installed only because ACPI is turned off.

---

