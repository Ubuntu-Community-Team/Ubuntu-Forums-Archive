---
title: "[SOLVED] old nvidia card- driver help"
date: 2007-07-21
forum: Desktop Effects &amp; Customization
---

### Post by dbbolton on 2007-07-21
i have an old desktop (3-4 years) with integrated nvidia graphics. the identifier in my original xorg.conf called it "nVidia Corporation NV18 [GeForce4 MX - nForce GPU]".

back in the hayday of edgy, i somehow got the nvidia driver installed (i downloaded a binary from the nvidia site) and even got beryl working. i have since had to wipe the hard drive, and after that i installed feisty.

basically, i want to get the nvidia driver installed again and play around with some compositing stuff, just to see what the machine is capable of. i need to know which version of the nvidia driver i need to download from their site, or whether there is a package in the repos that i can install.

i tried the package nvidia-glx-legacy but i had no x server after i specified the nvidia driver in my xorg.conf

---

### Post by hyperair on 2007-07-22
Use nvidia-glx instead of nvidia-glx-legacy. Your card is supported by that driver. After you've installed nvidia-glx instead, restart your X server, and if it fails, go to the terminal (Ctrl+Alt+1) and post the outputs of:
```
dmesg| grep nv
```
and
```
sh -x /sbin/lrm-video nvidia
```

Also, attach the file "/var/log/Xorg.0.log".

---

### Post by dbbolton on 2007-07-22
> **hyperair said:**
> Use nvidia-glx instead of nvidia-glx-legacy. Your card is supported by that driver. After you've installed nvidia-glx instead, restart your X server, and if it fails, go to the terminal (Ctrl+Alt+1) and post the outputs of:
```
dmesg| grep nv
```and
```
sh -x /sbin/lrm-video nvidia
```Also, attach the file "/var/log/Xorg.0.log".
after i install nvidia-glx , do i need to change the driver from "nv" to "nvidia" in my xorg.conf ?

---

### Post by dbbolton on 2007-07-22
ok, i tried changing the driver to "nvidia" and x crashed.

```
dmesg| grep nvidia

[ 43.043893] nvidia: module license 'NVIDIA' taints kernel
```

```
sh -x /sbin/lrm-video nvidia

+ PATH=/sbin:/bin
+ MODULE=nvidia
+ shift
+ [ nvidia = nvidia ]
+ [ -e /lib/linux-restricted-modules/.nvidia_legacy_installed ]
+ [ -e /lib/linux-restricted-modules/.nvidia_new_installed ]
+ XORG=nvidia
+ cat /etc/X11/xorg.conf
+ sed -n -e /^[ \t]*section[ \\t]*"device"/I,/^[ \t]*endsection/I{/^[ \t]*driver[ \t]*/I{s/^[ \t]*driver[ \t]*"*//I;s/"*[ \t]*$//;p}}
+ grep -q -w nvidia
+modprobe --ignore-install -Qb nvidia
```

---

### Post by dbbolton on 2007-07-22
also, here is the log file

---

### Post by hyperair on 2007-07-23
Do this: ```
sudo nvidia-xconfig --add-argb-glx-visuals --allow-glx-with-composite --composite
``` in a terminal and restart your X server. Then I need the Xorg.0.log immediately after the crash if it crashes again. Because this log shows you using the nv driver. You can copy the xorg.0.log over to your desktop using this command:

```

cp /var/log/X11/Xorg.0.log ~/Desktop

```

And you can access a terminal using Ctrl+Alt+F1. To get back to your X server, use Ctrl+Alt+F7.

---

### Post by dbbolton on 2007-07-23
ah, ok. here is the file right after the crash.

---

### Post by hyperair on 2007-07-23
What happens when you try to do this?
```
sudo modprobe nvidia
```

And could you also provide the /etc/X11/xorg.conf file? Also, the dmesg output has to be AFTER the X server has crashed.

---

### Post by dbbolton on 2007-07-23
after i did 'sudo nvidia-xconfig --add-argb-glx-visuals --allow-glx-with-composite --composite' , i restarted X and it crashed. i hit ctrl+alt+f1 to access the terminal. when i did 'sudo modprobe nvidia', it didn't print anything. the dmesg output was
```
[ 43.043893] nvidia: module license 'NVIDIA' taints kernel
```i attached the xorg.conf that induced the crash.

---

### Post by hyperair on 2007-07-24
Ok how about:
```

sudo dpkg-reconfigure -phigh xserver-xorg
sudo nvidia-xconfig -add-argb-glx-visuals --allow-glx-with-composite --composite

```

Also please post your "/etc/defaults/linux-restricted-modules-common" file.

---

### Post by dbbolton on 2007-07-24
after i did those commands and restarted X, it still crashed.

the only uncommented line in '/etc/default/linux-restricted-modules-common' is:

```
DISABLED_MODULES=""
```

---

### Post by hyperair on 2007-07-25
Strange. After the "sudo modprobe nvidia" could you check the output of "lsmod | grep nvidia" and try restart the server if there's output?

---

### Post by dbbolton on 2007-07-25
> **hyperair said:**
> Strange. After the "sudo modprobe nvidia" could you check the output of "lsmod | grep nvidia" and try restart the server if there's output?
the output was:
```

nvidia          4715860     0
i2c_core          22656     3     nvidia, i2c_ec, i2c_nforce2
nvidia_agp          9500     1
agpgart          35400     2     nvidia, nvidia_agp
```

after i restarted x, it crashed.

---

### Post by hyperair on 2007-07-25
And it gets stranger. Oo Your nvidia module is loaded, but your X server refuses to recognize it. I wonder what's the problem. Do you have the nvidia-glx package installed or nvidia-glx-legacy?

---

### Post by dbbolton on 2007-07-25
> **hyperair said:**
> And it gets stranger. Oo Your nvidia module is loaded, but your X server refuses to recognize it. I wonder what's the problem. Do you have the nvidia-glx package installed or nvidia-glx-legacy?
i have nvidia-glx installed. i purged nvidia-glx-legacy before installing nvidia-glx, too. :/

---

### Post by dbbolton on 2007-07-31
> **dbbolton said:**
> i have nvidia-glx installed. i purged nvidia-glx-legacy before installing nvidia-glx, too. :/
well hyperair, thank you very much for your help. it's really appreciated. 

can you think of any other resources that might be helpful for me to figure out whats going on?

---

### Post by hyperair on 2007-07-31
Hmm at this point you could try this:
```
sudo apt-get remove --reinstall linux-restricted-modules-`uname -r`
```

---

### Post by dbbolton on 2007-08-01
i should have done this a long time ago: when x crashed, i selected "yes" when it asked me whether i wanted to review the x server output to diagnose the problem. it told me:
```
  Error: API mismatch: the NVIDIA kernel module has the version 1.0-9639, but the X module has the version 1.0-9631
```the prior is the version that i downloaded from the nvidia site to install manually, because i thought that was the version i had used on feisty. so i downloaded 9631 from the nvidia site and installed it manually. it seems to be working fine now.

thank you very much for all the help!

---

