---
title: "Lucid's FCEUX"
date: 2011-11-17
forum: Emulators
---

### Post by desktorp on 2011-11-17
A friend of mine is trying Ubuntu, but I am having some trouble helping him with the version of FCEUX (the NES emulator) that is provided by Lucid's repository.  Lucid provides version 1.2.2, which appears to be broken; the input config is messed up - appears to be an old bug.  Everything Maverick and up comes with "2.1.4a" and is labelled as a repack.

I have tested 2.1.4 and the bug is no longer present, so I am eager to get him upgraded to something newer than what Lucid is offering.  I am reluctant to have him build from the source (2.1.5, as indicated by the project's homepage) because I don't want him to jack up something delicate, like pulse and/or some big meta package.  He's still very new to the whole thing and he's been really brave so far, but I don't know how far his patience will go if I have to end up walking him through reinstalling the whole OS.  (because reinstalling would be an easier thing to explain than fixing some catastrophic problem that I obviously, barely understand)

I am pretty sure that no PPA or .deb exists that forces Lucid to upgrade FCEUX to 2.1.4, like its successors already have.. or 2.1.5 for that matter.

I am fairly hosed on this one.  The way I see it, I either have to bite the bullet and walk him through the use of the install script (which *seems* simple enough) and just tread carefully.. or walk him through upgrading to a newer release, which is ultimately the plan, anyway.  I just wasn't planning on talking about OS upgrade/fresh installation for another few months. (12.04)

I don't want to get in to the reasons why I chose to set him up with 10.04 (LTS security blanket + Gnome2 + functional Silverlight :oops:) but I find it ridiculous that I'm feeling so up against the wall because of something as silly as a broken config dialog in an emulator.

Am I overlooking a PPA or binary installer for a newer version of FCEUX?  If I have him run the install script and it says it wants to remove a bunch of critical junk, aside from hitting N for NOOOOOO! is there anything I can do to force it along?

Here's me about FCEUX: :confused:

---

### Post by punkrockguy318 on 2012-01-26
> **desktorp said:**
> A friend of mine is trying Ubuntu, but I am having some trouble helping him with the version of FCEUX (the NES emulator) that is provided by Lucid's repository.  Lucid provides version 1.2.2, which appears to be broken; the input config is messed up - appears to be an old bug.  Everything Maverick and up comes with "2.1.4a" and is labelled as a repack.

I have tested 2.1.4 and the bug is no longer present, so I am eager to get him upgraded to something newer than what Lucid is offering.  I am reluctant to have him build from the source (2.1.5, as indicated by the project's homepage) because I don't want him to jack up something delicate, like pulse and/or some big meta package.  He's still very new to the whole thing and he's been really brave so far, but I don't know how far his patience will go if I have to end up walking him through reinstalling the whole OS.  (because reinstalling would be an easier thing to explain than fixing some catastrophic problem that I obviously, barely understand)

I am pretty sure that no PPA or .deb exists that forces Lucid to upgrade FCEUX to 2.1.4, like its successors already have.. or 2.1.5 for that matter.

I am fairly hosed on this one.  The way I see it, I either have to bite the bullet and walk him through the use of the install script (which *seems* simple enough) and just tread carefully.. or walk him through upgrading to a newer release, which is ultimately the plan, anyway.  I just wasn't planning on talking about OS upgrade/fresh installation for another few months. (12.04)

I don't want to get in to the reasons why I chose to set him up with 10.04 (LTS security blanket + Gnome2 + functional Silverlight :oops:) but I find it ridiculous that I'm feeling so up against the wall because of something as silly as a broken config dialog in an emulator.

Am I overlooking a PPA or binary installer for a newer version of FCEUX?  If I have him run the install script and it says it wants to remove a bunch of critical junk, aside from hitting N for NOOOOOO! is there anything I can do to force it along?

Here's me about FCEUX: :confused:

I don't believe that there is a PPA of fceux 2.1.5 for Ubuntu 10.04 and it is not in backports that I know of.

Your best bet if you would like to continue running LTS would be to compile fceux from source.  I wrote this which outlines the process of installing fceux form source:

[http://xannode.com/blog/?p=14](http://xannode.com/blog/?p=14)

Alternatively, if you search the forums there is a thread with a howto that should be relevant 

[http://ubuntuforums.org/showthread.php?t=971455](http://ubuntuforums.org/showthread.php?t=971455)

There are way too many distributions for the fceux SDL developers (me and a few others) to release PPAs for every ubuntu version.  If you'd like to run the latest fceux (which has resolved a lot of issues), compile from source.

---

