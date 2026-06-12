---
title: "Questions about Configuring Desktop"
date: 2008-01-26
forum: Desktop Effects &amp; Customization
---

### Post by durdensbuddy on 2008-01-26
Hi Guys,

I am currently trying to work through the following walkthrough [http://ubuntuforums.org/showthread.php?t=659317&highlight=configure+ccsm](http://ubuntuforums.org/showthread.php?t=659317&highlight=configure+ccsm) and had a question

The theme I chose for my splash page is Usplash Theme - Fingerprint available @ [http://gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468](http://gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468)  now following the install HowTo for THAT i come up to this step:

       2- You also need a booting screen resolution of 1024x768. To set it, please open your grub     
           configuration file
                      sudo gedit /boot/grub/menu.lst
           find the paragraph about your current kernel version, and add the string
                      vga=791
           at the end of the kernel section, without modifying pre-existing values.
For example if this is your current configuration
    title Debian GNU/Linux, kernel 2.6.17-10-generic
    root (hd0,4)
    kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda5 ro quiet splash locale=en_EN
    initrd /boot/initrd.img-2.6.17-10-generic
    boot
you should add the string to this line
    kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda5 ro quiet splash locale=en_EN
    which will become

    kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda5 ro quiet splash locale=en_EN vga=791

Ok for those kind enough to be still reading I'm confused as to where to insert my edit.  

I have a section like this:
                                 # examples
                                 #
                                 # title		Windows 95/98/NT/2000
                                 # root		(hd0,0)
                                 # makeactive
                                 # chainloader	+1
                                 #
                                 # title		Linux
                                 # root		(hd0,1)
                                 # kernel	/vmlinuz root=/dev/hda2 ro
                                 #

And another section like this:
                                 ## ## End Default Options ##

                                 title		Ubuntu 7.10, kernel 2.6.22-14-generic
                                 root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8ceabcef-bf96-46a4-a9e3-03431f7df44e ro quiet splash
                                 initrd		/boot/initrd.img-2.6.22-14-generic
                                 quiet

                                 title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
                                root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8ceabcef-bf96-46a4-a9e3-03431f7df44e ro single
                                initrd		/boot/initrd.img-2.6.22-14-generic

                                title		Ubuntu 7.10, memtest86+
                                root		(hd0,2)
                                kernel		/boot/memtest86+.bin
                                quiet

*NOTE the kernel lines are left at margin to show full command with limited breaks.  Trying to make it as easy to diagnoze and fix as possible.  Thanks in advance

---

### Post by schiznik on 2008-01-26
you need to edit the below line, marked with a >
> **durdensbuddy said:**
> title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,2)
>kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=8ceabcef-bf96-46a4-a9e3-03431f7df44e ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet
so that it becomes 
> **durdensbuddy said:**
> kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=8ceabcef-bf96-46a4-a9e3-03431f7df44e ro quiet splash vga=791

---

