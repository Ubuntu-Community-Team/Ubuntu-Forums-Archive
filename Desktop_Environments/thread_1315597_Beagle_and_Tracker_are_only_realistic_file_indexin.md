---
title: "Beagle and Tracker are only realistic file indexing options?"
date: 2009-11-05
forum: Desktop Environments
---

### Post by brunjes on 2009-11-05
I've tried Beagle. I've tried Tracker. Both suck frankly. They do not reliably index my files and certainly do not index .pptx, .xlsx, .docx files (which I get by the boatload from my office workers and the web as part of my job).

Tracker was broken in Jaunty and now with Karmic, it won't index anything but stuff in my /home directory (and yes, I told it to visit other locations in the file system and it simply does not index them). And the complaint about indexing Microsoft Office 2007 formatted documents still stands. And the man page says run the trackerd program with -R (syntax error) or with --force-reindex (no syntax error, but does not do anything either).

It is amazing to me that with 1 TB hard drives a reality for desktop systems that people do not miss indexing capabilities much (or so it seems). I'm a fairly organized person but with more than 250 thousand files to search through, it's just not feasible to think that I can quickly find the documents I'm looking for without a search engine helping me. I do use 'locate' but of course that is only good for searching for filenames, not searching by file content.

Oh, and Google Desktop is also not an option -- already tried that and it also did not cut the mustard.

Is anyone working on this actively?

Microsoft does this, Apple does this ... it cannot be that hard if Microsoft can make theirs work with Vista (gasp). If Ubuntu wants to be a viable desktop replacement play they are going to need this functionality to work as reliably as any other major desktop tool they bundle with Ubuntu.

---

### Post by ShowMeGrrl on 2010-02-26
I sure do second what you say on this! 

I am a Linux newbie and thinking about replacing my Windows desktop machine with a Linux machine from System76. Today I was trying to search for some content on my Linux Starling netbook and was researching how to do it. It appears I can search only for file and folder names, not for content within the file.

I am sure disappointed to hear that there are no good utilities for searching the whole hard disk for words and phrases within a file, because that is something that I would find it very hard to do without.

I use Copernic on my Windows desktop, but it is Windows-only software, unfortunately.

---

### Post by larsbjo on 2010-03-03
I finally got tracker to work on my Karmic after experiencing similar problems as brunjes. I'm testing with the newest repository from here: **[https://launchpad.net/~alex-hunziker/+archive/ppa](https://launchpad.net/~alex-hunziker/+archive/ppa) **
After updating I had to manually remove all old versions in synaptic. 
sudo apt-get upgrade didn't update all components. Instead you have to  search for "tracker"in synaptic and uninstall every tracker program with version 0.6.*. Then install all the corrensponding 0.7.1* versions. 

What I did next was to delete the **/home/user/.local/share/tracker** and **/home/user/.config/tracker** folder. 
Finally I executed :

**tracker-control -r**

to reset tracker, and

**tracker-control -s**

to start it again. You can use: 
[B]
tail -F ~/.local/share/tracker/tracker-miner-fs.log[/B]

to follow the log from indexing process.

It seems as the indexing goes well and there is lots of information available from using the command line tools in tracker. The GUI sucks. I have no clue how to use the adwanced funtions and I cannot find any infor about how to eg. search for and add tags. 

If anyone knows about a better GUI or where to find info about how to filter by filetype etc. then please post the URL.

---

### Post by Porter Doran on 2010-05-09
What's wrong with Google Desktop Search? I've used it for a couple of years now, no complaints. It's quick and reliable, just as Beagle and Tracker aren't.

There's some buzz around a search program called Recoil, by the way (but I personally know nothing about it).

---

