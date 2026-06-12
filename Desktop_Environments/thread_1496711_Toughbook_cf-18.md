---
title: "Toughbook cf-18"
date: 2010-05-29
forum: Desktop Environments
---

### Post by elliotbeken on 2010-05-29
Hi all,

i have a panasonc toughbook cf-18 and have ubuntu 9.10 installed.

there are a few yey features missing like being able to right click with the touch screen and a good on screen keyboard...


does anyone have a set up or some applications that i can install and play with ??

thanks

---

### Post by sotirovlyu on 2010-06-06
Hi there,

Did you try the latest Ubuntu 10.4 with this panasonic? I'm trying to boot it with no luck.. on the other hand i booted lates backtrack linux (4), which i have some suspicion that is based on ubuntu 9.10.

cheers.

---

### Post by sotirovlyu on 2010-06-25
I solved the issue, it is realated to Intel 855GM chipset video driver. One has to use 
```
i915.modeset=1
```

kernel boot parameter to resolve the issue (a workaround though.. ).

---

### Post by alx9r on 2010-10-08
> **sotirovlyu said:**
> I solved the issue, it is realated to Intel 855GM chipset video driver. One has to use 
```
i915.modeset=1
```kernel boot parameter to resolve the issue (a workaround though.. ).

I confirm this works with the netbook LiveCD on my CF-18:
1.  Boot LiveCD.
2.  Press F6 when you see the two little icons at the bottom of the screen.  This'll bring you to the good old Boot Options screen.
3. Press F6 again to add [FONT=Courier New]i915.modeset=1[/FONT] to the Boot Option Configuration Line a la [https://help.ubuntu.com/community/LiveCDBootOptions#Changing%20the%20Boot%20Option%20Configuration%20Line]("https://help.ubuntu.com/community/LiveCDBootOptions#Changing%20the%20Boot%20Option%20Configuration%20Line").
4.  Boot.  Video should now work.

---

### Post by elliotbeken on 2010-12-21
i have just installed ubuntu 10.10 32-bit on my toughbook and everything works fine.

thanks

---

