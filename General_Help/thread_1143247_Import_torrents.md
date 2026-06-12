---
title: "Import torrents"
date: 2009-04-29
forum: General Help
---

### Post by screaminj3sus on 2009-04-29
Ok, so I have tons (around 200) torrents seeding on utorrent in windows. I want to be able to seed all the same ones in linux using deluge. Is there a way I can import all the torrents I have in windows into a torrent client in linux? re downloading the .torrent files would literally be impossible.

---

### Post by NFblaze on 2009-04-29
I dont know what client you use in Vista but see if  you just get the torrent files into a temporary folder in Vista... and then drag and drop in ubuntu Transmission.

Do a search on your computer in Vista for .torrent and see if you can see where the temporary torrent files are stored.

---

### Post by screaminj3sus on 2009-04-29
I'm using utorrent.

The big problem is I found the files but  lot of them are stuff I haven't been seeding in ages, and I have my torrents I uploaded myself in a  separate folder so deluge is trying to download all of them.

---

### Post by aktiwers on 2009-04-29
I have the same problem in Ubuntu alone..  Started out using Vuze a long time ago, to respect some tracker rules, now Deluge is finally allowed to use, but all my seeds are in Vuze, pointing in all directions.

Not hijacking the thread, just keeping an eye with the responses :)

---

### Post by NFblaze on 2009-04-29
Thats really confusing what you wrote....but this is how i bring the files i want to seed from Vista

I use the default transmission and what seems to work for me is to copy the torrent. Open it into transmission let it download like .01 percent or something... that makes it create the partial file and the folder and such...so then I just overwrite the partials files with the already completed ones from Vista... restart Transmission, file is at 100%, and it keeps seeding.

---

### Post by screaminj3sus on 2009-04-29
> **NFblaze said:**
> Thats really confusing what you wrote....but this is how i bring the files i want to seed from Vista

I use the default transmission and what seems to work for me is to copy the torrent. Open it into transmission let it download like .01 percent or something... that makes it create the partial file and the folder and such...so then I just overwrite the partials files with the already completed ones from Vista... restart Transmission, file is at 100%, and it keeps seeding.

Probably because its confusing how I have things organized haha.

I have one folder that I downlaod everything to and seed from, and when I upload my own torrents, I keep those files in a different folder.

I tried importing all the .torrent files from utorrents appdata folder into deluge. I had deluges download location set to the same folder as my utorrent one so those torrents got checked and started seeding, but all the others try to download (which I can probably fix myself)
The biggest problem is a LOT of the torrent files in utorrents appdata folder are really old ones that never got deleted and are torrents I don't want to seed and it will take forever to manually weed them out.

I just wish utorrent had a way of only exporting my currently in use .torrent files :(

---

### Post by NFblaze on 2009-04-29
So you just want the torrents that are currently running...well Im not home right now but maybe if you navigate to your /AppData in Explorer and then enable the Details mode... and add the extra detail tab of Last Accessed.

Then run utorrent...maybe try to right click "Update Tracker Data" or whatever the choice is for the running torrents.

 Go back to explorer then click the Last Accessed to sort by the date it was Last Accessed...maybe all the ones you updated from tracker will have the most recent Last Accessed dates...

but then again Im still at work...Try it out let us know...

---

### Post by mb_webguy on 2009-04-29
Actually, you're liable to run into problems dropping torrents you're seeding or downloading in Windows into your Linux client, because the paths to those files are going to be different.  So even if you do manage to identify your active torrents, you're going to have to go through them and manually set the file locations for each one.

---

### Post by screaminj3sus on 2009-04-29
> **NFblaze said:**
> So you just want the torrents that are currently running...well Im not home right now but maybe if you navigate to your /AppData in Explorer and then enable the Details mode... and add the extra detail tab of Last Accessed.

Then run utorrent...maybe try to right click "Update Tracker Data" or whatever the choice is for the running torrents.

 Go back to explorer then click the Last Accessed to sort by the date it was Last Accessed...maybe all the ones you updated from tracker will have the most recent Last Accessed dates...

but then again Im still at work...Try it out let us know...

good idea, I'll have to give this a shot.

@mb_webguy you are right but I have all my torrents in only 2 folders, whicever ones don't start seeding I'll know which folder to move them all to.

---

