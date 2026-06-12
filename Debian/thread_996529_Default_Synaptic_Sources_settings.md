---
title: "Default Synaptic Sources settings"
date: 2008-11-28
forum: Debian
---

### Post by frank.zappa on 2008-11-28
Could someone post their unedited sources.list file (/etc/apt/sources.list) and a screenshot or list of the default settings for 'Software Sources' (just the 'Debian Software', 'Third-Party Software', and 'Updates' tabs).

And if someone could explain the difference between the 'main', 'contrib', and 'non-free' branches (is that what they're called?).

All I want to do is be able to access all of the available software, even non-free, can I do this from within the 'Software Sources' page without manually editing my sources.list file? This is what I did last time, I just added non-free to whatever was listed, and now when I do a 'sudo apt-get update', I always get an error about it not being able to connect to something and in Synaptic, it says 'duplicate entries' or something. 

And I guess this is kind of related, but why do I always have to keep on installing a new kernal every other day?? I always end up commenting out the excess options in my /boot/grub/menu.lst file.

Here's what it looks like right now:
```
title		Debian GNU/Linux, kernel 2.6.26-1-686
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.26-1-686 root=/dev/sda3 ro quiet
initrd		/boot/initrd.img-2.6.26-1-686

title		Debian GNU/Linux, kernel 2.6.26-1-686 (single-user mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.26-1-686 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.26-1-686

#title		Debian GNU/Linux, kernel 2.6.26-1-486
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.26-1-486 root=/dev/sda3 ro quiet
initrd		/boot/initrd.img-2.6.26-1-486

#title		Debian GNU/Linux, kernel 2.6.26-1-486 (single-user mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.26-1-486 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.26-1-486

#title		Debian GNU/Linux, kernel 2.6.24-1-686
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-1-686 root=/dev/sda3 ro quiet
initrd		/boot/initrd.img-2.6.24-1-686

#title		Debian GNU/Linux, kernel 2.6.24-1-686 (single-user mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-1-686 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.24-1-686

```

Thanks.

---

### Post by oswaldkelso on 2008-11-29
[http://forums.debian.net/viewtopic.php?p=189641&sid=45fe34292195a99476cba75da0e48bf7](http://forums.debian.net/viewtopic.php?p=189641&sid=45fe34292195a99476cba75da0e48bf7)

[http://wooledge.org/~greg/sidfaq.html](http://wooledge.org/~greg/sidfaq.html)

Assuming your running Lenny and in the usa your sources list would look something like this

deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) lenny main contrib non-free
deb-src [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) lenny main contrib non-free

deb [http://security.debian.org/](http://security.debian.org/) lenny/updates main contrib non-free
deb-src [http://security.debian.org/](http://security.debian.org/) lenny/updates main contrib non-free

Comment out any duplicates from your sources.list file with a hash # 

as root

cd /etc/apt/

then 

nano sources.list

edit and save

I don't use contrib or non-free you may not need it ? you will want to add debian multimedia for dvd playback and ripping etc. Add the key after. Here's my sources.list so you get the idea. Go and spend some time searching the Debian forum you'll find all your questions answered already. Be sure to do some home work as its generally seen as lazy to ask basic questions without at least trying to find your own answers first. The forum is much less moderated than here. More of a down town beer parlor than a up town wine bar.   


# deb cdrom:[Debian GNU/Linux testing _Lenny_ - Official Snapshot powerpc CD Binary-1 20080407-13:58]/ lenny main 

# deb cdrom:[Debian GNU/Linux testing _Lenny_ - Official Snapshot powerpc CD Binary-1 20080407-13:58]/ lenny main 

deb [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) lenny main  
deb-src [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) lenny main  

# deb [http://security.debian.org/](http://security.debian.org/) lenny/updates main 
# deb-src [http://security.debian.org/](http://security.debian.org/) lenny/updates main 

deb [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) experimental main 
deb-src [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) experimental main 

deb [http://ftp.uk.debian.org/debian/](http://ftp.uk.debian.org/debian/) lenny main 
deb-src [http://ftp.uk.debian.org/debian/](http://ftp.uk.debian.org/debian/) lenny main 

deb [http://security.debian.org/](http://security.debian.org/) lenny/updates main 
deb-src [http://security.debian.org/](http://security.debian.org/) lenny/updates main 

deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) lenny main 
deb-src [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) lenny main

---

### Post by markharding557 on 2008-11-30
You can uninstall any unwanted kernels in synaptic.
In the sources list you need only add contrib non-free to your existing list which can be done from synaptic.
your servers should be in your country for best performance

---

