---
title: "USplash problems after 2.6.17 kernel upgrade. Splashy not working"
date: 2006-08-12
forum: Desktop Environments
---

### Post by phenolholic on 2006-08-12
Hello,
I recently installed 2.6.17.7 and as a result, my usplash is not working. All I get is a blank screen, which then goes into X after the boot sequence. I tried installing splashy, and that didn't help much either. Same thing with splashy, just a blank screen. Can someone give me the rundown on installing usplash from scratch? I've found threads here and there but none seemed to have worked. So I would like the entire process from scratch if possible. TIA

---

### Post by xXx 0wn3d xXx on 2006-08-12
1. Do you have vesa graphics enabled in your kernel ?

2. Did you select the boot up logo option while compiling your kernel ?

3. Have you tried re-installing usplash ?

---

### Post by phenolholic on 2006-08-13
1) Vesa is enabled.

2) I did not mess with the boot up logo option. If that is enabled by default, then yes I have it enabled.

3) I tried re-installing usplash, but with no results. Still the blank screen.

---

### Post by vijirajan on 2006-08-13
It turned out that the Boot up logo options is not on by default. You have to enable it.

Device Drivers -> Graphics Support -> Logo configuration -> Boot up logo

---

### Post by phenolholic on 2006-08-13
That means I need to recompile the kernel?

---

### Post by vijirajan on 2006-08-14
I tried rebuilding 2.6.17.8 kernel with Boot up logo option enabled but I still get a blank screen.

---

### Post by llamakc on 2006-08-14
Do you have the appropriate line for splash in menu.lst?

---

### Post by phenolholic on 2006-08-15
yes i do. i've given up on splashy as i've found it's buggy, as per other posts. anyway, my usplash is in text mode, how does one enable the default graphic splash screen on usplash?

---

### Post by Azathoth_ on 2006-09-04
I think it cannot be showed in this kernel. I have the same problem and I cannot enable this

---

### Post by heavyt on 2006-09-04
> **phenolholic said:**
> Hello,
I recently installed 2.6.17.7 and as a result, my usplash is not working. All I get is a blank screen, which then goes into X after the boot sequence. I tried installing splashy, and that didn't help much either. Same thing with splashy, just a blank screen. Can someone give me the rundown on installing usplash from scratch? I've found threads here and there but none seemed to have worked. So I would like the entire process from scratch if possible. TIA

Had the same problem with 2.6.17.7 here is the fix that help me.
this method was suggested by gborzi

type: sudo nano -w /etc/mkinitramfs/modules

and add these modules to the list (if they are not already there): 
```
capability
 vesafb 
fbcon 
unix
```
then```
sudo dpkg-reconfigure <name of your kernel>
```

Note, for me the second code gave me an error. I had luck with (it took about 5 mins, I have a slow chip)
```
sudo dpkg-reconfigure usplash
```

---

