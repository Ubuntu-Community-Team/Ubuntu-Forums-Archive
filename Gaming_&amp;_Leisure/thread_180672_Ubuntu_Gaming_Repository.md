---
title: "Ubuntu Gaming Repository"
date: 2006-05-22
forum: Gaming &amp; Leisure
---

### Post by brynjarh on 2006-05-22
The idea of creating a repository dedicated to having up to date versions of native linux games for Ubuntu has definitely come up before, but what do people think of it? Is it a stupid idea or is it just a resource problem?

If the idea does have some reason behind it but there is limited resources to back it up it could just be a small repository with few chosen games and as requests start coming in few new games would be chosen to be added, that way it would grow both according to resources and gamers requests.

I find it unlikely this could be an official project but what about the people behind Ubuntu Gamers Arena?

What do you people think?

---

### Post by graigsmith on 2006-05-23
it's a good idea. especially if new versions took a day or so to get to the new repository.  but couldn't we just use universe? or something for games? and just update them as soon as a new version comes out?

---

### Post by leech on 2006-05-23
There are only a few problems I see with this idea.  

1) Distribution licenses;  Not all the games that people would want can be put in any sort of repository.  Either due to legalities, or simply their license statements.  

2) Build System;  There would need to be a build system in place, much like what Debian/Ubuntu have now that will automate the building of packages for all architectures.  This would be easy enough to set up, but would still need maintainers to upload the new source from their upstream projects.  Much like what is done now, but it would double the work of the Maintainers.

3) Backports;  Really, something like this would best go into the backports project, since once a particular release is out, then the versions freeze with the exception of security updates and bug fixes.  

Personally I think it is a great idea, because I know I hate waiting for the latest packages, especially for emulators.  Speaking of which, Debian has Mednafen (a multi-console emulator [http://mednafen.com/](http://mednafen.com/) ) but Ubuntu does not.  I really badly want the newest xmame packages always installed in Ubuntu, but their packages are always quite out of date.  Debian's currently at 0.104 (0.105 if you have ppc, apparently there is a build problem for i386 for it right now.  I know, I tried building from source...)  Dapper has 0.101 in the repositories.

Same goes for e-uae.  I'd love to have the latest version in the repositories.  Currently the CVS has issues, but it looks like they are finally working on the debian packaging part of it.  

As I said, the biggest problem is getting the maintaner of the packages to update them, especially since most maintainers do it on a voluntary basis.

Leech

---

### Post by KingBahamut on 2006-05-23
Id certainly support this kind of movement. How many packages do you think wed be talking about? It might be possible to host it off of the Gaming Arena server (barely maxed out on his bandwidth) or else where?

---

### Post by Wr8EYilK8Y on 2006-05-23
Problem: Who would maintain it?

I do support it, though

---

### Post by mp3guy on 2006-06-19
Its great idea, make installing stuff like quake3 easier too

---

### Post by seth0x2b on 2006-06-19
On with the votes people :).It would be great to have something like this. And with a nice wittle site attached so newcomers might browse a list of game names/screenshots


Cheers

---

### Post by bvanaerde on 2006-06-19
you have my vote too :)

---

### Post by thak on 2006-06-19
One thing that I think would put Ubuntu over the top in terms of "acceptability of the home user" would be to use a repository like this along with some sort of GUI that would allow the "Windows newbie" to install his UT2004 or Quake III or whatever automatically.

That GUI would have to be something that would help eliminate that whole "can't host copyrighted games in a repository" while also making the Linux install brain-dead simple.

I'm envisioning something like EasyUbuntu or Automatix or whatever, where you pick the games you already own from a list, and then you're prompted to insert the CD for it to copy the art/music/resources from.  Combine that with the ".deb" packages from the repository, and you're good to go.  Should make the suits happy enough--and be easy enough for Windows users to understand.

We really need to get some sort of "support of native ports" built into Ubuntu.  If there was some sort of way to "send a vote to the Ubuntu mothership" that you have installed a copy of that native port, perhaps those aggregate statistics could be shown to gaming companies (EA, Ubisoft, whatever) to get them to see that the Linux market is larger than they think--and growing.

Yes, Wine is getting more and more awesome--but native Linux games are obviously a hell of a lot better...

---

### Post by Lord Illidan on 2006-06-19
I like the idea.

---

### Post by wangdang on 2006-06-19
i support this 100%
if there was an easy way to submit debs and whatnot i could prolly maintain at least some miniscule thingy.

---

### Post by AngryKidJoe on 2006-06-20
You've my vote and support.

---

### Post by lordmule on 2006-06-20
would there be any legal issues supplying the demo versions of linux games? ut2004, quake3, enemy territory...

---

### Post by Simian on 2006-06-20
Wow, I've never seen a poll where everyone votes the same way.

---

### Post by the_guy1 on 2006-06-20
I was realy shocked that nobody realy made one already I would realy like that nobody did that I would realy like to support such a project

---

### Post by DirtDawg on 2006-06-20
I'm using Hoary. Would the updates be only for the most recent version of Ubuntu? How would that work exactly?

Either way, I love video games so a big hearty AYE!

---

### Post by Isoss on 2006-06-20
Count me in! I vote.

---

### Post by deathbyswiftwind on 2006-06-22
I second the motion for a gaming repo and I would gladly build debs for games for the 386 series when needed :)

---

### Post by GuitarHero on 2006-06-22
What games would be in it?

---

### Post by Megatog615 on 2006-06-22
[QUOTE=Simian]Wow, I've never seen a poll where everyone votes the same way.[/QUOTE]
Yea, I mean geez, 129-0?

---

### Post by chrism66 on 2006-06-22
I am also in favor of this idea!

---

### Post by Phreaker on 2006-06-23
Very-nice idea,indeed

---

### Post by c1ean on 2006-06-23
Brilliant :)

---

### Post by Chozabu on 2006-06-23
haha, 163 votes yes, 0 no

---

### Post by Frem on 2006-06-23
Even if the license of a free game won't permit us to distribute directly, we could make packages that automatically download and launch the installer for said games.
I mean, you know how Gentoo lets you emerge scripts that will grab and install games for you, but it's a special command to do so after the emerge?
Why not make a dialog pop up after installation?
It could ask if you wanted to:
a) download the game from the internet, but don't install it right now
b) install the game (from internet download or cdrom)
c) don't do anything right now.

If a or c is chosen, an icon that launches the dialog could be placed on the games menu and removed when the game is installed. After the game is installed, the package would reconfigure the icon to launch the game. When the package is removed, the game is deleted as part of the deconfiguration or something. 
The point is, to make it easy for the user to install or remove the game without worrying about metapackages or having to drop down to the command line.

---

### Post by DJ_Max on 2006-06-25
[QUOTE=lordmule]would there be any legal issues supplying the demo versions of linux games? ut2004, quake3, enemy territory...[/QUOTE]
Yes, but look at [this post]("http://ubuntuforums.org/member.php?u=96550") for a solution for most licenses.

---

### Post by Omnios on 2006-06-25
I like the idea of a game repository in that it could possibly list a lot of hidden gems, a couple weeks ago I started scouring the web for Linux capable games and found some realy cool gems. Some are a bit older and a lot are fairly new. Anyways it took me over a week of web searching to find a lot of these games. One thing I would like to add would be that it should have web support from the comunity and have descriptions and revies of the games. There a re currently a few Linux gamming sites and I have found thse very usefull. I think that having screen shots and reviews to be very inportand to suppord a gamming repositly as going blind does not always work.

---

### Post by Frem on 2006-06-30
Ok, so we all want it. Now what? Who's going to be in charge of this thing?
I'll learn how to make Debs and contribute some packages if needed.

---

### Post by msixp_k7 on 2006-07-01
Count me in!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Max Luebbe on 2006-07-02
I could easily do 686 and k7 packages if this gets going.

---

### Post by Mathias-K on 2006-07-03
[QUOTE=thak]One thing that I think would put Ubuntu over the top in terms of "acceptability of the home user" would be to use a repository like this along with some sort of GUI that would allow the "Windows newbie" to install his UT2004 or Quake III or whatever automatically.

That GUI would have to be something that would help eliminate that whole "can't host copyrighted games in a repository" while also making the Linux install brain-dead simple.

I'm envisioning something like EasyUbuntu or Automatix or whatever, where you pick the games you already own from a list, and then you're prompted to insert the CD for it to copy the art/music/resources from.  Combine that with the ".deb" packages from the repository, and you're good to go.  Should make the suits happy enough--and be easy enough for Windows users to understand.

We really need to get some sort of "support of native ports" built into Ubuntu.  If there was some sort of way to "send a vote to the Ubuntu mothership" that you have installed a copy of that native port, perhaps those aggregate statistics could be shown to gaming companies (EA, Ubisoft, whatever) to get them to see that the Linux market is larger than they think--and growing.

Yes, Wine is getting more and more awesome--but native Linux games are obviously a hell of a lot better...[/QUOTE]

Nice ideas.. I'd really like such a repo :)

---

### Post by tzulberti on 2006-07-03
It is a great idea.

---

