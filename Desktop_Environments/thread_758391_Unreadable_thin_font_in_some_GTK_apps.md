---
title: "Unreadable thin font in some GTK apps?"
date: 2008-04-17
forum: Desktop Environments
---

### Post by chmmr on 2008-04-17
I just installed the latest version of Google Earth, and was dismayed to see that a bug that's always afflicted XMMS on my system:

[IMG]http://img238.imageshack.us/img238/3852/screenshotum8.png[/IMG]

has now spread to Google Earth:

[IMG]http://img168.imageshack.us/img168/3504/screenshot1sw1.png[/IMG]

Any idea what could be causing this?  Obviously this isn't the font I've specified in my Appearances settings (see the nice font in the titlebar for the expected look).  I looked in my .gtk* files for any weird config stuff, but it's totally standard.  Nothing weird in my xorg.conf font settings either.

---

### Post by chmmr on 2008-04-27
Just upgraded to Hardy.  XMMS has been removed from the repos(?), so that problem no longer applies.  Google Earth still looks bad.  I dug up this on their newsgroup, which is about a 50% fix for the problem:

[http://groups.google.com/group/earth-linux/browse_thread/thread/dd32d0436741d005/47990e6cc9a0a163?lnk=raot#47990e6cc9a0a163](http://groups.google.com/group/earth-linux/browse_thread/thread/dd32d0436741d005/47990e6cc9a0a163?lnk=raot#47990e6cc9a0a163)

I can make the fonts larger, but they're still squashed horribly.  Regardless I think it's a GE-specific issue rather than an Ubuntu one, so I'll follow it up there.  Just wanted to post the resolution here for future searchers.

---

### Post by larson0699 on 2008-05-26
Bump.

I have searched up and down for solutions to this with little resolve.

I use PCLinuxOS 2008 "MiniMe" which is more or less an intermediate release, a small taste of the upcoming full build. It uses KDE3 by default, which--for the sake of Qt versus GTK+ interface--I prefer greatly. Naturally, it comes with only as much GTK stuff as necessary to run Synaptic, though that's GTK2, and thus unaffected by this ugly font problem.

I registered on their forums a few minutes ago, but with them, all new users must be manually approved by the admins before getting permission to post. No such problem here ;-) and it's great to finally find this issue replicated elsewhere instead of posting new. (You learn that with any Linux problem, there's always someone who discovered it first...)

To business:
chmmr nailed it by citing the two apps we commonly use (xmms, GE) though I wonder if all the right configuration files were in place had he not been using GNOME (no such thing as kubuntu/xubuntu forums... no telling)

I have only gathered pieces of the big puzzle, mostly revolving around incorrect bytecode (borked freetype2? utf8 locale rather than iso8859-1?) and the .gtkrc file, and even then, some said to make a ".gtkrc.mine" file in /home/<username> while others suggested checking inside of /etc/gtk/. What a mess; frankly don't know where to start.

I see that this still isn't a dead issue with chmmr (just not as evident in xmms's absence) and while it may be suggested I consult with PCLOS forums, I find to be a universal cause-and-effect in any Linux distro, and I am more than familiar with ubuntu--it's just not my preference. I believe the majority (ubuntu) may be the most responsive; being able to post immediately is a good start to progress.

Side: I used hardy for a week and also noticed no xmms, even having enabled universe, multiverse, partner, backports, everything. No xmms. There's an xmms2 (eww, reminds me of the azureus -> vuze transition) and audacious which is *sort of* similar but not all there. I would suggest make/installing xmms source since nothing compares.

It may help to know the specifics of the running platform for troubleshooting (IIRC PCLOS Gnome Edition gave me no trouble except for GNOME :lolflag:):
* PCLinuxOS 2008 "MiniMe", dist-upgraded to testing (no change), kernel 2.6.22.15.tex2
* KDE 3.5.9 + GTK2 apps all over (firefox, pidgin..), unrelated
* NVIDIA GeForce3 Ti200 with nvidia driver 96.43.05, xorg 1.4.0.90 (X11R7.3)
* compiz-fusion 0.7.4 + emerald, unrelated

Also attaching screenshot:

---

