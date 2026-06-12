---
title: "Overwritten windows"
date: 2009-05-30
forum: General Help
---

### Post by quee0849 on 2009-05-30
Hello,

I'm looking for some advice - I seem to have done something rather stupid. 

I had my parents old PIII 700MHz PC running Windows ME, and since there was no longer any, even half decent, anti-virus software available, I decided to install Xubuntu on and set it up as a dual boot. There were two FAT32 partitions previously a 12GB (7GB of data) and an 8GB (4GB), with the latter just holding documents, media etc. Using the Xubuntu installation CD I tried to free up some room for Xubuntu. Foolishly, I used the 'copy data to other partition' to copy data from the 2nd partition to the 1st, not realizing that this would overwrite the data on the 1st partition. 

Now I have two copies of the data from the 2nd partition, and windows of course will not boot. 

Is there a realistic chance of recovering the first partition (or at least some of the files)?

---

### Post by Rhubarb on 2009-05-30
Don't touch the hard drive / the computer anymore, until you have found some good ways to try and restore the data.
- If you power it up, download files etc there's a good chance it'll overwrite the old data on it.

Unfortunately I can't tell you much, as I'm a bit sleepy and don't wish to give you any information that could be mis-interpreted.

But, just to point you in the right direction, there's an application for ubuntu called "testdisk", in that package an excellent program called "photorec".
Photorec is really good at recovering lost files from accidental deletions / reformatting.

Please don't install testdisk on that computer, as doing so can overwrite the old files - you'll have to use a live CD / different computer to mount the hard drive as read only.

I'm a little confused, are all the old documents ok?  Or is it just Windows that has been overwritten?

If it's just windows, well windows can always be re-installed (or not).
If it's the documents, then stop everything and try to recover them - as they're probably quite important.

As always, it's always a good practice to backup your documents on a regular basis.

Hope this made some sense, as I am a bit sleepy here.

**Edit:**  I just read the title of this thread, so windows was overwritten.
In that case try and fish out the Windows ME disc and install it.
photorec won't be able to restore all of those files.
- Just please, please backup the documents first on a physically separate media.
It's always easier to install windows before Ubuntu.

---

### Post by quee0849 on 2009-05-31
Thanks for your message. Unfortunately there were documents on both partitions and so a fresh install of Windows ME will mean losing some data at this stage. There is only 168MB of RAM so the Xubuntu live cd runs painfully slow and sometimes hangs. 

I will try and get hold of another hard drive, install xubuntu on there and try photorec. Thanks again.

---

