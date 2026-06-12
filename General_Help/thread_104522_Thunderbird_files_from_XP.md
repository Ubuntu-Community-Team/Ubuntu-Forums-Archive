---
title: "Thunderbird files from XP"
date: 2005-12-16
forum: General Help
---

### Post by DJiNN on 2005-12-16
If this is in the wrong forum please forgive me, i wasn't sure where 2 put it. :)
I have got Ubuntu working (5.10) & it's great, have run "Automatix" & installed all the extra stuff & it now works really well... but one thing that i would love 2 do is get my emails etc from my T-Bird folder in WinXP & somehow get them into my T-Bird folder in Ubuntu. Is this indeed possible? 

I have done some searching with regards 2 this, and did try the whole "Profile" route, but it was much 2 complicated (Not the process, but my particular T-Bird setup) so i thought i'd ask if there's a way that i can physically "Move" the files (NOT the Profile per se, just the relevant .sd or .sb files (or whatever they're called)) over 2 the relevant folder on Linux...... I have already setup my Linux T-Bird profile & it all works great.

Any help or advice would be much appreciated.

Many thanks......

DJiNN

---

### Post by nik on 2005-12-16
It's possible. I can't remember exactly how I did it though. It seems to be the same mailbox format, so I simply moved the folders from C:\Documents and Settings\Application data\whatever in XP, and put them in $HOME/.mozilla-thunderbird/something_strange/Mail/Local Folders and chown'ed them recursively.

---

### Post by BathroomNinja on 2005-12-16
Should be under:

C:\Documents and Settings\[YOUR PROFILE NAME]\Application Data\Thunderbird\Profiles\[A BUNCH OF NUMBERS].default

look for:
inbox    (without an extension, also it will be the BIG file)
etc.. for each folder.

---

### Post by BrooksOfSheffield on 2005-12-16
The easiest way to do it is to actually copy your profile directory (vvkaekl8.default for example) to a mounted Fat32 partition.

Then edit ~/.mozilla-thunderbird/profiles.ini to reflect:
IsRelative=0
Path=<path to directory on mounted Fat32 partition>

Instructions are based on Mozilla Thunderbird 1.0.7 since 1.5 can't load a profile on a Fat32 partition ATM.

And under Windows edit C:\Documents and Settings\[Your Username]\Application Data\Thunderbird\profiles.ini with

IsRelative=0
Path=<path to new directory>

---

