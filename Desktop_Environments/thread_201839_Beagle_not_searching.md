---
title: "Beagle not searching"
date: 2006-06-22
forum: Desktop Environments
---

### Post by Hender on 2006-06-22
I've installed Beagle, and it's had days to index whatever it wants to index. Today I decided to try it out for fun, and I searched for a .pdf document in my home folder. Nothing was found.

I searched for some pictures in my home folder. Nothing found again.

Hmm.

I remembered something called beagled (Beagle Daemon) that's meant to run in the background and index stuff. I used the terminal to killall beagled, and then started the process again (this was after I'd made sure the preferences file was unhelpful in determining indexing status). I tried searching. This time, it continued searching forever without giving a "not found" error or a result.

I checked the system monitor and made sure the beagle daemon is running. I still can't find anything.

Help?

---

### Post by Hezekiah on 2006-06-22
If beagled is running and not finding anything, go to System->Preferences->Searching and Indexing
Then uncheck and recheck the "Index my home directory" box on the Indexing tab.

I have no idea why this is not working by default.  I've had the same problem on a few install I have done for myself and family as well.

---

### Post by Hender on 2006-06-22
:(

I unchecked and checked the option like you suggested, and opened beagle. First search I did, the program crashed. I reopened it, and when I searched, it found nothing.

I tried to uncheck and check again, but this time, it didn't even crash, it just didn't find anything (again).

Thanks for the help, though! :) I'll be off now for a while. Hopefully some insightful comments will have surfaced when I'm back. ;)

---

### Post by Hezekiah on 2006-06-22
It will still take a while for beagle to index your home directory - possibly hours for the initial indexing.

However, one way to check if the checking/unchecking actually did anything is to look in the ~/.beagle/config/ directory.  If you see several .xml files then things should be ok.  If not, then that may be your problem - you can try deleting the ~/.beagle directory and then doing the unchecking/rechecking thing again.

If that still doesn't work... I'm not sure what the problem is :-)  Good luck though!

---

### Post by jongkind on 2006-06-22
I had the same thing yesterday. It turned out that I had to remove the hidden .beagle folder to get it indexing again. One drawback is that this takes some time, but at least it is working again. I suspect that the course is related to a hardlock that I had the day before.

---

### Post by dpm on 2006-06-22
Not that this will bring much to this thread, but I just wanted to say that after spending lots of time trying to get it to work, asking on the beagle IRC channel and generally reading about it, I finally gave up on beagle.

I find the version on the Ubuntu repos way too buggy.

I got around most of the problems most of the time by deleting the .beagle directory as you did, but it then either takes ages to rebuild the index or it starts rebuilding the index in every session. Too many times I've been able to get beagle to see a particular file in one session but not in the next login...  ](*,)

So, I just decided to uninstall beagle altogether and wait until it is a more mature application. If we're lucky perhaps the version that comes with Edgy will be usable...

But anyway, as some developer on IRC recommended, if you place something at the root of your home directory and 'touch' it (i.e. run 'touch file-I-would-like-to-get-indexed' at the terminal), beagle will index it straight away (or as soon as it can).

Cheers.

---

### Post by Hender on 2006-06-22
Ah, I see. I found some .xml files in the .beagle/config directory, although they don't appear to be too extensive. If nothing happens for an hour, I think I'll delete the folder to be sure something's happening (I have a pretty small /home).

Thanks to everyone who helped out! I'll report back later and let you know how it went!

Here's hoping Beagle will come included in Edgy. :KS

---

### Post by Hender on 2006-06-22
:KS

I had to delete the .beagle folder, but it worked out in the end. Thanks, guys!

Beagle sure is a great app!

---

