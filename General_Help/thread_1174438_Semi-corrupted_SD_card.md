---
title: "Semi-corrupted SD card"
date: 2009-05-30
forum: General Help
---

### Post by MrKimi on 2009-05-30
This one may fall between the cracks of everything else but it was all working fine until Linux got involved so I think it does belong here.

I have an SD card in my Nikon 3200 camera. I have a Dell Insprion 9400 laptop with an SD reader. Under Windows XP I have been transferring photos for year now by pulling the SD card out of the camera and putting it into the laptop. No problems.

But I am migrating this laptop to Unbuntu 8.04 (yay!) and everything is going very well. I thought I had better check the SD reader was working. No problem. Ubunu saw the card when I inserted it and loaded the phot app (I forget which one) to load the photos etc. Very nice.

Then I put the card back into the camera and it told me it could not read the card? Huh? Well it never did that before. I put the card back in the laptop, no problems. I rebooted Windows, still no problems. Something happened to the card that the camera doesn't like. Something that involves Ubuntu and not Windows.

The specifcs from the camera are that it says 'Out of memory' on startup and if I try to display existing photos then I get WARNING!! THIS CARD CANNOT BE READ. There is lots of space on the card according to both Windows and Linux.

Anyone else seen this? I searched a lot for this, but didn't find anything.

Obviously I can reformat the card and it will probably come right. What I need to learn is how to avoid having to format the card every time I copy photos from it. Also note that I haven't lost any photos 'cos I can read them from the computer. I have, however, lost the use of my camera because it needs an SD card that works.

---

### Post by dcstar on 2009-05-30
> **MrKimi said:**
> 
........
I have an SD card in my Nikon 3200 camera. I have a Dell Insprion 9400 laptop with an SD reader. Under Windows XP I have been transferring photos for year now by pulling the SD card out of the camera and putting it into the laptop. No problems.

But I am migrating this laptop to Unbuntu 8.04 (yay!) and everything is going very well. I thought I had better check the SD reader was working. No problem. Ubunu saw the card when I inserted it and loaded the phot app (I forget which one) to load the photos etc. Very nice.

Then I put the card back into the camera and it told me it could not read the card? Huh? Well it never did that before. I put the card back in the laptop, no problems. I rebooted Windows, still no problems. Something happened to the card that the camera doesn't like. Something that involves Ubuntu and not Windows.
.........

Did you unmount the card before "pulling it out" (as you must do with **all** removable media), if not then chances are you corrupted the filesystem.

Put the card back into the system and use the Partition Editor to unmount it and then run a Check on it.

---

### Post by MrKimi on 2009-06-02
I possibly failed to unmount in all the excitement of seeing it just work:(
But I just used the partitioner to check it: yes there were errors.
So I ran the format and another check, no errors now.
But the camera still doesn't like this card. 
I tried another card reader and that is happy.

I reformatted the card using the camera and it still doesn't like it.
I think I will get another card and make sure I have not got a problem on the camera.

Thanks for the help though. Still finding my way around Linux. Used to be a Unix guru long ago so I should know better than to fail to umount, but it was long ago.

---

