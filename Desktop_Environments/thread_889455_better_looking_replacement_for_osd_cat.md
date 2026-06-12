---
title: "better looking replacement for osd_cat?"
date: 2008-08-14
forum: Desktop Environments
---

### Post by jetsabel on 2008-08-14
hello, i am using osd_cat a lot in my fluxbox keys file (to show time, mpd status, alsa volume, etc..)

i was wondering if there is a program that is still simple to use(reads from stdin) but looks nicer. ideally a coloured & semi-transparent background and fade in/out
it would be a bonus if it also if it used an rc file to change the defaults

any ideas? i had a look at gnome-osd but the whole client/server architecture seems overkill.

---

### Post by segalion on 2008-09-04
In gnome you have gnome-osd-client, but more complex, heavy, slow time-response than osd_cat.

I.e. you can have a osd.sh file with:

```
#!/bin/sh
gnome-osd-client -f "<message id='lirc' osd_fake_translucent_bg='off' osd_vposition='top' animations='on' hide_timeout='5000' osd_halignment='right'> <span font_desc='Sans 24' foreground='white' size='x-large'> $1 </span> </message>"

```

And i.e I have a .lircrc file, very useful that show me position and length-time of the movie from mplayer, and actual time with gnome-osd-client at a time.

With my remote I have a button to know if I have time to see fully the movie before late night.

```
begin
         button = DVD_Info
         prog   = mplayer
         config = osd 3
         config = osd 0
end
begin
         button = DVD_Info
         prog   = irexec
         config = ~/osd.sh `date +%H:%M`
end

```

---

