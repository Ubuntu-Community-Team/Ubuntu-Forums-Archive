---
title: "Nautilus STILL locks up on folders with many files"
date: 2012-01-28
forum: Desktop Environments
---

### Post by p_code on 2012-01-28
I am running an up to date installation of Ubuntu 10.04 with Gnome Nautilus 2.30.1

Folders  with several hundred files can take 20 seconds or more to open, and  with a few thousand files Nautilus locks up completely and requires a  Force Quit to recover control.

This has been going on basically FOREVER with 10.04

Several  months ago, I found a thread that recomended to disable and remove  Ubuntu One to fix this, and that did at least partially fix things - at  least for awhile.

I have also tried disabling thumbnail rendering, but this doesn't seem to help either.

Also, copying large files, or large numbers of  files through external USB drives also remains hit or miss through  Nautilus (reports the dreaded bogus "*Error splicing* file").  

Note:  This is NOT due to an attempt to copy a single file larger than 4 Gigs  onto a Fat32 drive (I know that is not possible due to limitations of  the Fat32 file system).  It happens many times when simply copying  several hundred megabytes of small files onto a Flash Drive.

Add to this the fact that the touchpad on my Gateway Netbook is STILL being incorrectly handled as [ a generic PS2 mouse]("http://ubuntuforums.org/showthread.php?p=9683372#post9683372") and you have a recipe for a very frustrating user experience.

I  don't want to confuse things because these issues most likely have  different root causes, but there is one unifying theme - Core  functionality like mouse drivers, and file management, IS BADLY  BROKEN.

More than 15 years ago Windowz 95 was much faster, and in many ways more capable,  with a tenth the resources, than Ubuntu 10.04 (sure as hell didn't crash  trying to read a folder with 600 files). 

The last thing Ubuntu had going for it was 'stability', but even that seem to have gone out the window . . .  :sad:

---

### Post by typhoon_tip on 2012-01-29
> **p_code said:**
> Note:  This is NOT due to an attempt to copy a single file larger than 4 Gigs  onto a Fat32 drive (I know that is not possible due to limitations of  the Fat32 file system).  It happens many times when simply copying  several hundred megabytes of small files onto a Flash Drive.

Pay attention that FAT32 has a limit also on the number of files per directory, actually a very small one I think. I get the same problem with my MP3s. Seems a single folder cannot contain more than a certain number of files or bytes. I resolved that once by splitting files into folders A, B, C etc.

---

### Post by p_code on 2012-01-30
> **typhoon_tip said:**
> Pay attention that FAT32 has a limit also on the number of files per directory, actually a very small one I think. I get the same problem with my MP3s. Seems a single folder cannot contain more than a certain number of files or bytes. I resolved that once by splitting files into folders A, B, C etc.

First, I guess that I didn't make it clear . . .

The SAME problems ALSO happen when opening large native EXT4 Ubuntu folders.

Second, the restrictive limit on the number of files allowed in fat file systems (something like 255 files) only applies to the ROOT folder of some older fat file systems (which of course will probably not be / in linux, so you do have to be careful to take that into consideration).

For all other folders on a Fat32 volume, the file allocation table allows 65535 entries which is more than twenty times the number of files that crashes Gnome Nautilus.

In addition to that, I have installed PCManFM from the repository, and that file manager has no problem opening the same folders.

So why not just use PCManFM???

In fact, I would be perfectly happy switching to PCManFM, even though it's not as well integrated into Gnome, but PCManFM IS ALSO SCREWED UP.

Although PCManFM  can open folders with hundreds (or even thousands) of files, the PCManFM search "Find Files" capability (which is critical when managing this number of files), will fail to find files properly in these folders.  

With large numbers of files, and long file names, it looks like PCManFM runs out of space internally while indexing the folder contents then just stops indexing.

If the part of the name you are looking is there in the index at that point, fine, PCManFM can find it, but if not, then the file isn't found.

For example, I have a folder with about a thousand EBook files from free public domain sites like FeedBooks and Project Gutenburg.   These files are named based on both the author's name, and the work's title, so the names can be as short as a few dozen characters, up to fifty or more.

I suspect that PCManFM only allows a single old-style code page (65536 bytes) and that's not enough to fully sort and index the all the file names in the folder.

A partial work around is to search for only the first few letters of your search term.

For example, a search for  *ver* may work, where a search for *verne* fails, even though there IS a file matching both search terms  (the name "Jules Verne - Twenty Thousand Leagues Under the Sea").   

The default PCManFM search is not case sensitive (so that's not the issue), and PCManFM can find this title based on the shorter search term *ver* but NOT when searching for *verne*.   This suggests that it's doing an incomplete job of b-tree style indexing, and has gotten to the point of associating the file with the short key "ver" but not with the key "verne".

But there is no guarantee, even with shorter search terms, and not having a reliable search capability effectively makes PCManFM useless for me.

And, ONCE AGAIN, these limitations are NOT related to any built in limitations of those evil MS DOS type file systems - Gnome Nautilus and PCManFM ALSO don't work right, EVEN WITH NATIVE LINUX FOLDERS.

. . . and the same large folders open and search just fine in Win98, WinXP, and Win7.

Sad, really really, SAD.

---

### Post by ColdnitroX on 2012-01-30
#include <iostream>
#include <string>
using namespace std;
cout << "Maybe try using Thunar? Also try removing all nautilus add ons, because those slow it down tremendously. Switch from the icon view in nautilus to the list view, that might help... As well, go to the edit menu in nautilus, and click the option that says 'Preferences'. Then go to the 'Preview' tab, and set 'Show text in icons' and 'Show thumbnails' to Never. That should speed everything up as well. You COULD also set 'Count number of items' to Never, but because that feature is more useful than slow, I would not do that myself. 

I hope those steps help speed up the opening of folders.
Check your machine's specs. Does it have low memory or a slow processor? That could be part of the problem.";

string Remember("Remember kids... NEVER divide by zero.");
return 0;

---

### Post by p_code on 2012-01-30
Thanks ColdnitroX, I did try thunar some time back.  It didn't seem to work much better, and I didn't like the interface.

It's a shame that the search feature of PCManFM is not reliable,  because it's ten time faster on opening large folders and had some features that I really liked (like the ability to easily open a terminal in the current folder, or open the current folder as root).

I also tried your suggestion of using list-view as the default when opening folders in Nautilus, and though some folders would randomly open in that view, there were still some lock-ups requiring force-close, and on the average, when Nautilus does succeed in opening folders in list-view, it's even SLOWER than icon view.

It has occured to me that some of the issues with Nautilus may be due to some extension, but I have not intentionally installed ANY add-on extensions to Nautilus.  None the less, I did install the MD5,SHA hashing which does seem to hook into Nautilus, as well as ClamAV anti-virus, which also seems to hook into Gnome and Nautilus.

I'm not sure; Is there any way to remove the extension functions that these applications may have hooked into Nautilus without completely loosing their functionality?

It's just a little disappointing that Nautilus doesn't work better given Gnome's supposedly mature status as a desktop environment.

It looks like, just as Slackware did some years ago, Ubuntu is getting ready to dump Gnome, but that's no excuse for not fixing bugs in their 'Long Term Support' 10.04 release.

Canonical, I know you are hard at work DUMBING DOWN OUR DESKTOP TO LOOK LIKE A STUPID 'SMARTPHONE', so it's more 'moron-friendly' but it would be really nice if someone would actually spare a few minutes to support the CURRENT Ubuntu LTS release.

Now I know what it must have been like to live after the fall of the Roman Empire and watch the world slide back technologically from where they could build something like the Colosseum, to barely being able to build mud huts.

Just another sad example of Writh's Law, the corollary to Moore's Law, annunciated by Niklaus Writh, the creator of the Pascal Language (and attributed by him to an original comment made by Martin Reiser).

[Writh's Law]("http://en.wikipedia.org/wiki/Wirth%27s_law") -

"Software is getting slower more rapidly than hardware becomes faster."

Or the frustrated hardware engineer's corollary to Moore's Law.

Morons Law -

"Most programmers are MORONS, who can barely walk and chew gum at the same time, and their aggregate stupidity is increasing exponentially, at a rate that exceeds Moore's law."  :rolleyes:
[COLOR=Blue]

EDIT:[/COLOR] [COLOR=Blue]
I just tried disabling ALL the preview options under Nautilus' preferences, including "Show text in icons" *and* "Count number of items"  (I had missed "Count number of items" previously) and this does indeed seem to speed things up and improve Nautilus' stability.  Also went back to icon-view as default, and set the icon default scale to 66%.   Strange thing is, Nautilus STILL seems to be counting the number of items in the folder and reporting it in the status line  #-obut the speed is MUCH better and most of the crashes have gone away.

Hope it stays that way.    :)[/COLOR]

---

