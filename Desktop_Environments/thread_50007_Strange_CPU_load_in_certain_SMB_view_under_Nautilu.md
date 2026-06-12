---
title: "Strange CPU load in certain SMB view under Nautilus (repeatable)"
date: 2005-07-18
forum: Desktop Environments
---

### Post by Ethan on 2005-07-18
Hello  :-) 

Before I get to the topic of this first post, let me first of all say shortly - as a brand new Ubuntu user - that I'm *very* impressed and satisfied with my Ubuntu desktop. Haven't touched my Windows since I installed Ubuntu about 2 weeks ago!  ;-)  :razz: 

So far everything has been working perfectly for me, but in the last half an hour I've noticed something odd and I'm wondering if it's just something I am experiencing:

I'm currently in the process of migrating and copying some data from Windows machines to my Ubuntu system and I noticed that sometimes file transfers via SMB/Samba were very very slow  :-? 

Then I found a post somewhere about similar slow transfer rates where someone mentioned a thing about  Nautilus not dealing with SMB properly/fast enough... and it was recommended to just mount the Windows share using:

mount -t smbfs //machine/share /mnt/point -o username=yourwindowsuser,password=yourwindowspwd

So far so good! that really improved the rate of transfer (40GB @ ~300KB/sec is not something to be too happy about ;) )

However, at a certain moment I noticed that the speed had once again gone down from about full speed 100Mbit (inc. some accounting for overhead/headers/etc)... to that awfully slow speed again...

Suddenly I did notice that my system monitor, which I have in a panel, was indicating that something was almost completely claiming all my cpu time.... seconds later I found out that it was a Nautilus window!

Diving a bit deeper I found it was the Nautilus window, displaying the *contents* of a Windows share using the 'Nautilus way'; more specifically the "smb://machine/share" view...

However, clicking 'up'/'back' to the *overview* of this particular machines shares, cpu load dropped instantly!

Hmm..very odd.. 

Going back to viewing a directory: wham, instant 99% load.. back up.. everything's fine!

The transfer rate of the copy process running during this behaviour responded directly with a jump from 300KB/sec to ~8MB/sec and back again, depening on the view!?!  (see attached image - I'm only switching the Nautilus view between: "smb://machine" and "smb://machine/share".

Too make things even more odd imho:

it only happens when I view:

"smb://machine/D"  (10GB - FAT32)

and not while viewing

"smb://machine/E"  (80GB - NTFS)



Has anyone ever experienced something similar?

And, if so, is there any known explanation/solution for this?!
(of course I'll be watchful for it now, but it could be that others might be bitten by this as well..)


Many thanks and once again: keep up the great work on this distro, the How-To's, etc. I love it  \\:D/

---

### Post by evilghost on 2005-07-18
I think it's because you're in thumbnail view and it's reading the files (media) and attempting to generate thumbnails from the content.  You can adjust the view to use listview.  I also think under [Preferences] look at [Preview] and drop the value from 3MB to 100KB?

As FYI, I have seen this before, especially when having an open folder when copying content that is previewable, such as video's or pictures.

---

### Post by Ethan on 2005-07-19
Although it was certainly a very good sugestion, I'm always using the list view since I never seem to be able to navigate easily using the icon view somehow.  :-P 

Besides, I also always disable almost all the preview options for that same reason: I don't find it easy to use. (* there are no text files on that smb drive)

(Attached are my preferences)

It remains odd behaviour...  :-?

---

