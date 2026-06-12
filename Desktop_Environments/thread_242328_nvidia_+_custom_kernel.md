---
title: "nvidia + custom kernel"
date: 2006-08-23
forum: Desktop Environments
---

### Post by matko on 2006-08-23
hello,

i compiled custom kernel. after that i installed nvidia driver from nvidia site. all succesfull. nvidia installer uses /usr/src/linux
to build driver and extensions.
but i want compile another kernel than means i will remove /usr/src/linux . i will also remove now used (my compiled) kernel to test new one. of cource i wll keep .deb packages. 

i would like to know how can I install nvidia when there will be another kernel source in /usr/src/linux.

Is enught if I keep only libglx.so nvidia_drv.so  nvidia_drv.o
from /usr/lib/xorg/modules/ ?

---

### Post by matko on 2006-08-29
I found no answers but i found good solution.

here is my solution how compile you kernel to work with nvidia kernel too.

this howto is good [http://ubuntuforums.org/showthread.php?t=217657&highlight=custom+kernel]("http://ubuntuforums.org/showthread.php?t=217657&highlight=custom+kernel")

hwto follow it.
just modification after step **3.**
Do this after step 3. to work you nvidia driver without other kernel needed installed .

```
cd /usr/src/linux
```

```
sudo cp /boot/config-`uname -r` .config && sudo make xconfig
```
```
cd /usr/src/
```
```
sudo apt-get install nvidia-kernel-source
```
unpack it
```
sudo tar xzvf nvidia-kernel-source
```

you can also create modules and drivers for other like 

[I]sudo apt-get install ndiswrapper-utils 
sudo apt-get install ndiswrapper-source[/I]
also for the other (optional)
*sudo tar -jxvf ndiswrapper-source.tar.bz2*

```
cd /usr/src/linux
```
```
sudo make-kpkg clean
```
```
sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers modules_image
```

replace custom with whaever you want (lama, mama, me) :mrgreen: 
<...................................................> compilation
after finnish move to folder
```
cd /usr/src
```
you should see there

```
kernel-image-2.6.15-custom_10.00.Custom_i386.deb kernel-headers-2.6.15-custom_10.00.Custom_i386.deb
```
and also 
```
ndiswrapper-modules-2.6.15-custom_1.1-4ubuntu2+10.00.Custom_i386.deb nvidia-kernel-2.6.15-custom_1.0.7667-0ubuntu3+10.00.Custom_i386.deb
```

now install all EXCEPT nvidia 
```
sudo dpkg -i name_of_the_module
```
Now we will apply and install you own compiled nvidia driver
```
ctrl+alt+F1
```
```
sudo /etc/init.d/gdm stop
```
install your custom compiled nvidia located in /usr/src/
```
sudo dpkg -i nvidia-kernel...
```

```
sudo apt-get install nvidia-glx-dev 
```

```
sudo depmod -a
```

```
sudo nvidia-glx-config enable
```

now you can remove your other kernel and nvidia will still work.

---

### Post by hyperair on 2007-05-27
Ah, that worked perfectly for me. Thanks.

---

