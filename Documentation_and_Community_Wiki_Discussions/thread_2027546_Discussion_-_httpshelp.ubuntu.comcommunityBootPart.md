---
title: "Discussion - https://help.ubuntu.com/community/BootPartition"
date: 2012-07-16
forum: Documentation and Community Wiki Discussions
---

### Post by YannBuntu on 2012-07-16
Please use this thread for discussion regarding

[https://help.ubuntu.com/community/BootPartition]("https://help.ubuntu.com/community/BootPartition")

Support threads/questions should be posted in normal forums.

Thank you.
__________________

---

### Post by royhampac on 2012-09-01
I followed the procedures in boot-repair and boot partition but it didn't work. It keeps on complaining that there is no internet connection even when it has an internet connection.

---

### Post by YannBuntu on 2012-09-03
@royhampac:
- please indicate your [Boot-Info]("https://help.ubuntu.com/community/Boot-Info") URL
- if you use Wifi, please try with wired connection. 
- connect internet, then open a terminal (Ctrl+Alt+T) and indicate the output of the 2 following commands:
```
wget -T 10 -q -O - checkip.dyndns.org
```
```
ping -w 10 -c 1 paste.ubuntu.com
```

---

### Post by alex349 on 2015-03-15
I'm stuck on Step 6. After clicking 'Apply' it stucked on 'Purge kernels then reinstall last kernel sda1 (ins). This may require several minutes...'
It works more that 10 hours and still keeps saying that. I thought it's copying something on my hdd and since it's 1 TB than it may take long time. But now it seems to be stuck.
Please, help!

I also posted the question on SO [http://askubuntu.com/questions/597127/cannot-create-separate-boot-partition-with-boot-repair](http://askubuntu.com/questions/597127/cannot-create-separate-boot-partition-with-boot-repair)

My boot info: [URL="http://paste.ubuntu.com/10604364/"]http://paste.ubuntu.com/10604364/
[/URL]

---

### Post by claytonbagwell on 2015-06-18
I am working from LiveCD 12.04.4. I have downloaded boot-repair from yannubuntu and installed using sudo apt-get install boot-repair AND AGAIN using sudo apt-get install -y boot-repair. Both ways I get the following error:
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.8C4O0X': No such file or directory

Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

and I am left with a blinking cursor that returns to terminal home when I hit 'Enter.'

Boot-repair is installed and when I run boot-repair and click  'advanced' ; 'grub location' produces a blank box - no choices, nothing.
I went back to the first page and selected 'recommended repair.' Without warning nor the opportunity to accept/reject the process went to completion without giving a URL. It did produce a file (very long) but it did not produce a boot sector.

I closed out of LiveCD and booted the computer and got a terminal-like screen with the following:
Error: file not found
grub rescue> blinking cursor

I have re-booted with LiveCD and re-installed boot-repair twice to the same series of failures. Please help.

---

### Post by Jan_Pearce on 2015-08-09
[**[COLOR=#000000]claytonbagwell[/COLOR]**]("http://ubuntuforums.org/member.php?u=1329348"), I  recommend making the partition 2GB instead of 1GB. boot-repair will not  give you a partition option if the partition is too small.

---

### Post by trip3commy on 2017-04-22
Hi. I made it all the way to the final step, but boot repair wouldnt allow me "tick" to the 1gb partition i had created with gparted.
~B

---

