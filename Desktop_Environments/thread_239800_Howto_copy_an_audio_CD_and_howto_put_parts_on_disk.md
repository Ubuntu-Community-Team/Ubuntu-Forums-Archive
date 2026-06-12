---
title: "Howto copy an audio CD? and howto put parts on disk?"
date: 2006-08-19
forum: Desktop Environments
---

### Post by kline on 2006-08-19
First, Gnomebaker is busted; it cannot find one of the reuired gnome libraries and I don't se it in the Synaptic list.  But GnomeBaker may not be what I want .  I want to copy an entire audio CD.  Is there a suite to do this?  [[[ It would be nice to have some  of this CD on my hard drive; is there a program to let me do this? ]]]

Gnome, KDE, or anything will be fine.  Here, I'm a complete newbie.


thanks up front for any clues!

---

### Post by ScottMorris on 2006-08-19
Sound Juicer can copy the Audio tracks to the hard drive in a compressed format.  Also if you copy the tracks as wave files then just burn another Audio CD then it will be about the same as the original.  Programs you could also try are [NeroLINUX]("http://ww2.nero.com/enu/NeroLINUX.html") or [k3b]("http://www.k3b.org/").  Both are excellent CD writing programmes. *Sound Juicer is installed with Ubuntu.*

---

### Post by murataht on 2006-08-19
k3b is a nice piece of software that can replace gnomebaker. so try it.
for rip some of the cd, try goobox. it can rip the audio to your harddisk.

---

### Post by kline on 2006-08-19
Thanks for your feedback.  I think I *will* use the KDE app; KDE is much nicer in lots of ways.  I used google to find xcdroast as a cd copier, but again ran into problems with missing gnome libraries.   This kind of stuff is driving me up the wall!  So yet another question is:: is there a way to install missing gnome [[ or other ]] libraries??

One thing I need is libgail.so.  Or, rather, locate finds it, by xcdroast doesn't see it.   The other one is libatk-bridge.so  that is MIA.    

[INDENT]
Gtk-WARNING **: Failed to load module "libgail.so": libgail.so: cannot open shared object file: No such file or directory

Gtk-WARNING **: Failed to load module "libatk-bridge.so": libatk-bridge.so: cannot open shared object file: No such file or directory

Suspended
localhost# bg
[1]    xcdroast &
localhost# locate libgail.so
/usr/lib/gtk-2.0/modules/libgail.so
localhost# lt `locate libgail.so`
-rw-r--r-- 1 root root 300544 Mar 13 10:30 /usr/lib/gtk-2.0/modules/libgail.so
localhost# lt `libatk-bridge.so`[/INDENT]


Comments on this  last bit will be much appreciated...

---

### Post by kline on 2006-08-19
Rats.  Synaptic won't install k3b.    "unrsolvable dependencies"...

---

### Post by ScottMorris on 2006-08-19
Try adding a Kubuntu repository.

**Edit:** Try *deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main*

---

### Post by quonsar on 2006-08-19
or you could just install the gstreamer .8 libraries then gnomebaker will work.

---

### Post by kline on 2006-08-20
> **quonsar said:**
> or you could just install the gstreamer .8 libraries then gnomebaker will work.

unfortunately, not all the 08 gstreamer files installed; same thing. GnomeBaker just hangs...

---

### Post by kline on 2006-08-20
> **ScottMorris said:**
> Try adding a Kubuntu repository.

**Edit:** Try *deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main*

Can you please explain what t do with dapper/main?  How I create the respoitory?

I've moved to the KDE manager and find that there is lots of basic config work to do to get to where my Gnome setup is.  I'd like to use both sets of tools, altho probably more of the KDE set than Gnome.  But from the Gnome desktop.   It seems that I've  manage to mess up lots of libraries and hose lots of dependencies too.  If there is an easy way of getting things straightened  out, I'm open to any suggestions!

---

### Post by jocheem67 on 2006-08-20
I'm a n00b too, but can answer yor question. Go to synaptic and edit your sources ( under preferences ). Here you can uncomment some of your sources and/or add new sources. Just look around in synaptic and you will find out how to do that. It's not difficult. Remember to update your sources after adding new sources.
This should help you with getting rid of this dependency error.

It's important to know that ubuntu comes with some closed sources due to copyright issues....it's easy to open them though through synaptic....

Further I recommend reading the ubuntu ( or kubuntu ) desktop guides. They're pretty illuminating for a n00b.....

---

### Post by ScottMorris on 2006-08-20
Your Dependency error may be because of what is needed is in the Universe or Multi-verse repositories.

> Can you please explain what t do with dapper/main? How I create the respoitory?


The dapper part tells that it is the dapper folder on the sever, the main tells it that it is the main repository, insead of universe, etc.

You would just add a custom repository where jocheem67 has pointed out.

---

### Post by kline on 2006-08-20
> **jocheem67 said:**
> I'm a n00b too, but can answer yor question. Go to synaptic and edit your sources ( under preferences ). Here you can uncomment some of your sources and/or add new sources. Just look around in synaptic and you will find out how to do that. It's not difficult. Remember to update your sources after adding new sources.
This should help you with getting rid of this dependency error.

It's important to know that ubuntu comes with some closed sources due to copyright issues....it's easy to open them though through synaptic....

Further I recommend reading the ubuntu ( or kubuntu ) desktop guides. They're pretty illuminating for a n00b.....[FONT="Times New Roman"]

Thanks for your pointers.  I got to "Preferences" via Settings and only see several
click-on headers, nothing to indicate sources.  I found a different preferences via
Settings -> "Repositories -> "Software Preferences".  This probably isn't what you mean, tho.  (One problem is that when I clickon "Apply" everything freezes up and I've got to kill -9 stuff and /bin/rm a lock in the /var/lib/dpkg directory.  In short, I'm going in circles.)


Further n00b insights much appreciated.  Or insights from anyone, for that matter![/FONT]

---

