---
title: "bad update??"
date: 2009-01-03
forum: General Help
---

### Post by mcrene on 2009-01-03
so after running Ubuntu for a few days now and being rather impressed with it, I am now having an upsetting problem.

the media player wanted to update to find a codec of somekind, it did but after downloading/installing it said the codec was incorrect. then it tried doing the same thing for some reason, but froze. Ubuntu continued working, but the update box would not close, cancel, open, install anything.

so I restarted (power button, choose restart) and figured that would be ok.

now here I am, all my bookmarks in FF3 are gone, Evolution Mail is wonky, Pigeon MSGer will start but not stay going (wifes mac MSN says I log on for a sec than off) In FF when I open a page, I can no longer go back a page as its gone, even the arrow is grayed out as if this is the first page I have opened.

I have no idea whats going on, but it sucks. I understand there is no 'restore point' here, and I just started using Ubuntu and have been getting everything updated so I havent' backed up anything yet. 

So what could be going on?

---

### Post by kellemes on 2009-01-03
Can you explain how you tried to install this codec? What steps did you take before your system froze?
This in order to get an idea of what went wrong..

---

### Post by mcrene on 2009-01-03
I have been trying to clear my HDD, surfing thru the wasted space folders (aka porn) and deleting a bunch of crap.
There were 2 files (avi movies) which did not show any picture for the thumbnail, when the first one tried to load it asked to download the codec, I said go for it and it did. It was a large download, 19files, one of which was about 18megs. Anyway, after the download and install the media player tried to play the movie, which again gave an error msg. It again tried to download the codec, but thats where it froze.
Just to re-iterate, the **downloader froze**, everything else seemed to be working. But when I tried to use FF3 my bookmarks were gone, Evolution was wonky, etc etc. When typing in a website it knows my history and shows recent visits, but bookmarks are gone. I guess I'll have to search them again and load from my XP FF3. I still can not go "back" pages in FF3... no matter how many pages I click too, the last one is unavailable.
I restarted via power button, same problems continued, and here I am.

---

### Post by namdung on 2009-01-03
First, see if any issues from previous attempt to install
```
sudo dpkg --configure -a
```

Update system
```
sudo apt-get update
```

Install **Gstreamer** codecs from **Add/Remove Applications** to play proprietary audio/video formats like DVD, mp3, avi, mpeg etc.

---

### Post by mcrene on 2009-01-03
[I]> **namdung said:**
> First, see if any issues from previous attempt to install
```
sudo dpkg --configure -a
```[/I]
**so that code gave no reply, when entered, nothing came up**
[I]Update system
```
sudo apt-get update
```[/I]
**that code gave a large run out, updating I take it. no result other than that tho.**
[I]Install **Gstreamer** codecs from **Add/Remove Applications** to play proprietary audio/video formats like DVD, mp3, avi, mpeg etc.
[/I]


I am still stuck with no option to go back pages in firefox.
New emails don't pop up in Evolution at all, even when I hit Send/Receive.

I'm sure there are other fun new problems that I'll find over the next little while.

---

### Post by mcrene on 2009-01-03
So found some others.
In FF, I looked into Edit>Preferences> and clicked on Manage Add-ons... which resulted in FF shutting down completely. Tried again, same result.
When I restarted FF, each time, it loses whatever pages I have recently viewed (all the ones from before this fiasco started are there, but any new ones get wiped) and any log-ins/passwords I have used (this site for example) are gone and I need to log in again each time FF is started.

Is there a chance I have a virus of somekind? I don't know jack about this linux os yet, learning, but what started as a good thing has gone downhill rather quickly. seems a lot like a windows problem all over again... great.

---

### Post by mcrene on 2009-01-03
some more;

tried to update Firefox... it shut down.

Ubuntu updating itself, with files and downloads it updated itself with 3 days ago after I first installed it.

Its as if Ubuntu and every program in it, resorts back to its initial install state every few seconds. Sounds silly but I can't think of anything else. 

Nothing is working properly here, updating anything causes either no change, or shuts down whatever program is running...

After its all said and done, my initial install of Ubuntu screwed up my XP (deleted some rather important .sys files) so now I have a laptop which runs like crap in one OS, and won't boot the other at all.

Can't say I am really impressed with this Ubuntu, I got it understanding I wasn't going to experiencing these Windows like problems... I was wrong.

---

### Post by mcrene on 2009-01-03
wow, this place is busier than the MS webhelp site. 

help.

now, clicking "Applications" only highlights it Orange, no scroll up options, no programs to choose from, nothing, just turns orange. Places/System still works fine... Apps... orange. wow.

this is worse than XP, here n I was worried about downgrading to Vista sometime.

---

### Post by mcrene on 2009-01-04
is ubuntu slowing degenerating into an MS like state?
 
I installed it onto a partition with 2gigs of space (was supposed to be 20gig, forgot a 0 when entering size)
it went from having 800megs of space to 85megs of space. Could this lack of room be causing these problems? If so, now what?

slowly new problems pop up, or if something should pop up, it doesn't (see Applications not working in post above)

Since I can't resort back to XP (thanks ubuntu) and this pile of it isn't working worth a... what is a guy supposed to do?

---

### Post by Prodigious Penguin on 2009-01-04
Having too small a partition definitely has some bearing on things not working right.  I experienced a crapton of issues back with Ubuntu 6.06 when my /home directory got above 85% full.  Had trouble logging in, everything was sluggish, programs would close with random errors...  I personally give my root system partition 10gb, and my /home directory the rest of the drive.  In your situation, I'd say either 5gb for / and 15gb for /home would suffice, or you could repartition to 20gb for / and not use a separate /home partition (going this method would put both / and /home on the same partition).

By the way, I followed your link from your Firefox bug over on Launchpad, which I closed if you weren't able to see.

As for XP not starting up, I haven't ever encountered a situation where Ubuntu deleted something necessary from a Windows partition by itself.  I think most likely XP got borked up when you repartitioned - sometimes not doing a defrag in Windows before you resize/repartition will mysteriously eat data.  Did you use a tool like gparted to repartition, or did you use the partitioner in the Ubuntu installer?

---

### Post by Sef on 2009-01-04
> the media player wanted to update to find a codec of somekind, it did but after downloading/installing it said the codec was incorrect. then it tried doing the same thing for some reason, but froze. Ubuntu continued working, but the update box would not close, cancel, open, install anything.


1) What media player and what codec?

2) What site were you at?

3) I'm thinking that codec was actually some type of malware.  If it is, it can't infect your system, but it is trying to run and causing the problems with Firefox.

> Having too small a partition definitely has some bearing on things not working right. I experienced a crapton of issues back with Ubuntu 6.06 when my /home directory got above 85% full. Had trouble logging in, everything was sluggish, programs would close with random errors

To check how much disk space is being used, go to Applications > Accessories > Disk Usage Analyzer

---

### Post by mcrene on 2009-01-04
> **Sef said:**
> 1) What media player and what codec?
[B]the default media player for Ubuntu, not sure which codec, and not sure how-to check. I don't know how to check for recent codec downloads/updates
[/B]
2) What site were you at?
[B]I wasn't on any site. I don't even think I had Firefox open when this first happened. I noticed the errors when I tried posting about the problems, when I went to use my bookmarks to get here, they were gone.
[/B]

3) I'm thinking that codec was actually some type of malware.  If it is, it can't infect your system, but it is trying to run and causing the problems with Firefox.[B]
Is there a way I can remove the codec then? I really don't understand this OS yet (obviously) so finding the problems is proving difficult.[/B]



To check how much disk space is being used, go to Applications > Accessories > Disk Usage Analyzer
[B]
I can't get into Applications. As I said it just highlights orange, but I have nothing to choose from, the programs don't scroll up as normal[/B]


I don't know how/why this install may have screwed up XP, I didn't use any partition program. The Ubuntu install asked for different install options, and I used the "Use largest free partition" or something along those lines. When it asked how large to make it (there was about 28G free) I thought I said use 20G but realized after it was only 2G (stupid mistake on my part)

So this is my thought... remove Ubuntu. I have the install CD so I can install it again. I am not sure how to remove Ubuntu, then re-install it without using XP tho.

thanks for continued help.

---

### Post by mcrene on 2009-01-05
looking for continued help.

can I re-install Ubuntu, than remove this version without any for-seeable problems from the masses?

little help here, cause this sucks as it is right now.

---

### Post by Prodigious Penguin on 2009-01-05
Yeah, start installing using the CD, then use the partitioner to delete your current Ubuntu partition, then repartition the drive with a bigger amount of space for Ubuntu.

---

### Post by jerome1232 on 2009-01-05
> **mcrene said:**
>  
I installed it onto a partition with 2gigs of space (was supposed to be 20gig, forgot a 0 when entering size)
it went from having 800megs of space to 85megs of space. Could this lack of room be causing these problems? If so, now what?

Bingo, 2 GB's... I didn't think Ubuntu could even fit on that. I've seen all of the problems your describing happen on a system with a full disc. I think it's time to grow that file system from a live cd. 

Or just repartition and reinstall.

---

### Post by mcrene on 2009-01-05
thanks for the helpful advice.

I already have 2 external HDD's, but I picked up a 3rd tonite to use as a backup only HDD. 
I plan on copying over all the files/folders I want to keep from my laptop, than re-installing Ubuntu again, but wiping the complete internal HDD once and for all.

I appreciate the help everyone has given me, sucks this all stemmed from a stupid missed 0 when first installing.

Well let the backing up begin, than I'll hopefully be back on sometime later tonite, or tomorrow maybe... wish me luck.

---

### Post by mcrene on 2009-01-05
well I am back, running just Ubuntu and currently updating after the install.

I used the whole HDD, but will partition it for an XP install in a week or two. Sadly I still need XP for a few programs I use.

thanks again to those who gave me the help, advice and affirmation about the lack of space causing the problem.

looking forward to see what a smooth running Ubuntu can really do.

---

