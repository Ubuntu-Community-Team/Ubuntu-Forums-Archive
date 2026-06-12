---
title: "A few things that are important"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Curlydave on 2005-10-13
I just did a clean install of the Breezy Badger, and while I got many things working, including fglrx and the k7 kernel, I have a few problesm that were fixed before with a nub install script that I can no longer find here.

1: How do I add the extra repositories? I need them for imwheel. (which I shouldn't need in the first place...)

2: How do I get MP3 support?

3: How do I get flash?

How do I make a root browser go by default to the filesystem, not my home folder? iirc it was gksudo nautilus --nodesktop --/, but it keeps dumping me in my home folder.

---

### Post by Wolki on 2005-10-13
> **Curlydave]
1: How do I add the extra repositories? I need them for imwheel. (which I shouldn't need in the first place...) [/quote]

The Ubuntu extra repositories are still added in the same way as before said:**
> https://wiki.ubuntu.com/AddingRepositoriesHowto[/url]

> 2: How do I get MP3 support?

3: How do I get flash?

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Section 2 & 3 for a complete codec set, section 2 & 8 for flash.

Try to follow the instructions as closely as you can, end everything should work perfectly. (especially remember to remove the marillat repository used to install w32codecs before doing any upgrade on your system)

[quote]How do I make a root browser go by default to the filesystem, not my home folder? iirc it was gksudo nautilus --nodesktop --/, but it keeps dumping me in my home folder.

Nearly correct. Try the following: gksudo "nautilus --nodesktop /"

---

### Post by Curlydave on 2005-10-13
Thanks for the info! The root browser now works properly. However, I can't get the other things to work. I get a ton of errors when refreshign the repositories, or when I use that guide to install java, mp3 codecs and I still can't get imwheel due to similar errors. Is somethign up with the repositories?

---

### Post by Wolki on 2005-10-13
[QUOTE=Curlydave]Thanks for the info! The root browser now works properly. However, I can't get the other things to work. I get a ton of errors when refreshign the repositories, or when I use that guide to install java, mp3 codecs and I still can't get imwheel due to similar errors. Is somethign up with the repositories?[/QUOTE]

Not that 'I know of. That said, it's release day (yaaaaay! :)), so the servers might be under stress; maybe its your mirror?

Exactly what errors did you get?

I followed these instructions a few days ago after reinstalling, and everything worked, so it should still.

---

### Post by dbott67 on 2005-10-13
[QUOTE=Wolki]Not that 'I know of. That said, it's release day (yaaaaay! :)), so the servers might be under stress; baybe its your mirror?

Exactly what errors did you get?

I followed these instructions a few days ago after reinstalling, and everything worked, so it should still.[/QUOTE]

I've been getting errors all day here in the Great White North (although it's still mostly green in my area, with a touch of orange & red --- autumn is here!).

I've also been seeing many posts from people with respect to the repositories, so I suspect that it's just due to the flood of traffic and updating of the localized mirrors for each country.

-Dave

---

### Post by Curlydave on 2005-10-14
Ohh, OK thanks! I guess it's a repos issue. Apparently IMwheel installed OK even though it got errors, and now flash just installed itself automatically like it does in windows via a quick little gui in firefox... awesome!! I guess I'll just wait on the repos for mp3 support.

---

### Post by g14 on 2005-10-14
Under synaptic do this:
Settings --> Repositories --> Add
[X] Universe
[X] Multiverse


Check universe and multiverse. Then search for these 2 packages:
gstreamer0.8-plugins
gstreamer0.8-plugins-multiverse

That will pull in all of the multimedia plugins including divx and mp3 support.

---

