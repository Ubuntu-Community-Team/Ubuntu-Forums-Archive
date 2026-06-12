---
title: "Sometimes fails to boot, *ERROR* atombios stuck"
date: 2011-04-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aeronutt on 2011-04-23
When booting into 10.10 or 11.04, Dell Vostro 3350 goes to black screen and stops. It seems to hang on the following, (found from booting into recovery mode, copied from dmesg):

```
[   18.470689] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
[   18.470750] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CCAE (len 62, WS 0, PS 0) @ 0xCCCA
[   23.467247] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
[   23.467308] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CCAE (len 62, WS 0, PS 0) @ 0xCCCA
[   28.463804] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
[   28.463862] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CCAE (len 62, WS 0, PS 0) @ 0xCCCA
[   33.460362] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
[   33.460420] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CCAE (len 62, WS 0, PS 0) @ 0xCCCA
[   38.456921] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
[   38.456980] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CCAE (len 62, WS 0, PS 0) @ 0xCCCA
[   43.453479] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
[   43.453538] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CCAE (len 62, WS 0, PS 0) @ 0xCCCA
```

Some laptop specifics:
Dell Vostro 3350
Intel Core i3-2310M
3GB DRAM
AMD Radeon HD 6630M 1G Graphics
And the file above was from failure to boot into 10.10, specifics:
Linux jjjj-Vostro 2.6.38-02063802-generic #201103281246 SMP Mon Mar 28 14:09:46 UTC 2011 i686 GNU/Linux

Any ideas?  Frustrating having to reboot multiple times. This problem seems much worse booting into Natty/11.04 beta-2, but it certainly does occur under 10.10.

---

### Post by aeronutt on 2011-04-24
Any ideas?

---

### Post by sauthess on 2011-04-26
Hi,

I do not know if you find a solution but I have too a lot of problem because of 2 graphics shipsets integrated to my laptop (HD 5470 + core i5).

I do not know if your radeon is well supported (mine isn't so I deactivated it...), you can try blacklisting radeon at boot time : 

echo "blacklist radeon" > /etc/modprobe.d/blacklist-radeon.conf 
update-initramfs -u

other possibility is to deactivate modesetting for radeon (but I do not understand why it's a solution as without modesetting you :
- do not have vga_switcheroo so you can't deactivate radeon card
- you can't use radeon with full features...

I speak about it because I see post that indicate this as a solution...

I found your post by chance because I have trouble with vga_switcheroo under 11.04 (for your information if you want to try it ....)

Regards,

---

### Post by aeronutt on 2011-04-26
sauthess, thanks for your response. I'm still having problems. One thing I've realised, is that the boot problems under 10.10 are different than under 11.04. So...I'm waiting a few days to see if stable release of Natty will help in any way. It does seem all my problems are around the graphics accelerators in Sandy Bridge and AMD Radeon.  I'm disapointed that Windows supports these, and clues are that these won't get fully supported until 11.10. But we'll see. Thanks again.

---

