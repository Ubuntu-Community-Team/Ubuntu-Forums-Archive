---
title: "Splashy not working!"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by 2pacalypse on 2007-10-23
I have a terribly annoying problem, Splashy wont work, I've installed it 4 days ago and have been struggling to get it up ever since. I did as all the guides said but the default ubuntu splash (using usplash) keeps going up instead of my splashy one.

Heres the things i've done step by step:

```

apt-get install splashy

```

```

sudo gedit /boot/grub/menu.lst

```
changed the orig:
```

kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=1a1a7ea7-3f9d-4b1b-aae6-c1c949be61d9 ro quiet splash

```

to:

```

kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=1a1a7ea7-3f9d-4b1b-aae6-c1c949be61d9 ro quiet splash **vga=791**

```

```

splashy_config -i ~/Desktop/fingerprint-1.0-theme.tar.gz
splashy_config -s fingerprint
grub-update
iupdate-initramfs -u -t -k `uname -r`

```

but nothing happened, still the default ubuntu splashy :/.

now my guess is that the reason is here:
> 
Customizing Splashy

In order to install Splashy in your own custom distribution or variant of UNIX system, you would need to:

   1.
      tell the system to start ”/sbin/splashy boot” as early as possible
   2.
      some “glue” to calculate the progressbar and update it using: splashy_update “progress NN”
   3.
      you will need to exit Splashy at some point with: splashy_update exit



I dont know how to do the first part... how to make it boot up in the very beginning, and usplash probably boots up before him, hence the default usplash ubuntu theme.

So Please, Can Anyone help me out with this?

---

### Post by blueeyesmike on 2007-10-31
Well first I would remove usplash
```
sudo apt-get --purge autoremove usplash
```

Then update initramfs

```
sudo update-initramfs -u -k all
```

Hopefully that will sort out the problem, but also from a terminal run

```
sudo splashy test
```

This should help to at least test that splashy is working

---

### Post by no1peanut on 2007-11-28
Well - I have had my share of problems with splashy not running.

First I had the problem of splashy_start_splashy error -3 (if root) otherwise -2
Found out this had to do with 2 things:
1) framebuffer settings (vga=###)
and some comment out in /etc/modprobe/blacklist-framebuffer  - i used vesafb since im running the prop. nvidia driver

2) I still got the error though  - but it went away after I changed to a "sane" theme (one not using alpha since I only ran 16 bit!)
and yupti 
splashy test worked... but :(

When rebooting artifacts and weird fighting between usplash and splashy

removed usplash - whereby I broke ubuntu-desktop - whereby I broke desktop-effects and compiz-fusion 

back to usplash and compiz fusion ...

---

### Post by timbba on 2008-04-04
> **no1peanut said:**
> Well - I have had my share of problems with splashy not running.

First I had the problem of splashy_start_splashy error -3 (if root) otherwise -2
Found out this had to do with 2 things:
1) framebuffer settings (vga=###)
and some comment out in /etc/modprobe/blacklist-framebuffer  - i used vesafb since im running the prop. nvidia driver

2) I still got the error though  - but it went away after I changed to a "sane" theme (one not using alpha since I only ran 16 bit!)
and yupti 
splashy test worked... but :(

When rebooting artifacts and weird fighting between usplash and splashy

removed usplash - whereby I broke ubuntu-desktop - whereby I broke desktop-effects and compiz-fusion 

back to usplash and compiz fusion ...

I have to ask, that where did you find this "sane" theme? My computer is suffering of usplash, so I have to find another splash  utility. I just can't get splashy working and I have same problems than you. Error -3 with root and -2 with user.

---

