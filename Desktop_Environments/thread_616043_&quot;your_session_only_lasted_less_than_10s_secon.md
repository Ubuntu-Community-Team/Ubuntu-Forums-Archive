---
title: "&quot;your session only lasted less than 10s seconds&quot; problem (after run out of disk space"
date: 2007-11-17
forum: Desktop Environments
---

### Post by darck on 2007-11-17
I've run out of disk space after apt-get install some-game, pressed CTRL+ALT+BACKSPACE and couldn't log in. I am getting error: 

> 
(process:7012): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:7016): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
mkdtemp: private socket dir: Permission denied

I deleted files from /tmp, purged that game and have some space now:

System plików         bl.  1K B        u&#380;yte dost&#281;pne %u&#380;. zamont. na
/dev/hdc2              3368004   2911344    285568  92% /
varrun                  517816       224    517592   1% /var/run
varlock                 517816         0    517816   0% /var/lock
udev                    517816       100    517716   1% /dev
devshm                  517816         0    517816   0% /dev/shm
lrm                     517816     34696    483120   7% /lib/modules/2.6.22-14-generic/volatile
/dev/hdc1              5205028   4503040    701988  87% /media/hdc1
/dev/hdc5             68878652  59045932   9832720  86% /media/hdc5
/dev/hdd1            156287848 155030972   1256876 100% /media/hdd1

But I still can't logg in (in fail mode too)...
I checked, folder /usr/share/apps/kxkb/ doesn't exists.
I was able to logg as root by
CTRL+ALT+F1
startx --: 1&

I have Gnome, Ubuntu 7.10.
Help :)
----------------------
I wrote this post too fast, because after 30th google webpage i found solution. I changed chmode of /tmp

---

### Post by Gatesgamer33 on 2007-11-20
I'm having the same problem, except I have plenty of disk space left. I really home that there is a solution, My parents are now yelling at me.:(

---

