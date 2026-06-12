---
title: "Sync-WBFS"
date: 2010-06-16
forum: Gaming &amp; Leisure
---

### Post by PeopleEater on 2010-06-16
[size=6]**Sync-WBFS**[/size]

Add Wii disc images to a wbfs formatted partition. Input can ge given as either a directory to be scanned for all supported files or as files. 
Supported files are .ciso, .iso, .wbfs and .wdf images and can be automatically extracted from 7zip, bzip2, gzip, rar, tar and zip and archives.

It uses Wiimm's awesome command line tool which you'll need to use this from [here]("http://gbatemp.net/t182236-wwt-wit-wiimms-wbfs-iso-tools")?.
You'll also need p7zip, unrar-nonfree, and unrar if you don't have them already.

I know there are plenty of wbfs managing programs out there but i hadn't been able to find one that could handle archives and that's how this was born.
Finally t may be a little rough as it's my first endeavor into bash scripting so any suggestion are welcome and of course use at your own risk.

On Ubuntu run the code below to install the requirements
```
sudo apt-get install p7zip-full unrar-nonfree unzip
```

**[size=4][Download]("http://www.mediafire.com/file/jjiyhiynztr/sync-wbfs")[/size]**

---

