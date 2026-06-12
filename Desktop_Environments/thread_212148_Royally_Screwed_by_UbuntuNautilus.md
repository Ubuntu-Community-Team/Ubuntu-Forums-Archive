---
title: "Royally Screwed by Ubuntu/Nautilus"
date: 2006-07-09
forum: Desktop Environments
---

### Post by Sweezel on 2006-07-09
I copied all of my Photos and Personal/Business Documents to my FreeNAS server using Nautilus, verified a few directories and wiped my disk for Dapper.

Little did I know that only about 70% of the files actually copied to the NAS! There are lots of empty subdirectories. There were absolutely no errors from Nautilus...

I will no longer trust anything in Ubuntu since I lost 30% of my digitally stored life. From now on, it's TAR, CRC, SCP, CD, BFD, AFA and whatever to copy files. Nautilus sucks and Ubuntu needs to fix it.

Can this truly be considered ready for the corporate environment, or even home user, with issues like this?

Flames and opinions are welcome.

---

### Post by woedend on 2006-07-09
i had a similar issue with moving digital pictures to the hard drive...only about 1/3 of them made it...no idea why.  sorry about your luck I feel for you!(by the way, this is most likely gnome related rather than ubuntu related)

---

### Post by Sweezel on 2006-07-09
For such a really important part of any desktop/OS, it's amazing that it doesn't work properly.

With Ubuntu supplying 5 (or is it 3) years of support for Dapper, hopefully they will fix it.

Even though the problem may be part of Gnome, it's up to Ubuntu to provide a stable solution.

What really stinks (besides the loss of pictures/documents) is the fact that I can't recommend Ubuntu due to this issue.

---

### Post by gillion on 2006-07-09
I spent an hour working on an important document in open office. 

Saved the same document to desktop. 

I plugged in my usb jump drive which brought up a nautilus window. 

I dragged the document to the open window and even saw my usb jump drive light flicker as if being written to.

When it was done, I unmounted (mac-habit) and unplugged the drive.

**Went to work, plugged the drive into my mac os x machine and no document.**

Jumped on my Windows laptop, no document. 

Called home, the document was still on the desktop (good thing i did not move it)

I have had _repeated experience_ with nautilus_ failing _to assist me in _copying files_.

I switched to kubuntu. Konqueror works much more reliably for me.

---

### Post by Rackerz on 2006-07-09
I haven't had any such problems yet, moving a 1.5GB folder worked perfectly. However I did notice when I deleted files on my flash drive Nautilus created a .Trash file which was hidden from me so I couldn't figure out why the disk space didn't free up.

It's a lesson learnt though, always check for the files.

---

### Post by gillion on 2006-07-09
> **Rackerz said:**
> I haven't had any such problems yet, moving a 1.5GB folder worked perfectly. However I did notice when I deleted files on my flash drive Nautilus created a .Trash file which was hidden from me so I couldn't figure out why the disk space didn't free up.

It's a lesson learnt though, always check for the files.

you have to empty trash

---

### Post by beameup on 2006-07-09
> **Rackerz said:**
> It's a lesson learnt though, always check for the files. Man, you got that right. Especially when dealing with pictures.
 I had a similar incident transferring pictures across my home network between 2 Windoze machines. Also while transferring from the NTFS partition to the Linux partition. I had about 4 or 5 GB of photos, and I thought to myself "man that was quick". Good thing it was a "copy" and not "cut" operation. No errors from either OS.

As much as we'd like to rely on these machines, they ARE made by humans.

---

### Post by Sweezel on 2006-07-09
At the very least, Nautilus should warn you if all files selected don't transfer. **The copy dialog should not just go away w/o warning of a failed operation.**

BTW - Would there be a log file somewhere showing these types of file operations?

---

### Post by jimmygoon on 2006-07-09
you have to unmount, nautilus some times wait to copy the files until after you've unmounted it. thats why it seems like an instantaneous copy and then it takes for ever for it to "unmount" later... because it is still copying.

I did that once with a USB drive too, and once I learned to unmount I've never had a problem since.

---

### Post by gThree on 2006-07-09
I've also had a problem or two copying large folders between a Ubuntu partition and a Kubuntu partition.  Some sub-folders/files didn't show up, no error.  Thought it was while using Konqueror on Kubuntu side, but could be wrong.  Now in habit of checking files in that situation.  No problems otherwise.

Reading this thread made me realize I have muCommander (Java, both), Midnight Commander (Ubuntu), and Krusader (Kubuntu) installed.  Should be using them more often to see if they're more reliable.  Anyone have enough experience with them to compare to Nautilus/Konqueror?

---

### Post by Sweezel on 2006-07-09
I tried Gnome-Commander with similar losses...

Is it Samba causing the issues?

---

### Post by mssever on 2006-07-09
> **Sweezel said:**
> I tried Gnome-Commander with similar losses...

Is it Samba causing the issues?

Are you familiar enough with the command line to test copying that way (by using cp, etc.)? That would help to isolate the problem. I've never had such a problem, but then I rarely use anything but the command line for file management.

---

### Post by Sweezel on 2006-07-10
cp -a gets:

8582 items, totalling 13.1 GB received by FreeNas

8621 items, totalling 13.2 GB was the original size/amount


That's a lot better, but where are the other 39 files?](*,)

---

### Post by mssever on 2006-07-10
That's odd. Maybe it's a problem with FreeNAS? I have no idea what FreeNAS is, but the fact that it doesn't work even from the command line provides pretty good evidence that Nautilus isn't at fault here IMO. Adding the -v flag to cp might help (cp -av files destination > output) if you look in the output file for info. Of course, there are a lot of files to wade through...

---

### Post by mdurham on 2006-07-10
try sudo cp -a
maybe it didn't copy some files that don't belong to you???

---

### Post by DavidFL on 2006-07-11
> **Sweezel said:**
> I copied all of my Photos and Personal/Business Documents to my FreeNAS server using Nautilus, verified a few directories and wiped my disk for Dapper.

Little did I know that only about 70% of the files actually copied to the NAS! There are lots of empty subdirectories. There were absolutely no errors from Nautilus...

I will no longer trust anything in Ubuntu since I lost 30% of my digitally stored life. From now on, it's TAR, CRC, SCP, CD, BFD, AFA and whatever to copy files. Nautilus sucks and Ubuntu needs to fix it.

Can this truly be considered ready for the corporate environment, or even home user, with issues like this?

Flames and opinions are welcome.

I agree about your criticism.  However these sorts of problems are not unique to Ubuntu.  On windows prior to wiping everything and reinstalling I backed up my files to cds. I used Nero and used the verify compilation option.  Well come to find out one of the disks had massive errors and so I lost a lot of data. :(  I guess there are a lot of things that can happen between the software and the hardware.

---

### Post by quonsar on 2006-07-11
i noted the same thing when copying files to my usb hard drive. next time i'll try the unmount thing - but this really really sucks and ought to be fixed.

---

### Post by JoWilly on 2006-07-11
Geezz....

Can you please **post a CRITICAL bug on launchpad** (search first) with a link to this thread _to inform the developers_ of this major problem so many people are having.

Edit: _AND people then please add a comment _once this bug is opened to confirm it, devels need to know many are confirming this to react.

---

### Post by sdhoigt on 2006-07-11
> **gThree said:**
> Reading this thread made me realize I have muCommander (Java, both), Midnight Commander (Ubuntu), and Krusader (Kubuntu) installed.  Should be using them more often to see if they're more reliable.  Anyone have enough experience with them to compare to Nautilus/Konqueror?

I've used Midnight Commander for 4-5 years.  Aside from a few minor annoyances, I highly recommend Midnight Commander for its 'get to the crux of the matter' file management.

Funny, the only file manager I like better is [2xExplorer]("http://netez.com/2xExplorer/") ([xplorer²]("http://zabkat.com/")) for Windows.  Krusader for Linux is close.  Actually, I should spend some more time with Krusdaer.  I tried it ~3-4 years ago and am happy to see it has come a long way since those days.

Nautilus is just about worthless IMO.

---

### Post by RAOF on 2006-07-11
> **quonsar said:**
> i noted the same thing when copying files to my usb hard drive. next time i'll try the unmount thing - but this really really sucks and ought to be fixed.
I remember the devs discussing this (or, more specifically, using the *sync* option on mounting removable media).  One problem with this option is that it can really kill disc performance (depending on how you're using the disc).  I belive the final decision was to enable sync (in Edgy, I believe), but even so you should still unmount (even in windows, although it's called "Safely remove hardware").  Failing to unmount will **eventually** destroy something that you care about, whether it's from Windows, Linux, or MacOS.  The sync option will merely make it take longer before that happens :)

---

### Post by Sweezel on 2006-07-12
I am ecstatic by the success of cp -a compared to Nautilus and Gnome-Commander.

This is what I reported, but I am not sure it is a complete enough report to be noticed. I also don't know how to mark it critical.

[https://launchpad.net/distros/ubuntu/+bug/52452](https://launchpad.net/distros/ubuntu/+bug/52452)

**Please add your comments to the bug to help get some attention.**

---

### Post by ba5e on 2006-07-12
I have had just misery with nautilus...it truly is full of bugs:

1)mounted a Promise RAID array once fine into ubuntu, opened the FAT32 partition on array in Nautilus and it trashed the lot on there!! (thinking hard for 10 minutes!)

2)Nautilus randomly closes/crashes EVERY time for me if I right click on a directory in the tree menu on the left and select delete.....EVERY TIME! try it yourself, and maybe we can raise a bug

3)Nautilus as you have all stated does NOT copy files correctly, it is also slow and can spit out not a single error to the user this makes me scared :(

---

### Post by Sweezel on 2006-07-13
Reported your bug with the Tree View as:

[https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/52836](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/52836)


Nautilus has issues and we need to report them all. I rely on the base Ubuntu programs to be stable and user friendly. So far, Nautilus and vino-server have failed miserably.

---

### Post by Sweezel on 2006-07-13
Let's try having 20 people comment on this bug to see if it gets "Triaged" faster.

I reported a bug on gfloppy and it has not been triaged in twenty days. I do not know a better way to move things like this along than a conspiracy.

[https://launchpad.net/distros/ubuntu/+source/gnome-utils/+bug/50685](https://launchpad.net/distros/ubuntu/+source/gnome-utils/+bug/50685)


Another example is vino-server. I have a slow computer everytime I log into my home PC from work. When I get home, the PC I logged into has to have vino-server killed or everything is slow. 

What is really scary, is that System Monitor only shows other programs taking up the CPU and vino-server looks fine sleeping there. But, when I kill it, everything goes back to normal speed.

Another scary thing is that fixes/patches are made, but don't make it into a release in a timely manner!

[http://bugzilla.gnome.org/show_bug.cgi?id=154467](http://bugzilla.gnome.org/show_bug.cgi?id=154467)


I am still trying to understand how things work in this Ubuntu world, but I know what I expect. Especially when I donate money and/or buy desktop support from Canonical.

---

### Post by phico on 2006-07-13
I had many issues also.  Go to the /tmp folder, from the left column
try to erase a folder (right click> move to garbadge bin) .... Nautilus
crashes ?!?! :confused:   Many other issues like other with missing files
or crashes while copying.  This is a serious problem in Ubuntu ...

---

### Post by mmcmonster on 2006-07-13
I had a large pictures folder w/ multiple subdirectories that I copied from an ext3 partition to an external HD fat32 partition.

I cam back later and the operation had completed.  Little did I know that it had just aborted in the middle.  Nautilus gave no error message.

My problem:  [B]Nautilus does did not give an error message when copying two files with similar names except for capitalization from a case-sensitive file system (ext3) to a case-retentive file system (fat32).

This is a big issue with photos, since various cameras (and sometimes the same camera mounted in different ways) use different rules for capitalization.
[/B]

---

### Post by mmcmonster on 2006-07-13
Also see [Bug 52881]("https://launchpad.net/distros/ubuntu/+bug/52881"), which I just filed for my issue.

---

### Post by dglock on 2006-07-13
Check your /etc/fstab for the drives in question.

  If the line in fstab says noexe then you need to change it to exe. noexe means it doesn't do the copying at the time you copy the files.

  don

---

### Post by MLevin on 2006-07-13
> **dglock said:**
> Check your /etc/fstab for the drives in question.

  If the line in fstab says noexe then you need to change it to exe. noexe means it doesn't do the copying at the time you copy the files.

  don

Did you mean "sync" flag? The one, "noexe" (noexec?) dealing with the copying files is new to me...

---

### Post by mmcmonster on 2006-07-13
I filed a gnome bug, [Bug 347457]("http://bugzilla.gnome.org/show_bug.cgi?id=347457"), regarding the issue that I mentioned earlier, and linked to it in [the bug I filled in launchpad]("https://launchpad.net/distros/ubuntu/+bug/52881").

---

### Post by Boelcke on 2006-09-16
Here's a similar Nautilus bug for you, where I think the ultimate error is not that it couldn't do what I asked, but that it provided no error flag whatsoever.

I was shuffling files around, and tried to move a 6Gb .tar file from an ext3 partition to a fat32 partition.  I had selected it, along with half a dozen other files.

Little did I know that FAT32 can't handle files above 4Gb.

Anyhow, Nautilus would copy one or two of the other files, and then just stop.  No error, no indicator at all.  The only way I knew something was wrong was because I was only copying 6 files over, and when I checked, only 2 had made it.  I would have never found it in a mess of files, unless I did a filecount.

Now, at the command line, ```
cp -a /fromfile /tofile
``` really did the trick.  When it choked, and falied to copy the file, I got an error message that gave me some clue about what was going on.  Nautilus really needs to provide that error message.

I too, share your loss of a warm fuzzy feeling.  I haven't been tempeded by the KDE desktop, because it's more processor intensive on my old, slow PC.  However, errors with no indicators are the worst there are, and it has me thinking...

---

### Post by pt123 on 2006-09-16
This is ridiculous how do they plan on releasing it to corporate clients? Are these bugs found in Suse's SLED?

---

### Post by mips on 2006-09-20
Now that I read this I recall a similair experience before I switchd to Kubunutu. Also copied files but they were not all at the destination.

---

