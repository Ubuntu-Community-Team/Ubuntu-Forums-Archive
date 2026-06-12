---
title: "Thinking about going back to Gentoo... why shouldn't I?"
date: 2006-09-11
forum: Desktop Environments
---

### Post by diabx0r on 2006-09-11
I have been away from Linux for about a year and I used Gentoo religiously before I went to Windows. 

I recently installed Ubuntu and like it a lot, but something in me misses Gentoo.

Is Gentoo still pretty decent nowadays?

Is Ubuntu superior now?

Thanks!

This isn't meant to turn into a war between distros thread or anything.  I am sincerely interested in the proc and cons.

---

### Post by Lord Illidan on 2006-09-11
If you feel the need to reuse Gentoo, why not? We don't want to keep you here besides your will..hehe!

---

### Post by diabx0r on 2006-09-11
I hear ya, man.

I am mainly curious as to how Gentoo is being kept up and such.

Are they still working as hard as they did a year ago on keeping emerge up to date and such?

How does it compare in it's present state to Ubuntu?

I'm sure someone here uses both. :P

---

### Post by dmizer on 2006-09-11
attempting to install gentoo was the most painfully unproductive 2 days i've ever spent. lol.

though i hear that once you have it installed, it's sweet.  i might try again some time for a headless server.

---

### Post by kickaha on 2006-09-11
The gentoo project has a forum, in which you can read what the gentoo users think of the distro.

You will probably get more appropriate feedback about the distro from the people who use it than you will here.

---

### Post by diabx0r on 2006-09-11
Unbiased opinions are a wonderful thing... :P

---

### Post by Kalif on 2006-11-16
Since I have been running Gentoo for more than 5 years, and Ubuntu for the last few years I have a few cents worth of advice for you.

Both distros got great communities which is important when you run into trouble. But, without wanting to start a flame war, if you are after configurability Gentoo wins. Even with their new automated installation tool, you will quite likely run into "interesting" configuration problems. Like selecting packages in your make.conf that will not build cleanly until your system is fully configured; this particular problem is either solved by reinstalling with a less demanding make.conf or by reverting to a manual install.
Then when the system has been "installed" it usually takes quite some tweaking before both graphics and sound is working, in most cases the process is very well documented but even if every single step is written down, it is easy to go astray.
For a server system, you may not have to bother with either X11 or sound and then all the configuration options can be very much the key to your success; in cases where a very particular set of applications are to work in harmony Gentoo will let you select everything in detail without to much complaints.

With Ubuntu you can install "server" and get a very basic system that can be tweaked and tuned in countless ways so configurability is not lacking. But the key to the success of Ubuntu is not its configurability but rather the fact that -almost- anyone can slam a CD into the player and get a working and even pretty system out of the deal without even trying to understand anything technical. Moreover, the installed system will have a very carefully chosen set of application installed that will be able to help most office workers to get through a full working day without problems.

If you are interested in cars, think of it like you where in the process of getting a new car, you can -for the same amount of money- either get a new car or a chassis and a large pile of components and set of constructing your own dream machine. In the end the later path _may_ give you a better car, but not without work.

With that said, Gentoo is still very well supported and documented and -personally- I prefer run it on most of
my servers even if I got one with debian and another one
with Ubuntu. On the desktop, though, Ubuntu is competing
with Windows and OS X rather than with Gentoo, at least
where I live 8-). But if you do not care for using neither
Gnome, KDE, or XFCE, then the bonus of getting a full working
desktop environment is plainly not there and then Gentoo
needs comparatively less configuration so it depends on
personality and requirements.

Another issue is the compilation thing, with Ubuntu you
will get precompiled binary packages for most everything.
In the Gentoo case you are supposed to be compiling,
almost, everything yourself. Even if you can get all
packages optimized for your particular CPU architecture,
building all your packages may take days even on a
quick system. Still judging this is hard, there is
seldom any reson for manually inspecting everything that
scrolls by while compiling the system. Ofcourse there
is more than CPU-optimization to compiling your own
system, you can easily chose if you are using features
like SSL, LDAP, and maildir, to me this is far more
valuable than the optimization.

Cheers, have fun with your computer regardless of which
operating system you prefer,
K.

---

### Post by Kalif on 2006-11-16
Hi again,

one more point, regarding the 2 days of time
waste as dmizer reported. With a pretty recent
and not too linux unfriendly system it should
be possible to set everything up (including
graphics and sound) if you go for the "stage3"
type install where most things are precompiled.


But even if everything goes well a full
recompilation is days of waiting; yes a newer
machine is faster but if you pay the price for
a fast machine, you do so because you are
demanding and then you usually demand more
than speed. Which -in most cases- increases
the number of packages needed to make
the system complete.

K.

---

### Post by WalmartSniperLX on 2006-11-16
What I have to say might not mean too much, but from what I remember with experimenting with gentoo, you can't really compare the 2 since they are pretty different.

I don't want to be bias but as far as my opinion I like Ubuntu more since I beleive an OS should just work, so I can get on the computer and do work. Gentoo requires a lot of work since you have to build packages and update/compile a lot. Ubuntu has a lot of package support, and things work right out of the box (like my volume controls on my laptop :D)

I barely used Gentoo for a week ](*,), but I would stay with Ubuntu (my opinion remember :P). It too can be customized just as much.

---

