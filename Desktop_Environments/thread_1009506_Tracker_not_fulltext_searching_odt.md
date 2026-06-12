---
title: "Tracker not fulltext searching odt"
date: 2008-12-12
forum: Desktop Environments
---

### Post by Zeedok on 2008-12-12
I've started using the deskbar applet to find files (along with gnome-do it has really sped up my work day) and it works fine when finding a particular filename . . . BUT . . . Yesterday I had to find a report I had sent to a particular client and when I searched for his surname no results were returned.  I did some reading through the forums and other places and it seemed to confirm what I had believed - that tracker was capable of fulltext odt searching.  I believe the text is supposed to be extracted and indexed.

So how can I check/troubleshoot tracker to make sure this is working (I have >500 reports and finding the one I needed is really time consuming by hand)??

Any help greatly appreciated.

---

### Post by Zeedok on 2008-12-13
Bump

---

### Post by Zeedok on 2008-12-14
Bump bump

---

### Post by Zeedok on 2008-12-14
Bump 3

---

### Post by Zeedok on 2008-12-22
Thought I'd try and revive this one.

Any takers??

---

### Post by jongkind on 2008-12-30
Same with me. I switched to Beagle.

---

### Post by Zeedok on 2009-02-01
I tried Beagle and it wasn't fulltext searching odt either.

---

### Post by laserline on 2009-02-21
Same here on tracker. ODT and ODS aren't indexed for fulltext

---

### Post by mlissner on 2009-02-21
I would try cranking the specs of what gets indexed, and how much memory/CPU your computer consumes. You can also kill the trackerd process, and then start it again with trackerd -v 3, and it will show you its debugging messages. That might help...

---

### Post by ridgeland on 2009-06-09
I did not think tracker could read text in odt files.  
I like tracker and wanted to use it to search my odt files as well as the txt files and scripts I have written.
My solution sounds complex but is all automated.
First I use odt2txt to create a copy of my entire /Data/Writer directory, all my odt files.  My odt files total 45MB so it's no big deal.  The translated files (redundant copy) are 1MB.  Only text gets copied so photos etc are not in the translated files.
A cron job runs a script that each day checks the time stamps of the source odt files vs the time stamps of the odt2txt copy.  If the source file has a newer date odt2txt is run to update that one file's copy.  The copy is named with *.odt.txt
Tracker monitors my txt files and scripts, the odt files are crawled once a day.  When a search finds hits in the odt.txt file it's obvious from the file name that its an odt file.  Still a quick look in the odt.txt file will tell me if this is the odt file I want.
The only software needed is odt2txt from Synaptics and the script I wrote.  If anyone asks for the script I'll post it here (75 lines)

---

### Post by laserline on 2009-06-09
Hi,

But this is a workaround for a feature that Tracker says it has.

-- Or am I reading the features list wrong: [http://live.gnome.org/Tracker/SupportedFormats](http://live.gnome.org/Tracker/SupportedFormats)

It says it requires 'unzip' which I already have installed.

Thanks,
Idan.

---

