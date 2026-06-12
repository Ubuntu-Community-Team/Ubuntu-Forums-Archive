---
title: "Switching to Ubuntu"
date: 2010-09-25
forum: Desktop Environments
---

### Post by drewesq on 2010-09-25
Hey guys, please don't think of this as a moan, because it isn't, but a lot of stuff in the repo that I have tried doesn't seem to work. 
ie. various CD & DVD ripping software
evolution kept crashing, until you use it without any plugins
can't get banshee to write metadata to CDs, but did get it to sync with my Android phone!

I'm not that bothered about this stuff but it does stop me from totally committing to Ubuntu. It is probably because I am quite new to Linux and need to learn more! 

I still love using Ubuntu as an "everyday machine".

Has anyone else had similar issues?
Can anyone get Ubuntu to do all they want it to?

---

### Post by MGMorden on 2010-09-25
> Can anyone get Ubuntu to do all they want it to?

Mostly, yes.  I still have a Windows XP system on a KVM that I can flip to, but it's used strictly for playing games and syncing my iPod Touch (which I have never got to work well in Ubuntu, but I will be getting an Android phone in December that will eliminate that problem).

Which particular apps from the repos are you having issues with?  I can't say that I've tried them all as at this point I have an app that I'm comfortable with for most uses and just use that, but what I do tend to try from the repos does tend to work.

I will say though that if you're new to a Unix-type desktop, it will take a while to adjust.  I started dabbling with Linux off and on (dual-booting and such) back around 1998.  Used Solaris heavily during my college years as that's what the university comp sci labs ran.  Since that was largely remote usage via terminals I really got a good feel for Unix in general from that.  I still didn't switch to Linux as my main everyday OS until mid-2009.  Now that was largely a case of waiting for the platform to mature too, but still, it'll take a while before you feel truly comfortable in the new OS.

---

### Post by drewesq on 2010-09-26
Well I am quite happy using Ubuntu, and I use Linux servers at work. What I would really like is some DVD & CD ripping software that actually works! Have tried thoggen, acid rip, k9copy, k3b, brasero, banshee, rythmbox. none of them rip DVD/CDs, maybe I am doing something fundamentally wrong?!

Still I did get sopcast to work properly in time to watch the mighty Hammers beat Spurs yesterday!! ;)

---

### Post by 0N3 on 2010-09-26
Thunderbird i find best for Email and for DVD ripping Handbrake has never failed me to rip any DVD

---

### Post by drewesq on 2010-09-26
Doesn't look like Handbrake will work with 10.04. May give thunderbird a go.

---

### Post by 0N3 on 2010-09-26
Handbrake works with 10.04 im used it on 10.04 and 10.10 
[http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php)
You may need the nightly release of it but it works on 10.10 and 10.04 32bit ive had difficulty getting it installed on 64bit

---

### Post by drewesq on 2010-09-26
Cool, cool. Thanks mate!! ;)

---

### Post by 0N3 on 2010-09-26
sudo add-apt-repository ppa:handbrake-ubuntu/ppa

sudo apt-get update

will be now available to install via synaptic package manager

---

### Post by SeijiSensei on 2010-09-26
I installed Handbrake for Lucid on my Maverick system using John Stebbins repository here: [https://launchpad.net/~stebbins/+archive/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/handbrake-snapshots)

Worked for me the first time.

I'll just mention in passing that software to rip DVDs runs afoul of the "anti-circumvention" provisions of the US Digital Millennium Copyright Act.  That's why things like libdvdread (and thus Handbrake) and ffmpeg aren't distributed by default with distributions like Ubuntu or Fedora.

---

### Post by drewesq on 2010-09-26
Hmmm, so how exactly do you download this? I have got the PPA and updated.... what next?!

---

### Post by drewesq on 2010-09-26
ah, sorry, you already answered!

---

### Post by 0N3 on 2010-09-26
Go to Applications > System > Administration > Synaptic Package Manager and search for Handbrake or Handbrake Gtk and mark for installation. Theres also Handbrake Cli which is comand line version i'd recommend Gtk version.

---

### Post by 0N3 on 2010-09-26
Let us know if it works!! :)

---

### Post by drewesq on 2010-09-26
so which music player do you prefer? I have got banshee working with my Streak, syncing and stuff, but banshee isn't very good with metadata... any recommendations?

---

### Post by 0N3 on 2010-09-26
go to [www.ubuntu-tweak.com](www.ubuntu-tweak.com)

Download ubuntu-tweak i hink its fantastic software you will have a selection of hundreds of music players and rippers

The best i guess Rhythmbox or Amarok (Amarok is more for the KDE Desktop) but runs perfectly on gnome.

---

### Post by drewesq on 2010-09-26
Hi, yeah. I have got ubuntu-tweak and it is great! I use rythmbox too as it better for metadata. Actually ubuntu-tweak is the reason for my most recent frustration - I inadvertently deleted the linux kernel, the first one you see on dual boot! I have spent ages googling that and apparently there isn't a way of getting it back. Not that fussed though as I will upgrade to 10.10 when it is released in a couple of weeks. 
Is it possible to upgrade versions of ubuntu without torching everything you have on your machine?

Oh, and I especially like the backup/restore feature on ubuntu-tweak, for obvious reasons!! lol

---

### Post by 0N3 on 2010-09-26
I split my HDD in 3 during installation / (root) partition /home (home) partition and swap partition
/ (root) Programs ect........ will be wiped on fresh install

/home (home) All my files Documents, Pictures, Movies, Themes ect...... doesn't have to be formatted during install hence keeping all your documents, pics, vids, even remembers all your program settings bookmarks ect.....

Very handy unlike Windows where you lose your files or have to restore them from a backup not with Linux if you set up your HDD like above although i still do recommend backing up your files

---

