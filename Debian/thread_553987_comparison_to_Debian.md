---
title: "comparison to Debian"
date: 2007-09-18
forum: Debian
---

### Post by phendric on 2007-09-18
For you linux gurus out there, how would you compare / contrast Ubuntu to Debian?

P

---

### Post by eoghanmurray on 2007-09-18
Ubuntu's debian based, hence the *.deb package installers. It has a better user base and more users, and has backing from DELL, and it's better supported I think, so I contrast that it's better.

---

### Post by Malibu Illusion on 2007-09-18
Ubuntu is essentially a fork of the latest Debian Sid (Unstable) line at the time of release, apparently made more stable.  

Ubuntu is a nice OS to run on a desktop box if you want bleeding edge applications and whatnot.  Debian's stable line, and Lenny (testing) to a degree, is substantially more stable than Ubuntu as it has older, time-tested and reliable software which is already proven.

To briefly summerize, Ubuntu is nice on the desktop for end-users looking for the latest stuff but I wouldn't consider deplying it in any environment that demanded rock solid stability.  That's where Debian comes in.

Take care.

---

### Post by p_quarles on 2007-09-18
Debian has been around a lot longer, and continues to have a larger selection of packages in the repositories than Ubuntu does. Generally speaking, you can still get all of those packages as downloads. Ubuntu has a very large userbase and a more active support forum, but generally speaking Debian's userbase is more technically adept. Debian is no less user-friendly, it's just tended to draw more of power user crowd.

Probably the biggest single difference is that Debian doesn't ship with a "restricted modules" package for the kernel. Thus, if you have any difficult hardware, it may be a bit more work to get everything to function. Debian also asks you to create a root password during installation. 

Apart from that, most of basic design underlying each system is pretty much the same. Ubuntu made some modifications to the administrative interfaces, but apart from these things Ubuntu is basically a version of Debian that aims to be friendly to newcomers.

---

### Post by Bachstelze on 2007-09-18
Moved to Other OS Talk.

---

### Post by angryfirelord on 2007-09-21
Debian is a more customizable distribution. It puts effort on the free vs. non-free software and tries to be the "one solution for every problem" distro, which I think is great. 

The problem is the updates for packages. Ubuntu tries to give you a frozen, but up-to-date system and every 6 months, Ubuntu takes a snapshot of Sid and makes it more stable. It's good because the packages don't change, but you have to make a big upgrade or do a re-install every 6 months if you want the newest packages.

Even if you don't use Debian, I recommend that every Ubuntu user should at least try it because the knowledge that you learn on one carries over to the other.

---

### Post by mojoman on 2007-10-18
I wouldn't call Ubuntu a fork from Debian. Ubuntu is made from snapshots of the Debian testing respository. So, it's not like there is a point in time where Ubuntu is developed independently from Debian. Rather, Ubuntu is based on Debian. To put it bluntly, without Debian, Ubuntu dies. Without Ubuntu, Debian would probably get a few less users (people who migrate from Ubuntu to Debian) but I'd say they'd hardly notice any difference at all. 

A lot of people call Ubuntu more user friendly but I disagree. Ubuntu is easier to use, I agree on that one, and a lot of stuff works out of the box as well but for something to be user friendly, IMHO, it requires customization and I believe Debian got the upper hand there.

Two really big arguments for Debian is that you have a lot more packages available and it's more stable. This is obviously true about Debian stable (currently Etch) but I'd say it's also true of Debian Testing (currently Lenny). Debian testing is also more up to date than Ubuntu. 

Two really big arguments for Ubuntu is that a lot of stuff just works, even restricted stuff, so you don't have to compile it yourself and it got, in linux terms, a huge user base with a very active forum so you'll get support very fast. 

So, what you'll use will pretty much depend on what you need, what you want to do and can do rather than which is the best distro.

/mojoman

---

### Post by kellemes on 2007-10-18
> **eoghanmurray said:**
> Ubuntu's debian based, hence the *.deb package installers. It has a better user base and more users, and has backing from DELL, and it's better supported I think, so I contrast that it's better.

There is no backing from DELL at all, they only need to sell hardware fast or they die.. Ubuntu is backing DELL.
There are about 360 distro's out there, DELL can replace Ubuntu with many others any minute. And I'm sure they will..

More users? Based on what? And what users are you talking about? Are you also looking at the use of Debian in the enterprise? You have any idea the important role Debian plays in the servermarket?
Trust me, if Ubuntu dies today absolutely nothing will change in GNU/Linux except for a couple of thousand of n00bs desperately looking for there automatic-update button. All the others will choose another distro (probably Debian) and continue like nothing has happened.

---

### Post by mojoman on 2007-10-18
> **kellemes said:**
> More users? Based on what? And what users are you talking about? Are you also looking at the use of Debian in the enterprise? You have any idea the important role Debian plays in the servermarket?
Trust me, if Ubuntu dies today absolutely nothing will change in GNU/Linux except for a couple of thousand of n00bs desperately looking for there automatic-update button. All the others will choose another distro (probably Debian) and continue like nothing has happened.

When it comes to servers Debian clearly has a lot more users than Ubuntu but when it comes to desktops my impression is that Ubuntu has quite a lot more users than Debian.

---

### Post by tturrisi on 2007-10-18
my 2 cents:
debian is Debian and Ubuntu is Ubuntu.  Ubuntu is a "branded" Debian built from a Debian unstable kernel snapshot.  And Ubunti packages are Debian packages mostly, some modified to fit the Ubuntu btranding and hacks.

Ubunti is great for the first time linux user or for thise that want a quick install as close to "it just works" as you can get in Linux.   But Ubuntu is NOT for production servers and is NOT for office environments that require day to day no-glitches stability.

I've used both.  I still have  Debian Woody server w/ my business database that has been running non stop for 4 years, except during power outages from storms.  I have not manually booted that more than a half dozen times in 4 years.  It just keeps ticking and ticking and ticking...

If you want to learn the ins and outs of Linux, installl Debian stable (base system) and build up from there, installing only the software you want.  In two montes, after you've figured out most of the basics, you'll get bored and wipe the disk and install Debian testing or unstable, and these you'll never get bored with!

---

### Post by p_quarles on 2007-10-18
@tturisi: Yeah, the uptime on Debian stable is truly ridiculous. I'm running a home server with it, on an old POS Dell, and it has yet to blink at me.

Btw, if your database server is at all open to the internet, I would suggest upgrading to Etch. Woody is no longer getting any security updates, so it's fine for an intranet-only machine, but is somewhat vulnerable if it's accessible from the outside.

---

### Post by kellemes on 2007-10-18
> **mojoman said:**
> When it comes to servers Debian clearly has a lot more users than Ubuntu but when it comes to desktops my impression is that Ubuntu has quite a lot more users than Debian.

Could be.. don't know actually.. just be carefull not to base usernumbers on silly things like DistroWatch-clicks or the number of responses in the forums.. **or** the amount of hits you get from [http://www.google.nl/search?q=ubuntu](http://www.google.nl/search?q=ubuntu)

Also I feel the majority of Debian-users have much more knolledge of there system and GNU/Linux in general as there Ubuntu counterparts.
Maybe I'm trying to say Debian-users will less likely leave there beloved Debian as Ubuntu-users leave there's. It's the attitude of "if it doesn't **just** works it sucks!".
And so I'm sure Debian will be alive and kicking in 30 years from now, Ubuntu? I'm not so sure..:popcorn:

---

### Post by mojoman on 2007-10-18
> **kellemes said:**
> Could be.. don't know actually.. just be carefull not to base usernumbers on silly things like DistroWatch-clicks or the number of responses in the forums.. **or** the amount of hits you get from [http://www.google.nl/search?q=ubuntu](http://www.google.nl/search?q=ubuntu)

Also I feel the majority of Debian-users have much more knolledge of there system and GNU/Linux in general as there Ubuntu counterparts.
Maybe I'm trying to say Debian-users will less likely leave there beloved Debian as Ubuntu-users leave there's. It's the attitude of "if it doesn't **just** works it sucks!".
And so I'm sure Debian will be alive and kicking in 30 years from now, Ubuntu? I'm not so sure..:popcorn:

I don't base it on distrowatch or google and also note that I wasn't betting my last dollar on the statement that Ubuntu powers more desktops than Debian (though I would bet my last dollar on the statement that Debian power more servers than Ubuntu). I guess I mostly got this impression from forums and the number of people that are active on them. Granted, it's certainly not a scientific method but then again, I didn't say it was.

As for the average Debian user being more knowledgeable than the average Ubuntu user, I sure agree with you on that one. Fact is, I'd bet my last dollar on it. :wink:

30 years? Long time...Remember, even Debian is only 14 years old as it is but if I'd be giving odds they'd be in Debian's favor.

/mojoman

---

### Post by kellemes on 2007-10-18
> **mojoman said:**
> 
30 years? Long time...Remember, even Debian is only 14 years old as it is but if I'd be giving odds they'd be in Debian's favor.

/mojoman

Just guessing.. :)
Asnswering the question of OP.. I think Debian is a great choice for the long run, it had a long time to mature, this includes it's userbase I guess..
If you wanne be part of the bleeding-edge of tuxing Debian is possibel but not  the number one choice. Ubuntu seems to be doing fine in this area.

@mojoman: I didn't mean stuff personally.. it was just a general rant I guess.. :) I have that sometimes..

---

### Post by mojoman on 2007-10-19
> **kellemes said:**
> Just guessing.. :)
Asnswering the question of OP.. I think Debian is a great choice for the long run, it had a long time to mature, this includes it's userbase I guess..
If you wanne be part of the bleeding-edge of tuxing Debian is possibel but not  the number one choice. Ubuntu seems to be doing fine in this area.

@mojoman: I didn't mean stuff personally.. it was just a general rant I guess.. :) I have that sometimes..

No worries, I didn't take it personally, I just wanted to make clear what my view were on how the user base of the different distros looked like (which maybe was a bit off topic, sorry...)

When it comes to Debian vs Ubuntu, I'm using both and I'll probably keep doing it for a long time.

/mojoman

---

### Post by tturrisi on 2007-10-19
> **p_quarles said:**
> @tturisi: Yeah, the uptime on Debian stable is truly ridiculous. I'm running a home server with it, on an old POS Dell, and it has yet to blink at me.

Btw, if your database server is at all open to the internet, I would suggest upgrading to Etch. Woody is no longer getting any security updates, so it's fine for an intranet-only machine, but is somewhat vulnerable if it's accessible from the outside.

The Woody server is intranet only.  It has Internet access, and apache listens on port 80, but my isp filters port 80 connections and the router also prohibits unsolicied requests for port access from the wan.  I have no port-forwarding rules for that server.

My Etch server is open to the wan via uncommon ports for apache, mysql, ssh and phpmyadmin.

BTW, the Woody server is a 1998 Compaq Presarion celeron 333 w/ 384 ram and an additional hd for /home.  It's taken at least 40 power surges since then, many many cold resets, been banged around, bumped, used regularly, and still won't die.  The bios is set to auto-reboot on power failure, thus I have not had to login in many years!  Updating this box to Etch would break my php-mysql scripts.

---

