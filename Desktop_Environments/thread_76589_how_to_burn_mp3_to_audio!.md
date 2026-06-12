---
title: "how to burn mp3 to audio!"
date: 2005-10-15
forum: Desktop Environments
---

### Post by dietrying on 2005-10-15
i've got problems with burning audio cd's from mp3-files. The same promblem ith either gnomebaker and serpentine. Serpentine brings: converting files failed. Gnomebaker simply aborts! I wonder if i have forgotten some libs? Gstreamer-mad and gstreamer-lame are both installed. Help would be very nice! 

David

---

### Post by pingswept on 2005-10-15
[QUOTE=dietrying]i've got problems with burning audio cd's from mp3-files. The same promblem ith either gnomebaker and serpentine. Serpentine brings: converting files failed. Gnomebaker simply aborts! I wonder if i have forgotten some libs? Gstreamer-mad and gstreamer-lame are both installed. Help would be very nice! 

David[/QUOTE]

I *think* that mad and lame are just for encoding wav files into mp3 format, not the other way. You're trying to generate wav files to make a CD like one you would buy in a store, right?

 Are you sure that you need to do that? Many newer CD players will play CDs of mp3s directly.

---

### Post by ceoran on 2005-10-15
Install Graveman and try with that

---

### Post by dietrying on 2005-10-15
> I *think* that mad and lame are just for encoding wav files into mp3 format, not the other way. You're trying to generate wav files to make a CD like one you would buy in a store, right?

Are you sure that you need to do that? Many newer CD players will play CDs of mp3s directly.

hmm, i have to convert because my cd-player doesn't support mp3 playback. It's not a newer model. Anyway how can i get it working? Any ideas?
Thanx for the fast reply so far!

greetings, david

---

### Post by buster on 2005-10-15
Install Kb3 with Synaptic. Very easy to use. Will probably tell you if codecs are missing. Though it's a KDE program it works well in Gnome. I use it to do exactly what you want to do.

---

### Post by dietrying on 2005-10-15
> Install Graveman and try with that

yeah, this works! Thanks ceoran.:D 

I like k3b too, t's a very strong application, but i would prever something wich uses gk interface. Graveman seems ok.....
thanks for all the fast reply's!

david

---

### Post by mcduck on 2005-10-15
[QUOTE=dietrying]yeah, this works! Thanks ceoran.:D 

I like k3b too, t's a very strong application, but i would prever something wich uses gk interface. Graveman seems ok.....
thanks for all the fast reply's!

david[/QUOTE]
I think that gnomebaker can also do that, and it's GTK :D

(I just tried, and at least it did let me put my mp3's to an audio disk, I didn't try to burn it because I don't have any empty disks now)

---

### Post by rockrhino27 on 2005-10-16
Hello all, 

     Gnomebaker can do this.  I'm positive of it.  I did it with Debian 3.1 about a month ago.  I just switched to Ubuntu three nights aho.  I'm having the same exact problem.  I'm thinking that there is a library missing.  If anybody knows what the library is, please let us know.  Gnomebaker is a great program, and I wouldn't want to use another one just for making music CD's.

---

### Post by rockrhino27 on 2005-10-16
I figured it out.  The missing library is gstreamer0.8-mad .  I installed that library and all was well.  If you are curious how i found exactly what library the missing one was.  Do a "apt-cache search gstreamer0.8" from a terminal and look at the description for the one with "-mad" at the end.  Hope I helped a fellow gnomebaker fan.  :cool:

---

### Post by fachtofer on 2005-10-25
This forum rocks! Same exact problem- worked for me in Sarge also, completely confused me when it asked for "plugin for mp3 audio".  Now fixed thanks to your post. 

Cheers

---

### Post by cvmostert on 2005-11-03
yea! ubuntu people rock! take over the world ubuntu!

---

### Post by smoshe on 2005-12-23
Another answer would be that the latest version of K3b that comes with Ubuntu does not include the k3b-mp3 package like the old one did. You actually have to install it seperately, but it is part of breezy, so you're good.

---

