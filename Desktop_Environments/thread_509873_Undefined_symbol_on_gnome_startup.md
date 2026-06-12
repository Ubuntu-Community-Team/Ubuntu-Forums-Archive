---
title: "Undefined symbol on gnome startup"
date: 2007-07-25
forum: Desktop Environments
---

### Post by BotLobsta on 2007-07-25
On startup, my X server starts (the nvidia splash screen comes up) and then I am left hanging with a busy mouse cursor on a black background.  Whenever I try to start X myself afterwards, I get the following error:

symbol lookup error: /usr/lib/libgdk-x11-2.0.so.0: undefined symbol: g_once_init_enter_impl

Im assuming that means the library I have is missing that routine, but does anyone know where I could find a working library or some other way to fix this problem?

Thanks

P.S. Im sorry if the formatting on this post is horrible.  Ive never posted using lynx before.

---

### Post by kidders on 2007-07-27
Hi there,

Nice work posting with Lynx! :-)

The error you mentioned is unusual on binary distros like Ubuntu. It's suggestive of a reverse dependency violation. Imagine...

[COLOR=Navy]**Package A** -> [/COLOR][SIZE=1][COLOR=Navy]depends on[/COLOR][/SIZE][COLOR=Navy] -> **Package B** -> [/COLOR][SIZE=1][COLOR=Navy]depends on[/COLOR][/SIZE][COLOR=Navy] -> **Package C**
[/COLOR]
Package B would (obviously) be aware of its own dependencies (ie Package C), and could take appropriate measures to see that they're not broken during the course of a software update, or similar. Conversely, there's not often a convenient way of establishing what depends *on* it ... so making misguided changes to Package B would break Package A, and Ubuntu may make no attempt to stop you, in accordance with Linux's cardinal rule "He who types **sudo** knoweth what he's doing" hehe.

My suggestions are:
[LIST]
[*]If this error is the likely product of a very recent system update, wait a little while, and see if anyone else complains about it, or files a bug report. Given the nature of this particular problem, you won't have to wait long!
[*]If not, check for relevant bug reports anyway, to eliminate the possibility that the error isn't your fault.
[*]Check for filesystem corruption. It's at least *possible* that the error is the result of an unclean shutdown, or damage caused to your filesystem in some other way.[/LIST]Assuming this *isn't* a bug in Ubuntu, or filesystem damage...
[LIST]
[*]Have you been doing odd things with your package manager, like forcing on software that's incompatible with your system architecture, not designed for the specific version of Ubuntu you're running, or in conflict with other installed applications?
[*]Was the problematic system library installed by a package you compiled from source, or installed without Ubuntu's package manager's help? (Note that installing things without involving your package manager is not recommended, unless you know what you're doing.)[/LIST]Essentially, my suspicion is that you've done something unwise that isn't recommended. One way of correcting the problem is to identify installed packages from Ubuntu's _official_ software repos that contain the damaged library, and reinstall one of them, to replace the library with a version consistent with the rest of your system. The downside is that this action may break the uninstaller belonging to the application that put the faulty library there in the first place, making it more difficult to clean up its mess, later on. Any such application may also start segfaulting, moaning about messed up libraries, or crashing your system.

I hope that helps. Even though the solution to your problem is probably a simple reinstall of something containing  /usr/lib/libgdk-x11-2.0.so.0, I would encourage you to try to identify the original cause first, in case anything similar crops up in the future. If you feel that whatever's gone wrong shouldn't have, feel free to submit a bug report on the issue for further investigation.

---

### Post by geppy on 2007-07-29
BotLobsta, I've had the exact same issue crop up.  It happened a couple of days ago.  I didn't boot back into Ubuntu (until now) because I was rather frustrated.  Now I've found the error message (which leads me to your post), and it is completely useless.  I did not upgrade anything between my last successful boot and first unsucessful boot.  There's no reason this should have cropped up.  I did have a failed attempt to "Hibernate", which I assume is the cause for my woes.  I'm also posting from lynx, which is a rather poor excuse for a web browser.

Anyway, not sure what's to be done, as no one is owning up to the issue: `dpkg -l /usr/lib/libgdk-x11-2.0.so.0` doesn't return any results (the same for the file that it points to, "blahblahblah.1106.0".

Also, apt-cache search doesn't return any results for libgdk; it only returns libgdk-pixbuf.  Installing these packages, predictably, does nothing useful.

---

### Post by geppy on 2007-07-29
Keeping in mind what kidders said, I fscked my root filesystem to no avail.

---

### Post by geppy on 2007-07-29
Okay, I managed to get it working.  I issued a "simple":
[b]sudo apt-get install --reinstall `dpkg -l | grep libgtk | cut -f 2 -d " "`[\b]

What that does is first evaluate the expression bounded by accent characters, which lists all of the installed packages, prunes the list to only contain ones that contain the string "libgtk" and then, my favorite part, selects the third character group (with character groups delimited by the space character (" ")) because dpkg -l gives you the completely useless output format:
[I]. . . 
ii  libgtksourceview-dev                       1.8.5-1                                    development files for the GTK+ syntax highli
ii  libgtksourceview1.0-0                      1.8.5-1                                    shared libraries for the GTK+ syntax highlig
ii  libgtkspell0                               2.0.10-3                                   a spell-checking addon for GTK's TextView wi
. . .[/I]

After evaluating that portion of the command it echoes it at that point and then runs the whole bit, which reinstalls everything listed.

By the way, Lobsta, I thought I'd tell you the same thing my mother has always told me: never trust a Gentoo user, especially a self-professed one.

---

### Post by kidders on 2007-07-29
> **geppy said:**
> Anyway, not sure what's to be done, as no one is owning up to the issue: `dpkg -l /usr/lib/libgdk-x11-2.0.so.0` doesn't return any resultsYou wouldn't expect it to. "/usr/lib/libgdk-x11-2.0.so.0" is unlikely to be part of a package name.

> **geppy said:**
> By the way, Lobsta, I thought I'd tell you the same thing my mother has always told me: never trust a Gentoo userLol.

This sort of error crops up every now and then in Gentoo. It really shouldn't happen in Ubuntu though ... so it's worth pinning down the cause before destroying the evidence! Strictly speaking, reinstalling *all* packages with "libgtk" in the name isn't necessary, but it can't do any harm. :-)

---

### Post by BotLobsta on 2007-07-31
So I thought I had fixed this little problem by reinstalling an older version of libgtk2.0-0, the package from which this library (and the 2 others which I have found to give this same error message libgtk-x11-2.0.s0.0 and libgdk-pixbuf-2.0.so.0) come from.  The actual libraries that work end in .1000.11.  (the .0 files are just links).  This solved enough of my problems that xfce works now so this post comes from firefox.

However, I still occasionally get that error message but it doesnt show what library it comes from.  That is until today when I tried to start my gnome-terminal and it said that the library libvte.so.9 was broken.  So im guessing that there is some other library that all of these are dependent upon that doesnt have this method defined.  I dont know what that would be because my system is almost completely up to date with upgrades and I havent compiled anything of my own that would affect this.  The only package that isnt the latest is gaim because I dont like the look of pidgin so I keep it from upgrading and firefox which somehow depends on the latest version of gaim.  (I run firefox 3.0 alphas so I dont use that package).  Does anyone know what library would have this mysterious function defined?  I can keep finding older versions of these broken libraries but its getting annoying.

---

### Post by geppy on 2007-08-18
> **kidders said:**
> You wouldn't expect it to. "/usr/lib/libgdk-x11-2.0.so.0" is unlikely to be part of a package name.

Ah, yes, I meant 'dpkg -S'.

[QUOTE=bash]geppy@geppy-desktop:~$ dpkg -S /usr/lib/libgdk-x11-2.0.so.0
libgtk2.0-0: /usr/lib/libgdk-x11-2.0.so.0[/quote]

---

### Post by geppy on 2007-08-18
BotLobsta,

I don't believe that the library package is actually missing the definition: it's probably an issue with the installation that you have.  I would try running what I ran (to reinstall GTK+).

---

