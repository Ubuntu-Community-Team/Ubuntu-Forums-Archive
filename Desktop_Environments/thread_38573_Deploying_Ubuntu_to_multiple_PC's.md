---
title: "Deploying Ubuntu to multiple PC's"
date: 2005-06-01
forum: Desktop Environments
---

### Post by jegerean on 2005-06-01
Hi All,

I've just discovered Ubuntu (thank god) , and am looking to deploy it on my Lan here at work. Currently there are about 50 machines.

Here is what I need help on:

1. An automated way to deploy Ubuntu over a network, also taking into account that most of the pc's do unfortunately have different hardware. Have no idea where to begin with that.

2. Im considering if I should run something like crossover office, so that I can pre-install microsoft and custom windows applications into the ubuntu image before I distribute. And ideas on this ? Crossover office seems rather good, although is there another (free?) open source solution that can run and install MS office, IE, photoshop etc ..ontop of ubuntu ?


Im basically sick of paying so much money for over 60 users here to Email and browse the internet on an expensive MS OS. Something which takes up 90% of a normal users day.

Thanks in advance!

---

### Post by lakcaj on 2005-06-01
You could check out systemimager:

[http://www.systemimager.org/](http://www.systemimager.org/)

or you could look at something similar to what was discussed in this thread (some bugs where worked out towards the end, so make sure to give it a full read)

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by ltmon on 2005-06-01
WINE is the free version of CrossOver (i.e. CrossOver is an extended, tested, supported WINE).  It has the advantage of being free, but the disadvantage of being not quite as polished.  I would simply try out WINE and see if it runs all your required apps well enough.

As for the other question, I'm not sure myself how you would "push" ubuntu out to a PC.  My best answer would be to set up a network install, and then do each pc individually by booting off a minimal floppy and beginning the install.  This is usually faster than install by cd at least.  There are a few forums posts on how to do this and [here](http://www.ubuntulinux.org/wiki/NetbootInstallHowto).  Once that's done you would then configure apt to autoupdate from your own local repository, and only allow packages in that mirror that you want to push out to the users.  I'd be interested to see other peoples ideas though on how to manage a linux desktop deployment (without expensive tools that are only certified for SuSE/RedHat, as I know there's a couple in that category).

L.

EDIT: The previous post suggested an imager.  I would caution against this, as I had bad experiences with imaging (on windows).  Maintaining images for large numbers of configurations and different hardware can be a real pain, and you already mentioned you have varied hardware.

---

### Post by jegerean on 2005-06-01
Thanks guys. 
Yup, I had a feeling I could deploy in that method. Seems like its the best option on mis-matched hardware. There is only around 50 machines or so on the LAN, so running an attended install from a server shouldnt be to bad at all. Then I get apt-get WINE and all applicable software for each install.

Just another question ... does Ubuntu support Windows domain Authentication/smb out of the box ? Basically the users here need to share\move data between windows shares. I was thinking that as long as they can be authenticated, then that is enough to get them working as usual. Then I dont have to bother about them actually "joining" a domain to get access to network resources. Thoughts on that ?

---

### Post by ltmon on 2005-06-01
[QUOTE=jegerean]Thanks guys. 
Just another question ... does Ubuntu support Windows domain Authentication/smb out of the box ? Basically the users here need to share\move data between windows shares. I was thinking that as long as they can be authenticated, then that is enough to get them working as usual. Then I dont have to bother about them actually "joining" a domain to get access to network resources. Thoughts on that ?[/QUOTE]


[This](http://ubuntuguide.org/#sambaserver) should help for a start with Samba sharing.

---

