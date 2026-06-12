---
title: "[SOLVED] Tracker shows results but they don't open"
date: 2008-01-14
forum: Desktop Environments
---

### Post by firefeather on 2008-01-14
I've been putting off posting but I decided I need to learn to ask for help more often. I can't figure out why, but when I search through Tracker, it'll show me the relevant results but I can't open them. Double-click doesn't work. Right-clicking and selecting either of "Open" or "Open Folder" don't result in any action.

I realized this happens only when I get into Tracker Search Tool from Deskbar (I don't use the live search results for it, by the way). I tried opening through terminal and couldn't replicate the bug .:-k

---

### Post by benanzo on 2008-01-14
I have the same problem, though it seems to be rather sporadic.  Sometimes it will work just fine in Applications -> Accessories -> Tracker Search Tool and other times I will have the same problem as you.  It will show the category of results found in the left pane but nothing will display in the main view.

---

### Post by firefeather on 2008-01-15
Anyone have any ideas? :)

---

### Post by firefeather on 2008-01-19
Bump, please...

---

### Post by geo909 on 2008-01-19
Same problem for me...
Anyone?
Any solution?

---

### Post by firefeather on 2008-01-21
Bump again...
If nobody knows of a solution for this, does anyone know if I should go ahead and file a bug report?

---

### Post by firefeather on 2008-01-29
Bump...I'm feeling lonely here, I'd like to get a response besides a "me too"...

---

### Post by R Smit on 2008-01-30
I installed Google desktop search; MUCH better! Fast, indexes Thunderbird, clearly states the status of indexing.
However: not supported by Ubuntu :-(

---

### Post by firefeather on 2008-02-04
> **R Smit said:**
> I installed Google desktop search; MUCH better! Fast, indexes Thunderbird, clearly states the status of indexing.
However: not supported by Ubuntu :-(

Thank you for your response. This doesn't answer my question, however. Also, AFAIK, Google Desktop search doesn't integrate with Deskbar, which I use as my "jumping-off point" anyway.

---

### Post by geo909 on 2008-02-07
> Bump...I'm feeling lonely here, I'd like to get a response besides a "me too"... 


Yeah, me too!

---

### Post by hades_6_6_6 on 2008-02-07
> **benanzo said:**
> It will show the category of results found in the left pane but nothing will display in the main view.
same for me :(

---

### Post by ashdezign on 2008-02-08
I am having some of the same issues, also tracker doesn't seem to index a lot of files, even those kept in the home folder or a subdirectory of the home folder.

And does anyone know if and when Tracker will index Thunderbird emails (I know it doesn't yet)?

I know google desktop search (GDS) does, but i tried installing it and my gnome panel kept disappearing.I had to keep killing and restarting the panel for it to reappear. Plus GDS slowed my boot time considerably, boots took 3 times as long and GDS seemed to get stuck on 0.5% of files indexed after  3 days of at least 8 hours a day idle time.

I ended up uninstalling it and now it seems I am bereft of a decent desktop search tool. Copernic Desktop Search is the one program I am missing from my windows days.

---

### Post by geo909 on 2008-02-08
Hmmm...
Is this a bug, maybe?

---

### Post by firefeather on 2008-02-09
Could be; I'm not sure whether to file it under Deskbar or Tracker. Since a few people have confirmed the report but nobody seems to have an idea why it's happening, I'll go take a look at launchpad and try filing a bug.

> **geo909 said:**
> Hmmm...
Is this a bug, maybe?

---

### Post by firefeather on 2008-02-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/190549](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/190549) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've posted a bug report if any of you have additional information that could be useful.

---

### Post by ashdezign on 2008-02-11
I ended up switching over to kubuntu (after finally figuring out how to get compiz fusion to run stable) and tried strigi. When strigi's index reached 2.5Gigs in size and still hadn't indexed some of the files in my home folder, froze up and ate my core duo cpu alive I decided to give Google Desktop another go.

After 36 hours google has indexed a whopping 465 files.... (and yes, I disabled Strigi first)

Desktop search, while showing promise, seems broken in Linux.. for the time being at least.

---

### Post by firefeather on 2008-02-11
I don't know about for you, but when I open Tracker on its own or use Deskbar's Tracker Live Search, the index works fine. I don't know much about KDE or whether Tracker works over there but I do think Tracker is a fine desktop search solution.

> **ashdezign said:**
> Desktop search, while showing promise, seems broken in Linux.. for the time being at least.

---

### Post by ashdezign on 2008-02-11
I found that tracker just wasn't indexing all my files and took entirely too long to give a result. When I searched for a file in tracker I generally had to wait 30 seconds or more to get the results and then it was several pages of partial matches before I found the file I was looking for, IF I found the file I was looking for.

At first this didn't seem to be the case, but the more it indexed the slower it became at delivering results and the less accurate they would be.  For example I have a file in my home directory called music.xml which is simply a list of all the tracks in my music library. Searching for this file by name... the file would appear 3-5 pages into the search results.

Deskbar I absolutely loved. Alt+F3 was how I started all my programs :). I do miss that in KDE. With the live search feature enabled though it kept crashing so I had to disable it.

---

### Post by firefeather on 2008-02-23
The bug report has been marked as invalid; looks like the problem doesn't show up in the Hardy alphas. If any of you testing Hardy see this in the alphas, feel free to update the bug status.

---

