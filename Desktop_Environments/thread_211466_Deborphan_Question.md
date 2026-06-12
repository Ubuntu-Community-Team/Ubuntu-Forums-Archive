---
title: "Deborphan Question"
date: 2006-07-08
forum: Desktop Environments
---

### Post by Thund3rstruck on 2006-07-08
I'm curious at to why these gstreamer packages keep showing up as orphans by the bebian packager. I try to keep my system clean by running 

```

sudo apt-get -y remove `deborphan`

```

to remove un-necessary orphan (unused) packages weekly. These packages keep showing up as orphans and keep getting removed and then mplayer no longer works. 

```

$ deborphan
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-gl
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly-multiverse

```

---

### Post by Thund3rstruck on 2006-07-08
anyone...

---

### Post by aysiu on 2006-07-08
An orphan is a package on which no other packages depend.

No other packages depend on those gstreamer ones.

It doesn't mean they have to be removed.

---

### Post by Thund3rstruck on 2006-07-08
Thanks for the reply,

 So even though mplayer will not work without these packages, mplayer does not 'depend' on these packages? 

 In this case, I suppose I will have to rethink the strategy of using deborphan as a basis for cleaning the system.

---

### Post by Dr. Nick on 2006-07-08
Mplayer doenst *need* them packages to run, therfore it doent depend on them so deborphan sees this. While actually if you want to view certain formats in mplayer those are probably necessary so you *need* them.

---

### Post by aysiu on 2006-07-08
MPlayer does work. It just won't play the formats *you* want to play.

A missing dependency usually means you can't even *install* the package in question, and clearly you can install MPlayer without the *gstreamer* packages.

---

### Post by Thund3rstruck on 2006-07-08
So is there a way to force mplayer to *depend* on these packages so deborphan doesn't indentify them as orphans?

---

### Post by aysiu on 2006-07-08
No. You could conceivably (not that I know how to do this, but I believe it can be done) create a metapackage that depends on both MPlayer *and* the plugins.

That's probably more trouble than it's worth, though. Why not just... not remove those packages? Just because they're called "orphans" doesn't mean you *have* to remove them.

---

### Post by Dr. Nick on 2006-07-08
try this

** sudo  deborphan --add-keep *packagename***

I got that from the manual page

**man deboprhan** has a few things talking about how to do it
> 
   KEEP FILE MANAGEMENT
       -A, --add-keep PKG1...PKGn
              Add packages to the list of  packages  which  are  never  to  be
              reported,  regardless of their state. You may specify &#8217;-&#8217; to use
              standard input. Note that package names are case-sensitive.

       -R, --del-keep PKG1...PKGn
              Remove packages from the list of packages which are never to  be
              reported.   You may specify &#8217;-&#8217; to use standard input.  If there
              are no dependencies for this  package  next  time  deborphan  is
              invoked, it will be reported again.

       -L, --list-keep
              Show the list of packages that are being kept back.

       -Z, --zero-keep
              Purge  the entire list of packages that are being kept back. The
              only option possible in combination with this option is -A.

       -k, --keep-file=FILE
              Use FILE to store the list of kept-back packages.

---

### Post by frenkel on 2006-07-08
Or try running keepedit -a

---

### Post by Thund3rstruck on 2006-07-08
@Dr Nick,

 Thanks.. that worked like a charm. I do appreciate it. 

> 
Why not just... not remove those packages? Just because they're called "orphans" doesn't mean you have to remove them.

The point here is automation. By "not removing" these packages means that I must move from an automated systems management stance to a manual administration stance. I try to not do anything manually, most especially anything that runs on any type of schedule.

---

### Post by aysiu on 2006-07-08
You run *deborphan* on a schedule?

Why not just use *aptitude*? [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by Dr. Nick on 2006-07-08
yeah, aptitude is good, especially for programs you are unsure you will keep, makes complete removal much easier

You can also add a orphanerd fllter to synaptic, if you use apt-get

Open Synaptic.
Settings Menu -> Filters -> Click the "new" button and set the name, then unselect everything but "orphaned". 

The new filter will appear under "custom" in the bottom corner of the main windows with the other 4 buttons

---

### Post by Thund3rstruck on 2006-07-08
ok great, I have never actually used Synaptic, I've always used apt for everything. 

Right now, yea, I run a cron job once a week that removes all orphans. Thanks for the tips!

---

### Post by Dr. Nick on 2006-07-08
all synaptic does is launch apt-get from a gui.

aptitude is used similary as apt-get from the command line, its just alot better at removing dependencies after a prog is removed. Look at aysiu's link

---

### Post by Thund3rstruck on 2006-07-09
Ahh.. ok, I see. All this time I thought Synaptic and Aptitude were synonyms for one another. I did not realise they were seperate programs. 

Thanks for that tip. I'll start using Aptitude instead of apt-get

---

