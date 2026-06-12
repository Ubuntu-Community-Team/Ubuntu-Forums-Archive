---
title: "Black screen with blinking cursor in top left corner"
date: 2023-02-08
forum: Desktop Environments
---

### Post by jfc-junior on 2023-02-08
[COLOR=#333333][FONT=monospace]Dear friends,[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Please, I need to solve this very serious problem, which is happening with the installation of my Ubuntu 22.04, Kernel 5.15.0-58-generic, NVIDIA RTX 2060 SUPER 8GB, 64GB Memory, 02 Intel Xeon E5 v3/core i7 physical processors, each with 12 cores, HD SSD).[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]After updating the system "sudo apt" (update, upgrade, autoremove and clean) I worked normally on my PC, during the whole afternoon and the day after starting it, lightdm does not start, there is a black screen with the cursor blinking on the top left corner.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]I've done everything, including installing the nvidia driver version 525.85.05 and it still didn't work.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]I even changed the /etc/X11/xorg.conf file and it didn't work.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]I changed /etc/default/grub adding the parameters "i915.enable_dc=0 intel_idle.max_cstate=2", and it didn't work either...[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]I changed the monitor cables to "Display Port, HDMI and DVI" and that didn't work either...[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Note: I downloaded the "Ubuntu 22.04 x86_64.iso" image from the Ubuntu website, mounted the OS on a bootable USB stick and was able to run Ubuntu perfectly with a perfect graphical environment.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]However starting the initialization/boot by the PC itself does not open the Lightdm desktop...[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]I'm desperate because I don't know where else to look and what to do.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]I'm almost giving up...[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Help me please!!![/FONT][/COLOR]

---

### Post by ActionParsnip on 2023-02-08
I'd start with removing the proprietary NVidia driver and rebooting, you can then reinstall it

---

### Post by jfc-junior on 2023-02-08
> **ActionParsnip said:**
> I'd start with removing the proprietary NVidia driver and rebooting, you can then reinstall it

[COLOR=#232629][FONT=-apple-system]Thanks friend, I did the procedure you indicated, I removed the NVIDIA downloaded from the [/FONT][/COLOR]**nvidia.com website and installed the one from the Ubuntu repository, but it didn't work. So I installed [B]GDM3 - commad: apt install ubuntu-gnome-desktop set it as default, but it didn't work either... **[/B]:(:(:(

---

