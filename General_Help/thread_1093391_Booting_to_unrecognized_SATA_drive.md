---
title: "Booting to unrecognized SATA drive"
date: 2009-03-11
forum: General Help
---

### Post by bnordin on 2009-03-11
I set up Ubuntu on my desktop and then transfered the hard drive with the installation to my PVR.  The PVR bios isn't recognizing the drive, but the Ubuntu Live CD does.  Is there a way to boot my installation?

---

### Post by samborambo on 2009-03-11
You'd have to give more details. What motherboard are you running in your PVR? 

Try a couple of things:

[LIST=1]
[*]Set the jumper on the hard drive to SATA-1 only (150MB/s)
[*]Check the BIOS settings to make sure you haven't got RAID enabled on the SATA ports.
[/LIST]

---

### Post by bnordin on 2009-03-12
SOLVED!

I had actually given up on booting from the hard drive.  I was looking for a boot disk solution.  However, setting the drive to use SATA allowed the drive to boot.  Thanks!

For those who may come across this...  I had a SATA I motherboard with a SATA II hard drive.  I had to set a jumper (5-6 on Wester Digital) for the motherboard to recognize the drive.

---

