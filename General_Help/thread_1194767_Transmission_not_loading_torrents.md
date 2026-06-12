---
title: "Transmission not loading torrents"
date: 2009-06-23
forum: General Help
---

### Post by jomo56 on 2009-06-23
The problem started when I ran out of room on the Linux partition of my hard drive.All down/up load activity stopped,along with almost everything else.I moved a bunch of folders,none of my torrent folders,and freed up 10gs of space.When I restarted transmission it sees all my torrents as 0% complete and starts re downloading them from step one,even ones that should read 100% and should be seeding.I looked at .config/transmission/torrents and all of them are there.I have even gone to the bit torrent web suite and re downloaded the bit torrent but nothing happens,I don't get the files window that I usually when You first down load a torrent where you can click add to start it.Any advise would be appreciated,I would like to start seeding again and would hate to lose my sharing ratio.

---

### Post by hibliss on 2009-06-23
Are the files stored on a drive that is not mounted? If you have them they should recheck and start seeding automatically unless they no longer pass the hash check. What type of files are these?

---

### Post by jomo56 on 2009-06-24
They are on my home folder where they always were that why I can understand why they don't auto load.They are music and dvd concerts.What is the hash check.They were all working perfectly until I ran out of hd space.

---

### Post by varunbhatbm on 2009-06-24
Use K-Torrent, its the best :popcorn:

---

### Post by hibliss on 2009-06-24
> **varunbhatbm said:**
> Use K-Torrent, its the best :popcorn:

Actually, rtorrent is the best linux client as far as resources and usability go. Of course that is all personal opinion, but rtorrent is not banned anywhere, but ktorrent is (at least conflicting versions are permitted).

Switching client is not the solution though if you are happy with Transmission. Can I get a screenshot of the torrent details in Transmission, specifically where it is storing the files?

---

### Post by jomo56 on 2009-06-24
I just downloaded a new file to see if every thing was working and if downloaded fine and is now seeding,but the old ones still won't show as already down loaded.

---

### Post by jomo56 on 2009-06-24
Would that be what shows up when I start Transmission?

---

### Post by jomo56 on 2009-06-24
I found what you want,how do I take a screen shot?Anyway it says Torrent location home/john/.config/transmission/torrents/Arcade...... but I just noticed something.The destination should be a file named Public but on the old ones it says desktop.In my preferences it is set for Public but these aren't changing.

---

### Post by hibliss on 2009-06-24
Sounds like it is just pointing to the wrong location. That is a strange location for torrents to be stored.

I am not terribly familiar with Transmission, though I do have it installed and have used it. For me, Transmission defaults to storing torrents on the desktop. You can go in to preferences and choose whatever path you like, and edit each torrent's path individually for the ones you have completed already.

---

### Post by jomo56 on 2009-06-24
Does anyone know how I could change it using command lines?

---

### Post by jomo56 on 2009-06-24
I had it set up to send them to public but when my disk space ran out it set itself to default settings.I changed it back but it hasn't changed on each file.when I open properties for the individual file it just shows the properties and doesn't let you change them.

---

### Post by jomo56 on 2009-06-24
Just moved one of my files to desktop and it started to verify it.Now if only I could get  it to find them in the public file.

---

### Post by hibliss on 2009-06-24
> **jomo56 said:**
> Does anyone know how I could change it using command lines?

If you like a command line client, rtorrent/libtorrent is for you.

---

### Post by jomo56 on 2009-06-24
No I thought maybe you could override the settings using line commands.

---

### Post by hibliss on 2009-06-24
Just move the files wherever your default directory currently is for Transmission to save downloads to. Next delete the torrent from Transmission, then reload it. It will vertify the data and start seeding. I just tested it and it works.

---

### Post by jomo56 on 2009-06-25
After I do that can I move them back to where I want?

---

### Post by hibliss on 2009-06-25
Move them where you want them to stay, and point your client (Transmission) to download to that location. Then reload the torrent file and it will recheck/verify the data and you will be seeding. There is no reason to do this twice.

---

### Post by jomo56 on 2009-06-25
I tried removing the torrent from Transmission and re downloading it and it found the file w/o moving anything.It's slow for some reason but it's working.Thanks for your help,this really had me puzzled.

---

### Post by Vikhyath on 2009-06-25
no dude, just go to preference or options screen and change the torrent file save destination:wink:

---

### Post by paul_be on 2009-06-25
If you open up transmission go to 

edit > preferences 
check the automatically add torrents from
point to where your torrent files are located 

You will also need to tell transmission where the data files are located or it will start downloading them again automatically.

---

### Post by jomo56 on 2009-06-25
If you read the thread you will see it wasn't changing the file location when I changed it in properties.It's working now.Ended up being easy but time consuming.

---

### Post by Vikhyath on 2009-06-25
configure the destination onto another partition.
And for the screenshot tool, i think it is in the application menu

---

### Post by Charles Kerr on 2009-06-28
FWIW, this is less painful to do in the newer 1.7x releases, which have a "Set Location" button.  You can use that to tell Transmission to move a torrent to, and also where Transmission should look to find a torrent's contents.

---

