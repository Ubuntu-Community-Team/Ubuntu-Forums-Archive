---
title: "CD ripping problem"
date: 2006-04-29
forum: Desktop Environments
---

### Post by blueturtl on 2006-04-29
I've been getting into recording my music cds to my hard-drive for easy listening. I use the integrated "Sound Juicer CD ripper" which does a good job most of the time, however: my drive is pretty new, meaning that it spins very fast (about 40x I think). Sometimes some of the recorded songs will have skips or clips in them, that suggests the drive is not doing an accurate job at this speed. I've looked, and I haven't found any way to reduce the ripping speed in Sound Juicer. I even tried setting the spin speed with HDPARM, but that doesn't work with cd-ripping. Does anyone know how to do this, or of an alternate ripper that does the job better?

---

### Post by blueturtl on 2006-05-02
Bump. I've been looking into this more and came across Grip. However Grip doesn't have a setting for ripping speed either, and both Sound Juicer and Grip seem to use cdparanoia for the actual ripping process. :confused:

---

### Post by az on 2006-05-02
[QUOTE=blueturtl]Sometimes some of the recorded songs will have skips or clips in them, that suggests the drive is not doing an accurate job at this speed. [/QUOTE]

I'm not sure about that.  Ripping is not like burning.  If your drive can't read an area of the disk, it will stop and start over until it thinks it got it right.  While burning, you can slow down, but you can't stop.

If it had trouble reading a few spots of a song, it would just wait until it got them right, but it wouldn't continue on blindly.

I also think that the paranoia level is set at 3 by default, which is full error-correction.

I think you can set the paranoia level using gconf-editor.

---

### Post by ComplexNumber on 2006-05-02
[quote=blueturtl]Bump. I've been looking into this more and came across Grip. However Grip doesn't have a setting for ripping speed either, and both Sound Juicer and Grip seem to use cdparanoia for the actual ripping process. :confused:[/quote] try graveman. [click]("http://graveman.tuxfamily.org/index.php"). [here]("http://gnomefiles.org/subcategory.php?sub_cat_id=103") are some others.

---

### Post by blueturtl on 2006-05-02
> I'm not sure about that. Ripping is not like burning. If your drive can't read an area of the disk, it will stop and start over until it thinks it got it right.

Actually I think some drives are known to perform poorly at direct audio extraction (aka. the drive thinks it's being accurate while the transferred data is not in fact flawless). This is usually an issue with poorer quality drives.

> I also think that the paranoia level is set at 3 by default, which is full error-correction.

I think you can set the paranoia level using gconf-editor.

In fact I have investigated this and found a setting in gconf-editor:
apps -> sound-juicer -> paranoia

The value of 'paranoia' was set to 4 (= overlap checking) but I've now modified the value to 255 (= full paranoia) to test. Hopefully this will fix my problems.

> try graveman

Thanks. I'll see if enabling "Full paranoia" mode of Sound Juicer will fix my problem. If not, I will look onward.

---

### Post by ytene on 2006-05-03
Like blueturtl, I have a question/request for help with respect to CD ripping. Am a recent convert to ubuntu, having come from Mandrake/Mandriva, on which I used grip/Amarok to enjoy my CD collection from my PC.

I have installed both the grip and the lame packages to a system. However, when I try and launch grip [from KDE] I see the grip icon tagged to the desktop cursor [arrow] for a brief period of time and the grip program apparently loading in the task bar. Then the arrow reverts to an ordinary icon and the task bar grip entry disappears.

I checked deployment of grip and lame by using the "which" command and both installations seemed OK. Removed and re-installed to make sure.

I then tried a couple of other applications supported by Breezy and although these install in exactly the same way, none of these programs gets as far as launching a window under KDE. 

I have checked /var/spool/messages and even monitored it with "tail -f" but do not see anything of significance. I have tried launching from a command prompt [hoping for error messages] and nothing comes through. 

I have tried installing other software components [ie non-Audio] and these all seem to work fine [though I'm not discount some form of package management system corruption]. Amarok is installed and loads fine.

What I'd really like to have is grip+lame running OK, but am starting to run out of things to check. Have to admit that I've not yet tried this under GNOME, but I will when I get a moment. 


Would really appreciate suggestions as to what might be wrong and where I might look. FWIW, this build is relatively new [from scratch last Saturday] and is very lightweight, being really just for surfing the web and basic word processing etc. Based on ubunu 5.10, fully patched, SMP kernel and then with KDE layered on top. 

Ideas anyone?

---

