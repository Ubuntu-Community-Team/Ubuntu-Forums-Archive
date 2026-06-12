---
title: "anyone else frustrated by lack of updated libs for 8.04?"
date: 2009-06-05
forum: General Help
---

### Post by logos34 on 2009-06-05
Gotta say, for an LTS release that has another year to go (+2 for support), I'm running into too many roadblocks compiling the latest versions of apps...So many unsatisfiable dependencies...Why aren't more updated libs backported to Hardy? 

(and even enabling proposed and unsupported backport updates in synaptic doesn't always yield the newest vers.) 

8.04 is the best, most stable release I can remember, yet a lot of the .deb pkg versions in the repos are ancient! I'm having to update by getting stuff through GetDebs website


any similar experiences?

---

### Post by Soul-Sing on 2009-06-05
yes, newest version of sun java....pfff. [COLOR="Red"]Update -13 was a major security update[/COLOR], hardy delivers no -13 update...I do not understand why. So i do most updates myself, but thats not the way it should be imo.

---

### Post by mcduck on 2009-06-05
That's how it is.

After release, program versions in Ubuntu are not supposed to be updated.Updates are provided only for security reasons and to fix serious bugs, never just to add new features. And quite often the security updates are even handled by patching current program version instead of packaging a new one.. Anything backported should be considered as nice extra, definitely not something you're supposed to expect to happen.

If you are not happy with using stable and tested program versions, Ubuntu probably isn't the distribution for you. Or at least you should update to latest Ubuntu releases.

(By the way, unless you are doing active package testing you shouldn't be using the proposed-repository. That's where packages are added for testers, after they are confirmed to work without issues they are always moved into backports repository. So you will get same programs week or two later but with smaller risk of things breaking by using the backports only.)

---

### Post by abhilashm86 on 2009-06-05
this is so bad, ubuntu told it'll support untill 2011 the updates, i hardly see 2 or 3 updates per week, how many of you think 8.04 is great?? 
its lot more stable, user friendly, updates should be given.........

---

### Post by abhilashm86 on 2009-06-05
> **logos34 said:**
> Gotta say, for an LTS release that has another year to go (+2 for support), I'm running into too many roadblocks compiling the latest versions of apps...So many unsatisfiable dependencies...Why aren't more updated libs backported to Hardy? 

(and even enabling proposed and unsupported backport updates in synaptic doesn't always yield the newest vers.) 

8.04 is the best, most stable release I can remember, yet a lot of the .deb pkg versions in the repos are ancient! I'm having to update by getting stuff through GetDebs website


any similar experiences?


i agree to your words, i just tried ubuntu 8.10, it was more of security and lot of problems, instant restart and once it got hanged......
but hardy heron is best i've seen, so smooth in performance............

---

### Post by Steelmourne on 2009-06-05
Why not try Jaunty. I always tend to update to the newest version of software. 6mths between OS releases is great. Keeps everything fresh.

---

### Post by mcduck on 2009-06-05
> **abhilashm86 said:**
> this is so bad, ubuntu told it'll support untill 2011 the updates, i hardly see 2 or 3 updates per week, how many of you think 8.04 is great?? 
its lot more stable, user friendly, updates should be given.........

Support doesn't mean the same as providing new program versions. It meas providing security updates.

---

### Post by logos34 on 2009-06-05
> **mcduck said:**
> That's how it is.

After release, program versions in Ubuntu are not supposed to be updated.Updates are provided only for security reasons and to fix serious bugs, never just to add new features. And quite often the security updates are even handled by patching current program version instead of packaging a new one.. Anything backported should be considered as nice extra, definitely not something you're supposed to expect to happen.

If you are not happy with using stable and tested program versions, Ubuntu probably isn't the distribution for you. Or at least you should update to latest Ubuntu releases.

(By the way, unless you are doing active package testing you shouldn't be using the proposed-repository. That's where packages are added for testers, after they are confirmed to work without issues they are always moved into backports repository. So you will get same programs week or two later but with smaller risk of things breaking by using the backports only.)

thanks for backport vs. proposed repo tip...yeah, maybe I should be running debian sid or the like!  But I like ubuntu too much to ever leave it

---

### Post by Yellow Pasque on 2009-06-05
Running Debian sid might be a bit challenging, especially if you try to use GNOME. I like Debian sid in the form of the Sidux distro, but of course, they don't support GNOME. I'm currently running Jaunty, but waiting patiently for the 2009-02 release of Sidux.

---

### Post by snowpine on 2009-06-06
Ubuntu 8.04 is a bad choice for someone who wants "the latest versions of apps" (sorry to be so blunt) The LTS releases like 8.04 are really designed for enterprise deployment, servers, and conservative users who frankly don't want a lot of updates. 

Sounds to me what you really want is a rolling release distro, so you get new apps when they are available (instaed of waiting for the next scheduled release). Arch, Sidux, and Debian Testing (Squeeze) are my favorite 3.

---

### Post by logos34 on 2009-06-06
why *isn't* there a rolling release version of ubuntu?  just about every other flavor
[URL="http://ubuntuforums.org/showthread.php?t=901693"]
"Suggestion: A rolling release Ubuntu based on Hardy?"[/URL]

---

### Post by Yellow Pasque on 2009-06-06
> **logos34 said:**
> why *isn't* there a rolling release version of ubuntu?  just about every other flavor
[URL="http://ubuntuforums.org/showthread.php?t=901693"]
"Suggestion: A rolling release Ubuntu based on Hardy?"[/URL]
That goes against the nature of Canonical/Ubuntu itself.

EDIT: Methinks this thread is headed towards "Recurring Discussions"

---

### Post by snowpine on 2009-06-06
> **logos34 said:**
> why *isn't* there a rolling release version of ubuntu?  just about every other flavor
[URL="http://ubuntuforums.org/showthread.php?t=901693"]
"Suggestion: A rolling release Ubuntu based on Hardy?"[/URL]

Ubuntu is derived from Debian Sid (Unstable), which is rolling release. Ubuntu's "innovation" was to turn Sid from a rolling to a 6-month stable release distro. If you want rolling release Ubuntu, just try Sid (or sidux) or possibly Debian testing.

---

### Post by joezamboni on 2009-06-06
ext3>ext4

---

### Post by logos34 on 2009-06-06
> **joezamboni said:**
> You should just do an upgrade to jaunty. Or, if you have some free time, reinstall with jaunty and use ext4 (its way faster.).

I'm trying to avoid that...happy with 8.04 LTS...got everything set up like i want...Too many niggles and bugs still in 9.04...

---

