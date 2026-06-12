---
title: "Using a Sansa c250 with Ubuntu"
date: 2009-01-06
forum: General Help
---

### Post by Kopachris on 2009-01-06
Well, I just bought a refurbished SanDisk Sansa c250 MP3 player.  The features initially looked very good, FM radio, recording, FM radio recording...  The problem is that it just didn't want to work well with Ubuntu.  It took a while for Ubuntu to mount it, and then it was usually as a USB drive.  The main problem getting in the way of using it is that SanDisk updated their firmware, taking out the USB option in the Settings menu that allows you to switch between MTP (Media Transfer Protocol, the default) and MSC (Mass Storage Compliant).  My guess is that this is supposed to be some sort of DRM compliance.  Make it harder for them to put pirated songs by taking away drag-and-drop. :mad:

Well, I had to dig through Google results to fix it, but here it is: [http://forums.sandisk.com/sansa/board/message?board.id=...]("http://forums.sandisk.com/sansa/board/message?board.id=c200&thread.id=2135&view=by_date_ascending&page=1")
That's where most of the info in this tutorial comes from.

Anyway, for step 1, you need to download an older firmware.  This older firmware is totally unsupported by SanDisk, and putting this old firmware on your Sansa might void whatever warranty you might have, but it *does* work.  The firmware package is [here]("http://files.zefie.com/PMP/sansa/c200/v1/firmware/1.00.03/").  If you're in America, download and unzip the one with an 'A' in it.  If you're in Europe, download and unzip the one with an 'E' in it.  The packages are 7-zipped.  I think Ubuntu's archive manager comes *with* that functionality, but I'm not sure since I installed 7-Zip from the repos virtually as soon as I installed Ubuntu.

Once you have it unzipped, you should have three files in the folder that it unzipped.  Now we need to boot the Sansa into utility mode so we can manually "update" the firmware.  First, turn your Sansa off and unplug it from your computer.  Now, move the "Hold" switch in the lock position (so that the orange is showing).  Press the power button **while holding down the record button**.  When it asks you to plug in your USB cable, you can let go of the record button and plug in the USB cable.  After a few seconds (or a few minutes), you should have a 16MB volume showing up as a USB device.  Go into it and drag the three files that you unzipped into the 16MB volume.

Now here's the weird part.  You'll either have to turn off your Sansa and then unplug it and turn it back on to update the firmware, or you'll have to simply unplug it (without ejecting) and it will update its firmware right then and there.  I don't think there's any way of knowing which of the two methods will work, so I'd try the first one first, then if that doesn't work, I'd try the other one (you'll have to boot into utility mode and drag the files over again).

Now me, I already had all my music moved over to my c250 before I rolled-back the firmware like this.  I put it in MSC mode via the USB options in the settings menu, but the songs still weren't there.  I left it overnight because it was late and time to go to bed.  This morning, I plugged it in, ready to move all the songs over again, then unplugged it because I realized I should make sure that I *did* put it in MSC mode.  Lo and behord, it began reconstructing the database right before my very eyes.  Now all the music is there.

Now the old firmware is picky about whitespace in the filenames (use underscores) and the ID3 tags.  It won't use songs with ID3 v1 tags, so you'd have to convert them all to v2 and get rid of the v1 ones.  It's also picky about whitespace in the genre tags (can't handle it).  I don't think the same restrictions apply to the new, older firmware, but if it does, please let me know so I can add that to this post.  Thanks, and enjoy your new Sansa c250! :)

---

