---
title: "possibly add some games to ubuntu repo/&quot;ubuntu games pack&quot;?"
date: 2006-10-10
forum: Gaming &amp; Leisure
---

### Post by sgamer on 2006-10-10
I have had Ubuntu installed as the sole OS on my machine for about a year now, and I have found five games that are irreplaceable. It would be a great boost to Ubuntu, I think, to either have these games in the repos, or at least in a concentrated list of good games for the OS. All of them are FPS games (or FPS/RTS hybrids), but still very good games to showcase the fact that there ARE viable fun games for a linux desktop.

[Tremulous]("http://www.tremulous.net")
[Warsow]("http://www.warsow.net")
[Savage]("http://www.s2games.com")
Enemy Territory, which includes two great mods:
[True Combat:Elite]("http://www.truecombatelite.net")
[Enemy Territory Fortress]("http://www.etfgame.com")
[Nexuiz]("http://www.nexuiz.com")

Between all of these, my leisure time on my linux desktop is taken. If I'm still starving for some other action, I play freeciv or civ3+cedega. :P 

Any other games that are permanent fixtures on your hd?

---

### Post by Naegling23 on 2006-10-11
I would second that, I would love to see an ubuntu gaming repository.  What about adding the linux clients for popular commercial games, like nwn, or doom3, including updates and patches?  That way, we could download the client, copy and info off of the cd's, and play.  

I understand that this couldnt be a ubuntu supported thing, but it would make a lot of people very happy imho.

---

### Post by MrBlond83 on 2006-10-11
Nexuiz is in the repositories, in a rather up to date version as well - in edgy at least. Tremulous latest version is in the edgy repositories as well.

About Enemy Territory and Savage, I doubt they'll get in the repositories, maybe in some private 3rd party repository but probably not in the ubuntu official repositories.

As for being listed, I recommend to all my friends moving to linux to visit [http://doc.gwos.org/index.php/Native_Games]("http://doc.gwos.org/index.php/Native_Games")
I think there is a good selection there of linux native games, that unlike other websites doesnt contain crap games from 2-3 years ago :)

---

### Post by sgamer on 2006-10-15
I do agree with it needing a private 3rd party repo, and the list of games you present is pretty nice. I personally like using [www.happypenguin.com](www.happypenguin.com), and I think they do a great job with updates. 

Now, back to savage. :)

---

### Post by leech on 2006-10-15
I'll preface this with a "I could be wrong, but.." and say that with reguards to some games, like Enemy Territory, there is a clause in the distribution license that says no one but the original creators can distribute the software with a modified installer.

I think the installers for Doom 3 and Quake 4 fall into this category.  Though I really don't see why you could have something similar to the Flash installer that basically is just a script to fetch and run the installer for these games.

On the other hand, the Neverwinter Nights installer is not made by Bioware, and could be modified to use python-gtk or maybe even the Loki installer (though I'd prefer the GTK2 version that Google Earth uses).

Here's my thoughts at least as far as the Neverwinter Nights installer could be.

Put it in the proper repository (universe or multiverse) and then have it basically just a script that calls gtk so that it pops up a dialog that says something like "This is commercial software, you need the original version of it to install"  Then with Neverwinter Nights you'd have to select which release you have (Original, Gold, Platinum, Diamond, plus separate expansion packs, if you have the original) then from there, the CD or DVD version.  Then just copy the files over, and prompt for a disk change when/if needed.  Then ask if you'd like to download the patch, etc.  

Unfortunately I can't program worth a damn.  Otherwise I'd write this myself.  This would be a nice shiny GUI version and would simplify installing games a lot.  It wouldn't be too hard to whip up the interface for it, it's mostly a matter of the internal workings.  

We could try doing this for several commercial games.  Perhaps we could have these in the Canonical commercial repositories, where they have Realplayer, Opera, etc.

Leech

---

### Post by Perfect Storm on 2006-10-15
Savage is also a no-no.

---

### Post by MrBlond83 on 2006-10-15
I would recommend against this. I think the official repositories should only include free software (open source or not) that could be installed anywhere with just the .deb file.

For everything else there is private repositories and google, but keep the official repositoreis for everyone.

Just my 2 euro.

---

