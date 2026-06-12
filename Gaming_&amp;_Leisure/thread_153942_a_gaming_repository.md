---
title: "a gaming repository"
date: 2006-04-02
forum: Gaming &amp; Leisure
---

### Post by Asraniel on 2006-04-02
wouldnt it be great if there was a up to date gaming repository?
you know, one click and you have games like:
Nexuiz
Tremolous
enemy territory
cube
sauerbraten
wesnoth
...

installed. sadly i dont have a server that can handle the amount of downloads that this would generate. but perhaps i would help with making packages (never did a package before, but usualy i learn very fast)

---

### Post by Zyphrexi on 2006-04-02
i've been thinking along the same lines, it always bugged me to find source for stuff and not be able to build it because of the differing versions. I never had problems in slackware. Still I like my system clean or relatively clean, and i often forget how to do the check-install thing. Debs are nice. I vote for better emulator UI's. AFAIK there are no UI's for nes or genesis in the repos. :mad:

---

### Post by Jabberu on 2006-04-02
I must say that's one thing I miss from my old gentoo installation... the abillity to just type "emerge unrealtournament" or "emerge nwn", with the cdrom in the tray, letting portage handle the installation. Made updating the games helluva lot easier to, and mods installed as easy as pie.

Granted, Ubuntu runs a slightly different approach... but I'd love to have something equivalent.

---

### Post by Zyphrexi on 2006-04-04
that's one reason i consider switching to gentoo, but the Installation is always intimidating. Scares the hell out of me. (honestly the guide doesn't help much)

---

### Post by ELD on 2006-04-04
I beleive they have GUI installer now do they not?

On topic -- it would be nice to have a repo with the latest stuff.

---

### Post by ELD on 2006-04-04
Okay a quote from their install guides "The Gentoo Installer LiveCD contains everything you need to install Gentoo. It provides a graphical environment, a graphical as well as console based installer which automatically carries out the installation for you, and of course, the installation instructions for your architecture."

---

### Post by Syo on 2006-04-04
Yea Gentoo is WAY WAY WAY easier to install than it was a few years ago... However i would recomend to anyone wanting to try Gentoo that you use the old install method. Reason being, you will be getting into the guts of your system  more often in Gentoo. It really helps to have a the understanding of what everything does that the old install gives you.

---

### Post by Toxicity999 on 2006-04-04
Repos aren't really needed I mean... sure for ease of access definitely but I mean... a orginized guide containign all the GOOD games and installion/compilliation instructions would do nicely for anyone who gets bored doing their real work often like me... lol...

---

### Post by Perfect Storm on 2006-04-04
Well if someone will/want to dedicate a server and someone build the packages then cool :)

Nexuiz - Got dynamic package, no need to compile if you don't/can't.
Tremolous - script install. sudo sh and you'll running
enemy territory - Is a script to run, no problems here.
cube - have dynamic package, so no need to compile this one if you don't want to.
sauerbraten - Okay this need to be compiled
wesnoth - and this needs also for the latest.

---

### Post by shinygerbil on 2006-04-04
As I've said in another thread, maybe some kind of Automatix, but for games :)

---

### Post by ELD on 2006-04-04
[QUOTE=shinygerbil]As I've said in another thread, maybe some kind of Automatix, but for games :)[/QUOTE]

That would actually be a pretty dam good idea.

Mabye someone can make a port of Automatix and change the list to games?

---

### Post by BathroomNinja on 2006-04-04
I have plenty of hosting but I'm no programer.  So if someone wants to make the scripts, I'm willing to setup a host.

pm me.

---

### Post by Zyphrexi on 2006-04-04
schweet...

hmm I was able to install sauerbraten with no trouble. (no building)

[http://prdownloads.sourceforge.net/sauerbraten/sauerbraten_2006_03_20_shader_edition_linux.tar.gz?download]("http://prdownloads.sourceforge.net/sauerbraten/sauerbraten_2006_03_20_shader_edition_linux.tar.gz?download")

but one click installs for everything would be fantastic. I'm curious, would it matter if the debs were built for dapper or breezy? And can we just take the urls from the server and put them in a script? I'm not sure what the legal implications are on this kind of stuff.

---

### Post by mrjohnston on 2006-06-05
hmmm....

Shouldn't be any legal ramifications thanks to the GPL.  A script would be fine.  I will have to look into how they did automatix and other scripts like that.  Should be easy, as when selected all it has to do is download, and then chmod +x and then place the command to start the .run file for several  Or simply untar some and then ideally create a desktop/menu link to the executable file to make it easy to run afterwards.  Compiling can be done easy enough and use checkinstall to create and install a deb file.  

This sound about right for people or what exactly are you hoping for?  I should have some time coming up, and while I am not much of a programmer, I have messed with bach some and have been wanting to learn python so I might be able to throw something together...

Say your piece now to flesh out what exactly this should look like.

---

