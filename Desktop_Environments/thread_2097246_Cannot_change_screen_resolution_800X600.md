---
title: "Cannot change screen resolution 800X600"
date: 2012-12-22
forum: Desktop Environments
---

### Post by yoramdavid on 2012-12-22
Hello all,

I have a desktop AMD processor, Nvidia graphic card computer with Ubuntu 12.10.
I was having many problems such as no flash video from youtube, very slow computer mainly when browsing the Internet.

I searched the net and came to the conclusion it might be a graphic drivers problem, so I installed the Nvidia Drivers.
But the result is now a desktop with a resolution of 800 X 600 which I cannot change.
Uninstalling the Nvidia drivers did not help, nor it helped to install linux-headers-generic, linux-source.

My Xorg.conf file has an entry Section Monitor whre the HorizYnc is set to 28.0 - 33.0 and a HorizSync set to 43.0 - 72.0

Under system configuration, under screens it does not detect my monitor, it detects a "Laptop"...

Any help is welcome, as I have already done many things with no luck.

Thank you.

Yoram

---

### Post by yoramdavid on 2012-12-26
I searched on my monitor on the net and found that the "Samsung SyncMaster T220" has a  Vertical Refresh Rate 75 Hz and a Horizontal Refresh Rate 81 kHz, so I changed that in the xorg.conf file, restarted the Xserver and now the screen is at  1280 x 1024, a little better but a little distorted.
It must be another Vertical and Horizontal refresh rate, any body knows how to know that?

I also tried what this old threat says: [http://ubuntuforums.org/showthread.php?t=779038](http://ubuntuforums.org/showthread.php?t=779038)
But the ```
% xvidtune -show
``` returns the following error:```
bash: fg: %: trabalho não existe

```

Flash still does not work either by the way.
Regards and happy festivities to all.

---

### Post by gasquangchuyen on 2012-12-26
you should make: Control Panel -> Device Manager -> Graphic Cards
click with right button of your mouse on your graphic card there and choose ' Uninstall driver '.

---

### Post by yoramdavid on 2012-12-27
> **gasquangchuyen said:**
> you should make: Control Panel -> Device Manager -> Graphic Cards
click with right button of your mouse on your graphic card there and choose ' Uninstall driver '.

Thank you for replying, but that sounds like windows.
Where do I find that in Ubuntu 12.10?

---

### Post by Petro Dawg on 2012-12-27
> **yoramdavid said:**
> Thank you for replying, but that sounds like windows.
Where do I find that in Ubuntu 12.10?

You might try typing "Drivers" into the Dash.  Open the additional drivers app and see if you can remove any old drivers and install different ones.

Could also try typing this in terminal... 

```
gksudo amdcccle
```

which opens the AMD catalyst control center (if it is installed on your computer).

---

### Post by Drone4four on 2012-12-28
yoramdavid: You said that your graphics card is an "AMD Nvidia".  AMD and Nvidia are two different companies.  What graphics card do you have? One or the other? Can you please share the output of these two commands?

```
lspci -v | grep nvidia
lspci -v | grep amd
lspci -v | grep AMD
```

---

### Post by yoramdavid on 2012-12-28
> **Drone4four said:**
> yoramdavid: You said that your graphics card is an "AMD Nvidia".  AMD and Nvidia are two different companies.  What graphics card do you have? One or the other? Can you please share the output of these two commands?

```
lspci -v | grep nvidia
lspci -v | grep amd
lspci -v | grep AMD
```

Hello Drone4four, thank you.

I was not clear, the processor is AMD, the Graphic card is Nvidia.
I will put the output here of these commands soon.

Yesterday, I pressed the configuration button on the monitor and I lost connection with it. I tried a different cable and it works, is it coincidence having changed the Vertical Refresh Rate to 75 Hz and a Horizontal Refresh Rate to 81 kHz might have be the cause?

---

### Post by Pjotr123 on 2012-12-28
Have you tried nvidia-settings?
[https://sites.google.com/site/easylinuxtipsproject/display#TOC-Wrong-resolution:-Nvidia-card](https://sites.google.com/site/easylinuxtipsproject/display#TOC-Wrong-resolution:-Nvidia-card)

---

### Post by yoramdavid on 2012-12-28
> **Petro Dawg said:**
> You might try typing "Drivers" into the Dash.  Open the additional drivers app and see if you can remove any old drivers and install different ones.

Could also try typing this in terminal... 

```
gksudo amdcccle
```

which opens the AMD catalyst control center (if it is installed on your computer).

The above code does nothing, probably due to the confusion of my graphic card not being AMD, but Nvidia.

---

### Post by yoramdavid on 2012-12-28
> **Drone4four said:**
> yoramdavid: You said that your graphics card is an "AMD Nvidia".  AMD and Nvidia are two different companies.  What graphics card do you have? One or the other? Can you please share the output of these two commands?

```
lspci -v | grep nvidia
lspci -v | grep amd
lspci -v | grep AMD
```

```
lspci -v | grep nvidia
```
Returns:
```
lspci -v | grep nvidia
Kernel driver in use: agpgart-nvidia
Kernel modules: nvidia_current, nouveau, nvidiafb

```


```
lspci -v | grep amd
```returns:
```
lspci -v | grep amd
Kernel driver in use: pata_amd
Kernel modules: pata_amd

```


```
lspci -v | grep AMD
```returns nothing

---

### Post by yoramdavid on 2012-12-28
> **Pjotr123 said:**
> Have you tried nvidia-settings?
[https://sites.google.com/site/easylinuxtipsproject/display#TOC-Wrong-resolution:-Nvidia-card](https://sites.google.com/site/easylinuxtipsproject/display#TOC-Wrong-resolution:-Nvidia-card)

Thank you,

Yes I tried that.
The output when I open that program is:

```
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
```

When I run the command```
nvidia-xconfig
```
It creates a Xorg.con file which looks like this:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 304.64  (buildmeister@swio-display-x86-rhel47-01.nvidia.com)  Tue Oct 30 12:19:38 PDT 2012


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       81.0 - 81.0
    VertRefresh     75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

---

### Post by Drone4four on 2012-12-28
I ran into a very similar problem yesterday that I resolved today.  The first issue is increasing your screen resolution.  You can do that manually.  Refer to the solution in this thread that I found using Google [_**here**_]("http://ubuntuforums.org/showthread.php?t=1659556&page=2").   But to fix the resolution and get your nvidia drivers activated, you can refer to my thread [_**here**_]("http://ubuntuforums.org/showthread.php?t=2098925").  The solution for me boiled down to this:

```
sudo apt-get purge nvidia*
sudo apt-get install linux-headers-generic  linux-source linux-image linux-image-extra
sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig
```

Then reboot and report back here.

---

### Post by yoramdavid on 2012-12-29
Thank you, yes I had already seen that threat and tried it, but I did it again.

Here are the results of the commands:

```
sudo apt-get purge nvidia*
[sudo] password for yoram: 
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
Note, a seleccionar 'nvidia-180-libvdpau-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-173-updates' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-185-libvdpau-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'libgl1-nvidia-legacy-71xx-glx' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-glx-173-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-current' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-libvdpau-ia32' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-cuda-debugger' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-libvdpau1' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-glx-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-glx-185-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-173' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-settings-updates' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-libopencl1-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-settings' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-185-libvdpau' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-185-kernel-source' para a expressão regular 'nvidia*'
Note, a seleccionar 'libgl1-nvidia-legacy-173xx-glx' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-vdpau-driver' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-96-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-opencl-profiler' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-cg-toolkit' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-96' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-libvdpau1-ia32' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-glx-legacy-173xx' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-glx-96-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-173-updates-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-96-updates' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-experimental-304' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-experimental-310' para a expressão regular 'nvidia*'
Note, a seleccionar 'libkwinactivenvidiahack4' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-glx-173' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-glx-180' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-glx-185' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-180-modaliases' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-cuda-profiler' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-glx-legacy-96xx-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-visual-profiler' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-current-updates' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-cg-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-cg-doc' para a expressão regular 'nvidia*'
Note, a seleccionar 'libglx-nvidia-alternatives' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-kernel-common' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-opencl-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-current-updates-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'libkwinnvidiahack4' para a expressão regular 'nvidia*'
Note, a seleccionar 'libgl1-nvidia-glx' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-glx-legacy-71xx' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-libvdpau' para a expressão regular 'nvidia*'
Note, a seleccionar 'boinc-nvidia-cuda' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-current-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'glx-alternative-nvidia' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-compute-profiler' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-glx-96' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-experimental-304-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-glx-legacy-71xx-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-glx-180-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-installer-cleanup' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-va-driver' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-current-modaliases' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-173-modaliases' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-185-modaliases' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-glx-legacy-96xx' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-experimental' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-texture-tools' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-glx-legacy-173xx-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-common' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-tegra3' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-tegra' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-current-experimental-304' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-96-kernel-source' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-cuda-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-cuda-doc' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-173-kernel-source' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-cuda-gdb' para a expressão regular 'nvidia*'
Note, a seleccionar 'libgl1-nvidia-legacy-96xx-glx' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-experimental-310-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-180-kernel-source' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-cuda-toolkit' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-libvdpau-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'libgl1-nvidia-alternatives' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-glx' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-settings-experimental-304' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-settings-experimental-310' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-173-dev' para a expressão regular 'nvidia*'
Note, a seleccionar 'nvidia-180-libvdpau' para a expressão regular 'nvidia*'
O pacote 'libgl1-nvidia-alternatives' não está instalado, por isso não será removido
O pacote 'nvidia-libvdpau-dev' não está instalado, por isso não será removido
O pacote 'nvidia-vdpau-driver' não está instalado, por isso não será removido
O pacote 'nvidia-libvdpau' não está instalado, por isso não será removido
O pacote 'nvidia-libvdpau-ia32' não está instalado, por isso não será removido
O pacote 'nvidia-libvdpau1' não está instalado, por isso não será removido
O pacote 'nvidia-libvdpau1-ia32' não está instalado, por isso não será removido
O pacote 'nvidia-180-modaliases' não está instalado, por isso não será removido
O pacote 'nvidia-185-modaliases' não está instalado, por isso não será removido
O pacote 'nvidia-current-modaliases' não está instalado, por isso não será removido
O pacote 'nvidia-173-modaliases' não está instalado, por isso não será removido
O pacote 'nvidia-current-experimental-304' não está instalado, por isso não será removido
Note, a seleccionar 'libnvtt-bin' em vez de 'nvidia-texture-tools'
O pacote 'nvidia-libopencl1-dev' não está instalado, por isso não será removido
O pacote 'nvidia-glx' não está instalado, por isso não será removido
Note, a seleccionar 'vdpau-va-driver' em vez de 'nvidia-va-driver'
O pacote 'libgl1-nvidia-glx' não está instalado, por isso não será removido
O pacote 'libgl1-nvidia-legacy-173xx-glx' não está instalado, por isso não será removido
O pacote 'libgl1-nvidia-legacy-71xx-glx' não está instalado, por isso não será removido
O pacote 'libgl1-nvidia-legacy-96xx-glx' não está instalado, por isso não será removido
O pacote 'libglx-nvidia-alternatives' não está instalado, por isso não será removido
O pacote 'nvidia-glx-legacy-173xx' não está instalado, por isso não será removido
O pacote 'nvidia-glx-legacy-71xx' não está instalado, por isso não será removido
O pacote 'nvidia-glx-legacy-96xx' não está instalado, por isso não será removido
O pacote 'nvidia-installer-cleanup' não está instalado, por isso não será removido
O pacote 'nvidia-glx-dev' não está instalado, por isso não será removido
O pacote 'nvidia-glx-legacy-173xx-dev' não está instalado, por isso não será removido
O pacote 'nvidia-glx-legacy-71xx-dev' não está instalado, por isso não será removido
O pacote 'nvidia-glx-legacy-96xx-dev' não está instalado, por isso não será removido
O pacote 'nvidia-cuda-debugger' não está instalado, por isso não será removido
O pacote 'nvidia-compute-profiler' não está instalado, por isso não será removido
O pacote 'nvidia-cuda-profiler' não está instalado, por isso não será removido
O pacote 'nvidia-opencl-profiler' não está instalado, por isso não será removido
O pacote 'nvidia-tegra' não está instalado, por isso não será removido
O pacote 'nvidia-tegra3' não está instalado, por isso não será removido
O pacote 'nvidia-173-kernel-source' não está instalado, por isso não será removido
O pacote 'nvidia-180-kernel-source' não está instalado, por isso não será removido
O pacote 'nvidia-180-libvdpau' não está instalado, por isso não será removido
O pacote 'nvidia-180-libvdpau-dev' não está instalado, por isso não será removido
O pacote 'nvidia-185-kernel-source' não está instalado, por isso não será removido
O pacote 'nvidia-185-libvdpau' não está instalado, por isso não será removido
O pacote 'nvidia-185-libvdpau-dev' não está instalado, por isso não será removido
O pacote 'nvidia-96-dev' não está instalado, por isso não será removido
O pacote 'nvidia-96-kernel-source' não está instalado, por isso não será removido
O pacote 'nvidia-glx-173' não está instalado, por isso não será removido
O pacote 'nvidia-glx-173-dev' não está instalado, por isso não será removido
O pacote 'nvidia-glx-180' não está instalado, por isso não será removido
O pacote 'nvidia-glx-180-dev' não está instalado, por isso não será removido
O pacote 'nvidia-glx-185' não está instalado, por isso não será removido
O pacote 'nvidia-glx-185-dev' não está instalado, por isso não será removido
O pacote 'nvidia-glx-96' não está instalado, por isso não será removido
O pacote 'nvidia-glx-96-dev' não está instalado, por isso não será removido
O pacote 'nvidia-kernel-common' não está instalado, por isso não será removido
O pacote 'nvidia-173-dev' não está instalado, por isso não será removido
O pacote 'nvidia-173-updates' não está instalado, por isso não será removido
O pacote 'nvidia-173-updates-dev' não está instalado, por isso não será removido
O pacote 'nvidia-current-updates-dev' não está instalado, por isso não será removido
O pacote 'nvidia-experimental-304' não está instalado, por isso não será removido
O pacote 'nvidia-experimental-304-dev' não está instalado, por isso não será removido
O pacote 'nvidia-settings-experimental-304' não está instalado, por isso não será removido
O pacote 'nvidia-settings-updates' não está instalado, por isso não será removido
O pacote 'glx-alternative-nvidia' não está instalado, por isso não será removido
O pacote 'nvidia-cg-dev' não está instalado, por isso não será removido
O pacote 'nvidia-cg-doc' não está instalado, por isso não será removido
O pacote 'nvidia-cg-toolkit' não está instalado, por isso não será removido
O pacote 'nvidia-cuda-dev' não está instalado, por isso não será removido
O pacote 'nvidia-cuda-doc' não está instalado, por isso não será removido
O pacote 'nvidia-cuda-gdb' não está instalado, por isso não será removido
O pacote 'nvidia-cuda-toolkit' não está instalado, por isso não será removido
O pacote 'nvidia-opencl-dev' não está instalado, por isso não será removido
O pacote 'nvidia-visual-profiler' não está instalado, por isso não será removido
O pacote 'nvidia-settings-experimental-310' não está instalado, por isso não será removido
O pacote 'nvidia-experimental-310' não está instalado, por isso não será removido
O pacote 'nvidia-experimental-310-dev' não está instalado, por isso não será removido
O pacote 'libkwinactivenvidiahack4' não está instalado, por isso não será removido
O pacote 'libkwinnvidiahack4' não está instalado, por isso não será removido
O pacote 'boinc-nvidia-cuda' não está instalado, por isso não será removido
O pacote 'nvidia-current-dev' não está instalado, por isso não será removido
Serão REMOVIDOS os seguintes pacotes:
  nvidia-173* nvidia-common* nvidia-current* nvidia-current-updates*
  nvidia-settings*
0 pacotes actualizados, 0 pacotes novos instalados, 5 a remover e 0 não actualizados.
Após esta operação, será libertado 112 MB de espaço em disco.
Deseja continuar [Y/n]? y
(A ler a base de dados ... 300109 ficheiros e directórios actualmente instalados.)
A remover nvidia-173 ...
A purgar os ficheiros de configuração para nvidia-173 ...
dpkg: aviso: while removing nvidia-173, directory '/usr/lib/nvidia-173/tls' not empty so not removed
A remover nvidia-common ...
A purgar os ficheiros de configuração para nvidia-common ...
A remover nvidia-current ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in modo automático
INFO:Disable nvidia-current
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match ASUSTeK Computer INC. with Dell Inc.
DEBUG:Quirk doesn't match
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match ASUSTeK Computer INC. with LENOVO
DEBUG:Quirk doesn't match
update-initramfs: deferring update (trigger activated)
A purgar os ficheiros de configuração para nvidia-current ...
update-initramfs: deferring update (trigger activated)
A remover nvidia-current-updates ...
A purgar os ficheiros de configuração para nvidia-current-updates ...
update-initramfs: deferring update (trigger activated)
A remover nvidia-settings ...
A purgar os ficheiros de configuração para nvidia-settings ...
A processar 'triggers' para bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
A processar 'triggers' para libc-bin ...
ldconfig deferred processing now taking place
A processar 'triggers' para man-db ...
A processar 'triggers' para desktop-file-utils ...
A processar 'triggers' para gnome-menus ...
A processar 'triggers' para initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-21-generic
```

```
sudo apt-get install linux-headers-generic  linux-source linux-image linux-image-extra
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
E: Não foi possível encontrar o pacote linux-image-extra
```

```
sudo apt-get install nvidia-current nvidia-settings
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
Serão instalados os seguintes NOVOS pacotes:
  nvidia-current nvidia-settings
0 pacotes actualizados, 2 pacotes novos instalados, 0 a remover e 0 não actualizados.
É necessário obter 40,0 MB de arquivos.
Após esta operação, serão utilizados 112 MB adicionais de espaço em disco.
Obter:1 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ quantal/main nvidia-current i386 304.64-0ubuntu1~quantal~xup1 [38,2 MB]
Obter:2 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ quantal/main nvidia-settings i386 304.64-0ubuntu1~quantal~xup1 [1810 kB]
Obtidos 40,0 MB em 5min 4s (131 kB/s)                                          
Selecting previously unselected package nvidia-current.
(A ler a base de dados ... 299872 ficheiros e directórios actualmente instalados.)
A descompactar nvidia-current (desde .../nvidia-current_304.64-0ubuntu1~quantal~xup1_i386.deb) ...
Selecting previously unselected package nvidia-settings.
A descompactar nvidia-settings (desde .../nvidia-settings_304.64-0ubuntu1~quantal~xup1_i386.deb) ...
A processar 'triggers' para desktop-file-utils ...
A processar 'triggers' para gnome-menus ...
A processar 'triggers' para bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
A processar 'triggers' para man-db ...
A instalar nvidia-current (304.64-0ubuntu1~quantal~xup1) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in modo automático
update-alternatives: aviso: skip creation of /usr/lib32/libOpenCL.so because associated file /usr/lib32/nvidia-current/libOpenCL.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: aviso: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: aviso: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: using /usr/lib/nvidia-current/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in modo automático
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match ASUSTeK Computer INC. with Dell Inc.
DEBUG:Quirk doesn't match
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match ASUSTeK Computer INC. with LENOVO
DEBUG:Quirk doesn't match
Loading new nvidia-current-304.64 DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-21-generic
Building for architecture i686
Building initial module for 3.5.0-21-generic
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-21-generic/updates/dkms/

depmod....

DKMS: install completed.
A instalar nvidia-settings (304.64-0ubuntu1~quantal~xup1) ...
update-alternatives: aviso: forcing reinstallation of alternative /usr/lib/nvidia-settings/ld.so.conf because link group nvidia_settings_conf is broken
A processar 'triggers' para bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
A processar 'triggers' para initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-21-generic
```

```
sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

And the new xorg.conf file looks like this on the monitor seciton:
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       81.0 - 81.0
    VertRefresh     75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

And nothing has changed. :(

---

### Post by Drone4four on 2012-12-29
I'm stumped.  I wish I could have been more helpful.

---

### Post by cariboo on 2012-12-30
Depending on what version you are running, 12.04 and 12.10, don't use /etc/X11/xorg.conf any more. Have you tried renaming the file and then using nv to set your resolution.

```
sudo mv /etc/X11/xorg.conf xorg.conf.bak
```

It would also help if you told use what make/model monitor and and make/model graphics card you are using.

---

### Post by yoramdavid on 2012-12-30
> **cariboo907 said:**
> Depending on what version you are running, 12.04 and 12.10, don't use /etc/X11/xorg.conf any more. Have you tried renaming the file and then using nv to set your resolution.

```
sudo mv /etc/X11/xorg.conf xorg.conf.bak
```

It would also help if you told use what make/model monitor and and make/model graphics card you are using.

Thank you.

I am using Ubuntu 12.10
Monitor: Samsung SyncMaster T220
Graphic card (from "lspci"): VGA compatible controller: NVIDIA Corporation NV36 [GeForce FX 5700LE] (rev a1)
It is a MSI FX5700-LE 256MB DDR-TVOUT-DVI

I ran the command```
sudo mv /etc/X11/xorg.conf xorg.conf.bak
```
Then ran the Nvidia X Server Settings application which gave me the error:
```
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
```
And opened a blank application window.

I then ran ```

```
Which gave me the following output:
```
WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'

```

The new xorg.conf looks like this under the Monitor Section:
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Which is gives me a screen of 800X600 as before.
And I should be able to get a resolution of 1680 X 1050 @ 60 hertz

---

### Post by yoramdavid on 2013-01-11
Any body, please?

---

### Post by yoramdavid on 2013-01-14
](*,)

---

### Post by Petro Dawg on 2013-01-14
All I can do is suggest what I would do if I were you (and I'm sure many would disagree with me).  

I would run a live cd session of Ubuntu **12.04** and see if the monitor behaves correctly when booting from the CD.   If it does, then I would do a reinstall of the OS (sometimes that's just the best solution).  

If it still had the same problem using the live CD, I might try another Linux distro such as Mint or Fedora and see if it works correctly then.    

Otherwise, you might be waiting a while for a graphics guru to lead you into a better direction.

---

### Post by yoramdavid on 2013-01-16
Thank you Petro Dawg,

I had not tought about testing that, I am now from the live CD Ubuntu 12.04 Lts and it runs at the maxumum resolution automatically, i.e. 1680 X 
1050. It also detects my monitor! It says "Samsung Electric Copmpany 22" ".

I also tested if youtube videos would play on firefox, which is the main reason I installed the Nvidia drivers. The other reason was a very slow computer when viewing images and youtube videos work, I even did not need to install any plugin!

I guess a fresh install is my solution here then? I know there are workarounds, but I have no knowledge enough for that.

Regards,

Yoram

> **Petro Dawg said:**
> All I can do is suggest what I would do if I were you (and I'm sure many would disagree with me).  

I would run a live cd session of Ubuntu **12.04** and see if the monitor behaves correctly when booting from the CD.   If it does, then I would do a reinstall of the OS (sometimes that's just the best solution).  

If it still had the same problem using the live CD, I might try another Linux distro such as Mint or Fedora and see if it works correctly then.    

Otherwise, you might be waiting a while for a graphics guru to lead you into a better direction.

---

### Post by Yellow Pasque on 2013-01-16
> GeForce FX 5700LE
The nvidia-current driver (300-series) isn't going to work for that card. You need the nvidia-173 driver.

---

### Post by yoramdavid on 2013-01-17
> **Temüjin said:**
> The nvidia-current driver (300-series) isn't going to work for that card. You need the nvidia-173 driver.

Thank you Temüjin,

I  uninstalled the nvdidia-driver I had, and tried to install the nvidia-173 driver, but got an error :
[HTML]Os pacotes a seguir têm dependências não satisfeitas:
 nvidia-173 : Depende: xorg-video-abi-11 mas não é instalável ou
                       xorg-video-abi-12 mas não é instalável
E: Não foi possível corrigir problemas, você tem pacotes mantidos (hold) estragados.[/HTML]
Which means that dependencies are not satisfied and that I have broken packages held.

I then downloaded the Nvidia-173 from the site, it comes as .run and from the console ran the command sh and I got the errror (summarized):
```
You appear to run xserver, pleas quit xserver and try again
```
I went to command line pressing Ctrl+Alt+F1 and ran the sh  command again and had the same error.
Rebooting and booting into the recovery console, I could not find the directory where the driver is kept (says it does not exist).

When booted up again the screen was black with only a cursor.
I installed Nvidia-current again.
In the middle of this, I installed Lubuntu to see if it would made any changes, but I got the black screen and could not draw conclusions from that.
I rebooted again after installing the drivers and now it detects my monitor and it is running at the desired resolution.

That is a big plus.
The minus are that flash video still do not work and nor do google-earth

Regards,
Yoram

---

### Post by yoramdavid on 2013-01-18
Oh well, this morning when I started the computer it is as before, low resolution. I did nothing of my knowledge that might have changed anything.

I burnet a DVD with LinuxMint 14 to install, but after a few screens where things seems to load, I en up with a black screen.

I will try Fedora now.

---

### Post by jimmytbane on 2013-01-18
If you could mention exact products that would be helpful. Low resolution or not you can do that by going to the gear in the top right corner of your screen and choose, about this computer. For me it doesn't mention GPU for some reason but that may just be me. If you have an nvidia graphics card within the driver you can change your display resolution and refresh rate. there are currently 5 readily available nvidia drivers. Usually the 310 experimental is the best.

---

### Post by yoramdavid on 2013-01-23
> **jimmytbane said:**
> If you could mention exact products that would be helpful. Low resolution or not you can do that by going to the gear in the top right corner of your screen and choose, about this computer. For me it doesn't mention GPU for some reason but that may just be me. If you have an nvidia graphics card within the driver you can change your display resolution and refresh rate. there are currently 5 readily available nvidia drivers. Usually the 310 experimental is the best.

Thank you jimmytbane,

I am using Ubuntu 12.10 3.5.0-22-generic
Monitor: Samsung SyncMaster T220
Graphic card (from "lspci"): VGA compatible controller: NVIDIA Corporation NV36 [GeForce FX 5700LE] (rev a1)
It is a MSI FX5700-LE 256MB DDR-TVOUT-DVI

Is there any other information that would be useful?

Regards,
Yoram

---

### Post by Zimmer on 2013-01-23
The problems you are facing come from 3 areas:
1.
You need the 173 Nvidia drivers for this card if you want to use Nvidia drivers.
2.
It appears your monitor is NOT reporting its EDID file parameters to X correctly.
(in one of the links to a solution you will see a 
 Option               "IgnoreEDID" "1" 
statement in an xorg.conf file. This tells the X system to ignore settings from the monitor and to use Options you set manually in the xorg.conf file.)
3.
You have tried so much the install is now messy and could be corrupt.

-------------------------
Try fresh install. Install 173 Nvidia drivers. Install nvidia-settings. see if you can use nvidia-settings to correct the problem, or manually edit the xorg.conf file with settings for your monitor.
----------------

or, in desperation,(as I have done with an old ACER monitor) cheat using xrandr. 

In a Terminal type
xrandr -q

this will show you what resolutions are available to the monitor with the current driver.
Top of the list will be the default.. ( s 0)
the next on the list (s 1) etc..

The command xranr -s 0 will put the monitor to default resolution.
The command xrandr -s 1 will use the resolution that comes next and so on.

You can even put these commands in a desktop launcher for future convenience...

Good Luck...

---

### Post by yoramdavid on 2013-01-24
> **Zimmer said:**
> The problems you are facing come from 3 areas:
1.
You need the 173 Nvidia drivers for this card if you want to use Nvidia drivers.
2.
It appears your monitor is NOT reporting its EDID file parameters to X correctly.
(in one of the links to a solution you will see a 
 Option               "IgnoreEDID" "1" 
statement in an xorg.conf file. This tells the X system to ignore settings from the monitor and to use Options you set manually in the xorg.conf file.)
3.
You have tried so much the install is now messy and could be corrupt.

-------------------------
Try fresh install. Install 173 Nvidia drivers. Install nvidia-settings. see if you can use nvidia-settings to correct the problem, or manually edit the xorg.conf file with settings for your monitor.
----------------

or, in desperation,(as I have done with an old ACER monitor) cheat using xrandr. 

In a Terminal type
xrandr -q

this will show you what resolutions are available to the monitor with the current driver.
Top of the list will be the default.. ( s 0)
the next on the list (s 1) etc..

The command xranr -s 0 will put the monitor to default resolution.
The command xrandr -s 1 will use the resolution that comes next and so on.

You can even put these commands in a desktop launcher for future convenience...

Good Luck...

Thank you.
As in a 4 posts up, I explained I could not install the nvidia-173 driver, there seems to be a bug with that installer.
xrandr -q
Gave me 3 resolutions, being the higher (1024x768       61.0* ) the one in use but not the most the monitor can suport (1680 X 1050).

When you say fresh install, I suppose you mean fresh install of the operating system. That is what I tried already without success with mint and fedora. Both CD's load to a screen with no options to install are presente and I cannot do anything.
And I do not want to install Ubuntu any more (the Live CD works fine with a good screen resolution but no flash).

---

### Post by yoramdavid on 2013-01-25
As suggested before, I did a fresh install, but this time I am trying LinuxMint 14.
Resolution is ok now, but system is slow and I still cannot install additional drivers, it says "SystemError: E:Unable to correct problems, you have held broken packages" - now I just installed Mint !
But perhaps now I have to go to Mint forums?

It seemed that Mint got installed correctly, but I ended up with a black screen and a cursor when the system got loaded.
I pressed Ctrl+Alt+Delete and then "enter" and the login screen come up with an option to boot in "KDE Plasma Workspace (failsafe session) (previous).
It started with a desktop this time. But it is slow, no flash video, google-earth does not display the maps, and I cannot install the nvidia drivers from the Additional drivers application.

And from the console I still cannot install the nvidia-173

Regards,

Yoram

---

### Post by furything on 2013-01-25
Hi Yoram

Please see this thread?
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)
It details how to generate the screen mode you want and then how to add it to xorg.conf in the modes section.

---

### Post by yoramdavid on 2013-01-25
> **furything said:**
> Hi Yoram

Please see this thread?
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)
It details how to generate the screen mode you want and then how to add it to xorg.conf in the modes section.

Thank you furything,

I did something similar indeed, editing the xorg.conf and thanks to that I went from 800 x 600 to 1024 x 768 but I never went any near the desired 1680 x 1050.

Now I am in Mint desktop since this morning, I got rid of Ubuntu, and it runs at the desired resolution of 1680 x 1050.
The problem now is that I need to install nvidia-173 but cannot due to a bug I think!

Regards,
Yoram

---

### Post by furything on 2013-01-28
Have you tried to install the driver again now on mint???
I suggest you go through additional drivers gui found in system settings as this has always worked for me.
I think your issue with the driver is something with your environment as I run them quite happily and I believe so do most people.

---

### Post by yoramdavid on 2013-01-28
> **furything said:**
> Have you tried to install the driver again now on mint???
I suggest you go through additional drivers gui found in system settings as this has always worked for me.
I think your issue with the driver is something with your environment as I run them quite happily and I believe so do most people.

Hi furything,
Thank you for asking.

In Mint, I am having the exact same problems as before except the resolution of the screen is good.
Note that when I installed Ubuntu 12.10, the resolution also was good, it got bad after I installed some nvidia driver.

I am getting also help from the Mint forum and I was asked to run a command "inxi -Gx" that shows the nvidia nouveau does no load:

```
inxi -Gx
Graphics:  Card: NVIDIA NV36 [GeForce FX 5700LE] bus-ID: 03:00.0 
           X.Org: 1.13.0 drivers: nouveau (unloaded: fbdev) FAILED: vesa Resolution: 1680x1050@59.9hz 
           GLX Renderer: Gallium 0.4 on NV36 GLX Version: 1.5 Mesa 9.0 Direct Rendering: Yes

```

When I try to install additional drivers from the "additional drivers" gui (the nvidia-173 driver), it finds the drivers but tells me they are not activated, I click on activate, then I get an error of Broken packages being held.

---

### Post by furything on 2013-01-28
I have seen some post by bogan. He appears to be quite an expert although he would say otherwise.

See if you can find a thread by him/message him to see if you can get his help.

---

### Post by yoramdavid on 2013-01-28
> **furything said:**
> I have seen some post by bogan. He appears to be quite an expert although he would say otherwise.

See if you can find a thread by him/message him to see if you can get his help.

Thanks, I will search for his posts or ask his help.

---

### Post by furything on 2013-01-29
Hi Yoram
Don't know if you managed to catch bogan but I note form a post of his he states clear out old drivers before installing new
 sudo apt-get remove --purge <package-name>
Can I say though if you remove drivers make sure that you package manager is not reporting any errors other than nVidia driver.

If you remove driver then get a new driver installed before reboot otherwise you may end up being on command line only trying to fix this.

bogan looks to be on line so try and message him.

---

### Post by yoramdavid on 2013-01-30
> **furything said:**
> Hi Yoram
Don't know if you managed to catch bogan but I note form a post of his he states clear out old drivers before installing new
 sudo apt-get remove --purge <package-name>
Can I say though if you remove drivers make sure that you package manager is not reporting any errors other than nVidia driver.

If you remove driver then get a new driver installed before reboot otherwise you may end up being on command line only trying to fix this.

bogan looks to be on line so try and message him.

Hi furything,

Thank you.
I was getting help on the Mint forum and did not try to catch bogan yet, but since my problem did not get solved, I'll try to catch him now.

That is something I did not do, uninstall the old drivers. I opened the package manager and did a search for "nvidia" to see what I had installed and I realize that the nvidia-nouveau is not there any more. But nvidia-common was there, so I removed it using the command you provided (only 37kb were removed, that does not seem a lot to me for a driver, is it?).
nvidia-173 is already installed so I am hoping it will be ok after a reboot.

Regards,
Yoram

---

### Post by furything on 2013-02-01
HI Yoram 
Just seen your post.

I hope you can boot up ok?

The intention would be to clean off old driver damaged package and then install the correct driver.

When I removed without installing a new driver I could not boot into the desktop so had to fix the graphics from the terminal. 

You always want to make sure a driver is installed and configured with xorg before rebooting.

---

### Post by yoramdavid on 2013-02-01
> **furything said:**
> HI Yoram 
Just seen your post.

I hope you can boot up ok?

The intention would be to clean off old driver damaged package and then install the correct driver.

When I removed without installing a new driver I could not boot into the desktop so had to fix the graphics from the terminal. 

You always want to make sure a driver is installed and configured with xorg before rebooting.

Hi furything,

Yes, there was no problem. All was the same when rebooted.
Thank you for asking.
I am now searching for threads from bogan.

The nvidia-173 driver is installed and active but not loaded, according to the "additional drivers" gui: it lists two drivers: the first one called "NVIDIDA binary Xorg driver, kernel module and VDPAU library" which is not active.
The second entry is the "nvidia_173" driver and the status for this one is "activated but not in use".

---

### Post by furything on 2013-02-01
Phew glad you are working.

Have you rebooted since getting the 173 driver installed? IGNORE reread your post

Looks like your answer is here
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
this states about blacklisting the intel_agp which it looks like you may be using

---

### Post by bogan on 2013-02-01
Hi!, **All** the Posters on this thread,
[Responding to y**oramdavid**'s PM.]

First, I have read through this Thread on many occasions in the past, and have just re-read it. I have not intervened before, partly because I steer clear of 'cannot get out of Low Res' Threads as they always seem to wander around without getting anywhere, and there are people who have responded who clearly know a lot more about the subject than I do.

Added to which I have never heard of some of the things the OP posted - 'inix -Gx', 'amd' being installed on a m/c that does not have it, 'pata-amd', 'agpgart-nvidia'.

The first, I assume, is something from Mint, about which I know nothing; the others only confuse further an already confused situation, the last, Google has a lot to show for, all dating from 2005-8.

So first suggestion, run:```
lspci -nnk | grep iA3 amd # to make sure pata/amd is gone, and: 
lspci -nnk | grep iA3 vga # to see just what 
# drivers and modules are installed & used.
```Second, The correct driver for:"VGA compatible controller: NVIDIA Corporation NV36 [GeForce FX 5700LE] (rev a1)" is definitely 173, but must be 173.14 or later to use with 12.04 or later, as earlier versions were incompatible with the Xserver those distributions use.

Later versions of nvidia drivers do not support the GeForce FX 5xxx series cards.

So 2nd suggestion, run: ```
apt-cache policy nvidia-173* 
```Hopefully, that will show the version is "173.14.36-0ubuntu0.1.0" and is installed, or a candidate.

PLEASE POST RESULTS OF THOSE and I will try to take things a stage further.

Third, if you have to install nvidia-173 from the nvidia.com site, that is the version recommended.
 The 'error' you [**yoramdavid**] described, is not a system error but your mistake. 
You have to shut down the xserver before running the nvidia-xxxx-.run file, which should be found in the /home/username/Downloads folder - unless your browser is set to download & save elseware.
To do that: 'Ctrl+Alt+F1', login and enter password - it will not show - plus 'Enter', and run: ```
sudo service lightdm stop

``` [ 'Ctrl+Alt+F1' will return you to the GUI Desktop.]

Before you try that, however be sure to fully remove all the drivers you have tried to install since you re-installed the OS. ```
sudo apt-get remove --purge < packagename> # for all drivers by name, and then:
sudo apt-get remove --purge nvidia*.

```Chao!, **bogan**.

---

### Post by yoramdavid on 2013-02-01
> **bogan said:**
> Hi!, **All** the Posters on this thread,
[Responding to y**oramdavid**'s PM.]

First, I have read through this Thread on many occasions in the past, and have just re-read it. I have not intervened before, partly because I steer clear of 'cannot get out of Low Res' Threads as they always seem to wander around without getting anywhere, and there are people who have responded who clearly know a lot more about the subject than I do.

Added to which I have never heard of some of the things the OP posted - 'inix -Gx', 'amd' being installed on a m/c that does not have it, 'pata-amd', 'agpgart-nvidia'.

The first, I assume, is something from Mint, about which I know nothing; the others only confuse further an already confused situation, the last, Google has a lot to show for, all dating from 2005-8.

So first suggestion, run:```
lspci -nnk | grep iA3 amd # to make sure pata/amd is gone, and: 
lspci -nnk | grep iA3 vga # to see just what 
# drivers and modules are installed & used.
```Second, The correct driver for:"VGA compatible controller: NVIDIA Corporation NV36 [GeForce FX 5700LE] (rev a1)" is definitely 173, but must be 173.14 or later to use with 12.04 or later, as earlier versions were incompatible with the Xserver those distributions use.

Later versions of nvidia drivers do not support the GeForce FX 5xxx series cards.

So 2nd suggestion, run: ```
apt-cache policy nvidia-173* 
```Hopefully, that will show the version is "173.14.36-0ubuntu0.1.0" and is installed, or a candidate.

PLEASE POST RESULTS OF THOSE and I will try to take things a stage further.

Thank you bogan for stepping in.

Here are the results of the commands, but they gave no result:

```
lspci -nnk | grep iA3 amd
grep: amd: Ficheiro ou directoria inexistente # "File or Folder not existing"

```


```
lspci -nnk | grep iA3 vga
grep: vga: Ficheiro ou directoria inexistente # "File or Folder not existing"

```


```
apt-cache policy nvidia-173*
N: Não foi possível encontrar o pacote nvidia-173.run # "It was not possible to find the package nvidia-173.run"
N: Não foi possível encontrar o pacote através da expressão regular 'nvidia-173.run'
# "It was not possible to find the package though the regular expression 'nvidia-173.run'"
```

What am I doing wrong?

---

### Post by bogan on 2013-02-01
Hi!, **yoramdavid**,

> What am I doing wrong?     Nothing!
Woops! my bad typo; should be:
```
lspci -nnk | grep -iA3 amd # to make sure pata/amd is gone, and:  
lspci -nnk | grep -iA3 vga # to see just what  # drivers and modules are installed & used.
```Missing hyphen before iA3.

The other one is a total mystery, it works on my PC both with and without the '*'. try it without.
if that does not work try:
```
apt-cache policy nvidia*
```That should give you a long string of dozens of entries and you would have to search for the 173 entry.

I do not understand why it is looking for "nvidia-173[COLOR=Red].run[/COLOR]".

Did you copy/paste the command ? If not try it that way.

apt-cache policy nvidia-173

EDit If that does not work either, try:> apt-cache policy apt # to isolate it from videoAlso Post: ```
sudo lshw -C display
/usr/lib/nux/unity_support_test -p
```Chao!, **bogan**.

---

### Post by yoramdavid on 2013-02-02
> **bogan said:**
> Hi!, **yoramdavid**,

Nothing!
Woops! my bad typo; should be:
```
lspci -nnk | grep -iA3 amd # to make sure pata/amd is gone, and:  
lspci -nnk | grep -iA3 vga # to see just what  # drivers and modules are installed & used.
```Missing hyphen before iA3.

The other one is a total mystery, it works on my PC both with and without the '*'. try it without.
if that does not work try:
```
apt-cache policy nvidia*
```That should give you a long string of dozens of entries and you would have to search for the 173 entry.

I do not understand why it is looking for "nvidia-173[COLOR=Red].run[/COLOR]".

Did you copy/paste the command ? If not try it that way.

apt-cache policy nvidia-173

EDit If that does not work either, try:Also Post: ```
sudo lshw -C display
/usr/lib/nux/unity_support_test -p
```Chao!, **bogan**.

OK, we have some results now (and yes, I always copy/paste commands) :

```
lspci -nnk | grep -iA3 amd
        Kernel driver in use: pata_amd
        Kernel modules: pata_amd
00:0d.0 FireWire (IEEE 1394) [0c00]: NVIDIA Corporation nForce2 FireWire (IEEE 1394) Controller [10de:006e] (rev a3)
        Subsystem: ASUSTeK Computer Inc. Device [1043:809a]
        Kernel driver in use: firewire_ohci
```

```
lspci -nnk | grep -iA3 vga
03:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV36 [GeForce FX 5700LE] [10de:0343] (rev a1)
        Subsystem: Micro-Star International Co., Ltd. Device [1462:9590]
        Kernel driver in use: nvidia
        Kernel modules: nvidia_173, nouveau, nvidiafb
```

```
apt-cache policy nvidia*
N: Não foi possível encontrar o pacote nvidia-173.run
N: Não foi possível encontrar o pacote através da expressão regular 'nvidia-173.run'
```
> **bogan said:**
> I do not understand why it is looking for "nvidia-173[COLOR=Red].run[/COLOR]".
I do not know either, the only thing that occurs to me is that I downloaded the nvidia-173 driver from the nvidia website and renamed it 'nvidia-173.run' to install it in tty mode and after shutting down the xserver (which I think failed - you wrote about that also).

```
apt-cache policy nvidia
N: Não foi possível encontrar o pacote nvidia
```

```
apt-cache policy nvidia-173
nvidia-173:
  Instalado: 173.14.36-0ubuntu0.1
  Candidato: 173.14.36-0ubuntu0.1
  Tabela de Versão:
 *** 173.14.36-0ubuntu0.1 0
        100 /var/lib/dpkg/status
     173.14.35-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted i386 Packages
```

```
apt-cache policy apt
apt:
  Instalado: 0.9.7.5ubuntu5.2
  Candidato: 0.9.7.5ubuntu5.2
  Tabela de Versão:
 *** 0.9.7.5ubuntu5.2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ quantal-security/main i386 Packages
        100 /var/lib/dpkg/status
     0.9.7.5ubuntu5 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main i386 Packages

```

```
sudo lshw -C display
[sudo] password for yoram: 
  *-display               
       description: VGA compatible controller
       product: NV36 [GeForce FX 5700LE]                                                                                                                  
       vendor: NVIDIA Corporation                                                                                                                         
       physical id: 0                                                                                                                                     
       bus info: pci@0000:03:00.0                                                                                                                         
       version: a1                                                                                                                                        
       width: 32 bits                                                                                                                                     
       clock: 66MHz                                                                                                                                       
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom                                                                                
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5                                                                                     
       resources: irq:19 memory:e5000000-e5ffffff memory:d0000000-dfffffff memory:e6000000-e601ffff
```

```
/usr/lib/nux/unity_support_test -p
bash: /usr/lib/nux/unity_support_test: Ficheiro ou directoria inexistente # file or folder not existing
```

> EDit If that does not work either, try:Also Post: ```
sudo lshw -C display
/usr/lib/nux/unity_support_test -p
```Chao!, **bogan**.
I have a doubt here, if you post two lines of code in one box, am I supposed to copy paste one line at a time in the konsole or both together?
I tried both ways and got nothing for the second line when pasting both lines at the same time.

I am assuming you want me to do one step at a time, ie I have not done anything about your third point of your first post here.

Thank you once more.
Yoram

---

### Post by yoramdavid on 2013-02-02
> **furything said:**
> Phew glad you are working.

Have you rebooted since getting the 173 driver installed? IGNORE reread your post

Looks like your answer is here
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
this states about blacklisting the intel_agp which it looks like you may be using

Hi furything,

Yes, I had tried that also, the driver seems to be installed, **is active** but is not in use.
Blacklisting the intel_agp did not help.
I have 3 blacklisted enties there already: 
```
blacklist amd76x_edac
blacklist nouveau
blacklist intel_agp
```

Would any of those blacklisted be the reason the driver is active but not in use?

```
gksudo gedit /etc/modprobe.d/blacklist.conf
O programa 'gksudo' não está instalado actualmente. Pode instala-lo escrevendo:
sudo apt-get install gksu
```
Why is it gksudo does not work?
kdesudo works though, so does sudo.

Thank you once more.
Yoram

---

### Post by bogan on 2013-02-02
Hi!, **yoramdavid**,

I am a bit confused as to what the present state of things is. Could you summarize what is still not to your liking and needs, and which problems you have raised are not yet solved, apart from those which are just a need for 'Why's and 'What For's.

You are getting the Resolution you want ?  Right ??


Ok, at least some of it now makes sense [ to me ].

1st: 'gksudo' not working, 2 possibilities [actually guesses] either, as you are using 'kdesudo', and it works, you have kde installed with Mint, and that inhibits 'gksudo'; or, in the long ago days when nvidia-173 was cutting edge, everyone was told to use 'gksu' for graphical programs, 'gksudo' was introduced - I believe - about v10.04 and around v11.10 we were told 'gksu' was now deprecated and to use 'gksudo' instead. It seems probable that somehow gksudo is not recognised or not congenial to yourkernel/Motherboard combination.

Especially if [ 2nd:] the pata-amd, which is apparently a driver for your AMD Motherboard as a Kernal driver, is not working or is blacklisted and needed.

 Does the following show anything as installed modules in use & their dependencies ?: ```
lsmod | grep -ie intel -ie pata -ie nouveau -ie nvidia
```3rd: You Posted:> I am assuming you want me to do one step at a time, ie I have not done anything about your third point of your first post here.You are correct, if the intention was to run them in direct sequence, they would be on the same line with a space or '&&' between them. I am not sure which group of three you are reffering to, but if it is the one with a '#' at the start, that is just a comment, or a note of interest.

4th:In your response to **furything**:> Yes, I had tried that also, the driver seems to be installed, [COLOR=Blue]**is active** but is not in use.[/COLOR]I assume that referred to the 'intel-agp' driver, and the blue bit means that is shown that way in ADDITIONAL DRIVERS.

If so, there is a bug in that program that reports programs as active but not in use, when in fact they are running; so do not pay too much attention to that.

**Edit: **If I understand** furything's **Link correctly it referred to even older version of nvidia than 173, and 'intel-agp' was blacklisted to overcome the inability to Sleep or Suspend. 

5th: As I understand the present situation. 'nvidia-173' is running OK, but is still shown as 'not in use'. Is that correct?, and are you still getting 'unmet' or 'broken packages' ? or 'dependencies' errors ?.

Have you checked if the program you renamed as 'nvidia-173.run' still exists ?, if so delete it and again run:
```
apt-cache policy nvidia*
``` Some programs, expected to refer to several files, give up if any one  is not found, and do not deal with the rest.

6th: 'apt-cache policy is now working OK. The reason it does not find any 'nvidia' files, is that they are all named "nvidia-something', except for the kernal module.

7th: Which leaves the:  '/usr/lib/nux/unity_support_test -p' not being found. That should be present in all Ubuntu versions, from11.04 and after, which include Unity; if you are still running Mint, and it uses Kde and not Unity, then that would explain that.

However, that is unknown territory to me, and I am groping at straws.

Chao!. **bogan**.

---

### Post by yoramdavid on 2013-02-02
Hi Bogan,
> **bogan said:**
> Hi!, **yoramdavid**,

I am a bit confused as to what the present state of things is. Could you summarize what is still not to your liking and needs, and which problems you have raised are not yet solved, apart from those which are just a need for 'Why's and 'What For's.

You are getting the Resolution you want ?  Right ??

Yes I am getting the right resolution.
What is still not to my liking:
1. If I boot Mint on normal mode, I have a black desktop with only a cursor. I am now on safe mode.
2. No flash application is working on web pages, the application google-earth also does not work. I was told/read that installing the proper drivers that would be solved.
3. Sometimes the computer gets very slow, browsing the net also gets slow. I read somewhere it could be related to drivers.

> Especially if [ 2nd:] the pata-amd, which is apparently a driver for your AMD Motherboard as a Kernal driver, is not working or is blacklisted and needed.
My motherboard is a "ASUSTeK A7N8X-E" AMD? I am confused, the processor is AMD.


> Does the following show anything as installed modules in use & their dependencies ?: ```
lsmod | grep -ie intel -ie pata -ie nouveau -ie nvidia
```

```
lsmod | grep -ie intel -ie pata -ie nouveau -ie nvidia
nvidia               7108000  24 
snd_intel8x0           33106  2 
snd_ac97_codec        105616  1 snd_intel8x0
snd_pcm                80163  6 saa7134_alsa,snd_usb_audio,snd_cs4236,snd_wss_lib,snd_intel8x0,snd_ac97_codec
snd_page_alloc         14036  3 snd_wss_lib,snd_intel8x0,snd_pcm
snd                    61991  25 saa7134_alsa,snd_wavefront,snd_usb_audio,snd_usbmidi_lib,snd_cs4236,snd_wss_lib,snd_opl3_lib,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_intel8x0,snd_ac97_codec,snd_seq,snd_pcm,snd_seq_device,snd_timer
pata_amd               13750  6 

```

> 3rd: ...I am not sure which group of three you are reffering to, but if it is the one with a '#' at the start, that is just a comment, or a note of interest.
Yes, I understand the comment sign. I was referring to the third point of your first post on this threat:
> Third, if you have to install nvidia-173 from the nvidia.com site, that is the version recommended.
The 'error' you [yoramdavid] described, is not a system error but your mistake.
You have to shut down the xserver before running the nvidia-xxxx-.run file, which should be found in the /home/username/Downloads folder - unless your browser is set to download & save elseware.
To do that: 'Ctrl+Alt+F1', login and enter password - it will not show - plus 'Enter', and run:
Code:

sudo service lightdm stop

[ 'Ctrl+Alt+F1' will return you to the GUI Desktop.]

Before you try that, however be sure to fully remove all the drivers you have tried to install since you re-installed the OS.
Code:

sudo apt-get remove --purge < packagename> # for all drivers by name, and then:
sudo apt-get remove --purge nvidia*
I do not know if you want me to do that yet or not. I have not done it.

> 4th:In your response to **furything**:I assume that referred to the 'intel-agp' driver, and the blue bit means that is shown that way in ADDITIONAL DRIVERS.

If so, there is a bug in that program that reports programs as active but not in use, when in fact they are running; so do not pay too much attention to that.
Yes, it is in the Additional Drivers gui, it shows the nvidia-173 driver active but says "The driver is activated but not currently in use."

> 5th: As I understand the present situation. 'nvidia-173' is running OK, but is still shown as 'not in use'. Is that correct?, and are you still getting 'unmet' or 'broken packages' ? or 'dependencies' errors ?.
Yes, the driver is activated but not currently in use.
unmet: I have never seen that message.
Broken packages held: yes.
'dependencies' errors: I have not had messages of such.

> Have you checked if the program you renamed as 'nvidia-173.run' still exists ?, if so delete it and again run:
```
apt-cache policy nvidia*
``` Some programs, expected to refer to several files, give up if any one  is not found, and do not deal with the rest.
Yes, I had left the program 'nvidia-173.run' there. I deleted it and that made the difference:
**"nenhum" means "none"**
```
apt-cache policy nvidia*
nvidia-180-libvdpau-dev:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-173-updates:
  Instalado: (nenhum)
  Candidato: 173.14.35-0ubuntu3
  Tabela de Versão:
     173.14.35-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted i386 Packages
nvidia-185-libvdpau-dev:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
libgl1-nvidia-legacy-71xx-glx:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-glx-173-dev:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-current:
  Instalado: (nenhum)
  Candidato: 304.51.really.304.43-0ubuntu1
  Tabela de Versão:
     304.51.really.304.43-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted i386 Packages
nvidia-libvdpau-ia32:
  Instalado: (nenhum)
  Candidato: (nenhum)                                                                                                                                     
  Tabela de Versão:                                                                                                                                       
nvidia-cuda-debugger:                                                                                                                                     
  Instalado: (nenhum)                                                                                                                                     
  Candidato: (nenhum)                                                                                                                                     
  Tabela de Versão:                                                                                                                                       
nvidia-libvdpau1:                                                                                                                                         
  Instalado: (nenhum)                                                                                                                                     
  Candidato: (nenhum)                                                                                                                                     
  Tabela de Versão:                                                                                                                                       
nvidia-glx-dev:                                                                                                                                           
  Instalado: (nenhum)                                                                                                                                     
  Candidato: (nenhum)                                                                                                                                     
  Tabela de Versão:
nvidia-glx-185-dev:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-173:
  Instalado: 173.14.36-0ubuntu0.1
  Candidato: 173.14.36-0ubuntu0.1
  Tabela de Versão:
 *** 173.14.36-0ubuntu0.1 0
        100 /var/lib/dpkg/status
     173.14.35-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted i386 Packages
nvidia-settings-updates:
  Instalado: (nenhum)
  Candidato: 304.51-0ubuntu2
  Tabela de Versão:
     304.51-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted i386 Packages
nvidia-libopencl1-dev:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-settings:
  Instalado: 304.51-0ubuntu2
  Candidato: 304.51-0ubuntu2
  Tabela de Versão:
 *** 304.51-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main i386 Packages
        100 /var/lib/dpkg/status
nvidia-185-libvdpau:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-185-kernel-source:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
libgl1-nvidia-legacy-173xx-glx:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-vdpau-driver:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-96-dev:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-opencl-profiler:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-cg-toolkit:
  Instalado: (nenhum)
  Candidato: 3.1.0013-1
  Tabela de Versão:
     3.1.0013-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/multiverse i386 Packages
nvidia-96:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-libvdpau1-ia32:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-glx-legacy-173xx:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-glx-96-dev:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-173-updates-dev:
  Instalado: (nenhum)
  Candidato: 173.14.35-0ubuntu3
  Tabela de Versão:
     173.14.35-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted i386 Packages
nvidia-96-updates:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-experimental-304:
  Instalado: (nenhum)
  Candidato: 304.48-0ubuntu1
  Tabela de Versão:
     304.48-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted i386 Packages
nvidia-experimental-310:
  Instalado: (nenhum)
  Candidato: 310.14-0ubuntu1
  Tabela de Versão:
     310.14-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/restricted i386 Packages
libkwinactivenvidiahack4:
  Instalado: (nenhum)
  Candidato: 4:4.9.4-0ubuntu0.2
  Tabela de Versão:
     4:4.9.4-0ubuntu0.2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe i386 Packages
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe i386 Packages
nvidia-glx-173:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-glx-180:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-glx-185:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-180-modaliases:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-cuda-profiler:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-glx-legacy-96xx-dev:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-visual-profiler:
  Instalado: (nenhum)
  Candidato: 4.2.9-1ubuntu1
  Tabela de Versão:
     4.2.9-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/multiverse i386 Packages
nvidia-current-updates:
  Instalado: (nenhum)
  Candidato: 304.51-0ubuntu1
  Tabela de Versão:
     304.51-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted i386 Packages
nvidia-cg-dev:
  Instalado: (nenhum)
  Candidato: 3.1.0013-1
  Tabela de Versão:
     3.1.0013-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/multiverse i386 Packages
mate-sensors-applet-nvidia:
  Instalado: (nenhum)
  Candidato: 1.2.0-3+precise
  Tabela de Versão:
     1.2.0-3+precise 0
        700 http://packages.linuxmint.com/ nadia/import i386 Packages
nvidia-cg-doc:
  Instalado: (nenhum)
  Candidato: 3.1.0013-1
  Tabela de Versão:
     3.1.0013-1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/multiverse i386 Packages
libglx-nvidia-alternatives:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-kernel-common:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-opencl-dev:
  Instalado: (nenhum)
  Candidato: 4.2.9-1ubuntu1
  Tabela de Versão:
     4.2.9-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/multiverse i386 Packages
nvidia-current-updates-dev:
  Instalado: (nenhum)
  Candidato: 304.51-0ubuntu1
  Tabela de Versão:
     304.51-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted i386 Packages
libkwinnvidiahack4:
  Instalado: 4:4.9.4-0ubuntu0.2
  Candidato: 4:4.9.4-0ubuntu0.2
  Tabela de Versão:
 *** 4:4.9.4-0ubuntu0.2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe i386 Packages
        100 /var/lib/dpkg/status
     4:4.9.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe i386 Packages
libgl1-nvidia-glx:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-glx-legacy-71xx:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-libvdpau:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
boinc-nvidia-cuda:
  Instalado: (nenhum)
  Candidato: 7.0.27+dfsg-5ubuntu0.12.04.1
  Tabela de Versão:
     7.0.27+dfsg-5ubuntu0.12.04.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/multiverse i386 Packages
     7.0.27+dfsg-5 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/multiverse i386 Packages
nvidia-current-dev:
  Instalado: (nenhum)
  Candidato: 304.51.really.304.43-0ubuntu1
  Tabela de Versão:
     304.51.really.304.43-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted i386 Packages
glx-alternative-nvidia:
  Instalado: (nenhum)
  Candidato: 0.2.2
  Tabela de Versão:
     0.2.2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/multiverse i386 Packages
nvidia-compute-profiler:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-glx-96:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-experimental-304-dev:
  Instalado: (nenhum)
  Candidato: 304.48-0ubuntu1
  Tabela de Versão:
     304.48-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted i386 Packages
nvidia-glx-legacy-71xx-dev:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-glx-180-dev:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-installer-cleanup:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-va-driver:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-current-modaliases:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-173-modaliases:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-185-modaliases:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-glx-legacy-96xx:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-experimental:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-texture-tools:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-glx-legacy-173xx-dev:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-common:
  Instalado: (nenhum)
  Candidato: 1:0.2.71.1
  Tabela de Versão:
     1:0.2.71.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe i386 Packages
     1:0.2.71 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe i386 Packages
nvidia-tegra3:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-tegra:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-current-experimental-304:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-96-kernel-source:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-cuda-dev:
  Instalado: (nenhum)
  Candidato: 4.2.9-1ubuntu1
  Tabela de Versão:
     4.2.9-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/multiverse i386 Packages
nvidia-cuda-doc:
  Instalado: (nenhum)
  Candidato: 4.2.9-1ubuntu1
  Tabela de Versão:
     4.2.9-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/multiverse i386 Packages
nvidia-173-kernel-source:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-cuda-gdb:
  Instalado: (nenhum)
  Candidato: 4.2.9-1ubuntu1
  Tabela de Versão:
     4.2.9-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/multiverse i386 Packages
libgl1-nvidia-legacy-96xx-glx:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-experimental-310-dev:
  Instalado: (nenhum)
  Candidato: 310.14-0ubuntu1
  Tabela de Versão:
     310.14-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/restricted i386 Packages
nvidia-180-kernel-source:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-cuda-toolkit:
  Instalado: (nenhum)
  Candidato: 4.2.9-1ubuntu1
  Tabela de Versão:
     4.2.9-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/multiverse i386 Packages
nvidia-libvdpau-dev:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
libgl1-nvidia-alternatives:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-glx:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:
nvidia-settings-experimental-304:
  Instalado: (nenhum)
  Candidato: 304.48-0ubuntu2
  Tabela de Versão:
     304.48-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted i386 Packages
nvidia-settings-experimental-310:
  Instalado: (nenhum)
  Candidato: 310.14-0ubuntu1
  Tabela de Versão:
     310.14-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/main i386 Packages
nvidia-173-dev:
  Instalado: (nenhum)
  Candidato: 173.14.35-0ubuntu3
  Tabela de Versão:
     173.14.35-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/restricted i386 Packages
nvidia-180-libvdpau:
  Instalado: (nenhum)
  Candidato: (nenhum)
  Tabela de Versão:

```

> 6th: 'apt-cache policy is now working OK. The reason it does not find any 'nvidia' files, is that they are all named "nvidia-something', except for the kernal module.
ok

> 7th: Which leaves the:  '/usr/lib/nux/unity_support_test -p' not being found. That should be present in all Ubuntu versions, from11.04 and after, which include Unity; if you are still running Mint, and it uses Kde and not Unity, then that would explain that.
I am using Mint 14 KDE desktop.

I hope I answered all your questions, thank you a lot for your time.
I will be away for 4 days from now.

Regards,
Yoram

---

### Post by bogan on 2013-02-02
Hi!, **yoramdavid**,

You posted:> I do not know if you want me to do that [ install nvida.com downloaded driver ] yet or not. I have not done it.:No I do not want you to do that; I Posted that info as you had Posted you had tried to install a Download,with errors, and, at the time I thought it likely you would need to do so.

'apt-cache' now works as it should, and shows you have only nvidia-173, nvidia settings, and nvidia-common installed. [ The later is a program to find legacy nvidia drivers ].

There is a potential problem there, as the version of nvidia-settings is: 304.51-0ubuntu2.

I have no idea if it will work OK with 173 installed. Have you tried it to set your Resolution??

You could run Synaptic Package Manager and see if it lists a 173 version, with your set-up, but we can look into that when you get back after your four days.

Chao!, **bogan**.

---

### Post by furything on 2013-02-04
Hi Yoram
Now that you have bogan engaged I will stay out of this post.

I am glad you are here bogan helping Yoram. 

Thanks

---

### Post by bogan on 2013-02-04
> **furything said:**
> Hi Yoram
Now that you have bogan engaged I will stay out of this post.
...... ThanksPlease do not stop offering anything you feel relevant, just because I have responded to a personal appeal.

At least keep on eye on the Thread, you never know what might come along.

I see my Guru, MAFoElffen is back in contact, and he knows a vast amount about setting Resolution and related problems, if that is still an issue for the OP.

Chao!, **bogan**.

---

### Post by furything on 2013-02-05
Hi Bogan
Yes I still keep a look out for anything I may learn on any thread I have posted to.

Unfortunately although I have had many issues since dapper and have googled and fixed myself, my memory is not that great so I cannot always remember what I have done. 

I think you are in a much better position to help Yoram but if I do remember anything I will of course post.

Thank you

---

### Post by yoramdavid on 2013-02-07
> **bogan said:**
> Hi!, **yoramdavid**,

There is a potential problem there, as the version of nvidia-settings is: 304.51-0ubuntu2.

I have no idea if it will work OK with 173 installed. Have you tried it to set your Resolution??

Chao!, **bogan**.

Hi Bogan,

Back I am.

Now, you ask me to set my resolution with Nvidia Xserver setings. Note that my resolution is good, it is the rest that is not :

[Quote=yoramdavid]
What is still not to my liking:
1. If I boot Mint on normal mode, I have a black desktop with only a cursor. I am now on safe mode.
2. No flash application is working on web pages, the application google-earth also does not work. I was told/read that installing the proper drivers that would be solved.
3. Sometimes the computer gets very slow, browsing the net also gets slow. I read somewhere it could be related to drivers.
[/Quote]

I opened the nvidia-settings any way and I am not sure where to change the resolution, I see a lot of other options which I have no idea what they do, but no where to change resolution. Perhaps because it is not working as you say.
Under the menu "X Sever Display Configuration" (perhaps it would be here I should be able to change resolutions) there are no setting options, just an error message:

```
Unable to load X Server Display Configuration page:

The NVIDIA X driver on yoram-I:0.0 is not new
enough to support the nvidia-settings Display Configuration page.
```

> 
You could run Synaptic Package Manager and see if it lists a 173 version, with your set-up, but we can look into that when you get back after your four days.

In synaptics, I searched for nvidia-173 and the following come up:
- nvidia-173 version 173.14.36-0ubuntu0.1 # this is the one installed
- nvidia-173-updates version 173.14.35-0ubuntu3 # not installed
- nvidia-173-updates-dev version 173.14.35-0ubuntu3 # not installed
- nvidia-173-dev version 173.14.36-0ubuntu0.1 # not installed

Thank you.
Yoram

---

### Post by yoramdavid on 2013-02-07
> **furything said:**
> Hi Yoram
Now that you have bogan engaged I will stay out of this post.

I am glad you are here bogan helping Yoram. 

Thanks

Hi furything,

Yes, I understand, I wanted to reply to your post any way.

Thank you.
Yoram

---

### Post by yoramdavid on 2013-02-07
The original threat was about not being able to set the resolution to 800 x 600 in Ubuntu/Lubuntu.

Then following advices I installed a fresh Linux which happened to be Mint 14.

No the resolution is ok, but the original problems (which led me to install nvidia-drivers and got stuck at 800 x 600) are still there.

This threat continued here despite that it refers now to a Mint distro.
And the thread in Mint forums died...

Shall I change the title to "No flash" or something of the kind?
Or shall I just leave it as it is?

---

### Post by bogan on 2013-02-07
Hi!, **yoramdavid**,

You Posted:
> The NVIDIA X driver on yoram-I:0.0 is not new enough to support the nvidia-settings Display Configuration page.That is what I was afraid of, when I wrote: "There is a potential problem".

The object of running Nvidia XserverSettings, was: firstly, to see if the version you have would run with the installed driver - clearly it does not - secondly, - if it did run - to see if it correctly showed the resolution, and that the driver was correctly installed, and saw your monitor correctly as well.

Had it run OK, the resolution could be checked or set using the 2nd menu item: "X Server Display Configuration", which you tried. 
There should be a screen image with the Monitor name and its native resolution in the middle; below, one of the boxes  labelled: "Resolution",  may show "Auto", or a specific resolution, with a drop-down button, which will show the available resolutions which can be displayed.

You could try a Synaptic search for 'nvidia-settings' and see if it lists one for 173.
If it does, use Synaptic to remove the present 304.51 version or:```
 sudo apt-get remove --purge nvidia-settings* 
```and install the 173 version.```
 sudo apt-get install nvidia-settings # make sure the package name is correct
```As far as the basic problem of difficulties with Flash and Google Earth are concerned, all I know is that there are a lot of Posts about those things, but I have not studied them, or even noticed if they are marked as 'Solved'.

Nor do I know if they are considered to be video driver issues.

I would think your best bet would be a Forum search for solved Threads, and to post a new Thread , including in the title: Mint, nvidia-173, Flash, & Google Earth; or adding those names as Tags as well, rather than change the title of this one. Then Post a link to it here.

Sorry I am not able to assist you with those issues. 

Chao!, **bogan.**

---

### Post by yoramdavid on 2013-02-07
> **bogan said:**
> Hi!, **yoramdavid**,

You Posted:

You could try a Synaptic search for 'nvidia-settings' and see if it lists one for 173.
If it does, use Synaptic to remove the present 304.51 version or:```
 sudo apt-get remove --purge nvidia-settings* 
```and install the 173 version.```
 sudo apt-get install nvidia-settings # make sure the package name is correct
```

Chao!, **bogan.**

In synaptics, there is no nvidia-settings 173, there are:

- nvidia-settings 304.51 (the one installed),
- nvidia-settings-experimental-304 version 304.48-0ubuntu2
- nvidia-settings-experimental-310 version 310.14-0ubuntu1

I could try those one by one to see if any luck.
Today, google-earth was working (perhaps some updates)

Thank you Bogan.
Yoram

---

### Post by SeijiSensei on 2013-02-07
Is there any real advantage to using a proprietary NVIDIA driver for a card as old as an FX5700?  It doesn't support VDPAU.  Even if it did Adobe left behind that lovely bug in Flash that turns people into smurfs if you enable hardware acceleration.  As far as I can tell, that will never be fixed since Adobe is no longer supporting Linux.  

I'd just let Ubuntu install the Nouveau driver and be done with it.  I don't have the sense that Yoram is trying to play 3D games or anything like that.

---

### Post by yoramdavid on 2013-02-07
> **SeijiSensei said:**
> Is there any real advantage to using a proprietary NVIDIA driver for a card as old as an FX5700?  It doesn't support VDPAU.  Even if it did Adobe left behind that lovely bug in Flash that turns people into smurfs if you enable hardware acceleration.  As far as I can tell, that will never be fixed since Adobe is no longer supporting Linux.  

I'd just let Ubuntu install the Nouveau driver and be done with it.  I don't have the sense that Yoram is trying to play 3D games or anything like that.

Thank you SeijiSensei, no I am not willing to play that kind of games...
But the reason I installed those drivers is because that with the nouveau drivers I had no flash, no google-earth, a black screen if I log into normal mode.

Regards,
Yoram

---

### Post by yoramdavid on 2013-02-08
Hi all,

Today I tried something I had tried some time ago but did not work, which is running the following codes to reinstall the flash plug-in:
```
sudo apt-get remove flashplugin-installer
sudo apt-get clean
sudo apt-get install flashplugin-installer

```

Only this time I opened the youtube page and clicked on a video, it did not play.

I ran the first line of code:
```
sudo apt-get remove flashplugin-installer

```

Nothing happened.

I ran the second line of code:
sudo apt-get clean
[/CODE]

Youtube site tells me there is a plug-in that needs to be installed, I did nothing and the video started playing after say, 3 seconds.
I tried a few, they all show the message about the missing plug-in, then they all worked.
I tried a web page which I know has a flash menu, it did not function, it asks to install a plugin.
If I click on the "install plugin" icon, it opens a window telling the plugin is unknown (application/x-shockwasve-flash) and gives me the option to manual install.

I ran the third line of code:
```

sudo apt-get install flashplugin-installer

```

Flash in youtube stopped to work and does not display the message of missing plugin.
The same web page which I know has a flash menu, did not function either but does not display the message of missing plugin.

I tried the "install plugin" icon, which opens a window telling the plugin is unknown (application/x-shockwasve-flash) and gives me the option to manual install.
The manual install takes me to a web page: [http://get.adobe.com/br/flashplayer/]("http://get.adobe.com/br/flashplayer/"). There is a list there: a .yum file, a tar.gz, a .rpm and a apt files.

I tried apt and it failed with an error message of "Canal desconhecido 'nadia-partner'" (unkown partner 'nadia-partner')

I tried the .rpm file and followed the instrucions where I have to run the following commands:
```
          + # rpm -Uvh <rpm_package_file>
          + Click Enter key and follow prompts
```
But the code was not recognized.

I then tried the tar.gz, unpacked it and the instrucions are to copy a "libflashplayer.so" to the plugins folder in firefox. I do not find such folder under /home/username/.mozilla nor in /home/username/.mozilla/firefox, so I created one in both and copied the file in both (not knowing in which I had to put it).

Then I have to copy the /usr folder to /usr which I did.
Flash stopped working on both pages.


Now I am back where I removed the plugin with the two first lines of code, and removed the "libflashplayer.so" from the mozilla plugin folder. At least I have most of youtube videos working.

---

### Post by bogan on 2013-02-09
Hi!,** yoramdavid**,

Have you done an update with Update Manager/Software Updater recently ??

There is an update to Flash Player [ to 11.2.202.262  12.10.1. ] and an installer for if it is not installed. [10.00 HRS  09/02/13]

[COLOR=LemonChiffon]  I do not know if there is one on offer for 12.04 - I forget what you are running.[/COLOR]

Edit: I just checked, there is an update to the Flashpug-installer on offer in 12.04.

I am no expert on this, but I would have thought you needed to** run **the flashplug-installer, as well as to install it.

Then check again for the update.

Chao!,** bogan**.

---

### Post by yoramdavid on 2013-02-09
> **bogan said:**
> Hi!,** yoramdavid**,

Have you done an update with Update Manager/Software Updater recently ??

There is an update to Flash Player [ to 11.2.202.262  12.10.1. ] and an installer for if it is not installed. [10.00 HRS  09/02/13]

[COLOR=LemonChiffon]  I do not know if there is one on offer for 12.04 - I forget what you are running.[/COLOR]



Hi **Bogan**

I am running LinuxMint Nadia 14, Kernel 3.5.0-17-generic
I opended the update manager, there were some errors (there are often errors of such (404)):

```
Falhou obter http://ppa.launchpad.net/diesch/testing/ubuntu/dists/nadia/main/source/Sources  404  Not Found
Falhou obter http://ppa.launchpad.net/diesch/testing/ubuntu/dists/nadia/main/binary-i386/Packages  404  Not Found
Falhou obter http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu/dists/nadia/main/source/Sources  404  Not Found
Falhou obter http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu/dists/nadia/main/binary-i386/Packages  404  Not Found
Falhou o download de alguns ficheiros de índice. Foram ignorados ou os antigos foram usados em seu lugar.
```

There were no updates available.
The flash plugin I downloaded is the 11.2.202.262 2012, that is all I find on their webpage.

> Edit: I just checked, there is an update to the Flashpug-installer on offer in 12.04.

I am no expert on this, but I would have thought you needed to** run **the flashplug-installer, as well as to install it.

Then check again for the update.

Chao!,** bogan**.

I am not sure what is the difference between running and installing it?

To install I use the command:```
sudo apt-get install flashplugin-installer

```
And it installed the 11.2.202.262ubuntu0.12.10.1
So that is just the installer? How do I run it?

---

### Post by bogan on 2013-02-09
Hi!, **yoramdavid**,

You Posted: > So that is just the installer? How do I run it?Same as any other program from a terminal, just its name : ```
sudo flashplugin-installer
``` Though you may need to make it executable first: ```
sudo chmod a+x flashplugin-installer
```

But bear in mind I am only guessing, keep an eye out for any other error messages.

The 404 errors are either because your internet connection was not working properly, or there are faults in your Software Sources list. Whether it is important, depends on what you are trying to install from 'diesch-testing' & 'guiseppe-iuculano'.

Chao!, **bogan.**

---

### Post by SeijiSensei on 2013-02-09
I find it much easier to install Flash by enabling the "partner" repository in Ubuntu then running 
```

sudo apt-get update
sudo apt-get install adobe-flashplugin

```
That has worked flawlessly for me.

---

### Post by yoramdavid on 2013-02-10
> **bogan said:**
> Hi!, **yoramdavid**,

You Posted: Same as any other program from a terminal, just its name : ```
sudo flashplugin-installer
``` Though you may need to make it executable first: ```
sudo chmod a+x flashplugin-installer
```

But bear in mind I am only guessing, keep an eye out for any other error messages.

The 404 errors are either because your internet connection was not working properly, or there are faults in your Software Sources list. Whether it is important, depends on what you are trying to install from 'diesch-testing' & 'guiseppe-iuculano'.

Chao!, **bogan.**

Hi Bogan.

I did not succeed with those codes, I do not think what I have downloaded coincides with these codes.
But I think it was installed, it just does not work. I used those codes to install:
```
sudo apt-get install adobe-flashplugin
sudo apt-get install flashplugin-installer
```

Worse now, nothing plays as flash and it freezes the firefox and the computer with a script error on firefox if I open a page with flash video.```
Um script desta página pode estar ocupado, ou pode ter parado de responder. Pode parar o script agora, ou aguardar que o script termine.

Script: http://s.ytimg.com/yts/jsbin/www-watch-extra-vflGsPx5A.js:1
```
I understand it is from the youtube website or from firefox trying to play a youtube video.

'guiseppe-iuculano' was to install kompozer but it failed.
I do not remember what 'diesch-testing' is for.

I'll have to do more research on those on the net.

Thank you.
Yoram

---

### Post by yoramdavid on 2013-02-10
> **SeijiSensei said:**
> I find it much easier to install Flash by enabling the "partner" repository in Ubuntu then running 
```

sudo apt-get update
sudo apt-get install adobe-flashplugin

```
That has worked flawlessly for me.

Hi SeijiSensei,

Unfortunately not for me.
After doing that, I got a script error on firefox if I try to play a flash video on youtube.
```
Um script desta página pode estar ocupado, ou pode ter parado de responder. Pode parar o script agora, ou aguardar que o script termine.

Script: http://s.ytimg.com/yts/jsbin/www-watch-extra-vflGsPx5A.js:1

I understand it is from the youtube website or from firefox trying to play a youtube video.
```

Which freezes the firefox and the computer until I close that tab.

Thank you.
Yoram

---

### Post by bogan on 2013-02-10
Hi!,** yoramdavid**,

You Posted:>  I do not remember what 'diesch-testing' is for.I use the 'diesch-testing ppa' for 'Classicmenu-Indicator' to give menus with Unity.

If those error messages worry you, it is possible to remove them with PPA-Purge.

I tried running 'flashplugin-installer', both from dash and from a terminal, but neither did anything and the later said it could not be found, though Synaptic and Dash both showed it.

In another 12.10 installation Synaptic listed 'adobe-flashplugin' as not installed and when I tried to get Synaptic to install it, there was a warning that it needed to uninstall 'flashplugin-installer' first.

So that makes things even more confused than ever.

But at least it confirms that Synaptic will tell you what is actually installed.

Chao!, **bogan.**

---

### Post by yoramdavid on 2013-02-10
> **bogan said:**
> Hi!,** yoramdavid**,

You Posted:I use the 'diesch-testing ppa' for 'Classicmenu-Indicator' to give menus with Unity.

If those error messages worry you, it is possible to remove them with PPA-Purge.

I tried running 'flashplugin-installer', both from dash and from a terminal, but neither did anything and the later said it could not be found, though Synaptic and Dash both showed it.

In another 12.10 installation Synaptic listed 'adobe-flashplugin' as not installed and when I tried to get Synaptic to install it, there was a warning that it needed to uninstall 'flashplugin-installer' first.

So that makes things even more confused than ever.

But at least it confirms that Synaptic will tell you what is actually installed.

Chao!, **bogan.**

Oh, yes. Classic-menu indicator I installed it but found out it does not work under KDE.
I do not like the menu of KDE, installed Lubuntu-desktop, I like it better.
These ppa, I removed them from the Program manager as with ppa-purge I get errors of ppa not found...
No more errors now.

Thank you.
Yoram

---

### Post by yoramdavid on 2013-02-12
I was quite upset about that script error every time I would open youtube or a flash web-page (which freezes the firefox and the computer until I would close that tab) I mentioned on an earlier post, so I tried to track what was the cause.

I deactivated all my extras in Firefox and restarted firefox, opened youtube and same script error. Same behaviour but different error message.

Then I deactivated all the languages and dictionnary extensions, nothing changed. I then deactivated the flash plugin along with all the other plugins and no more script error.

I removed any installation of flash I had and then Installed the flashplugin-installer.
I knew that with it I could assist some content of youtube.

I then did research on the web as suggested by **bogan** for threats about flash with the solved label again, not that I had not done it already before.
I found one that solved my problem: [http://forums.linuxmint.com/viewtopic.php?f=175&t=104222]("http://forums.linuxmint.com/viewtopic.php?f=175&t=104222") which mentioned the  mint-flashplugin-10.3. I installed the mint-flashplugin-10.3 but left the flashplugin-installer unlike **mauromol** did (and I am not trying anything else just in case things go wrong!) and tested:
Results: flash works on all youtube I tested so far and other web-pages I tested it with that have flash for menus or animations.
The Nvidia X server Settings still cannot display the page "X server display Configuration" but I can live with that since I have the resolution I want and flash works :)

I restarted Firefox, re-enabled all the extras, rebooted the computer and it is OK.

It seemed so easy after everything we tried that I could not believe it! :)
I hope it stays like that for a long time now.

Thank you all for your help, I am now going to mark this as solved.

Regards,
Yoram

---

### Post by yoramdavid on 2013-03-04
I found out today that the videos on facebook do not work, it says there is no flash plugin installed.
Therefore this threat is not solved 100%. I see no option to mark as unsolved, so I'll olive it as it is.

:frown:

---

### Post by Yasho on 2013-05-06
Hi
I have the same issue with screen resolution. I am now unable to change it from 640 x 480. Ive followed this thread and more, and ended  with the same results as yoram. I'm still not yet about to do a reinstall, because there is too much reconfiguring to do. :)
I'm using a Samsung NP 300ESX-S01 IN. Intel CoreI5, with Nvidia 610M optimus card. Ubuntu 12.04 and gnome desktop (because I didn't like Unity). System is regularly updated so no issues there, I suppose.
My problem was only that Google earth was not able to run, however had no issues with youtube videos etc. I had read in some posts that Nvidia drivers were causing problems in runnng google earth, and found that the Nvidia driver was not in use.  I have been happily using this same installation with no issues of screen resolution for the past about 4 months. 
The problem started when I tried to get and install Nvidia drivers - this because Google earth would not load. I'm not using this for games or anything , except need to use Google Earth a lot. I have tried the 173 drivers and removed them, I have downloaded drivers from Noobs and tried to install via command line, but still no joy. I downloaded the Nvidia latest driver from their website, and installed it after stopping my xserver. I still have the same problem. 
Screenshot of Synaptec shows only 310 drivers are in use, 173 is deselected and noveau also not in use. I have tried changing the xserver settings as suggested in the Nvidia drivers dialogbox I got, and the only thing that happens is that it writes the configuration to a new file. 
 I also get a message from System Settings>Hardware>additional drivers that Samsung Backlight driver is activated but not in use. I tried a Live CD and my laptop worked well with a live CD of 12.10. I have no problem on Windows 8 which is the alternate install (sadly, some programs still need Windows).
My System > Displays does not have any option of changing screen resolution, and so can only see half the things in a screen.
I have attached screenshots, so any help will be much appreciated.


Thanks in advance.
Yasho
[ATTACH=CONFIG]242250[/ATTACH][ATTACH=CONFIG]242251[/ATTACH][ATTACH=CONFIG]242252[/ATTACH]

---

### Post by Yasho on 2013-05-14
Thanks. The problem was that due to Nvidia, and intel drivers being both in use, I could not get the resolution. Solved with a friend of mine. 
In any case, now I am running 13.04, and no problems with Google earth or with the display resolution. VIrtual box support is also better in this release.
Bye

---

