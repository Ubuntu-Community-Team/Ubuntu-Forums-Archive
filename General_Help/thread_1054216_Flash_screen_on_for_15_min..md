---
title: "Flash screen on for 15 min.?"
date: 2009-01-29
forum: General Help
---

### Post by Camilia on 2009-01-29
My flash screen stays on for 15min when booting up. 

Anybody know how to decrease the time of this?

---

### Post by Tomatz on 2009-01-29
> **Camilia said:**
> My flash screen stays on for 15min when booting up. 

Anybody know how to decrease the time of this?

You mean the splash screen?

---

### Post by Camilia on 2009-01-29
> **Tomatz said:**
> You mean the splash screen?

Yeh, I think that is what it is. It is the orange serene that comes before my screen picture.

):P Little 1, so cute!!!

---

### Post by Slim Odds on 2009-01-29
You should boot without "splash" and maybe also "quiet".

Then you can see what's going on when it's hanging......

These are options passed to the kernel.

---

### Post by Tomatz on 2009-01-29
Thanks :)

Open a terminal and run these two commands:

```
sudo update-alternatives --config usplash-artwork.so
```

Then

```
sudo update-initramfs -u
```

Reboot

;)

---

### Post by Camilia on 2009-01-29
> **Tomatz said:**
> 
```
sudo update-alternatives --config usplash-artwork.so
```
;)

 Nothing to configure is what I got.

> **Tomatz said:**
> 
sudo update-initramfs -u[/CODE]
;)

Got only this Generating /boot/initrd.img-2.6.24-23-generic

---

### Post by Camilia on 2009-01-29
> **Slim Odds said:**
> You should boot without "splash" and maybe also "quiet".

Then you can see what's going on when it's hanging......

These are options passed to the kernel.

I have no idea how to that.

---

### Post by Slim Odds on 2009-01-29
> **Camilia said:**
> I have no idea how to that.

Reboot... when you get to GRUB.. press Escape (don't miss it or you're have to reboot again).

Select 'e' to edit...
Select <Down> to get to the default boot item.
Select 'e' again to edit that item and then backspace over "splash" and "quiet". (press enter when done).
Select 'b' to boot with this configuration.

See where it hangs......

---

### Post by Camilia on 2009-01-30
Problem solved!!  Thanks all!!

---

### Post by Slim Odds on 2009-01-30
> **Camilia said:**
> Problem solved!!  Thanks all!!

What was the problem?

---

