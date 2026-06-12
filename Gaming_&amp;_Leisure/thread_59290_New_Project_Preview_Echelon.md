---
title: "New Project Preview: Echelon"
date: 2005-08-23
forum: Gaming &amp; Leisure
---

### Post by dcraven on 2005-08-23
Echelon is a GNOME applet to be used for monitoring a favorite set of game servers. Any game that is supported by qstat can be monitored by Echelon (eventually :)). It also keeps track of a "friends" list and will notify you via the icon when one or more of them is online. You can easily get various up to date server statistics such as the number of players, the current map, your current ping, and a list of players including their pings and scores.

We made our first release public last night, and I think this version is quite strong and stable. Testers are appreciated, and any bug reports, comments, or suggestions can be sent to [our mailing list](http://lists.sourceforge.net/lists/listinfo/echelon-applet-users/). Membership to the list is not necessary though, you can just send an email to [email]echelon-applet-users@lists.sourceforge.net[/email] and it'll get to us.

The project's website is at [http://echelon-applet.sourceforge.net](http://echelon-applet.sourceforge.net) . There are, of course, a few screenshots there too.

The gamer's forum seemed like an appropriate place to announce this. Sorry if this appears as spam :)

Thanks,
~djc

---

### Post by GameGod on 2005-08-25
Sweet, this is incredibly useful, and the GUI is simple and easy to use!!

Thanks! :)

---

### Post by dcraven on 2005-09-01
Can you guys help me out with some stuff here? :)

I'm trying to add the ability to run the game and join a server right from Echelon. The problem is that I need to know the basic structure of the command line for games that qstat supports (at least the more popular ones).

The only games (so it seems) I've played extensively are Quake based games, and hence those are the only ones I'm familiar with. These include Q1, Q2, Q3, ET, RTCW, Doom3. I'm having difficulty finding the appropriate command lines from other popular games like Unreal Tournament, UT2003, UT2004, America's Army etc etc..

Essentially, I'd like the equivalent to this (in Quake syntax):
```
quake3 +set fs_game [MODNAME] +connect [SERVER]
```

Any other fancy stuff can be added from a proposed dialog, per server. Maybe some popular *and safe* default options wouldn't hurt, but not necessary. I've tried Googling for this stuff but the web is such a mess and cesspool of misinformation that it's impossible to find what I need.

I'm hoping that there are some UT and AA (and whatever else, Halflife?) fans out there that read this thread and can help out. At least a relatively reliable source online would be nice :)

Cheers,
~djc

---

### Post by crane on 2005-09-03
I tried to install with dpkg but and istall had errors:

dpkg: dependency problems prevent configuration of echelon:
 echelon depends on qstat; however:
  Package qstat is not installed.
dpkg: error processing echelon (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 echelon

oh and qstat is installed.

---

### Post by dcraven on 2005-09-04
Well isn't that interesting... What is the output of the following look like? 
```
apt-cache policy qstat
```

Installed or not, it seems apt doesn't think it is. At least when asked that way :). I'm curios to see what the above command says because that's pretty definitive about whether apt thinks it's installed or not.

I'm hoping breezy uninstalled it when you weren't looking during some upgrade, and that all you need to do is reinstall and everything will be fixed ;P. If you installed qstat via source, then to my knowledge apt would not be aware of its presence. One solution in this case is to install qstat through apt, the install Echelon through dpkg. This might overwrite your qstat installation depending on what prefix you installed the source to. Another solution is to install Echelon via the source tarball.

I'd suggest the svn version of Echelon, but it's a little touch and go at the moment (unstable?). It has a bunch of changes such as threaded polling, game launching (some games), and the friends list is built into the main window instead of being its own window. But like I said, it is sometimes broken.

Cheers,
~djc

---

