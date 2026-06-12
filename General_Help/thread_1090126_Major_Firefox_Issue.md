---
title: "Major Firefox Issue"
date: 2009-03-07
forum: General Help
---

### Post by noxinvictus on 2009-03-07
Greetings,

I apologize if this may already be covered, but I cannot really check without being here all day due to the problems I currently face with Firefox.  Earlier today, I installed some ubuntu updates which mostly included files regarding Firefox.  Not too long after installation, my downloads ceased working and, in fact, some previous downloads "disappeared".  I restart the browser and now the following is gone:

- My bookmarks
- All History
- I cannot go "back" or "forward" in browsing
- All booksmarks in my bar are gone
- No "stop" or "refresh"

Sometimes I cannot access 'File', 'Edit', and any other option in Firefox.

Essentially, it saves -nothing- in history, in one direction or another, and is also running at about half the speed it was before the update.  If I follow a link to any given page, I have to start all over again.  In this case, the google search feature with the browser has been my means of getting anywhere on the net; thankfully IT still works.  It looks like an empty browser shell that's useless.  I've tried uninstall and purge with Firefox and attempted to use Swiftfox, which while I know it runs off some of the same directories as Firefox, I was still hoping something would differ...

Anyone have an idea of how to get it working again?

---

### Post by Chandler258 on 2009-03-08
Sounds like a profile mixup. Look [here]("http://support.mozilla.com/en-US/kb/Profiles#new") and try to recover your (I presume) lost profile. And please report back =)

---

### Post by Yashiro on 2009-03-08
Close Firefox.
Browse to */home/yourname/.mozilla/firefox/* using Nautilus. 
There should be a folder called axgfwp4c.default (or similar).
The string *axgfwp4c* will differ on your system.
Right click this folder and select create archive.
Once that is complete, delete the *axgfwp4c.default* folder.

If you open Firefox now you should have a clean slate that works.
Now check for updates to your extensions from within Firefox.

---

### Post by chinamusic on 2009-03-08
I am not having problems after the updates to Firefox 3.07.  But is it normal for Firefox to consume so much memory?  According to top:

Tasks: 125 total,   2 running, 123 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.8%us,  0.3%sy,  0.0%ni, 97.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2072608k total,   812968k used,  1259640k free,    45672k buffers
Swap:  2441840k total,        0k used,  2441840k free,   303908k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6155 user      20   0  277m 109m  29m S    3  5.4   7:05.74 firefox


This is on a fully patched 8.10 system running on my notebook.  So it seems to have grabbed 109mb of system memory.  The only plugin I've got is adblock.  Seems strange.

Best,

---

### Post by noxinvictus on 2009-03-08
I woke up this morning and Firefox isn't even recognized, as in "could not launch program" although the folders in the home directory are present.  I can only assume that its location may have changed between uninstalling it, purging and re-installing it.  Nevertheless, swiftfox/minefield is working.  

I checked profiles and ended up removing it as per Yashiro's directions, which did bring Minefield to working insofar as I can now move back and forth and history is recalled.  It's a good start.

I haven't used Minefield in at around a year.  Hopefully it's more stable than it was then and I can then figure out the rest of mess by then.  Thanks for all support in this matter.

---

### Post by Rallg on 2009-03-08
After reading about earlier problems with 3.0.7, I waited a day before upgrading. But problems seem limited to a few users. After I upgraded, no problems whatsoever. And, FF 3.0.7 does not use more memory than did 3.0.6 (around 40Mb).

Someone is taking a poll on another thread. The poll is new, but the first responders report no problems.

I can only guess that there is an add-on that passed compatibility check, but should have failed.

---

### Post by emarkay on 2009-03-09
3.0.7 is OK here -  my FF is using 204 mb - seems normal for me...
There's this thread also:

[http://ubuntuforums.org/showthread.php?t=1090141](http://ubuntuforums.org/showthread.php?t=1090141)

Which one has the poll?

---

