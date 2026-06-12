---
title: "Fedora Test 3 Live"
date: 2007-10-23
forum: Fedora/RedHat and derivatives
---

### Post by Antman on 2007-10-23
Well, I have to say that so far I am liking Fedora 8 test 3. I installed the Live CD onto my laptop and things that have some issues in other distros are working thus far in F8test3.

Working:
1. S2Ram (works in Sidux and OpenSuse 10.3, but not in Mandriva or *buntu's)
2. S2Disk (works in Sidux, OpenSuse 10.3, and MV2008, but not in *buntu's)
3. 3945ABG wireless (works in Sidux, *buntu's, and MV2008, but iffy in OpenSuse 10.3)
4. 1400x1050 res. (doesn't work out of the box in PClinuxOS)

Very nice so far. Going to keep in on the lappy until Fedora 8 final. But so far it's the only distro I have tried desides Sidux that supports all my key points above.:guitar:

---

### Post by pelle.k on 2007-10-24
This is a bit OT (still, thanks for the repost on fedora 8 ), but have you tried installing pm-utils or powersave in ubuntu?
As you know these two are frameworks designed to suspend/hibernate modern computers with "fixes" to bypass troubling hardware. Fedora actually uses pm-utils by default.
Ubuntu has it's own sleep/restore scripts in /etc/acpi, but those wouldn't work for me. powersave did though (with a little help from SUSPEND2RAM_SWITCH_VT="yes").

---

### Post by Antman on 2007-10-24
> **pelle.k said:**
> This is a bit OT (still, thanks for the repost on fedora 8 ), but have you tried installing pm-utils or powersave in ubuntu?
As you know these two are frameworks designed to suspend/hibernate modern computers with "fixes" to bypass troubling hardware. Fedora actually uses pm-utils by default.
Ubuntu has it's own sleep/restore scripts in /etc/acpi, but those wouldn't work for me. powersave did though (with a little help from SUSPEND2RAM_SWITCH_VT="yes").

Hmmm.... thanks for the tips.... I'll try them out.

---

### Post by karellen on 2007-10-26
I don't know about others but I'm waiting anxiously for fedora 8 :)

---

### Post by mthei on 2007-10-27
> **pelle.k said:**
> This is a bit OT (still, thanks for the repost on fedora 8 ), but have you tried installing pm-utils or powersave in ubuntu?
As you know these two are frameworks designed to suspend/hibernate modern computers with "fixes" to bypass troubling hardware. Fedora actually uses pm-utils by default.
Ubuntu has it's own sleep/restore scripts in /etc/acpi, but those wouldn't work for me. powersave did though (with a little help from SUSPEND2RAM_SWITCH_VT="yes").

THANK YOU!!
I've been told to install some other things, edit some files, and nothing worked. Of course, the most obvious package name was the one I haven't tried. I was going to switch to Sidux because of this problem (and also for the thing I complain about in the paragraph below).

And to stay on topic, Fedora 8 does look good, and I'm anxious to see if it's "bloated" or if you can remove the programs you don't need. My only complaint about Ubuntu is that you're stuck with a lot of things that cannot be removed without breaking the Ubuntu-Desktop metapackage.

---

### Post by igknighted on 2007-10-29
> **mthei said:**
> THANK YOU!!
I've been told to install some other things, edit some files, and nothing worked. Of course, the most obvious package name was the one I haven't tried. I was going to switch to Sidux because of this problem (and also for the thing I complain about in the paragraph below).

And to stay on topic, Fedora 8 does look good, and I'm anxious to see if it's "bloated" or if you can remove the programs you don't need. My only complaint about Ubuntu is that you're stuck with a lot of things that cannot be removed without breaking the Ubuntu-Desktop metapackage.

There is no "fedora metapackage".  However, to get complete control over what gets installed you need to use the DVD, as the liveCDs just dump the CD contents like Ubuntu (without the metapackage unk, of course)

---

### Post by mthei on 2007-10-29
Good to know. I'll certainly give Fedora a shot when it comes out next week. Not being the sort of person who installs/uninstalls things constantly, that sounds much more appealing as the next step after Ubuntu.

---

### Post by mivo on 2007-11-01
> **igknighted said:**
> There is no "fedora metapackage".  However, to get complete control over what gets installed you need to use the DVD, as the liveCDs just dump the CD contents like Ubuntu (without the metapackage unk, of course)

Thing is, though, that mostly everything that is installed by the F8 Live CD is stuff I actually use. Maybe I'm just really generic in that regard. ;) Ubuntu installs, for example, OpenOffice, which I have really no need for. Removing it cleanly is a little tedious. Fedora contains a number of apps that I always install manually in Ubuntu, and I have never seen a distro that installs this quickly.

Aptitude is still the best, though. :)

---

### Post by igknighted on 2007-11-01
> **mivo said:**
> Thing is, though, that mostly everything that is installed by the F8 Live CD is stuff I actually use. Maybe I'm just really generic in that regard. ;) Ubuntu installs, for example, OpenOffice, which I have really no need for. Removing it cleanly is a little tedious. Fedora contains a number of apps that I always install manually in Ubuntu, and I have never seen a distro that installs this quickly.

Aptitude is still the best, though. :)

They do miss a few that I really need... like wget and the gconf-editor.  But I agree, it is a very nice liveCD

---

### Post by mivo on 2007-11-01
RC3 of FC8 was released today, by the way -- both a LiveCD and the DVD installer:

[http://torrent.fedoraproject.org/](http://torrent.fedoraproject.org/)

You are right about gconf-editor. I didn't find it and was surprised to learn that it had to be downloaded separately.

---

