---
title: "My X server has got a memory leak! :O (What can I do against it?)"
date: 2009-06-29
forum: Desktop Environments
---

### Post by darthmob on 2009-06-29
My problem is rather simple. Upon startup the X server starts hogging memory. first it fills the ram, then the swap file and then it crashes.

my setup:
ubuntu 9.04
[gnome/openbox]("http://icculus.org/openbox/index.php/Help:GNOME/Openbox")

I have attached some pictures to show what I mean:
**the situation at startup:** [system monitor]("http://ubuntuforums.org/attachment.php?attachmentid=119337&stc=1&d=1246276337"), [htop]("http://ubuntuforums.org/attachment.php?attachmentid=119339&stc=1&d=1246276337")
**and after running for a while:** [system monitor]("http://ubuntuforums.org/attachment.php?attachmentid=119336&stc=1&d=1246276275"), [htop]("http://ubuntuforums.org/attachment.php?attachmentid=119338&stc=1&d=1246276337")

As you can see the x server runs on 50% cpu. There are no other programs involved. Interestingly enough there are no problems if I start the xfce desktop or openbox without gnome. Despite installing updates I did not change anything in the last few weeks / months.

Anyone got any ideas what may be the cause or what may help solve the problem?

---

### Post by iponeverything on 2009-06-29
After you machine is up for while and its heavily into swap:

run:

```
top 
```

Hit "M" to sort by memory utilization see what is at the top of the list. Your screen caps of htop are sorted by cpu utilization.

---

### Post by darthmob on 2009-06-29
like I said it's the x server hogging the memory. I made new screenshots with top and proper sorting. it's a slow but steady process which took about 45 minutes to get to the point the screenshots are made.

**500mb into swap:** [system monitor]("http://ubuntuforums.org/attachment.php?attachmentid=119347&stc=1&d=1246284523"), [top]("http://ubuntuforums.org/attachment.php?attachmentid=119348&stc=1&d=1246284523")

---

### Post by iponeverything on 2009-06-29
> 
like I said it's the x server hogging the memory. I made new screenshots with top and proper sorting. it's a slow but steady process which took about 45 minutes to get to the point the screenshots are made.

Sorry I doubted you, just had to see for myself.

===

Maybe its the driver or compiz 

I found these looking around launchpad:

[https://bugs.launchpad.net/ubuntu/+bug/353800](https://bugs.launchpad.net/ubuntu/+bug/353800)

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/372345](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/372345)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/360319](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/360319)

Here is one from the forums:

[http://ubuntuforums.org/showthread.php?t=1149294](http://ubuntuforums.org/showthread.php?t=1149294)

---

### Post by darthmob on 2009-06-29
I have got a nvidia card (8800gts) so I doubt it has to do with the ATI restricted driver. in addition I'm not running compiz. the only effects I use are with xcompmgr but it doesn't matter if it's running or not.

the strange thing is:
I only have the problem since a few days and it only occurs when I run GNOME/openbox (openbox as a wm with all the gnome panels and applications). running a bare openbox session or xfce shows no problems at all.

I wonder if it has to be with a recent update. is there a way to see which updates I installed recently? can I revert them? has there been a xorg update in the last few days?

nevertheless, thanks already for spending some time on google.

// EDIT: recently changed packages can be found in the [synaptic history]("http://www.watchingthenet.com/show-list-of-recently-installed-packages-by-date-on-ubuntu.html"). I'll have a look if there is something suspicious.

// EDIT2: Nice, you can downgrade packages by choosing package -> force version in synaptic.

// EDIT3: Reverting the most recent updates from xorg-server-video-intel and compiz do not seem to change anything. What grinds my gears is some kind of "ghost process" which I have been seeing a lot lately. I don't know what it is and it's always there when the memory gets hogged. I have attached two pictures of it.

the first shows the process at the top of the list. there is no information available despite the pid. it blocks a shutdown / logout unless I ignore it which is shown on the second screenshot. I have seen this for a few weeks / months now but never payed it much attention. I'm not sure if the memory leak was already existing there at well but I rather doubt it.

---

### Post by iponeverything on 2009-06-29
run lsof on that strange process:

```
sudo lsof -p <pid of process>

```

You can also attach a strace to it:

```
sudo strace -p <pid of process>
```

---

### Post by darthmob on 2009-06-30
it seems like that strange process is openbox which is starting endlessly. I can't run lsof on it as it's never running long enough to enter the pid. top shows it as openbox though and the increasing pid matches as well.

now I have to find out why it tries to start openbox all the time. maybe I managed to get a loop somewhere in the startup files..

// EDIT1:
When I start openbox-gnome-session via the failsafe terminal it spams the following error:
```
Openbox-Message: A window manager is already running on screen 0
```
there is no problem when I just start openbox without any gnome. maybe my guess was not that wrong. I'll have a further look into this.

---

### Post by onnod on 2009-06-30
Similar experience to Darthmob. Ubuntu 9.04/Gnome/Openbox (Compiz is not installed). Gateway 6301 laptop with external SyncMaster 940BW monitor. If I select "restart Openbox" from the Openbox menu, I can cause the 'loop' to stop, and all of the "opening usr/bin/openbox" dialogs close, and memory is freed up.

In my case, I did install some items today:

Installed the following packages:
scim-chinese (0.5.91-1ubuntu1)
ttf-baekmuk (2.2-2)
xfonts-baekmuk (2.2-3)

These items were also in the Synaptic history, but they are not installed:

language-support-translations-en (1:9.04+20090401)
openoffice.org-help-en-gb (1:3.1.0-3ubuntu2~jaunty1)
openoffice.org-l10n-en-gb (1:3.1.0-3ubuntu2~jaunty1)
openoffice.org-l10n-en-za (1:3.1.0-3ubuntu2~jaunty1)
thunderbird-locale-en-gb (1:2.0.0.14+1-0ubuntu2)

Snippet of lsof -p:
Xorg    9265 root  DEL    REG        0,9             127961 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127960 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127959 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127958 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127957 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127956 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127955 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127954 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127953 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127952 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127951 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127950 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127949 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127948 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127947 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127946 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127945 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127944 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127943 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127942 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127941 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127940 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127939 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127938 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127937 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127936 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127935 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127934 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127933 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127932 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127931 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127930 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127929 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127928 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127927 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127926 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127925 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127924 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127923 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127922 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127921 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127920 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127919 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127918 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127917 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127916 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127915 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127914 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127913 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127912 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127911 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127910 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127900 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127899 /drm mm object
Xorg    9265 root  DEL    REG        0,9             127895 /drm mm object
Xorg    9265 root  mem    CHR        1,1                838 /dev/mem
Xorg    9265 root  mem    REG        0,0               7786 /sys/devices/pci0000 (stat: No such file or directory)
Xorg    9265 root  mem    REG        8,1  120652    4711178 /usr/lib/xorg/modules/libfb.so
Xorg    9265 root  mem    REG        0,0               7784 /sys/devices/pci0000 (stat: No such file or directory)
Xorg    9265 root  mem    REG        8,1   34084    4622085 /usr/lib/libdrm_intel.so.1.0.0
Xorg    9265 root  mem    REG        8,1   63212    4711177 /usr/lib/xorg/modules/libexa.so
Xorg    9265 root  mem    REG        8,1  554804    4711107 /usr/lib/xorg/modules/drivers/intel_drv.so
Xorg    9265 root  mem    REG        8,1   34164    4622083 /usr/lib/libdrm.so.2.4.0
Xorg    9265 root  DEL    REG        0,9             128491 /drm mm object
Xorg    9265 root  mem    REG        8,1   22696    4711183 /usr/lib/xorg/modules/libvgahw.so
Xorg    9265 root  mem    REG        8,1    9628    4711229 /usr/lib/xorg/modules/extensions/libdri2.so
Xorg    9265 root  mem    REG        8,1   34428    4711228 /usr/lib/xorg/modules/extensions/libdri.so
Xorg    9265 root  mem    REG        8,1  338456    4711231 /usr/lib/xorg/modules/extensions/libglx.so
Xorg    9265 root  mem    REG        8,1   92276    4711230 /usr/lib/xorg/modules/extensions/libextmod.so
Xorg    9265 root  mem    REG        8,1  950424    4622757 /usr/lib/libstdc++.so.6.0.10
Xorg    9265 root  mem    REG        8,1  608280    4622726 /usr/lib/libsmbios.so.2.1.0
Xorg    9265 root  mem    REG        8,1  480644    4620533 /usr/lib/libfreetype.so.6.3.20
Xorg    9265 root  mem    REG        8,1   83552    2048161 /lib/libz.so.1.2.3.3
Xorg    9265 root  mem    REG        8,1 1442180    2065626 /lib/tls/i686/cmov/libc-2.9.so
Xorg    9265 root  mem    REG        8,1   54740    2048065 /lib/libgcc_s.so.1
Xorg    9265 root  mem    REG        8,1   30624    2065656 /lib/tls/i686/cmov/librt-2.9.so
Xorg    9265 root  mem    REG        8,1  149328    2065634 /lib/tls/i686/cmov/libm-2.9.so
Xorg    9265 root  mem    REG        8,1 1340132    5144604 /lib/i686/cmov/libcrypto.so.0.9.8
Xorg    9265 root  mem    REG        8,1  286148    5144605 /lib/i686/cmov/libssl.so.0.9.8
Xorg    9265 root  mem    REG        8,1   16628    4621883 /usr/lib/libXdmcp.so.6.0.0
Xorg    9265 root  mem    REG        8,1  222816    2048055 /lib/libdbus-1.so.3.4.0
Xorg    9265 root  mem    REG        8,1   66940    4620818 /usr/lib/libhal.so.1.0.0
Xorg    9265 root  mem    REG        8,1  268508    4622621 /usr/lib/libpixman-1.so.0.13.2
Xorg    9265 root  mem    REG        8,1   24252    4622141 /usr/lib/libfontenc.so.1.0.0
Xorg    9265 root  mem    REG        8,1    9508    4621872 /usr/lib/libXau.so.6.0.0
Xorg    9265 root  mem    REG        8,1  242704    4621889 /usr/lib/libXfont.so.1.4.1
Xorg    9265 root  mem    REG        8,1  116405    2065652 /lib/tls/i686/cmov/libpthread-2.9.so
Xorg    9265 root  mem    REG        8,1    9676    2065632 /lib/tls/i686/cmov/libdl-2.9.so
Xorg    9265 root  mem    REG        8,1   21912    4622611 /usr/lib/libpciaccess.so.0.10.2
Xorg    9265 root  mem    REG        8,1   26096    4711232 /usr/lib/xorg/modules/extensions/librecord.so
Xorg    9265 root  mem    REG        8,1   17860    4711227 /usr/lib/xorg/modules/extensions/libdbe.so
Xorg    9265 root  mem    REG        8,1  117348    2048023 /lib/ld-2.9.so
Xorg    9265 root    0r   REG        8,1   25954    2613304 /var/log/Xorg.0.log
Xorg    9265 root    1u  unix 0xf4040c40             127880 socket
Xorg    9265 root    2u   REG        8,1     859    2629681 /var/log/gdm/:0.log
Xorg    9265 root    3r  unix 0xf4040a80             127881 /tmp/.X11-unix/X0
Xorg    9265 root    4r   REG        8,1   29902    8101889 /usr/lib/xorg/protocol.txt
Xorg    9265 root    5r   CHR        4,7                847 /dev/tty7
Xorg    9265 root    6w   REG        0,3       0 4026531909 /proc/mtrr
Xorg    9265 root    7w  unix 0xf40408c0             127885 socket
Xorg    9265 root    8r   REG        0,0     256       7783 /sys/devices/pci0000:00/0000:00:02.0/config
Xorg    9265 root    9w   REG        0,3       0 4026531909 /proc/mtrr
Xorg    9265 root   10w   CHR     10,175               4823 /dev/agpgart
Xorg    9265 root   11w   CHR      226,0               8124 /dev/dri/card0
Xorg    9265 root   12w   CHR      226,0               8124 /dev/dri/card0
Xorg    9265 root   13w  unix 0xf3fef340             128492 socket
Xorg    9265 root   14w   CHR      13,68               1351 /dev/input/event4
Xorg    9265 root   15w   CHR      13,69               4926 /dev/input/event5
Xorg    9265 root   16w   CHR      13,67               2084 /dev/input/event3
Xorg    9265 root   17w   CHR      13,71               5152 /dev/input/event7
Xorg    9265 root   18u  unix 0xf4041340             128500 socket
Xorg    9265 root   19u  unix 0xf4ed8000             128871 socket
Xorg    9265 root   20u  unix 0xf4ed8e00             128890 socket
Xorg    9265 root   21u  unix 0xf4ed9340             128894 socket
Xorg    9265 root   22u  unix 0xf31c1500             129295 socket
Xorg    9265 root   23u  unix 0xf2066e00             129241 socket
Xorg    9265 root   24u  unix 0xf31c1c00             129475 socket
Xorg    9265 root   25u  unix 0xf5fe56c0             129476 socket
Xorg    9265 root   26u  unix 0xf31dac40             129552 socket
Xorg    9265 root   27u  unix 0xf31c0700             130322 socket
Xorg    9265 root   28u  unix 0xf4bd6380             129660 socket
Xorg    9265 root   29u  unix 0xf3246000             129703 socket
Xorg    9265 root   30u  unix 0xf23f7880             145109 socket
Xorg    9265 root   31u  unix 0xf3e6bc00             129932 socket
Xorg    9265 root   32u  unix 0xf3e6ba40             129969 socket
Xorg    9265 root   33u  unix 0xf3e6b6c0             129978 socket
Xorg    9265 root   34u  unix 0xf5fc6e00             130583 socket
Xorg    9265 root   35u  unix 0xf3643340             130093 socket
Xorg    9265 root   36u  unix 0xf2066a80             130491 socket
Xorg    9265 root   37u  unix 0xf467d880             130503 socket
Xorg    9265 root   38u  unix 0xf22d3a40             130998 socket
Xorg    9265 root   39u  unix 0xf234aa80             137280 socket
Xorg    9265 root   40u  unix 0xf22d2e00             135095 socket
(basically, it just goes on and on...)

Any help would be appreciated.

---

### Post by darthmob on 2009-07-01
> **onnod said:**
> If I select "restart Openbox" from the Openbox menu, I can cause the 'loop' to stop, and all of the "opening usr/bin/openbox" dialogs close, and memory is freed up.Nice, that does indeed work! Maybe it helps if you simply execute it on startup.

---

### Post by FAJALOU on 2011-02-11
I wish this issue was as clear cut for me;
I run straight gnome and Compiz and have been having the same issue.  My lsof -p looks very similar, but when i try to strace it, I get a crash.  Does anyone else have this issue, and/or ideas of what to do for it? Thanks!

---

