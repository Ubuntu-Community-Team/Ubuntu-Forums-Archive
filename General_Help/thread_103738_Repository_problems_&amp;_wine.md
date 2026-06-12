---
title: "Repository problems &amp; wine"
date: 2005-12-14
forum: General Help
---

### Post by cwkx on 2005-12-14
Hi all, i've been trying to get wine up and running (friend wants to use MS Access) however i've been having problems simply installing wine. - I redid my repositories following this guide:

[http://www.ubuntuforums.org/showthread.php?t=76132](http://www.ubuntuforums.org/showthread.php?t=76132)

And then went into synaptic to search for wine and got this sprinkling of errors:

[COLOR="Gray"]W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)[/COLOR]

If I try; sudo apt-get update, I get similar errors with this pretty note at the bottom, [COLOR="Gray"]"E: Some index files failed to download, they have been ignored, or old ones used instead." [/COLOR]

Any ideas on how I can solve the problem? I just want wine and some good repositories that wont cause errors.

Thanks [COLOR="DimGray"]*reads above comment & drinks a 2003 chardonnay*[/COLOR]

---

### Post by Drain on 2005-12-14
[QUOTE=cwkx]Hi all, i've been trying to get wine up and running (friend wants to use MS Access) however i've been having problems simply installing wine. - I redid my repositories following this guide:[/QUOTE]

It looks like A) your repository list is expecting that the Breezy Install cd will be in the drive, and B) that the [ftp://ftp.free.fr/](ftp://ftp.free.fr/) site will be available. 

I can connect to the ftp site now, so if typing "apt-get update" doesn't work now, then how about posting your sources.list file, and double-checking there aren't any little type-os in it? ;-) (that's usually how I foul it up)

---

### Post by jasay on 2005-12-14
As mentioned, the first two errors are from the install cd not being in the drive and the other two are because you can't reach the website for some reason.  I'm not sure what you were trying to get from the second repo, but both of these repos (4 if you have deb-src repos as well) could probably be commented out without messing anything up.  Wine can be found in the breezy's universe repo, but it is kind of old.  This newest version can be had straight from wine's official repo on [their site]("http://www.winehq.org/"): deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

[Help with wine download.]("http://www.winehq.org/site/download-deb")
[Help with installation/configuration.]("http://www.winehq.org/site/howto")

If you know how to edit sources.list just ignore the rest:
```
sudo gedit /etc/apt/sources.list
```
put a "#" (no quotes) in front of the malfunctioning repos and add the wine repo or remove the "#" from in front of the universe repo.  Save and close.
```
sudo apt-get update
sudo apt-get install wine
```

---

### Post by ubuntu_demon on 2005-12-15
My sources.list has a working plf repo and has wine. See my signature below.

edit your sources.list, replace it by mine and make sure you uncomment the wine repo :

$ sudo gedit /etc/apt/sources.list

No put it into effect :

$ sudo apt-get update

And install wine :

$ sudo apt-get install wine

Good luck!

---

### Post by cwkx on 2005-12-15
Hi, and thanks for your support & response. I tried all that and then realised it was due to the fact that im using an x86_64 bit distribution & wine doesn't have a 64 bit build. I just got thousands of errors when trying to follow the 32 chroot guide in the 64 forums. 

I decided, that due to the errors ive been having and the fact that I need wine flash & other things (including a stable system) that im going to scrap the whole 64 bit thing and install an i386 architecture. (My systems an AMD Athlon 64  3200+)

Couple of questions:

a) Will that be ok to do (ie use the i386 architecture)?
b) What download manager is best (ie lots of sources & resume support) for downloading 2.x gb iso image of breezy?
c) What program can I use to burn the .iso file onto a DVD?


Thanks ;)

---

### Post by ubuntu_demon on 2005-12-15
[QUOTE=cwkx]Hi, and thanks for your support & response. I tried all that and then realised it was due to the fact that im using an x86_64 bit distribution & wine doesn't have a 64 bit build. I just got thousands of errors when trying to follow the 32 chroot guide in the 64 forums. 
[/QUOTE]

I see :)

[QUOTE=cwkx]
I decided, that due to the errors ive been having and the fact that I need wine flash & other things (including a stable system) that im going to scrap the whole 64 bit thing and install an i386 architecture. (My systems an AMD Athlon 64  3200+)
[/QUOTE]

For a "multimedia desktop"  64 bit is probably not yet the way to go.

I recommend installing the k7 kernel :
$sudo apt-get install linux-k7

But maybe linux-k7-smp works too. You can search for this on the forums or try yourself.

[QUOTE=cwkx]
Couple of questions:

a) Will that be ok to do (ie use the i386 architecture)?
[/QUOTE]

of course :)

[QUOTE=cwkx]
b) What download manager is best (ie lots of sources & resume support) for downloading 2.x gb iso image of breezy?
[/QUOTE]

bittorrent is available in your gnome internet menu. So download the torrent and open it with bittorrent. 

[QUOTE=cwkx]
c) What program can I use to burn the .iso file onto a DVD?
[/QUOTE]

graveman , nero, gnomebaker or just use nautilus (the standard filemanager).

[QUOTE=cwkx]
Thanks ;)[/QUOTE]

np :)

---

### Post by cwkx on 2005-12-15
Hehe, how fast! - i'll try those programs and start fresh. Cheers for the help :smile:

---

### Post by ubuntu_demon on 2005-12-15
np and good luck!

(although reinstalling probably isn't required)

---

