---
title: "Custom Kernel: modprobe cannot find modules.dep, but the file exists"
date: 2006-03-22
forum: Desktop Environments
---

### Post by ElMarcel on 2006-03-22
Hello everyone,
I've a strage problem... I just compiled my custom kernel, but at boot time (before any other message) I have the following FATAL alert, repeated several times:

```

modprobe: FATAL: could not load /lib/modules/2.6.12-light-0.9.1/modules.dep: no such file or directory

```
But that file exists....

Then I have many alert messages about some modules that insmod could not load, and that is beacause all of them are compiled into the kernel, and not as modules.

After that, the system starts up normally :confused: 

Does somebody know hot to remove all those annoying messages? Where is the problem? And how to tell insmod not to load those modules that are now compiled into the kernel?

Thanks for the help!

---

### Post by ranf on 2006-03-24
[QUOTE=ElMarcel]
```

modprobe: FATAL: could not load /lib/modules/2.6.12-light-0.9.1/modules.dep: no such file or directory

```
But that file exists....
[/QUOTE]
How did you compile your kernel? The debian way? With or without initrd?

[QUOTE=ElMarcel]
Then I have many alert messages about some modules that insmod could not load, and that is beacause all of them are compiled into the kernel, and not as modules.

Does somebody know hot to remove all those annoying messages?[/QUOTE]

I can't read your computers screen from the distance :-)
What are the error messages you get?

---

### Post by kikkum on 2006-03-25
I'm having the same problem. Here's what I did:

First I made a custom kernel with

$ fakeroot (or sudo) make-kpkg --blabla kernel_image

and installed it's package with dpkg. After booting with this kernel and already getting the messages I made a modules.dep with

$ sudo depmod

The file contains all the modules, nothing wrong there for as far as I can judge. But still, before the usplash screen comes up, there's a whole lot of these FATAL modules.dep messages. Alas I can't read what's said before the messages show, because there's a lot and they're generated at such a speed that the message above soon leaves the screen (even though I've set my framebuffer to 1400x1050).

Also, after two of these screen filling sessions of FATAL messages I get the failed insmods, mostly containing modules containing fb.

Perhaps there's some scripts in Ubuntu that automatically load a few modules that needn't be loaded anymore with a custom kernel?

---

### Post by ranf on 2006-03-25
Did you compile the fb modules or did you turn them off?
This lists them
```
modprobe -l | grep fb
```

I know that usplash (the graphical bootsplash) uses vesafb.
I don't use that anymore because of some problems (with hibernate).

---

### Post by kikkum on 2006-03-25
I guess I compiled them in, but I can remember not being able to find the exact ones in the configuring of the kernel. Since there's no problem with the framebuffer though I think they have been compiled into the kernel. The usplash works fine so vesafb is probably compiled into the kernel as well.

There are no modules containing fb in the modules -l list. Here's what I get, perhaps you can use it:

```
$ modprobe -l
/lib/modules/2.6.12.lappum-1.2/fglrx/fglrx.ko
/lib/modules/2.6.12.lappum-1.2/misc/ndiswrapper.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/sch_teql.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/sch_tbf.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/sch_sfq.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/sch_red.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/sch_prio.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/sch_ingress.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/sch_htb.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/sch_hfsc.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/sch_gred.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/sch_dsmark.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/sch_cbq.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/sch_atm.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/em_u32.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/em_nbyte.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/em_meta.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/em_cmp.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/cls_u32.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/cls_tcindex.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/cls_rsvp6.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/cls_rsvp.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/cls_route.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/cls_fw.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/sched/cls_basic.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/ipv6/ipcomp6.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/ipv6/xfrm6_tunnel.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/ipv6/esp6.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/ipv6/ah6.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/ipv6/ip6_tunnel.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/ipv4/tcp_diag.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/ipv4/xfrm4_tunnel.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/ipv4/multipath_rr.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/ipv4/multipath_random.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/ipv4/multipath_wrandom.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/ipv4/ipip.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/ipv4/ipcomp.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/ipv4/multipath_drr.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/ipv4/esp4.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/ipv4/ah4.ko
/lib/modules/2.6.12.lappum-1.2/kernel/net/ipv4/ip_gre.ko
/lib/modules/2.6.12.lappum-1.2/kernel/lib/libcrc32c.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/usb/storage/usb-storage.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/usb/class/usblp.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/video/backlight/lcd.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/video/backlight/backlight.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/net/irda/via-ircc.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/net/irda/nsc-ircc.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/scsi/sd_mod.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/scsi/scsi_transport_spi.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/scsi/scsi_transport_iscsi.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/scsi/sg.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/scsi/scsi_mod.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/scsi/scsi_transport_fc.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/i2c/busses/i2c-isa.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/char/tipar.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/char/agp/via-agp.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/char/agp/ati-agp.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/char/agp/amd64-agp.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/char/agp/amd-k7-agp.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/char/nvram.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/base/firmware_class.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/ieee1394/sbp2.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/ieee1394/raw1394.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/ieee1394/eth1394.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/ieee1394/dv1394.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/ieee1394/cmp.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/ieee1394/amdtp.ko
/lib/modules/2.6.12.lappum-1.2/kernel/drivers/ieee1394/video1394.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/wp512.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/twofish.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/tgr192.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/tea.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/tcrypt.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/sha512.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/sha256.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/sha1.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/serpent.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/md4.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/khazad.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/des.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/deflate.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/michael_mic.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/crc32c.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/cast6.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/cast5.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/blowfish.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/arc4.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/anubis.ko
/lib/modules/2.6.12.lappum-1.2/kernel/crypto/crypto_null.ko
/lib/modules/2.6.12.lappum-1.2/kernel/arch/i386/crypto/aes-i586.ko

```

By the way (offtopic), about the problems you mention: is one of them perhaps getting a strange striped screen when you shut down the computer while in X? If so, maybe I should stop using it as well :-?

---

### Post by ranf on 2006-03-25
[QUOTE=kikkum]I guess I compiled them in, but I can remember not being able to find the exact ones in the configuring of the kernel. Since there's no problem with the framebuffer though I think they have been compiled into the kernel. The usplash works fine so vesafb is probably compiled into the kernel as well.

There are no modules containing fb in the modules -l list. Here's what I get, perhaps you can use it:
[/QUOTE]
Not very useful.
You can search your kernel config for FB:
```
grep FB /boot/config-$(uname -r)
```

[QUOTE=kikkum]
By the way (offtopic), about the problems you mention: is one of them perhaps getting a strange striped screen when you shut down the computer while in X? If so, maybe I should stop using it as well :-?[/QUOTE]
No, hibernate works but it doesn't resume.

---

### Post by kikkum on 2006-03-25
Here's what 
$ grep FB /boot/config-$(uname -r)
gives:

```
# CONFIG_BLK_DEV_OFFBOARD is not set
CONFIG_FB=y
CONFIG_FB_CFB_FILLRECT=y
CONFIG_FB_CFB_COPYAREA=y
CONFIG_FB_CFB_IMAGEBLIT=y
CONFIG_FB_SOFT_CURSOR=y
# CONFIG_FB_MACMODES is not set
CONFIG_FB_MODE_HELPERS=y
CONFIG_FB_TILEBLITTING=y
# CONFIG_FB_CIRRUS is not set
# CONFIG_FB_PM2 is not set
# CONFIG_FB_CYBER2000 is not set
# CONFIG_FB_ASILIANT is not set
# CONFIG_FB_IMSTT is not set
CONFIG_FB_VGA16=y
CONFIG_FB_VESA=y
# CONFIG_FB_HGA is not set
# CONFIG_FB_NVIDIA is not set
# CONFIG_FB_RIVA is not set
# CONFIG_FB_I810 is not set
# CONFIG_FB_INTEL is not set
# CONFIG_FB_MATROX is not set
# CONFIG_FB_RADEON_OLD is not set
CONFIG_FB_RADEON=y
CONFIG_FB_RADEON_I2C=y
# CONFIG_FB_RADEON_DEBUG is not set
# CONFIG_FB_ATY128 is not set
# CONFIG_FB_ATY is not set
# CONFIG_FB_SAVAGE is not set
# CONFIG_FB_SIS is not set
# CONFIG_FB_NEOMAGIC is not set
# CONFIG_FB_KYRO is not set
# CONFIG_FB_3DFX is not set
# CONFIG_FB_VOODOO1 is not set
# CONFIG_FB_TRIDENT is not set
# CONFIG_FB_PM3 is not set
# CONFIG_FB_GEODE is not set
# CONFIG_FB_S1D13XXX is not set
# CONFIG_FB_VIRTUAL is not set
```

---

### Post by ranf on 2006-03-25
OK, you have them compiled in.

Back to your original problem. Did you have a look at the messages file?
```
less /var/log/messages
```

Maybe there are some of the error messages you mentioned?

---

### Post by kikkum on 2006-03-25
They aren't there. I do remember now being able to see them when I was sent into custom disk repair during the boot process. Probably they're also visible if usplash is turned off. Is there any way to turn it off temporarily? Or perhaps to pause the booting process so I can write down what modules insmod exactly can't load?

---

### Post by ranf on 2006-03-25
[QUOTE=kikkum]Probably they're also visible if usplash is turned off. Is there any way to turn it off temporarily?
[/QUOTE]
In grub you hit e to edit the kernel you want to boot then down one line to kernel e to edit again. Now you are at the end of the kernel parameters. remove splash, hit Enter. Then b for boot.
This is temporary.

[QUOTE=kikkum]
Or perhaps to pause the booting process so I can write down what modules insmod exactly can't load?[/QUOTE]
Pausing should work with Pause key. 
If not I think Ctrl+S should stop and to go on you need Ctrl+Q.

---

### Post by kikkum on 2006-03-25
When splash is disabled the insmod loading doesn't show up anymore, so clearly they're modules the splash thing needs.

As for the rest: I don't seem to be able to pause (with ctrl-s, pause didn't work at all) fast enough to see the message above the first batch of

```
modprobe: FATAL: Could not load /lib/modules/2.6.12.bla/modules.dep: No such file or directory
```

messages. The second message (the one before the second batch of the above messages) I did catch though; it was

```
[4294679.034000] request_module: runaway loop modprobe net-pf-1
```

---

### Post by kikkum on 2006-03-25
[QUOTE=kikkum]```
[4294679.034000] request_module: runaway loop modprobe net-pf-1
```[/QUOTE]

This message shows up twice in dmesg (with different number before it of course), so I'm guessing the message before the first batch was the same.

---

### Post by ranf on 2006-03-25
I've never seen this error before. I'd google for this 
"request_module: runaway loop modprobe net-pf-1"

---

### Post by ElMarcel on 2006-03-27
I tried a bit and these are my results:

When I remove "splash" from the kernel entry in GRUB menu, I got the same errors. But that's not all: I noticed also another message, just after those of modprobe (the one that says that modules.deb cannot be found) and just before the first message of the boot process:

```

FATAL: Module ext3 not found

```

I have the ext3 driver compiled into my kernel.

I don't have the vesafb driver, but I have the vga one: 

```

CONFIG_FB_VGA16=y
# CONFIG_FB_VESA is not set

```

Usplash work with this configuration

Last thing: [COLOR="Red"]if I compile a kernel without creating an initrd image, I got no errors at all![/COLOR]
But usplash does not work, beacause it is launched from initrd.

So the problem seems to be someway correlated to initrd...
Now I'm gonna try to add the vesafb module, let's see.

What do you think abuot all of this?
I hope these information will be useful

Marco

---

### Post by ElMarcel on 2006-03-27
Another thing: dmesg and /var/log/messages do not show any of the errors described, I suppose because these are shown before the root file system is mounted.

---

### Post by ElMarcel on 2006-03-27
I tried to add the vesafb module... nothing changed

---

### Post by kikkum on 2006-03-27
I can confirm all those things you said ElMarcel; indeed I forgot to mention the ext3 module not being loaded, though it's compiled into the kernel.

Also, I tried a new kernel without initrd and indeed all the errors are gone. I have both the vesa and vga16 drivers compiled into the kernel.

So we've gotta look for the problem inside the initrd. Any suggestions anyone?

---

### Post by kikkum on 2006-03-27
I tried compiling from a clean 2.6.12 kernel from kernel.org. Here's what I did (I'm member of the src group so I can edit files in /usr/src without sudo):

```
$ cd /usr/src
**$ wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.12.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.12.tar.bz2)**
$ tar -xjf linux-2.6.12.tar.bz2
$ rm linux (removing old link to linux-source-2.6.12)
$ ln -s linux-2.6.12 linux
$ cd linux
$ cp ~/bla/old.config ./.config (using my customised .config file)
$ make-kpkg clean
**$ fakeroot make-kpkg --append-to-version=.bla-clean_kernel --revision=1 --initrd kernel_image modules_image (modules are ndiswrapper and fglrx)**
```
* Pressing ENTER a few times because of questions concerning options that weren't in the Ubuntu config. ENTER means not compiling them.

In this process my fglrx module totally doesn't compile anymore, but that could be because it's a strange package anyway (it doesn't really work out of the apt-get box). Ndiswrapper compiles fine though.

So I installed the packages, but still the errors show. So that didn't help much.

Another option (apart perhaps from some unknown (to me) "Ubuntu - initrd" connection) is that it's just something that's wrong in this kernel version, so next I'm going to try the same thing, but with the latest dapper source package.

---

### Post by ElMarcel on 2006-03-27
I have some news :D 

Once upon a time the initrd, init ram disk, was a loopback file, so as .iso files, with the difference that the filesystem type was cramfs (Compressed ROM File System (why not cromfs, then?? :-s ) )

Now, the initrd is saved on disk as a [cpio]("http://www.gnu.org/software/cpio/cpio.html") archive, compressed with gzip, so it is not necessary to have the cramfs support compiled inside the kernel any more.

It is also possible to unpack the initrd archive, modify it, and re-build it.

To unpack:
```

cp /boot/initrd.img-`uname -r` /boot/initrd.img-`uname -r`.bak        #backup the old initrd
mv /boot/initrd.img-`uname -r` /tmp/initrd.old.gz
gzip -dc /tmp/initrd.old.gz >/tmp/initrd.old.img        #unpack the image with gzip
mkdir initrd-image
cd initrd-image
cpio -i < /tmp/initrd.old.img        #extract the files from the cpio archive

```

To re-build the initrd image:
```

find . | cpio -H newc -o > /tmp/initrd.new.img
gzip -c /tmp/initrd.new.img >/tmp/initrd.new.gz
cp /tmp/initrd.new.gz /boot/initrd.img-`uname -r`

```

In the root directory of the image there is a "init" shell script, whose first line is:
```

echo "Loading, please wait..."

```

All the error messages that I (and suppose also kikkum) have are diplayed [COLOR="Red"]before[/COLOR] this message, so the problem must happen just before the init script is launched.

So the question now is: who launches the "init" script inside the initrd image?

Another very important thing: inside the image there is no /lib/modules/`uname -r`/modules.dep file!!! So the file is missing here, and not on the hard disk.
But... I looked inside the initrd image shipped with the precompiled kernel in the Ubuntu repository: there is no modules.dep file here too.
But... there is also the /sbin/depmod program, which [COLOR="Red"]is[/COLOR] called inside the "init" script, but, as I just said, the problem is just before init is launched

We're getting closer... ;)

---

### Post by ElMarcel on 2006-03-27
I think this will make me crazy...

I modified the "original" initrd init script, the one shipped with the precompiled kernel:

```

#!/bin/sh

echo "I am going to show the modules.dep file"
sleep 3
if [ -e /lib/modules/2.6.12-10-686/modules.dep ]        #if the file exists
then
	echo `cat /lib/modules/2.6.12-10-686/modules.dep`        #show the content
else
	echo "The modules.dep file does not exist!!!"
fi
echo "Loading, please wait..."

...#rest of file

```

What I have just seen is REALLY strange: the output on screen is
```

The modules.dep file does not exist!!!

```

Goodnight

---

### Post by ranf on 2006-03-27
Very interesting stuff (unpacking the initrd). I didn't know that.
Thank you.

---

### Post by ElMarcel on 2006-03-28
Placing my modules.dep (the one in the root filesystem) in the initrd solves the problem: the error messages aren't diplayed any more.
But it is a trick... I still don't know why those messages are diplayed.
I googled a lot, but nowbody seems to know.
Who should I ask? ...

---

### Post by kikkum on 2006-03-28
Cool, I'm going to try that! Makes me wonder though how the initrd's are created and why this goes wrong every time with a custom kernel. Perhaps there's some option for make-kpkg I'm missing...

*checking man*

Doesn't seem like it. Perhaps then somethings wrong in some initrd creation script. Will look into that later.

---

### Post by kikkum on 2006-03-28
I've been checking around a (tiny little) bit too on this initrd thing. Someone told me that the initrd isn't actually made during the creation of the kernel package, but rather during installation of the package. That is, there is no initrd before you've installed the package. Can anyone confirm this?

Another thing I've found is the file /etc/kernel-img.conf. It has its own man-page so I'd say it's kinda important ;) Anyway, in this file, things like the automated grub-updating when you install a new kernel are set and after looking at the man-file I found that perhaps the *ramdisk* option could be of some use to us (there's also a *mkimage* option, but I think that one is for making one of those old style initrds).

Only thing our puzzle's missing now is a neat little command to build us a proper initrd, that is, one including the modules.dep file. ](*,)

---

### Post by ranf on 2006-03-29
Just an idea (not sure if does the job): I think a dpkg-reconfigure also creates the initrd.
```
sudo dpkg-reconfigure linux-image-$KVER
```
$KVER - is either the output of `uname -r` (for the currently running kernel) or you supply with kernel version you want.

---

### Post by ranf on 2006-03-29
Just an idea (not sure if it does the job): I think a dpkg-reconfigure also creates the initrd.
```
sudo dpkg-reconfigure linux-image-$KVER
```
$KVER - is either the output of `uname -r` (for the currently running kernel) or you supply with kernel version you want.

So you basically 
- compile your kernel
- boot it
- depmod -a to create a modules.dep
- dpkg-reconfigure

---

### Post by ranf on 2006-03-29
[QUOTE=ElMarcel]I googled a lot, but nowbody seems to know.
Who should I ask? ...[/QUOTE]
The Ubuntu kernel developers are these:
[https://launchpad.net/people/ubuntu-kernel-team](https://launchpad.net/people/ubuntu-kernel-team)

The developers mailing list:
[https://lists.ubuntu.com/archives/ubuntu-devel/](https://lists.ubuntu.com/archives/ubuntu-devel/)

Or try to catch one of these guys on IRC on freenode.net at channel #ubuntu-devel

---

### Post by kikkum on 2006-03-29
[QUOTE=ranf]Just an idea (not sure if it does the job): I think a dpkg-reconfigure also creates the initrd.
...
- depmod -a to create a modules.dep
- dpkg-reconfigure[/QUOTE]

Afraid that doesn't work for me. I'll try browsing the mailinglist or IRC though!

---

### Post by kikkum on 2006-03-29
[QUOTE=ElMarcel]I have some news :D 

Once upon a time the initrd, init ram disk, was a loopback file, so as .iso files, with the difference that the filesystem type was cramfs (Compressed ROM File System (why not cromfs, then?? :-s ) )

...

We're getting closer... ;)[/QUOTE]

Tried this and indeed the most annoying messages (the modules.dep ones) are gone now, great work! The failed insmod loads are still there though, as is the ext3 modules one. I checked this by looking at tty1 (ctrl-alt-F1) during usplash boot. One of the names of the failed insmods I caught was with bitblit.ko. This seems to be some console module that I probably compiled into the kernel, because I can't find it at it's regular spot (/lib/modules/kernelname/kernel/drivers/video/console, in fact that last subfolder isn't even there).

---

### Post by ElMarcel on 2006-03-30
> 
**ranf wrote:**
The Ubuntu kernel developers are these:
[https://launchpad.net/people/ubuntu-kernel-team](https://launchpad.net/people/ubuntu-kernel-team)

The developers mailing list:
[https://lists.ubuntu.com/archives/ubuntu-devel/](https://lists.ubuntu.com/archives/ubuntu-devel/)

Or try to catch one of these guys on IRC on freenode.net at channel #ubuntu-devel


Thanks Ranf, I will try to ask there.

> 
**kikkum wrote:**
Tried this and indeed the most annoying messages (the modules.dep ones) are gone now, great work! The failed insmod loads are still there though, as is the ext3 modules one. I checked this by looking at tty1 (ctrl-alt-F1) during usplash boot. One of the names of the failed insmods I caught was with bitblit.ko. This seems to be some console module that I probably compiled into the kernel, because I can't find it at it's regular spot (/lib/modules/kernelname/kernel/drivers/video/console, in fact that last subfolder isn't even there).


Those messages are caused by /scripts/init-top/usplash (inside the initrd)

```

insmod /lib/modules/`uname -r`/kernel/drivers/video/console/bitblit.ko
insmod /lib/modules/`uname -r`/kernel/drivers/video/console/font.ko
insmod /lib/modules/`uname -r`/kernel/drivers/video/console/tileblit.ko
insmod /lib/modules/`uname -r`/kernel/drivers/video/console/fbcon.ko
insmod /lib/modules/`uname -r`/kernel/drivers/video/cfbcopyarea.ko
insmod /lib/modules/`uname -r`/kernel/drivers/video/cfbfillrect.ko
insmod /lib/modules/`uname -r`/kernel/drivers/video/cfbimgblt.ko
insmod /lib/modules/`uname -r`/kernel/drivers/video/softcursor.ko
insmod /lib/modules/`uname -r`/kernel/drivers/video/vgastate.ko

```

As you may see, the script does not check if this modules are compiled inside the kernel or not (I haven't them at all, but usplash still works)

For the ext3 error message, the problem is in /scripts/local file, function mountroot():
```

# FIXME This has no error checking
modprobe ${FSTYPE}

```

Here there is also a FIXME...

These last two problems (insmod errors end ext3 message) are easy bugs to find, because they are in a shell script. But to find the cause of the other one (modules.dep), we should know the exact initrd boot sequence (which is the C main function that is first invoked?)
The problem, as I said, is that [COLOR="Red"]inside the initrd of the precompiled kernel there is no modules.dep file!!![/COLOR]
What happens in a custom kernel that causes those messages?
We really should ask the Ubuntu team...

---

### Post by kikkum on 2006-03-31
What's kinda odd is that there isn't a modules.dep in the initrd of the original packages either (in lib/modules/'uname -r'). Shouldn't we get the messages with the original kernel as well? :-k

---

### Post by geearf on 2006-09-17
If anyone found something on this, I'm interested (edgy inside).

---

### Post by dranger003 on 2007-04-27
Did anyone found a solution for this? Aside from manually adding the modules.dep file in the initrd?

---

### Post by mrThefter on 2008-01-07
Chiming in here to say that after a day's worth of googling, I realized that I was getting the modules.dep errors during initramfs...
I had never bothered to check if they showed up in dmesg.

I tried compiling in my modules.dep, but initramfs fails to find the boot drive by UUID afterwards. =/

---

