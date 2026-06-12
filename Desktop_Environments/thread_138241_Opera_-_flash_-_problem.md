---
title: "Opera - flash - problem"
date: 2006-03-01
forum: Desktop Environments
---

### Post by Mis_Uszatek on 2006-03-01
So, let's begin :)

I have been using Ubuntu(Gnome).

I had a problem with sound in flash-opera, but after

[http://www.ubuntuforums.org/showthread.php?t=76743&page=2&highlight=opera+flash+sound](http://www.ubuntuforums.org/showthread.php?t=76743&page=2&highlight=opera+flash+sound)

> I have found a fix for my situation. After upgrading from Hoary to Breezy, I too could not get sound to work for flash animations. I investigated the libflashplayer.so file with the following:


Code:

[email]ncampbell@naaman:~/.mozi[/email]lla/plugins$ strings libflashplayer.so | grep esd
Desde
libesd.so
esd_open_sound
esd_get_server_info
esd_play_stream
esd_record_stream
esd_free_server_info
esd_get_latency
esd_close
libesd.so.1
/tmp/.esd/socket
esdescendercyrillic

This was how the "symlink hack" was discovered. It turns out that Breezy (or maybe Gnome 2.12 more specifically), has changed the way it creates ESD sockets in the /tmp directory. It creates a /tmp/.esd-1000 directory which differs to what the Flash Plugin is looking for. Suggested fix:


Code:

ncampbell@naaman:~$ cd /tmp
ncampbell@naaman:/tmp$ mkdir /tmp/.esd
ncampbell@naaman:/tmp$ ln -s /tmp/.esd-1000/socket /tmp/.esd/socket

Now sound works in the same laggy way it did before.

A potential problem exists when this issue arises when a multiuser environment needs flash sound..

and making a script which are doing this automatically at start, sound in flash in opera was working(under Gnome).

But I have moved to KDE, and now I don't have a sound :(

Anybody have got any ideas?

Where in KDE is ESD socket?
Does KDE read ~/.asoundrc at startup?
Does KDE use /etc/asound.conf?

If anybody could explain me about the differences beetwen soundservers in Gnome and KDE I would be thankful.
If someone could give some solution or ideas to this problem, I would be VERY thankful :)

---

