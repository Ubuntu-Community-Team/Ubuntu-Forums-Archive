---
title: "Firefox font problem"
date: 2005-12-23
forum: Desktop Environments
---

### Post by OtubrabNad on 2005-12-23
I was trying to re-install my Firefox plug-ins by following the directions in the following wiki: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

I entered the following in the command line:
```
cd ~/.mozilla/firefox
 mkdir ff1.5
 mv profiles.ini *.default ff1.5/
 cp ~/.mozilla.ubuntu//firefox/profiles.ini .
 cp -r ~/.mozilla.ubuntu//firefox/*.default .
```
and recieved this message:
```
cp: cannot stat `/home/hal/.mozilla.ubuntu//firefox/profiles.ini': No such file or directory
```

I gathered that this was because I never followed the directions at the beginning of the wiki to save my old mozilla profile. Anyway, I then moved the profile.ini file back into the firefox directory. However when I started Firefox again the default profile loaded.

I don't mind re-installing my plug-ins, extensions, etc., but I noticed that the font looks weird. I don't know how to describe it, but the font (the kind that can be highlighted such as that which you're reading right now) is cruder than it was before. How can I restore Firefox's basic fonts to its former glory? Thanks.

---

### Post by OtubrabNad on 2005-12-23
I think I figured out what I did. Somehow I accidentally created a new Mozilla profile. If I recall correctly a while ago I fixed the font problem, but since I'm using a new profile the font's back to the way it originally is. I guess a better question is how do I restore my old mozilla profile?

When I ls -a  ~/.mozilla/firefox I get:
```
.   7alfwddg.default  ff1.5            pluginreg.dat
..  emr48nez.default  .mozilla_backup  profiles.ini
```
.mozilla_backup also contains a firefox directory which contains the sub directory  56qy6ilq.default which contains the files:
```
bookmarks.bak      compreg.dat      install.log     secmod.db
bookmarks.html     cookies.txt      key3.db         signons.txt
Cache              defaults.ini     localstore.rdf  stumblerating713233
Cache.Trash        downloads.rdf    lock            stumbletags713233
cert8.db           extensions       mimeTypes.rdf   stumbleurls713233
chrome             formhistory.dat  prefs.js        ver
compatibility.ini  history.dat      search          xpti.dat
components.ini     hostperm.1       search.rdf      XUL.mfasl
```
I believe 56qy6ilq.default has something to do with my old profile. (7alfwddg.default and emr48nez.default contain similar files so I think they are related to two other profiles besides my old one). However I have no idea what to do next. Can any of this mumbo-jumbo help someone restore my old firefox profile and settings? Thanks again.

---

### Post by OtubrabNad on 2005-12-24
bump

---

