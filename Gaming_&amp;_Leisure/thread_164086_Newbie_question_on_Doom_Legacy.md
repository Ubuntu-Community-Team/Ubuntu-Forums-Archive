---
title: "Newbie question on Doom Legacy"
date: 2006-04-22
forum: Gaming &amp; Leisure
---

### Post by TheDoctor on 2006-04-22
Bear with me everyone. I'm a highly experienced user of Windows but know nothing of Linux. I've had Ubuntu for a few days now and I aint going back to Windows, but I need help.

I've done a few things now: installed a modem driver, added applications, but one thing eludes me.

I want to play Doom on Ubuntu. I downloaded Doom Legacy and upacked it into a folder in my Home folder. But, er, how do I "run" it? Clearly, as I've seen mentioned so many times, Linux does things very differently to Windows. Was I meant to install this zipped file somehow? If so, how? If not, what do I do next?

---

### Post by Yagisan on 2006-04-22
I suggest you try The Doomsday Engine instead (easier to get running, and looks pretty). There are packages available here [http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu/](http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu/) with detailed instructions. It will install a menu item for you to play it. (I assume you are on breezy. If you are on dapper, the breezy package should work)

I don't know what zip file you downlaoded from the doom legacy site, but the binary download (which may not work depending on differences in linux systems) is at [http://prdownloads.sourceforge.net/doomlegacy/legacy_142_linux.tar.gz?download](http://prdownloads.sourceforge.net/doomlegacy/legacy_142_linux.tar.gz?download) they usually have a README file with instructions on how to install it inside the tar.gz file.

Alternatively, prboom is in universe, that is another good doom engine.

---

### Post by TheDoctor on 2006-04-22
Erm, yeah, I'm running Breezy. That first link hangs, and I have the same problem using the zip file from your second link. Although I can unpack the contents, then what? How to I start the binary?

I tried prboom which is nice (except I have a tiny window and I can't work out how to change the resolution).

---

### Post by TheDoctor on 2006-04-22
Okay. Forget that last comment. I got Legacy to work. It seems to start a binary from the terminal I add the prefix "./" (and the fact you're supposed to add an original Doom WAD). But Legacy won't start. It goes to start musserver and then stops saying it cannot find /dev/sequencer. What gives?

---

### Post by DoktorSeven on 2006-04-22
As stated by Yagisan, it's better to try Doomsday over Legacy; Legacy has some problems like you describe.  Though if the link he gives hangs, I'm not sure where to get binaries.  I just compiled mine from source as usual and run it using a shortcut to a commandline (**doomsday -game jdoom -file /path/to/doom2.wad -userdir ~/.doomsday/jdoom/ -maxzone 128** usually is sufficient).

Search around for Doomsday binaries if you really need them, and there are a couple of frontends for it as well if you look.

---

### Post by Yagisan on 2006-04-23
[QUOTE=DoktorSeven]Though if the link he gives hangs, I'm not sure where to get binaries.[/quote]The link doesn't hang, although I admit it's not the quickest. It does have links to faster mirrors for downloading the .debs though.

[QUOTE=DoktorSeven]I just compiled mine from source as usual and run it using a shortcut to a commandline (**doomsday -game jdoom -file /path/to/doom2.wad -userdir ~/.doomsday/jdoom/ -maxzone 128** usually is sufficient).[/quote]Based on your commandline you must be using the old 1.8.6 release. We removed -maxzone in the 1.9.0 betas. 1.9.0beta3 (which I packaged for Ubuntu) performs much better.

[QUOTE=DoktorSeven]Search around for Doomsday binaries if you really need them, and there are a couple of frontends for it as well if you look.[/QUOTE]We (myself and the other doomsday developers) would suggest that you either use the provided .debs from my site (which is the only "official" release), or that you build it yourself. I plan to release the snowberry launcher with the beta4 release, until then, beta3 makes menu entries under games.

---

### Post by DoktorSeven on 2006-04-23
[QUOTE=Yagisan]Based on your commandline you must be using the old 1.8.6 release. We removed -maxzone in the 1.9.0 betas. 1.9.0beta3 (which I packaged for Ubuntu) performs much better.[/QUOTE]

Ah, really... never saw anything about -maxzone being depreciated, and the output doesn't say it's invalid.  Neat.

[QUOTE=Yagisan]We (myself and the other doomsday developers) would suggest that you either use the provided .debs from my site (which is the only "official" release), or that you build it yourself. I plan to release the snowberry launcher with the beta4 release, until then, beta3 makes menu entries under games.[/QUOTE]
I hated the Snowberry launcher in Windows.  It was completely unintuitive and much less straightforward than the older GUI launcher.  I'd rather see a continuation of the [Kickstart for Linux Doomsday](http://forums.newdoom.com/showthread.php?t=23529) program started on the Newdoom forums.

---

### Post by Yagisan on 2006-04-27
[QUOTE=DoktorSeven]Ah, really... never saw anything about -maxzone being depreciated, and the output doesn't say it's invalid.  Neat.[/quote] Yep. We ignore options we don't understand.

[QUOTE=DoktorSeven]I hated the Snowberry launcher in Windows.  It was completely unintuitive and much less straightforward than the older GUI launcher.  I'd rather see a continuation of the [Kickstart for Linux Doomsday](http://forums.newdoom.com/showthread.php?t=23529) program started on the Newdoom forums.[/QUOTE]
I don't think Kickstart for Linux is being developed anymore, in any case, I won't include snowberry in the same .deb as deng. I do agree that snowberry may need a bit of work (it still is alpha software), but as far as I can see, it is the only laucher still being developed, and as most packs are moving to snowberry format, I think it would be prudent of me to at least make it available.

---

### Post by DoktorSeven on 2006-04-27
Understood.  Myself, I've never needed anything really complex out of Doomsday -- the ability to run DOOM/II/Final/Heretic/Hexen, and add in pwads when desired. Simple launcher programs serve that need just fine. :)

---

