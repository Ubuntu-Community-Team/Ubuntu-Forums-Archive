---
title: "HomePNA problems in Ubuntu 5.10 with AMD 79c978 network adaptor"
date: 2005-10-24
forum: Desktop Environments
---

### Post by hafuch on 2005-10-24
Dear Ubuntu Community,

I'm desperate! Until yesterday, I've been happily surfing the net with my homePNA connection under Ubuntu 5.04 Hoary; now that I've upgraded to Breezy 5.10, I'm internet-less! :( 

Under Hoary 5.04, to get the homePNA connection working I would add the following lines to /etc/modules:

eth0 homepna=1
pcnet32 homepna=1

I would then type the following commands at the command line:

modprobe pcnet32 pcnet32_homepna=1
depmod -a

After a reboot, all was well with my homePNA internet connection under Hoary 5.04. \\:D/ 

Naturally, I tried the same procedure under Breezy Badger 5.10, but it leads nowhere!??!! :-k 

Can someone PLEASE tell me what has gone wrong? Why doesn't it work as it did before?

Most importantly: HOW CAN I GET MY HOMEPNA CONNECTION WORKING?

Your feedback/instructions would be GREATLY appreciated!

With utmost faith in this community, my thanks in advance,

Hafuch

Equipment: AMD 79C978 HomePNA Network Adaptor
Intel 1GHz processor, 512 MB SDRAM

---

### Post by vivame on 2005-10-28
Same problem here. I had hoary with updates when i did dist-upgrade which broke my homepna connection. I don't have a clue what to do. But. Internet connection seems to work when i choose older kernel (2.6.10-something).

Should somebody move this thread to "installation & upgrade" or "networking"?

---

### Post by lompolo on 2005-11-02
as root run 

```
modprobe -rv pcnet 32
modprobe pcnet32 homepna=1
dhclient
```

This removes pcnet32 module (ethernet) and loads it again (homepna) 

It works as before in 2.6.14 kernel. We don't have .deb yet.

---

### Post by vivame on 2005-11-03
I don't have time to try this now, but do I have to reload module every time I boot? I quess .deb will fix this permanently?

Thanks.

Edit. This really works :D

---

### Post by hafuch on 2005-11-04
Hi Lompolo and Vivame,

Thanks for the reply! I'll give this a try and let you know what happens.

By the way, please forgive my ignorance, but what is .deb? How would this fix the problem of having to reload the module every time one boots up? Just curious! :smile: 

Many thanks and I'll post the results soon!

Hafuch


EDIT:  Wow! Great! Thanks Lompolo for the above instructions! Works like a charm! Many thanks!!!

---

### Post by lompolo on 2005-11-07
> By the way, please forgive my ignorance, but what is .deb? How would this fix the problem of having to reload the module every time one boots up? Just curious! 

.deb is a debian package. (Ubuntu is debian based) If someone would compile new kernel (linux-image-2.6.14...) to us all, all users could just upgrade our kernels easy way with apt-get or synaptic.

You could maybe still use older image if you upgraded from hoary. 
Boot and press esc (when you see grub loading...) Choose older image (2.6.10-5).
If all works well you could remove linux-image-2.6.12-9 from synaptic.

I have had much more problems with 12-9 kernel than with 10-5 or compiled 14. vanilla kernel

you can also try add to /etc/init.d/networking 4 lines first beginning with #

<snip>
case "$1" in
    start)
        doopt spoofprotect yes
        doopt syncookies no
        doopt ip_forward no
        # added these lines to reload pcnet32 module with homepna=1
        log_begin_msg "Reloading pcnet32 module..."
        modprobe -rv pcnet32
        modprobe -v pcnet32 homepna=1
        log_begin_msg "Configuring network interfaces..."
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 120" || true
<snip>

not tested last myself

---

