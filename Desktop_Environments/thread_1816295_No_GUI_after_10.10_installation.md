---
title: "No GUI after 10.10 installation"
date: 2011-08-01
forum: Desktop Environments
---

### Post by Curnel_D on 2011-08-01
I'm trying to install 10.10 on a new laptop, but after each attempt to install, the GUI doesn't start after reboot.  

When rebooted after the install, I can login normally via prompt.  But if I try to start the GUI via xstart or gdm, it gives me a blank black screen.  

Any help is much appreciated.

---

### Post by Toz on 2011-08-01
What make/model computer do you have? Can you log into the terminal prompt, type in the following command to let us know what kind of video card you have?
```
lspci | grep VGA
```

---

### Post by Curnel_D on 2011-08-01
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834115994](http://www.newegg.com/Product/Product.aspx?Item=N82E16834115994)

---

### Post by Toz on 2011-08-01
It would be helpful if you could provide the results to the command from prompt #2.

Try booting with some kernel parameters. To test these parameters, follow the instructions here: [https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot]("https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot")

Try the following kernel parameters, one at a time (make sure you add them inside the last quote mark, space-separated from the other parameters):
[LIST]
[*]video=SVIDEO-1:d
[*]acpi_osi=Linux
[*]acpi_osi=\"Linux\"
[*]nomodeset
[*]xforcevesa
[*]i915.modeset=0 xforcevesa
[/LIST]

Do any of them work?

---

### Post by Curnel_D on 2011-08-02
How can I set grub to display on startup via terminal?

---

### Post by SuperGauntlet on 2011-08-02
> **Curnel_D said:**
> How can I set grub to display on startup via terminal?

You don't need to. You can hold shift during startup.

---

### Post by Curnel_D on 2011-08-02
> **Toz said:**
> It would be helpful if you could provide the results to the command from prompt #2.
Which prompt results do you want?   

> **Toz said:**
> 
Try booting with some kernel parameters. To test these parameters, follow the instructions here: [https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot]("https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot")

Try the following kernel parameters, one at a time (make sure you add them inside the last quote mark, space-separated from the other parameters):
[LIST]
[*]video=SVIDEO-1:d
[*]acpi_osi=Linux
[*]acpi_osi=\"Linux\"
[*]nomodeset
[*]xforcevesa
[*]i915.modeset=0 xforcevesa
[/LIST]

Do any of them work?

Just tried all of these; got same results.

---

### Post by Toz on 2011-08-02
> **Curnel_D said:**
> Which prompt results do you want? 

```
lspci | grep VGA
```

> Just tried all of these; got same results.
Just to confirm - you added these one at a time to the end of the linux line so that it looked something like:
```
linux /boot/mvlinuz-2.6.38-10-generic root=UID=1a45c3c5-e\
95c-4536-9c0q-dc4frf4frf4 ro splash quiet vt.handoff=7 xforcevesa
```

...and pressed Ctrl+x to boot?

---

### Post by Toz on 2011-08-02
Can you also try going back into the grub menu (via holding down the shift key), then: [LIST]
[*]press 'e' to edit the entry
[*]delete the line "set gfxpayload=$linux_gfx_mode" 
[*]then press "Ctr+x" (to boot the entry)
[/LIST]

Any luck?

---

### Post by Curnel_D on 2011-08-02
> **Toz said:**
> ```
lspci | grep VGA
```


Just to confirm - you added these one at a time to the end of the linux line so that it looked something like:
```
linux /boot/mvlinuz-2.6.38-10-generic root=UID=1a45c3c5-e\
95c-4536-9c0q-dc4frf4frf4 ro splash quiet vt.handoff=7 xforcevesa
```

...and pressed Ctrl+x to boot?
Yep

> **Toz said:**
> Can you also try going back into the grub menu (via holding down the shift key), then: [LIST]
[*]press 'e' to edit the entry
[*]delete the line "set gfxpayload=$linux_gfx_mode" 
[*]then press "Ctr+x" (to boot the entry)
[/LIST]

Any luck?
Nope

And thanks for the help in the mean time.

---

### Post by Toz on 2011-08-02
Ok. Edit the grub command line again and this time remove **splash quiet vt.handoff=7**. This should display bootup text on the screen as the system boots. Are any error messages displayed? Most likely just before the hang?

Also, if you have a chance, run the following command at the terminal prompt and post back the results:
```
lspci | grep VGA
```

---

### Post by Curnel_D on 2011-08-03
> **Toz said:**
> Ok. Edit the grub command line again and this time remove **splash quiet vt.handoff=7**. This should display bootup text on the screen as the system boots. Are any error messages displayed? Most likely just before the hang?
When running this param, bootup hangs instantly on a blinking cursor.  Nothing happens after.
Edit: I take that back.  It sits on the cursor for a while, then switches to a blank black screen after a bit. 

> **Toz said:**
> 
Also, if you have a chance, run the following command at the terminal prompt and post back the results:
```
lspci | grep VGA
```

VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

---

### Post by Toz on 2011-08-03
Been reading through: [http://ubuntuforums.org/showthread.php?t=1743535]("http://ubuntuforums.org/showthread.php?t=1743535"). Here's something that we haven't tried yet.

From the command prompt:
```
sudo nano /etc/default/grub
```
Add to the bottom of that file, this line:
```
GRUB_GFXPAYLOAD_LINUX=text
```
The update the grub files:
```
sudo update-grub
```

Reboot.

---

### Post by Curnel_D on 2011-08-03
Tried that, still didn't work.  

But.. I did manage to catch what looks like a few errors while messing around with it 

i915: gave up waiting for init of module intel_agp.
i915: unknown symbol intel_agp_enabled (err -16)
i915: gave up waiting for init of module intel_agp.
i915: unknow symbol intel_max_stolen (err -16)

---

### Post by Curnel_D on 2011-08-04
Fixed, "I Think".

After finally seeing some error messeges and being able to follow it to a similar issue thread, I found this. [http://ubuntuforums.org/showthread.php?t=1601023](http://ubuntuforums.org/showthread.php?t=1601023)

So now I'm definitely getting the GUI.  But... I honestly have no idea what effect this will have outside of the obvious.

---

