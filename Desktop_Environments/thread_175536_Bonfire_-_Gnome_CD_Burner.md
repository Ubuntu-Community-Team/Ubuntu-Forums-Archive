---
title: "Bonfire - Gnome CD Burner"
date: 2006-05-13
forum: Desktop Environments
---

### Post by brainkilla on 2006-05-13
Just seen this great app

[http://perso.wanadoo.fr/bonfire/](http://perso.wanadoo.fr/bonfire/)

seems much better than Graveman or GnomeBaker, "k3b for Gnome" I daresay... so an Ubuntu .deb would be really nice. Thanx.

---

### Post by Dr. Nick on 2006-05-13
[quote=brainkilla]Just seen this great app

[http://perso.wanadoo.fr/bonfire/]("http://perso.wanadoo.fr/bonfire/")

seems much better than Graveman or GnomeBaker, "k3b for Gnome" I daresay... so an Ubuntu .deb would be really nice. Thanx.[/quote]

I tried to compile on Dapper but got several libnotify errors, even though all dev files are istalled.

A .deb would be nice if someone got it to compile.

---

### Post by ato on 2006-05-13
Same here!!!
I'm looking for a solution ](*,)

---

### Post by ato on 2006-05-13
Same here
I'm lookin' for a solution

---

### Post by ketsugi on 2006-05-13
I managed to get past the libnotify errors; if you edit src/burn-dialog.c and look at the include lines, you'll see a line that says
```
#include <libnotify/notifynotification.h>
```
Change this to
```
#include <libnotify/notify.h>
#include <libnotify/notification.h>
```

Btw you need the **libgstreamer-plugins-base0.10-dev** package installed (and don't modify the metadata.c file).

---

### Post by simplyw00x on 2006-05-13
Damn, I was about to post that fix :p. I'm working on a .deb package; it'll be finished as soon as the blasted thing compiles!

---

### Post by Dr. Nick on 2006-05-13
Refer to post 12 for a proper build.

---

### Post by zachtib on 2006-05-13
ummm....

where's the attachment? ;)

If the board won't let you attach it, someone here can usually host it for you. I'd offer to myself, but my server is running on my home dsl line

---

### Post by Dr. Nick on 2006-05-13
[quote=zachtib]ummm....

where's the attachment? ;)

If the board won't let you attach it, someone here can usually host it for you. I'd offer to myself, but my server is running on my home dsl line[/quote] 
Its their now, I had to add it to a gz file as It wouldnt let me attach the .deb.

Hope it works, let me know if it doesnt

---

### Post by zachtib on 2006-05-13
awesome, installing now

EDIT:

the deb DID install gnome-shortcuts, they are in the Applications >> System Tools menu

EDIT2:

WOW, this is a nice app! To whoever wrote it, you just replaced gnomebaker for me

---

### Post by Dr. Nick on 2006-05-13
Glad it installed shortcuts for you, maybe mine will come after a log off/on. I installed gnome after using kde so my menus are bit goofed up :)

All credit goes to the origional author at [http://perso.wanadoo.fr/bonfire/](http://perso.wanadoo.fr/bonfire/)
and to some members here for helping sort the compile errors.

It may even be better then you see. Here is the compile summary

> bonfire configuration summary:
----------------------------------
Version: 0.3.0

        Build inotify: yes
        Build gdl : no
        Build search pane : no
        Build playlist pane : no
        Build Preview pane : yes
        Build libnotify support : yes


A few features seem to be missing from my build, anyone get thse activated on theirs?

---

### Post by simplyw00x on 2006-05-13
You cannae attach debs to posts - it's deemed insecure. Also, checkinstall is more for personal use than distribution and won't manage bonfire's hefty dependency list properly (or at all IMO).

Here is a dpkg-buildpackage version replete with menu shortcut (also steps to verify changes):
```
wget http://www.moho.frihost.net/bonfire_0.3.0-1_i386.deb
wget http://www.moho.frihost.net/bonfire_0.3.0-1_i386.changes
gpg --verify bonfire_0.3.0-1_i386.changes
sudo dpkg -i bonfire_0.3.0-1_i386.deb
rm bonfire_0.3.0*
```
(beagle and gdl support not compiled in because I didn't have gdl and not everyone has beagle)

EDIT: DAMN you people post fast.

---

### Post by Dr. Nick on 2006-05-13
[quote=simplyw00x]You cannae attach debs to posts - it's deemed insecure. Also, checkinstall is more for personal use than distribution and won't manage bonfire's hefty dependency list properly (or at all IMO).

Here is a dpkg-buildpackage version replete with menu shortcut (also steps to verify changes):
```
wget http://www.moho.frihost.net/bonfire_0.3.0-1_i386.deb
wget http://www.moho.frihost.net/bonfire_0.3.0-1_i386.changes
gpg --verify bonfire_0.3.0-1_i386.changes
sudo dpkg -i bonfire_0.3.0-1_i386.deb
rm bonfire_0.3.0*
``` (beagle and gdl support not compiled in because I didn't have gdl and not everyone has beagle)

EDIT: DAMN you people post fast.[/quote]

OK, I wasnt sure how well checkinstall did with dependencies. I will remove my attachment and just link people to your post if thats ok. Thanks for providing a better build. You know a good howto for dpkg-buildpackage?

And yes these boards are very timely :)

---

### Post by ketsugi on 2006-05-13
[Here's my deb](http://ketsugi.com/ubuntu/dists/dapper/main/binary-i386/bonfire_0.3.0-0ubuntu1_i386.deb) with all optional features compiled in: gdl, beagle, totem playlist, etc.

I used [this guide](http://www.ubuntuforums.org/showthread.php?t=51003) to do it.

You can also get my diff from [http://ketsugi.com/ubuntu/bonfire](http://ketsugi.com/ubuntu/bonfire)

```
bonfire configuration summary:
----------------------------------
Version: 0.3.0

        Build inotify: yes
        Build gdl : yes
        Build search pane : yes
        Build playlist pane : yes
        Build Preview pane : yes
        Build libnotify support : yes
```

---

### Post by Dr. Nick on 2006-05-13
I will have to look into that guide. 

If someone would please try something for me.

Open bonfire and hit audio project, then right click in the window, does it crash?
 
Oh and I got menu entries after a reboot Applications, System Tools, Disc burning application

---

### Post by ketsugi on 2006-05-13
[quote="Dr. Nick"]Open bonfire and hit audio project, then right click in the window, does it crash?[/quote]

Yes, yes it does.

---

### Post by Dr. Nick on 2006-05-13
[quote=ketsugi]Yes, yes it does.[/quote]

OK so I'm not the only onw having that problem, I ran it from a terminal and all it said was segmentation fault.... 

I dont know if dapper is causing this crash or if it is a bug with bonfire, Bonfire is still very useable just dont right click lol

---

### Post by brainkilla on 2006-05-13
Thanks you all for your efforts and great .debs, I'm glad my initial post came to fruition :)

---

### Post by simplyw00x on 2006-05-13
I think it may still be useful to have both my and ketsugi's packages as not everyone wants or needs those features. I hadn't seen that tutorial; I was working off:
[http://www.desktopos.com/modules/articles/article.php?id=39](http://www.desktopos.com/modules/articles/article.php?id=39)

I'll have to admit, decent packaging tutorials are thin on the ground given how easy they are (most of the time) and how much './configure && make && make install' is thrown around the internet when it's basically deprecated.

EDIT: On a side note, remembering the heady days of the Ubuntu 5.10 starter guide, software installed by apt or dpkg needs a 'killall gnome-panel' to appear in the menus. Just a heads-up.

---

### Post by ketsugi on 2006-05-14
If anyone wants to install bonfire directly through synaptic, you can use this repo I set up (what a fun learning experience this has been: compiling a deb package, and now setting up a personal repo):

```
deb http://ketsugi.com/ubuntu/ dapper main
```

Then you can run

```
sudo apt-get update; sudo apt-get install bonfire
```

---

### Post by ketsugi on 2006-05-14
I sent an email to the author about the deb, and he's very supportive. He also had this to say:

[quote="Philippe Rouquier"]I read this thread and someone mentioned a few bugs (especially build
bugs) that have already been reported and, I hope, will be addressed in
the next version to be released soon.[/quote]

So there you go. Hopefully we'll see a new version soon!

---

### Post by brainkilla on 2006-05-14
Yay, I've started a true free software avalanche ;) :D . Great news!

---

### Post by nedkelly on 2006-05-17
First I would like to say this looks like a great app.

Now to the downside there is not a deb for breezy:(

Hope someone will make one :)

---

### Post by it.henrik on 2006-05-17
Im not sure you breezy ppl are missing out on so much, yet.

The soft is unstable and have lots of bugs in it :) but it is still just v 0.3 so the future looks good.

Bugs I encountered so far: 
right klick in the window for files to be burnt before any files are droped in it crashes the app
adding files and then removing them from the list of files to be burnt does not decrease the amount of MB:s to be burnt :) 
preview movie crashes the app  (it was in the todo list on the webpage but anyway (; )
Didnt recognise my burner if the app was statrted without cd in drive.
etc... 

This, as dapper atm, is for the early adopters .. Im one of them :)

---

### Post by Rouquier on 2006-05-17
Hi,
I'm the author of bonfire.

> **it.henrik]
The soft is unstable and have lots of bugs in it :) but it is still just v 0.3 so the future looks good.[/QUOTE]
I hope so

[QUOTE=it.henrik]
Bugs I encountered so far: 
right klick in the window for files to be burnt before any files are droped in it crashes the app[/QUOTE]
FIXED in 0.3.1 to be released this afternoon.

[QUOTE=it.henrik]
adding files and then removing them from the list of files to be burnt does not decrease the amount of MB:s to be burnt :) [/QUOTE]
MAYBE FIXED in 0.3.1: could you check it. If not could you report a bug on sourceforge please.

[QUOTE=it.henrik]
preview movie crashes the app  (it was in the todo list on the webpage but anyway ( said:**
> 
Could you report a bug on sourceforge with some details please?
[http://sourceforge.net/tracker/?func=add&group_id=156415&atid=799692](http://sourceforge.net/tracker/?func=add&group_id=156415&atid=799692)

[QUOTE=it.henrik]
Didnt recognise my burner if the app was statrted without cd in drive.
Strange! Is your drive USB or Firewire? (That would be normal since nautilus-cd-burner doesn't notice them when hot plugged. I'll send a patch to fix that).
Could you report a bug on sourceforge with some details please?
[http://sourceforge.net/tracker/?func=add&group_id=156415&atid=799692](http://sourceforge.net/tracker/?func=add&group_id=156415&atid=799692)

Thanks in advance for your feedback and support.
Philippe Rouquier

---

### Post by az on 2006-05-17
[QUOTE=Rouquier]Hi,
I'm the author of bonfire.

[/QUOTE]

I will try it soon.  Why did you re-invent the wheel?

---

### Post by Rouquier on 2006-05-17
[QUOTE=azz]I will try it soon.  Why did you re-invent the wheel?[/QUOTE]
What wheel?
First, I use already existing elements (cdrdao, cdrecord, gstreamer, ...). Bonfire is just a middle man in between. 
Second, at the time I started bonfire there was no real alternative (at least not one that fits my needs).
Third, just for the pleasure of programming and ... having a message from you ;) .

Philippe

---

### Post by it.henrik on 2006-05-17
[QUOTE=azz]Why did you re-invent the wheel?[/QUOTE]

maybe we should ask mr Thorvalds the same :rolleyes:

---

### Post by Rouquier on 2006-05-17
An here it is bonfire-0.3.1. Nothing exciting just bug fixes.

Have fun (hopefully) and ... report bugs [http://sourceforge.net/tracker/?func=add&group_id=156415&atid=799692](http://sourceforge.net/tracker/?func=add&group_id=156415&atid=799692)

Philippe

---

### Post by Dr. Nick on 2006-05-17
[quote=Rouquier]An here it is bonfire-0.3.1. Nothing exciting just bug fixes.

Have fun (hopefully) and ... report bugs [http://sourceforge.net/tracker/?func=add&group_id=156415&atid=799692]("http://sourceforge.net/tracker/?func=add&group_id=156415&atid=799692")

Philippe[/quote] 
All the problems Ive had are now fixed. No crashing on right click on either data or audio and the size/time bar at the bottom seems to correctly adjust when adding/removing files. Looks like those bugs are gone now.

I did this using checkinstall after compiling from source, since checkinstall isnt the best method to use for distribuiting I wont post the .deb. But I am sure a good deb will be made soon. I may try just for fun after I get home from work.

---

### Post by ketsugi on 2006-05-17
I think someone with a clean development machine should make the deb... I tried making it and the script that finds the dependencies spat out such a large number of dependencies, some of which are obviously wrong (like compiz, which I don't even have installed on my system).

I'll be more than willing to host the deb on my little apt repo, but I think someone a little more experienced than me should make it. :/

---

### Post by az on 2006-05-17
[QUOTE=Rouquier]What wheel?
First, I use already existing elements (cdrdao, cdrecord, gstreamer, ...). Bonfire is just a middle man in between. 
Second, at the time I started bonfire there was no real alternative (at least not one that fits my needs).
Third, just for the pleasure of programming and ... having a message from you ;) .

Philippe[/QUOTE]

Well, there are two extremes, I guess.  One would be that the communities around the existing applications (Gnomebaker, Graveman) wanted nothing to do with you and your crazy new ideas.  The other would be that you needed to start over because you wanted to implement something that had never been done before; (Two steps back in order to take three steps forward.)  I thought that was the case when I read 

"change the backend. Bonfire doesn't use nautilus-cd-burner as a backend any more - though it still depends on it for nautilus-drive. It has its own backend which will hopefully become a library in a future release when it's fully ready."

But since you didn't mention this, I guess it is less relevant that I thought.

Is there one reason why you couldn't integrate your improvements into Gnomebaker or graveman at the time?  Or were all three projects started at the same time?

I know graveman and gnomebaker were.

Anyway, this won't affect whether I use it or not (actually, whether it is in the repos will)  But I'm sure that's a question you get a lot and I was just wondering...

---

### Post by Rouquier on 2006-05-19
I've started up setting up the sourceforge site so, if someone wants to send me any package, I can host your debian/ubuntu packages.

---

### Post by joshrobinson on 2006-05-19
[QUOTE=Rouquier]I've started up setting up the sourceforge site so, if someone wants to send me any package, I can host your debian/ubuntu packages.[/QUOTE]

an amd64 .deb would be very nice :-D

---

### Post by denisesballs on 2006-05-19
Anyone package .3.1 in a .deb yet? I'm trying to compile it and I keep getting Requested 'gstreamer-0.10 >= 0.10.6' but version of GStreamer is 0.10.4.1 . .3.0 .deb. worked beautifully.

---

### Post by ato on 2006-05-19
This is the 32bit package:
[http://ato.netsons.org/ubuntu/dapper/bonfire_0.3.1-ato1_i386.deb](http://ato.netsons.org/ubuntu/dapper/bonfire_0.3.1-ato1_i386.deb)

I hope it works for you

---

### Post by denisesballs on 2006-05-19
[QUOTE=ato]This is the 32bit package:
[http://ato.netsons.org/ubuntu/dapper/bonfire_0.3.1-ato1_i386.deb](http://ato.netsons.org/ubuntu/dapper/bonfire_0.3.1-ato1_i386.deb)

I hope it works for you[/QUOTE]


WoooooO! Thanks ato!

---

### Post by ketsugi on 2006-05-19
Repo updated with ato's package.

---

### Post by qpieus on 2006-05-19
Nice app, I like it. Something weird though, I swear I checked "test burn" (or however it was phrased) under Properties before I burned a data dvd, but it didn't do a test burn, it did a real burn. Not a big deal since I rarely use test burn. On the good side, I haven't been able to burn a dvd at greater than 4x using k3b or nautilus. This first dvd with bonfire appears to have been written at 8x, which is what i selected (burned 3.8 gig in about 7 or 8 minutes - does that seem like 8x?). During the burn the estimated speed did not show anything. Also, my drive is 16x and the media I used is 16x, but when I went to select the burn speed, I could choose 8x or 16x, but not 12x. I would like to use 12x. To the author, is that something that you can add? Thanks for the nice app, I hope you keep working on it!

---

### Post by Roderik on 2006-05-20
[QUOTE=ketsugi]Repo updated with ato's package.[/QUOTE]


there seems to be a problem with your repository. And i'm not the only one :) see this thread for more information: [http://www.ubuntuforums.org/showthread.php?t=179392&highlight=bonfire](http://www.ubuntuforums.org/showthread.php?t=179392&highlight=bonfire)

---

### Post by ketsugi on 2006-05-20
Yes, you're right. I took a closer look at ato's deb and realised it's also not a proper dpkg deb; it has no dependencies listed. I've since removed it from the repo.

So we still need someone to make a proper deb for Bonfire 0.3.1...

---

### Post by Rouquier on 2006-05-20
[QUOTE=qpieus]Nice app, I like it. Something weird though, I swear I checked "test burn" (or however it was phrased) under Properties before I burned a data dvd, but it didn't do a test burn, it did a real burn. Not a big deal since I rarely use test burn. On the good side, I haven't been able to burn a dvd at greater than 4x using k3b or nautilus. This first dvd with bonfire appears to have been written at 8x, which is what i selected (burned 3.8 gig in about 7 or 8 minutes - does that seem like 8x?). During the burn the estimated speed did not show anything. Also, my drive is 16x and the media I used is 16x, but when I went to select the burn speed, I could choose 8x or 16x, but not 12x. I would like to use 12x. To the author, is that something that you can add? Thanks for the nice app, I hope you keep working on it![/QUOTE]

So, let me recap the bugs you ran into:
- test burn doesn't work
- burn dialog did not show estimated speed

If I'm right could you file a bug report indicating the version of growisofs you're using and also indicating if remaining time was displayed. Thanks in advance.
[http://sourceforge.net/tracker/?func=add&group_id=156415&atid=799692](http://sourceforge.net/tracker/?func=add&group_id=156415&atid=799692)

Moreover you'd like to have more intermediate speed displayed in the option dialog. That should be doable.

As for the burning speed, 8x is a likely speed considering the numbers (size and time) you gave. Though it is a rounded one. I think it was much more like 7x.

Philippe

---

### Post by qpieus on 2006-05-20
Philippe - yes, your recap is correct. Thanks for replying. Time remaining for the burn was not displayed either.
Something strange happened last night when I tried to burn another dvd. I dragged and dropped files into bonfire, set it for 16x this time, and started the burn. Well, the program closed out right after I clicked to start the burn. I re-tried it several times and got the same result (crash, program closes). There were no error messages displayed. Very strange that the first burn I did completed properly, but the other attempts I made failed.

This second burn I tried did have more data than the first one - it was a nearly full disk, about 4.2 gig, but still within the disk size limit. I'll try again today and report back.

---

### Post by qpieus on 2006-05-20
So today I can't burn anything (see above post). As soon as I click on Burn, the program closes out, no error messages are displayed. Why would my first burn with bonfire work just fine and now it crashes? k3b and nero still can burn, but they're stuck at 4x, which has been an ongoing problem I can't get solved.

---

### Post by ketsugi on 2006-05-20
I have the same problem as qpieus. I've submitted [a bug](http://sourceforge.net/tracker/index.php?func=detail&aid=1492156&group_id=156415&atid=799692) for it.

One thing I really like about DVD Decrypter (for Windows) is that during burning, it will show the actual current burn speed in addition to the supposed speed. Can you get Bonfire to show us this info as well? ie instead of just saying "4x" or "8x" we'd see "5,144kB/s (4.1x)" or something like that.

---

### Post by it.henrik on 2006-05-20
Just remembered another bug I noticed before... at least in v0.3.0 the add and delete buttons does not work.

---

### Post by ajack on 2006-05-21
Hi all,

I tried downloading the latest version of Bonfire from the URL:

[http://bonfire.sf.net](http://bonfire.sf.net)

But the site seems to be empty.  Does anybody know where I can get a proper/official copy of the bonfire deb file?  

:-k

---

### Post by woedend on 2006-05-21
[http://sourceforge.net/projects/bonfire/](http://sourceforge.net/projects/bonfire/)
is a working website. no deb there yet but the source and rpm are.

---

### Post by sbassett on 2006-05-21
I'm just another chuckle head posting a Dapper deb for Bonfire. Looks VERY promising. Keep up the good work Rouquier. It really looks like it could tear me away from k3b (quite an accomplishment). Anyway:

[Dapper Deb]("http://simon.doesntexist.com/request.php?15")

If you happen to check out the downloads section, it's on page 2.

Again keep up the good work.


Edit:
Apologies. This is in fact a dapper deb.

Also, thanks to all who visited. This is clearly my most popular package. Over 130 d/ls to date, killing the newest version of K3b.

Update to an Update - This has been replaced by a real deb. This will iist depends and etc.

---

### Post by ketsugi on 2006-05-21
Is that a Dapper deb (like your post says) or a Breezy deb (like your link says)?

Too lazy to download and check :/

---

### Post by w000t on 2006-05-21
This is a checkinstall deb!
I'm trying to build a proper dapper deb package, but the configure script seems a little messed up to me. All i'm getting is:
```
No package 'gstreamer-plugins-base-0.10' found
No package 'hal' found
No package 'libnautilus-burn' found

```

Of course all of them are installed... Don't know what to do :-|

---

### Post by ajack on 2006-05-22
[QUOTE=woedend][http://sourceforge.net/projects/bonfire/](http://sourceforge.net/projects/bonfire/)
is a working website. no deb there yet but the source and rpm are.[/QUOTE]

Thanks for the update.  I am a lazy typist and usually type the project name followed by sf.net which usually brings me to the correct open source project.  :rolleyes: 

Anyway, found the proper page at sourceforge but am wondering if the programmer could help build a .deb file so that us users can just download that and used dpkg to install it.

---

### Post by MaX on 2006-05-22
[QUOTE=w000t]This is a checkinstall deb!
I'm trying to build a proper dapper deb package, but the configure script seems a little messed up to me. All i'm getting is:
```
No package 'gstreamer-plugins-base-0.10' found
No package 'hal' found
No package 'libnautilus-burn' found

```

Of course all of them are installed... Don't know what to do :-|[/QUOTE]
A stupid question then...

do you have the -dev equivalents installed as well?

(And why does the Bonfire homepage state that 0.3.1 was released 20/12-2005 I thought the new version came a week ago? that's 13/5-2006)

---

### Post by w000t on 2006-05-22
LOL I can't believe I was that stupid! I was certain I have those -dev packages installed but I obviously didn't have :D Now I got them and it works flawlessly!

Attached is a clean pbuilder deb, which should handle all dependencies correctly. Enjoy!

---

### Post by ubutux on 2006-05-22
can you made a .deb for 64 bit, plaese?

---

### Post by ketsugi on 2006-05-22
w000t, thanks for the deb. I've tested it and it's working (though I don't understand why it depends on cdda2wav, when my compiled version didn't require that... no real matter but it's odd).

The repo has been updated and has also been tested to work fine. Sorry for the problems it caused earlier for others.

---

### Post by w000t on 2006-05-22
Sorry, my bad! Don't know how the hell those dependencies got in there!!
Anyway, here is an updated version with correct dependencies!

---

### Post by MetalMusicAddict on 2006-05-22
Thanx for the .deb w000t.

And WOW @ Bonfire. I like the UI so far. Reminds me of GIMP in how you can move around the UI. 
Very nice Rouquier. Cant wait to see what becomes of this. :)

I do think Azz posed a good question though.

-Why didnt you help with existing projects? You have alot of talent.

-Also what is you vision for Bonfire?

---

### Post by ketsugi on 2006-05-23
Thanks again, w000t. I've updated the repo again.

---

### Post by Rouquier on 2006-05-23
[QUOTE=MetalMusicAddict]Thanx for the .deb w000t.

And WOW @ Bonfire. I like the UI so far. Reminds me of GIMP in how you can move around the UI. 
Very nice Rouquier. Cant wait to see what becomes of this. :)

I do think Azz posed a good question though.

-Why didnt you help with existing projects? You have alot of talent.[/QUOTE]
For a long time I had tried to have a project of my own and at the time I started bonfire (more than a year ago), I thought there was room for improvement in that area as I didn't know about gnomebaker. When I found out, I had too much code already for it to be mergeable so I carried on.

[QUOTE=MetalMusicAddict]Thanx for the .deb w000t.
-Also what is you vision for Bonfire?[/QUOTE]
During the next step (0.4), I want to fix as many bugs as possible, improve the UI (especially GDL I'll send patches to the maintainers), strengthen the underlying library by relying only on cdrtools and growisofs, improve the playlist pane. I should release that one soon (June or something).
For 0.5, I hope to make it possible to simply drag a video and create SVCD and DVD. This latter should be ready for gnome-2.16.

Philippe

---

### Post by ketsugi on 2006-05-23
I haven't tried Gnomebaker, though I did use Graveman for a while before Bonfire showed up on my radar, and I have to say that Graveman is a simpler program to use, but Bonfire is closer to a Nero equivalent for those of us who like a little more control over disc creation.

I don't understand why so many people are questioning why he didn't simply contribute to another existing program; isn't free software all about competition? As far as I'm concerned, the only reason he needs to start a new project is because he wants to, and that should be enough for anyone here.

---

### Post by Confuse on 2006-05-23
I seriously have to thank you for creating this app! This by no means even compares to gnomebaker or graveman, it is simply beyond and I am glad you went your own way in coding this app. This is truly what the Gnome/gtk community needs to match the likeness of K3B in KDE/QT. I really hope you continue developing ths wonderful app, it shows a lot of promise and I can't wait to see whats in store for its future! Thanks again and keep up the wonderful work!

Damian

---

### Post by hezral on 2006-05-23
can someone list the dependencies package it needs? i dont have internet at home so i need to download the packages one by one. thanks.

---

### Post by ketsugi on 2006-05-23
Hezral, you could just install it off the repo I created (deb [http://ketsugi.com/ubuntu](http://ketsugi.com/ubuntu) dapper main) and install via Synaptic; that'll take care of dependencies.

---

### Post by hezral on 2006-05-23
i know but im not at home now and my home pc doesnt have an internet connection...thats why im asking for the dependencies list ;)

---

### Post by ketsugi on 2006-05-23
Here you go.

```
$ apt-cache depends bonfire
bonfire
  Depends: libart-2.0-2
  Depends: libatk1.0-0
  Depends: libaudiofile0
  Depends: libavahi-client3
  Depends: libavahi-common3
  Depends: libavahi-glib1
  Depends: libbeagle0
  Depends: libbonobo2-0
  Depends: libbonoboui2-0
  Depends: libc6
  Depends: libcairo2
  Depends: libdbus-1-2
  Depends: libdbus-glib-1-2
 |Depends: libesd-alsa0
  Depends: libesd0
  Depends: libfontconfig1
  Depends: libfreetype6
  Depends: libgconf2-4
  Depends: libgcrypt11
  Depends: libgdl-1-0
  Depends: libglade2-0
  Depends: libglib2.0-0
  Depends: libgnome-keyring0
  Depends: libgnome2-0
  Depends: libgnomecanvas2-0
  Depends: libgnomeui-0
  Depends: libgnomevfs2-0
  Depends: libgnutls12
  Depends: libgpg-error0
  Depends: libgstreamer-plugins-base0.10-0
  Depends: libgstreamer0.10-0
  Depends: libgtk2.0-0
  Depends: libhal1
  Depends: libice6
  Depends: libjpeg62
  Depends: libnautilus-burn3
  Depends: libnotify1
  Depends: liborbit2
  Depends: libpango1.0-0
  Depends: libpng12-0
  Depends: libpopt0
  Depends: libsm6
  Depends: libtasn1-2
  Depends: libtotem-plparser1
  Depends: libx11-6
  Depends: libxau6
  Depends: libxcursor1
  Depends: libxext6
  Depends: libxfixes3
  Depends: libxi6
  Depends: libxinerama1
  Depends: libxml2
  Depends: libxrandr2
  Depends: libxrender1
  Depends: zlib1g

```

---

### Post by shenki on 2006-05-23
hmm... it shouldn't be depending on all thos xlibs, should it? something's wrong there...

---

### Post by joshuapurcell on 2006-05-23
[QUOTE=azz]Why did you re-invent the wheel?[/QUOTE][QUOTE=azz]Well, there are two extremes, I guess.  One would be that the communities around the existing applications (Gnomebaker, Graveman) wanted nothing to do with you and your crazy new ideas.  The other would be that you needed to start over because you wanted to implement something that had never been done before; (Two steps back in order to take three steps forward.)  I thought that was the case when I read 

"change the backend. Bonfire doesn't use nautilus-cd-burner as a backend any more - though it still depends on it for nautilus-drive. It has its own backend which will hopefully become a library in a future release when it's fully ready."

But since you didn't mention this, I guess it is less relevant that I thought.

Is there one reason why you couldn't integrate your improvements into Gnomebaker or graveman at the time?  Or were all three projects started at the same time?

I know graveman and gnomebaker were.

Anyway, this won't affect whether I use it or not (actually, whether it is in the repos will)  But I'm sure that's a question you get a lot and I was just wondering...[/QUOTE]
Don't you ever have the urge to do something for yourself even though you know that going to someone else will make your job easier? Isn't it nice to figure things out for yourself? Why doesn't everyone drive the best/same car? All these questions are very similar to the question you posed to the creator of this nifty new application. You seem to be supporting this application and the author while at the same time wondering why someone would want to re-invent the wheel... I and hopefully others here would rather just support this application and the author.

---

### Post by helpme on 2006-05-23
[QUOTE=joshuapurcell]I and hopefully others here would rather just support this application and the author.[/QUOTE]
Yes, me too.

Btw., I just installed it for the first time and it looks like a great app.

---

### Post by aamukahvi on 2006-05-23
Does it support composing bootable CDs? Adding a boot floppy image or such? That's basically the only reason I have k3b installed.

---

### Post by it.henrik on 2006-05-23
bug in 0.3.1

choose data project .. go to project - new - burn an image/copy disc.
The start-up screen gets drawn in the files-to-be-burnt-window :)

file previewer still makes the app crash when I try to play a mp3 or any kind of movie.

---

### Post by Rouquier on 2006-05-23
Still working on it.

---

### Post by pathik on 2006-05-24
Another request for a amd64 deb of this. Please please?

;(

---

### Post by ketsugi on 2006-05-24
Rouquier, I don't know if this is a bug or a limitation of the UI, but I can't drag more than one file into a disc. I only seem to be able to add one file at a time, unless I drag the files in from Nautilus.

---

### Post by Rouquier on 2006-05-24
No that's right. If you want to add more than one file, you have to use the add button. Gtk+ doesn't natively support mutli drag'n drop. If it's added in 2.10, then I'll add it as well but for the time being we have to wait :(. But it's definetly on my TODO list.

NOTE: nautilus has its own custom widget. That's a kind of workaround.

What you can do is double click on each file you want to add. That works well also.

---

### Post by Rouquier on 2006-05-24
[QUOTE=it.henrik]bug in 0.3.1

choose data project .. go to project - new - burn an image/copy disc.
The start-up screen gets drawn in the files-to-be-burnt-window :)
[/QUOTE]

Sorry, I didn't read well the first part. That's indeed a confirmed bug.
Thanks you're in the top ten bug reporters :).

---

### Post by ashrack on 2006-05-24
[QUOTE=Rouquier]No that's right. If you want to add more than one file, you have to use the add button. Gtk+ doesn't natively support mutli drag'n drop. If it's added in 2.10, then I'll add it as well but for the time being we have to wait . But it's definetly on my TODO list.

NOTE: nautilus has its own custom widget. That's a kind of workaround.

What you can do is double click on each file you want to add. That works well also.[/QUOTE]
how come NERO has this abilty and its coded in GTK 1.x??

Havent used your program yet but by looking at the screenis its gonna be killer!!!

ps. Does "verify written data" exist?

ps2. on your web site it says the following:
20/12/2005 Bonfire-0.3.1 release
but wasn't it released less than a month ago??

---

### Post by ketsugi on 2006-05-24
I'd like to second Ashrack's request for a "verify written data" option. As it is what I'm doing now is to include a text file of md5sums on each disc I burn, so I can also do verification at a later date (in case of disc failure and whatnot)

---

### Post by EmyrB on 2006-05-24
Woa, nice app Rouquier :)

And a big thanks to Ketsugi for the repo space :D

And also a big shoutout to w000t for the deb :D

Rouquire would you like us to post bugs here or through Sourceforge?

Cheers

---

### Post by Rouquier on 2006-05-24
[QUOTE=EmyrB]
Woa, nice app Rouquier :)

And a big thanks to Ketsugi for the repo space :D

And also a big shoutout to w000t for the deb :D

Rouquire would you like us to post bugs here or through Sourceforge?

Cheers[/QUOTE]

On sourceforge please so I can keep a better track of them.

[QUOTE=ashrack]
ps. Does "verify written data" exist?
[/QUOTE]
Not yet but since everybody keeps asking me that, that might be in the next release.

[QUOTE=ashrack]
ps2. on your web site it says the following:
20/12/2005 Bonfire-0.3.1 release
but wasn't it released less than a month ago??[/QUOTE]

Fixed. Thanks

---

### Post by ashrack on 2006-05-24
In the evening I will have gotten around 30DVDs and some CDs to record by tomorrow. 
So what is your opinion, is it stable enough for burning to replace the ugly but stable NEROLinux???

I have a NEC 4500DVDRW

---

### Post by ketsugi on 2006-05-24
ashrack: if you don't mind not being able to verify written data without doing your own verification (like md5sum or whatever) then yes, it is stable enough. It's not perfect (some of the user feedback at burn time is inaccurate for me) but the burn goes through fine, since it's basically just a GUI to the mkisofs and growisofs command-line tools.

---

### Post by Rouquier on 2006-05-24
I'd like to say a 100% yes, but I can't. At least I think it won't crash if you turn off the previewer (a crash was reported to happen randomly with it turn on).

Otherwise that should be OK but who knows, it hasn't been extensively tested yet.

At least if you choose to go for it, please tell me whether you had a problem or not.

---

### Post by encho on 2006-05-24
I am waiting for serious burning app for gnome for ages. This one looks very promising, hope you could keep up the good work and make it k3B equivalent for gnome (g3B :)  ).

I would like to see your roadmap as well. What exactly are you planning for the future, is there going to be support for making cue/bin, raw copies (with subchanel data), bootable, hybrid disks... Making support for video DVDs and CDs would be nice, but I suggest you to make it maybe as separate project, as it may complicate the GUI. Look for dvdstyler (gnome) and kmediafactory (kde), they are very easy to use.

Looking forward to the next release!

---

### Post by Floor19 on 2006-05-24
Thanks Rouquier for this great app and it is my default gnome burn program already!!

Video support would be much apprr because i now use the terminal to burn DVD video.

Keep up the good work and let us know what your plans are for the future!

---

### Post by qpieus on 2006-05-24
"g3b", I like it.
I also would love to see a verify data option.
nice job so far, keep up the good work!

---

### Post by j_baer on 2006-05-24
With all the built in CD burning capablity of gnome who would have thought anyone would need a CD burning app.

Well here it is, very nice and well thought out!

Thanks ...

:KS

---

### Post by azarro on 2006-05-26
hi,
is it possible to get it working on Breezy? I've tried compiling it and the .deb mentioned before, but there's a hell lot of dependencies I can't break through :( 
a Breezy repository would be nice ^_^

thanks

---

### Post by shu on 2006-05-26
Great application man. Finally a burning app to get serious work done.

---

### Post by prkfriryce on 2006-05-28
Great job! Looks good.

I have included gstreamer0.10-plugins-base to burn mp3 with your application, but i am receiving a codec error. :confused:

---

### Post by simplyw00x on 2006-05-28
> I have included gstreamer0.10-plugins-base to burn mp3 with your application, but i am receiving a codec error. 
AFAIK mp3 codecs are in gstreamer0.10-plugins-ugly.

---

### Post by Rouquier on 2006-05-28
They are in gst-plugins-ugly or you can use fluendo's ones if you have an intel CPU (the latter are much better).

---

### Post by prkfriryce on 2006-05-28
[QUOTE=simplyw00x]AFAIK mp3 codecs are in gstreamer0.10-plugins-ugly.[/QUOTE]

thanks these work, but i'm now receiving an "Error while buring: Internal data flow error.." when i attempt to burn the mp3 as an Audio project. It appears to be hanging up during Transcoding. Is there a debug paramter i can run or does anyone know the cause of this error?

---

### Post by MetalMusicAddict on 2006-05-28
I would suggest running it from a terminal and see. Or would that just give error messages?

---

### Post by prkfriryce on 2006-05-28
[QUOTE=MetalMusicAddict]I would suggest running it from a terminal and see. Or would that just give error messages?[/QUOTE]

The only standard output was

```
libnotify-Message: Unable to get session bus: No reply within specified time

```

---

### Post by Rouquier on 2006-05-28
Hi,

This is a gstreamer error message. Could you file a bug in sourceforge.net with the answers to these questions please.
Do your songs play well in totem (assuming it is a gstreamer version) ?
Do all your mp3s fail to be transcoded ? if not could you send me the faulty song at [email]bonfire-app@wanadoo.fr[/email]
Are you trying to burn your disc on the fly ? If you do, try to burn your disc in a regular way and tell me what happens.

NOTE: if they don't play well in totem I think it's a gtreamer problem.

---

### Post by Rouquier on 2006-05-28
[QUOTE=prkfriryce]The only standard output was

```
libnotify-Message: Unable to get session bus: No reply within specified time

```[/QUOTE]
you don't seem to have dbus running (though it's not the cause of the failure).

---

### Post by prkfriryce on 2006-05-28
[QUOTE=Rouquier]you don't seem to have dbus running (though it's not the cause of the failure).[/QUOTE]

```

105       4127     1  0 May27 ?        00:00:08 /usr/bin/dbus-daemon --system
cpage     4983  4941  0 May27 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus -launch --exit-with-session x-session-manager
cpage     4986     1  0 May27 ?        00:00:00 /usr/bin/dbus-launch --exit-with -session x-session-manager
cpage     4987     1  0 May27 ?        00:00:00 dbus-daemon --fork --print-pid 8  --print-address 6 --session
cpage     1559  1388  0 17:11 pts/3    00:00:00 grep dbus

```

[QUOTE=Rouquier]Hi,

This is a gstreamer error message. Could you file a bug in sourceforge.net with the answers to these questions please.
Do your songs play well in totem (assuming it is a gstreamer version) ?
Do all your mp3s fail to be transcoded ? if not could you send me the faulty song at [email]bonfire-app@wanadoo.fr[/email]
Are you trying to burn your disc on the fly ? If you do, try to burn your disc in a regular way and tell me what happens.

NOTE: if they don't play well in totem I think it's a gtreamer problem.[/QUOTE]

All mp3 play in Totem and XMMS ( default player ). 

I did notice there are 44 alphanumerical characters in the name. I was successful with shorter mp3 files so i will attempt to rename those original and try again.

edit*
after renaming to only 2 characters, the same error message appears. I sent you a link for the file. thanks in advance. : )

---

### Post by Rouquier on 2006-05-29
I did not receive anything yet.

---

### Post by MacgyverDXS on 2006-05-29
Rouquier, 

Thanks for this great app.  I just recently upgraded to Dapper and Gnomebaker completely quit working for me, so I decided to try Bonfire....works great!  The UI is a lot nicer than Gnomebaker and easier for me to understand.  Thanks again and keep up the good work!:)

---

### Post by ounn on 2006-07-12
Hi.

Im compiling but i cant enable the playlist panel, what package do i need to enable that option?

Thanks

ounn

---

### Post by Rouquier on 2006-07-13
hi

you need to have totem-devel installed to parse playlists. Once installed, just run ./configure and you should have playlists enabled. The required totem version is 1.2.0. 

Let me know if you run into any problem.
Philippe

---

### Post by ounn on 2006-07-13
Thanks, it was that package that was missing. The compilation runs ok, but i cant try it now because i have no cds do burn. When i do, i give some feedback.


ounn

---

### Post by g14 on 2006-07-17
Ketsugi,

I installed bonfire from your repository and now it does not work at all. Everytime I try to burn a cd, it says, "An unknown error occurred, please check your disk". I'm having to manually revert to .3.91 and multisession still does *not* work.

jschroed@ubuntu-desktop:~$ dpkg -l bonfire | grep bonfire
ii  bonfire        0.4.1-0ubuntu1 Yet another application to burn CD/DVD for the GNOME desktop

---

### Post by ketsugi on 2006-07-17
You'd best check with Rouquier about that. I did a straight compile with no modifications to source.

---

### Post by paulle on 2006-07-27
> **g14 said:**
> Ketsugi,

I installed bonfire from your repository and now it does not work at all. Everytime I try to burn a cd, it says, "An unknown error occurred, please check your disk". I'm having to manually revert to .3.91 and multisession still does *not* work.

jschroed@ubuntu-desktop:~$ dpkg -l bonfire | grep bonfire
ii  bonfire        0.4.1-0ubuntu1 Yet another application to burn CD/DVD for the GNOME desktop

The same happens to me "An unknown error occurred, please check your disk". I tried various types of CDs but all the time happens the same.

---

### Post by ketsugi on 2006-07-27
Eh, I just noticed that I'm getting the same error too (I haven't burned any discs in a while).

I'm going to try a recompile later this weekend and see if that fixes anything.

---

### Post by BitTorrentBuddha on 2006-07-28
Has anyone packaged 0.4.* yet?

---

### Post by Darrena on 2006-07-30
> **BitTorrentBuddha said:**
> Has anyone packaged 0.4.* yet?

I put some packages up at:
[http://darrenalbers.com/bonfire/](http://darrenalbers.com/bonfire/)

---

### Post by BitTorrentBuddha on 2006-07-31
Much obliged, works like a charm.

---

### Post by flamarro on 2006-08-01
finnaly
man, you are the man.....
i'm a gnome user,newbie, and i don't want to install any kde apps, and i was thinking that could not be possible because of K3B. Now there's finnaly a app that can really do one thing that i wanted the most in gnome, write multisections discs with no problems at all( gnomebaker gives me lots o errors that i could not understand but many of you guys sayed that's the best for gnome!!! graveman, well :-k .... For me, from here, what comes next only could be better =D> to you, really... you are the man Rouquier, and thanks to all of you that are helping him too, speading this and doing so helping all of us too.

PS: as you can see i liked really this app. :grin:

---

### Post by jimrz on 2006-08-07
THANK YOU !!!  ...  so far, have only used to burn one iso and really like the app. In fact, it was the Xubuntu Dapper "live" cd and am posting this from it.

Been having issues, most notably earlier today when all it would make was a couple of coasters when trying to burn iso, with gnome-baker and decided to give this a shot.

BTW, in case you had not seen, Bonfire is the highest rated ( 9.18 ) app on the gnome apps site...congrats.

---

### Post by wold on 2006-08-24
Can anybody build a .deb of **Brasero 0.4.2**? It's the new version of Bonfire :P

---

### Post by kpkeerthi on 2006-08-25
Multisession doesn't work yet. On to K3B again.

---

### Post by ketsugi on 2006-08-27
Now that I've switched to KDE, I've been using K3B and find that far more appropriate to my needs and expectations. I don't think I'll be compiling debs for Bonfire/Brasero any longer, since I no longer use Gnome as my desktop environment. Sorry!

---

### Post by catanzag on 2006-08-30
Look at [this]("http://www.ubuntuforums.org/showpost.php?p=1433654&postcount=2") post, maybe it can help you

---

### Post by ashrack on 2006-09-04
I can compile BONFIRE for U all! Just compiled the latest BONFIRE-BRASERO 0.4.2 with the following support:
```
brasero configuration summary:
----------------------------------
Version: 0.4.2
        Update caches: yes
        Build inotify: yes
        Build search pane : yes
        Build playlist pane : yes
        Build Preview pane : yes
        Build libnotify support : yes

```
Here U are! Plz let me know if it works 4U!

ps. U must first untar it and under it hides the DEB!
[ATTACH]15624[/ATTACH]

---

### Post by mogwai on 2006-09-06
Brilliant! Gnomebaker was just starting to piss me off...

I notice you can download a .rpm from the site. Has anyone had any luck using alien to convert and install it?

If no one has, I'm game to give it a shot.

---

### Post by ashrack on 2006-09-06
Why would U wanna RPM when U got mine DEB compiled and also U can get it from the repo here:
[http://www.ubuntuforums.org/showpost.php?p=1433654&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1433654&postcount=2)

---

### Post by qpieus on 2006-09-06
> **ashrack said:**
> I can compile BONFIRE for U all! Just compiled the latest BONFIRE-BRASERO 0.4.2 with the following support:
```
brasero configuration summary:
----------------------------------
Version: 0.4.2
        Update caches: yes
        Build inotify: yes
        Build search pane : yes
        Build playlist pane : yes
        Build Preview pane : yes
        Build libnotify support : yes

```
Here U are! Plz let me know if it works 4U!

ps. U must first untar it and under it hides the DEB!
[ATTACH]15296[/ATTACH]
I grabbed your file, but I can't untar it. Both Ark and command line "tar -xjvf brasero.0.4.2.tar.bz2" returns an error: 
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error exit delayed from previous errors

Can you check on your file? Maybe it got corrupted or something.
Thanks for your help and the deb creation.

---

### Post by mithras86 on 2006-09-08
I've made with alien a deb from the rpm, see the attachment. But you can use better the brasero repo. See [this thread]("http://www.ubuntuforums.org/showthread.php?t=252719") to add it to your sources.list.

---

### Post by ashrack on 2006-09-12
qpieus
I uplouded the new tar file. Hopefully this one works.
HEre it is:
[http://ubuntuforums.org/showpost.php?p=1462586&postcount=117](http://ubuntuforums.org/showpost.php?p=1462586&postcount=117)

---

### Post by finferflu on 2006-09-14
> **ashrack said:**
> I can compile BONFIRE for U all! Just compiled the latest BONFIRE-BRASERO 0.4.2 with the following support:
```
brasero configuration summary:
----------------------------------
Version: 0.4.2
        Update caches: yes
        Build inotify: yes
        Build search pane : yes
        Build playlist pane : yes
        Build Preview pane : yes
        Build libnotify support : yes

```
Here U are! Plz let me know if it works 4U!

ps. U must first untar it and under it hides the DEB!
[ATTACH]15624[/ATTACH]

Thanks a lot! I've installed it on two machines and the installation's gone flawlessly. Thank you!:D

---

### Post by pt123 on 2006-09-22
I just used Bonfire 0.41. It was nice using it with a gnome menu. But there were 3 things I didn't like:
1.On my 16x DVD burner and I chose to burn 8x but it burnt at only 4-6x.

2.There is no file verifying feature found in Nero & K3B

3.Is there anyway to access the ISO 9960 settings.

I was wondering if any of these 3 have been addresses in the later versions of Bonfire?

---

### Post by lamego on 2006-09-22
In case someone is looking for the latest stable release for Dapper:
[http://www.getdeb.net/search.php?keywords=brasero](http://www.getdeb.net/search.php?keywords=brasero)

---

### Post by pt123 on 2006-09-22
Thanks thats a great site

---

### Post by rocknrolf77 on 2006-09-22
Exellent site [www.getdeb.net](www.getdeb.net) Finally got bonfire (now brasero) working from their package. Have tried alot of different stuff. Alien was not any sucess either. We need more debs out there. I am not any good at compiling from source yet. The site is just in the start but I think it's going to be a good known site in some time. Good for the people who are "afraid" of the terminal. (not me, but I have a lot more to learn) :)

---

### Post by Rouquier on 2006-09-23
> **pt123 said:**
> I just used Bonfire 0.41. It was nice using it with a gnome menu. But there were 3 things I didn't like:
1.On my 16x DVD burner and I chose to burn 8x but it burnt at only 4-6x.

2.There is no file verifying feature found in Nero & K3B

3.Is there anyway to access the ISO 9960 settings.

I was wondering if any of these 3 have been addresses in the later versions of Bonfire?

hi, I'm the author of bonfire.

1- unfortunately we are dependent on growisofs for the time being and it doesn't always respect the settings. But new backends are emerging and I hope that this problem will be addressed in the future.

2- done in the unstable version.

3- Rock ridge is always on. In unstable, you can only choose to enable joliet or not. In stable, joliet is mostly enabled by default except when you add non joliet compliant files. What other settings would you need?

Feel free to open bugs to request feature enhancement at:
[http://bugzilla.gnome.org/enter_bug.cgi?product=bonfire](http://bugzilla.gnome.org/enter_bug.cgi?product=bonfire)

---

### Post by JGuru on 2006-09-23
Yeah, This is a better one than GnomeBaker. It has some cool features too.
 It's a nice CD/DVD burner.

---

### Post by SirPecanGum on 2006-09-23
> **ashrack said:**
> I can compile BONFIRE for U all! Just compiled the latest BONFIRE-BRASERO 0.4.2 with the following support:
```
brasero configuration summary:
----------------------------------
Version: 0.4.2
        Update caches: yes
        Build inotify: yes
        Build search pane : yes
        Build playlist pane : yes
        Build Preview pane : yes
        Build libnotify support : yes

```
Here U are! Plz let me know if it works 4U!

ps. U must first untar it and under it hides the DEB!
[ATTACH]15624[/ATTACH]

Perfect. Thank you very much!

---

### Post by noynac on 2006-09-23
The Brasero (Bonfire) web site states:

*As of today [9-16-06], development happens into GNOME CVS. Bye sourceforge and thanks a lot!"* 

Does this mean we can install Brasero using Synaptec? I did a search of Synaptic and couldn't find it.

Also, I need multisession capability, and the Brasero web site states that this capability is supported. Does multisession work well in Brasero?

Finally, if I install the Brasero deb file, do I have to set up any other dependencies? I'm still a noob when it comes to installing programs, and the whole issue of dependencies is a bit confusing. 

Thanks,

noynac

---

### Post by Rouquier on 2006-09-24
> **noynac said:**
> The Brasero (Bonfire) web site states:

*As of today [9-16-06], development happens into GNOME CVS. Bye sourceforge and thanks a lot!"* 

Does this mean we can install Brasero using Synaptec? I did a search of Synaptic and couldn't find it.

Also, I need multisession capability, and the Brasero web site states that this capability is supported. Does multisession work well in Brasero?

Finally, if I install the Brasero deb file, do I have to set up any other dependencies? I'm still a noob when it comes to installing programs, and the whole issue of dependencies is a bit confusing. 

Thanks,

noynac

No, it just means, that the source tree is now hosted by GNOME servers. As for ubuntu integration someone told me that he would make packages so that brasero would be in the next development release of ubuntu. So cross your fingers and wait.

multisession is supported but really needs to be improved. That will happen in 0.4.93 (that is full disc, including already burnt data, edition).

As for the dependencies, most of them are already in modern distribution. I removed the most fancy ones for everyone to be able to get it working. Now, if you build it yourself, don't forget to install the packages listed in the dependency list and their corresponding "name-dev." packages.

---

### Post by noynac on 2006-09-24
Rouquier,

Thanks for the quick response--I appreciate the help. 

Modred

---

### Post by CaveRat on 2006-09-24
This might sound like a silly question to some, but here it is. I would like to check out Brasero, but noticed it is based on i386 Kernel? Is that right, and if so can I still install/run it using the K7 kernel? I do not have the 386 kernel installed.

---

### Post by ashrack on 2006-09-24
CaveRat
Yes U can without problem. Since its all backward compatible

---

### Post by ashrack on 2006-09-24
Since we now have 
[http://www.getdeb.net/](http://www.getdeb.net/)
which compiles BRASERO and also lots of other apps is there any more need for me to compile U latest BRASERO?

---

### Post by Psquared on 2006-09-24
Will it work in Xubuntu? Anybody got it installed and working? Gnomebaker works and I have a lot of gtk libs installed. Maybe I should be the guinea pig???

---

### Post by CaveRat on 2006-09-24
> **ashrack said:**
> CaveRat
Yes U can without problem. Since its all backward compatible

Thank you for the post ashrack. I'm fairly new to all of this, so I'm slightly cautious to compatibility issues.

---

### Post by Psquared on 2006-09-24
I assume I have to install Nautilus in Xubuntu?? What else?

---

### Post by vuitton on 2006-09-24
Tried to get it to work with Edgy (GNOME 2.16), but the installation fails due to a dependency error.Hopefully Brasero will work with Edgy/Gnome 2.16 soon :)
EDIT:
This .deb-File seems to work:  :) [http://www.ubuntuforums.org/showpost.php?p=1524823&postcount=16](http://www.ubuntuforums.org/showpost.php?p=1524823&postcount=16)

---

### Post by ashrack on 2006-09-25
> **Psquared said:**
> I assume I have to install Nautilus in Xubuntu?? What else?
Just install the .DEB with GDEBI and it should automaticly take care of all the dependencies.

---

### Post by encho on 2006-09-26
> **ashrack said:**
> Just install the .DEB with GDEBI and it should automaticly take care of all the dependencies.

That's right. I have it up and running. It just needs libnautilus-burn from nautilus, not the whole prog.

---

### Post by Psquared on 2006-09-26
Thanks - I got it installed and I noticed it only grabbed a couple of nautilus files. I am going to make some CDs tonight and and ISO so I'll be pushing it pretty hard. We'll see how it takes it. :p

---

### Post by Psquared on 2006-09-29
Burned an ISO flawlessly and quickly. It surprised me how fast it did it on a DVD. 2.6 gigs worth. It took less than 10 minutes. Thats faster than Roxio in Windows.

Nice work.

---

### Post by dannyboy79 on 2006-09-29
i have been having a heel of a time trying to burn an iso image onto a dvd!! I get an error during the write in. i tried nerolinux (because I have a serial from when I purchased it for windows) I havew also tried gnomebaker. Is there something I am suppose to do somewhere to be able to burn to dvd's??? I can burn a smaller iso onto a cd? I am using Tayio Yuden DVD+R 8X. I have also tried a DVD-R can't remember which brand but it failed also. i think I was able to burn onto a dvd+rw from Memorix? If that's the case (being able to burn onto the memorix dvd+rw) is it the dvd+r and dvd-r media that isn't working or what else do I need to check?? I am using a 80 pin cable, dma is on. WTF. Please help

---

### Post by Psquared on 2006-09-29
Use the slowest burn speed possible. I think most of these programs come set by default at too high a speed. I used 2x and it still did it in less than 10 minutes and with no errors. 2.6 gigs.

---

### Post by dannyboy79 on 2006-09-30
well, thank you for informing me of this and pardon my sarcasism but I had asked you if you had done anything more to any config settings or anything more than usual to get your burner to burn DVD's? if you could answer that I would appreciate it.

---

