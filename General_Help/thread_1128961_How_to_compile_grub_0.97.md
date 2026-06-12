---
title: "How to compile grub 0.97"
date: 2009-04-18
forum: General Help
---

### Post by icc on 2009-04-18
For all of you having problems compiling grub 0.97 with netboot on ubuntu resulting in segmentation fault, here is your solution:

1. Install gcc-4.0. These packages are required: 
[LIST]
[*][cpp-4.0_4.0.3-1ubuntu5_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/cpp-4.0_4.0.3-1ubuntu5_i386.deb")
[*][gcc-4.0-base_4.0.3-1ubuntu5_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/gcc-4.0-base_4.0.3-1ubuntu5_i386.deb")
[*][gcc-4.0_4.0.3-1ubuntu5_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/gcc-4.0_4.0.3-1ubuntu5_i386.deb")
[/LIST]
For other than i386, browse: [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/").

2. Apply newest changes from ubuntu (Optional)
```
cd grub-0.97
wget https://launchpad.net/ubuntu/jaunty/+source/grub/0.97-29ubuntu53/+files/grub_0.97-29ubuntu53.diff.gz
gunzip -c grub_0.97-29ubuntu53.diff.gz | patch -p1
```

3. Patch the grub-0.97 source to be compatible with gcc-4.0
```
patch -Np1 << EOF
--- grub-0.97.orig/netboot/main.c       2004-05-21 00:19:33.000000000 +0200
+++ grub-0.97/netboot/main.c    2007-07-20 02:31:28.000000000 +0200
@@ -54,9 +54,9 @@
 
 static int vendorext_isvalid;
 static unsigned long netmask;
-static struct bootpd_t bootp_data;
+struct bootpd_t bootp_data;
 static unsigned long xid;
-static unsigned char *end_of_rfc1533 = NULL;
+unsigned char *end_of_rfc1533 = NULL;

 #ifndef        NO_DHCP_SUPPORT
 #endif /* NO_DHCP_SUPPORT */
EOF

```
(Yes, just paste into your terminal)

I'm told this might also work, but I prefer a patch my self:
```
sed -i '/static.*\(end_of\|bootp\)/s/static //' netboot/main.c
```

4. Compile using gcc-4.0
```
CC=gcc-4.0 ./configure --prefix=/usr --enable-diskless --enable-eepro100
make
```

I hope this how-to might prove useful for someone.

---

### Post by BOFH+ on 2010-02-18
THANKS, icc. Excellent post, everything worked flawlessly.

I've been looking for months for a grub compilation howto... IMO it should be moved to the Tutorials section.

---

### Post by BOFH+ on 2010-02-18
BTW if you just want to compile or patch Grub "legacy" but don't need the netboot feature you can compile it without the options: --enable-diskless --enable-eepro100

---

### Post by raf6202 on 2010-04-29
Hi, I would like to ask a question about compilation: if I compile using the above mentioned method everything works perfectly, but after choosing a system to boot I see the grub instructions to boot the system, the ones placed in menu.lst. If I reinstall grub from liveCD it goes back to normal. Below I attach the text displayed right after selecting an option.

GRUB from LiveCD:
```

Boot from UUID=blablabla
Starting up ...

```

my compiled GRUB, without any changes to the source:
```

  Booting 'My Ubuntu 9.04'


kernel    /vmlinuz-2.6.28-11-generic root=UUID=blablabla ro quiet splash
    [Linux-bzImage, setup=0x3000, size=0x35cd0]
initrd    /initrd.img-2.6.28-11-generic
    [Linux-initrd @ 0x3f7a6000, 0x729b8f bytes]

```

also, the new compiled version of grub, even though it is exactly the same version as the one from the 9.04 liveCD(grub-0.97-29ubuntu53) after I compile it, the grub file is twice the size of the original one. So can anyone tell me how to compile it to be the same as the one from liveCD? Or better yet, how to make grub not display those commands from menu.lst? 

I know it is done in stage2, and there are no commands for displaying this info in the source. There is a printf for prining the string "Booting \'%s\'\n\n", but after removing it the kernel and initrd stays the same... I'll try redirecting the output of kernel and initrd to /dev/null in menu.lst, but that will only remove (if it will) the info in square brackets, commands will stay...

Thank in advance for any help :)

//edit:

Nevermind, just took the old stage2 and replaced all unwanted strings with spaces in a hex editor...

---

