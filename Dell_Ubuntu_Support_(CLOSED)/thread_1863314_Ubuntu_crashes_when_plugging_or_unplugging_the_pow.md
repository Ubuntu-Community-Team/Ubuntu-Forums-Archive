---
title: "Ubuntu crashes when plugging or unplugging the power adapter"
date: 2011-10-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by emarco on 2011-10-17
I have a Dell Inspiron Duo and installed Ubuntu 11.10 on it by using Wubi. When I connect or disconnect the power adapter ubuntu crashes. How can I solve this problem?

---

### Post by grc01 on 2011-10-18
The computer freezes or crashes?

---

### Post by grc01 on 2011-10-18
If the computer freezes, the problem is related to the PM-UTILs. You will have to revert to the 1.3.0 of the Lucid distro and lock it .
Here is the procedure:

  	 	 	 	 	 	  

 
[LIST=1]
[*]Open up Synaptic Package Manager
[*]Settings > Repositories > 	Other Software, then add the following:
[*]deb 	[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main
[*]“Reload” the package list
[*]Find “pm-utils” then go to 	Package > Force Version.. and select 1.3.x
[*]Install the downgraded package
[*]Find “pm-utils” again, go to Package > Lock Version
[/LIST]

---

### Post by emarco on 2011-10-23
Thanks for yore help. The computer crashes: it dumps a lot of messages on a black screen and halts. I have to power it off. I am running ubuntu 11.10 (Oneiric Ocelot).

---

### Post by jfgomez on 2011-10-23
Hello, I have the same problem that you, I'm really thinking in change 11.10 to 11.04 or 10.XX, could you solve the problem?

---

### Post by emarco on 2011-10-24
Not, yet. I am going to test the above suggestion which, as I uderstand, would allow me to run an outdated (but functional) version of PM-utils while running 11.10. I'll be back with news after that.

---

### Post by emarco on 2011-10-24
Ok, gentlemen. I tried the downgrade of the pm-utils and worked fine: now I can plug or unolug the power adpater with no inconvenience. Thanks for the recommendation. 

Anyway, I think this solution should be treated as a walk-around and the problem reported as a bug.

---

### Post by jfgomez on 2011-10-24
Hello emarco,
May you explain us what steps do you follow?, I Deactivate the acpi support from the grub and it works for me. 

in the file:
/etc/default/grub 
Let the follow line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **clocksource=hpet acpi=off noacpi**"

Other question:
Do you use the dock?

---

### Post by emarco on 2011-10-26
Hello, jfgomez. After testing these days the different recommendations, the outcomes are:
1. Downgrading the pm-utils package, finally, did not solve the problem because it presented again.
2. I tried the acpi deactivation and, up to the moment, the problem disappeared. The battery icon in the upper bar went away.
3. I tried to solve the problem, having the acpi activated, by downgrading the package acpi-support (the scripts to handle acpi events) but the problem continued.
4. Then, so far, the only solution is the acpi deactivation. I will include this in the bug report.

---

### Post by christiaan_ on 2011-11-03
Hello emarco and jfgomez,

I tried your solution switching ACPI off - but this is not such a great idea on a laptop. But then re-edited the GRUB line and the bit about the **clocksource** works perfectly to solve the problem on it's own.

My GRUB line looked like this :

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **clocksource=hpet** usbhid.quirks=0x00eef:0x725e:0x40"
```

I updated grub and all worked perfectly - plugging in and out of power. All icons and ACPI active. The **usbhid.quirks** part in the GRUB line is from a forum post to help identify the touchscreen correctly. Without this line the touchpad / Touchscreen does not work correctly.

Thanks for the clue.

update:

Strange thing was that I could not get it to work by changing the GRUB file back to default and re-trying the fix.

Now I cannot get it to work again.

---

### Post by tompaten on 2011-11-14
I'm having the same problem on 11.10, but it isn't limited to the latest Ubuntu.

I also had the same problem on Sabayon 7 and Fedora 16. Remove the unit from wall power and it spits out some kind of memory dump and completely locks up. It looks pretty similar no matter what distribution I use.

---

### Post by jfgomez on 2011-11-16
> **grc01 said:**
> If the computer freezes, the problem is related to the PM-UTILs. You will have to revert to the 1.3.0 of the Lucid distro and lock it .
Here is the procedure:

  	 	 	 	 	 	  

 
[LIST=1]
[*]Open up Synaptic Package Manager
[*]Settings > Repositories > 	Other Software, then add the following:
[*]deb 	[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main
[*]“Reload” the package list
[*]Find “pm-utils” then go to 	Package > Force Version.. and select 1.3.x
[*]Install the downgraded package
[*]Find “pm-utils” again, go to Package > Lock Version
[/LIST]

This is de best solution, because is a kernel problem and the past version  works fine.

---

### Post by mahlerchiro on 2012-02-27
I altered the quiet splash line in grub and now it seems to work I am using Ubuntu 11.10 on a dell duo but am not using grub to get touch screen working so I was able to modify the grub line. Used Ubuntu dell duo remix thread to get tough screen working. grub modification is no longer needed in 11.10

Add: Had the same problem in mint 12 but switched back before finding this solution.

---

