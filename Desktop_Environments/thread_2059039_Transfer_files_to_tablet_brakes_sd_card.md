---
title: "Transfer files to tablet brakes sd card"
date: 2012-09-17
forum: Desktop Environments
---

### Post by rpdayton on 2012-09-17
I posted all of this problem [here]("http://ubuntuforums.org/showthread.php?t=2057276") but no body helped me with it not even to tell how to file a bug report.

So maybe it isn't a hardware problem but a desktop problem which I din't think of when I decided to post it, since the forum is called "Hardware / Laptops" I thought it was a hardware problem but I don't know.

But basically here is the issues:

I have ubuntu 12.04 on my desktop.
I plugged in my tablet (pandigital) to the usb to put music files on it, onto the memory card (32 gb pny microsd)
The files (50 files) began copying fine, but after about 50% it got slower and slower and slower, then finely stopped and ubuntu gave an error that the microsd card could not be found.
after a few seconds, it opened up like I had just plugged it in, only now i cant copy files to it because it says it is "read only".
I did a 'safely remove', and restarted my tablet, but now it says the card is not mounted or has no files.
I put the card into the card reader on my desktop, and ubuntu finds it, with all the files, but wont let me copy any files to it because it is 'read only'.
I put the card in my windows laptop, and it also says it is read only.

fsck dosfsck, chown, and remounting the drive all fail because "read-only file system."

Windows chkdsk finds nothing wrong, but cannot do a "automatically fix file system errors" because it is a "read only file system".

I see a lot of mentions online that complain about ubuntu making read-only file systems on memory cards, and i see a lot of mentions about file transfers in ubuntu getting slower and slower.

is this something that can be fixed or do i need to loose all my data and start all over, and why does ubuntu have a big problem causing this?

Then I tried to do this:

ok I took a 16gb pny card that was in my music player and i put it in the tablet and formated it with android. it was a good memory card and it was used for allmost a year with no troubles. if this works then it was a bad 32gb pny card.
i copied lots of files from the tablet's internal memory onto the sd card and it copied them just fine.
so then i copied 1 or 2 pictures from my ubuntu desktop computer and it copied them just fine using nautilus and drag and drop method.
then i copied a few songs about 2 or 3 and they copied fine.
then i tried to copy 10 songs at once and it copied the first ones ok then it got slower and slower and finely after about 5 minutes it said there was an error copying because it couldnt find the memory stick anymore.
so then i turned off the tablet and put in the memory stick to the card reader and yep it is read only now.
my windows laptop also said it is read only
so i erased it formatted it in windows on my laptop and then i copied files from windows to it almost 4 gb and no problem and very fast.
so i put it into the tablet and it can see all the files and i copy them from the card to the internal memory with no problem.
then i put the card in my ubuntu 12.04 desktop and after copyed 6 songs, about 56 mb, it slowed down and finely said it cant find the device then it was read only again.
i started my desktop with the live dvd and tried it from there and yep. same thing, still made it read only.
so now i took my 32gb card and reformated it and in windows it works just fine and in the tablet it works just fine but i want to know: how can i copy files from ubuntu to the card without making read only?

And finely I tried this:

ok so I had an idea to download a brand new live disk of ubuntu 12.04 and boot my laptop to ubuntu.
and just to make sure, i bought a new memory card (8gb).
and so I used windows chkdsk to make sure the card was good, and no errors found.
and then i used windows to copy "my documents" (about 200 files) and it only took a minute to copy with no problem.
then i erased them and ran chkdsk again, and no problem.
so the card is good right?
then I booted my laptop to the ubuntu live disk and tried to copy the same files from windows documents to the card and it copied and copied and copied and got slower and slower and finely it gave an error that it couldnt find the card anymore.
then i rebooted my laptop to windows (xp) and ran a chkdsk and ut oh its read only.
and i put it in my tablet and it cant mount it.

in conclusion: the only thing that makes my cards read only is ubuntu and on 2 different machines all together. so anyway with so many people online talking about how slow it is to copy files after a while in ubuntu and lot's of people saying they got a read only file system from ubuntu then what is the way to fix it?

And then I posted that maybe it is a bug which a lot of people report about but never filed a bug report, so do you know how I can do that if nobody is able to fix it here?  And if it is quick enough then maybe they can fix it before they get 12.10 made so everybody can not have this problem anymore \\:D/

Thank you very much.

---

