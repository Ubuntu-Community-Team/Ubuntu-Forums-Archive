---
title: "Howto:  Get Listen 0.5 Beta"
date: 2006-09-04
forum: Desktop Environments
---

### Post by Uncle Spellbinder on 2006-09-04
I just got the newest version of *Listen* installed. It scanned my large amount of mp3's (24,900+) in about 9 minutes. _Much_ quicker than the earlier version.

**For those who want to get the latest version, follow this quick howto:**. 


[color=#990000]**REMEMBER: This is NOT official Ubuntu repo - USE AT YOUR OWN RISK**[/color]

In terminal: 
```
gksudo gedit /etc/apt/sources.list
```

Then add:
```
##### Listen #####
deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen listen-unstable

##### Musicbrainz  (Gathers artist info from the web) #####
deb [http://users.musicbrainz.org/~luks/ubuntu](http://users.musicbrainz.org/~luks/ubuntu) dapper main
```

You'll need the public key for Musicbrainz. In terminal, type:
```
gpg --keyserver subkeys.pgp.net --recv 3A39A02A92132F7B
```
then press *Enter*

Then:
```
gpg --export --armor 3A39A02A92132F7B | sudo apt-key add -
```
Press *Enter*.

Then:
```
sudo apt-get update && sudo apt-get upgrade
```

If you have a previous version of Listen installed, this will get you up-to-date. If you don't, open Synaptic and Listen's new version will be there.

*Happy Listening*! [img]http://www.compiz.net/img/smilies/138.gif[/img]

---

### Post by Dr. Nick on 2006-09-05
worked like a charm, thanks

I like what I see, more windows resizeable then before.

---

### Post by Dr. Nick on 2006-09-05
Anyone else having problems changing views? If I swithc views it will work, but cant switch back to default. I have to erase the .listen folder to reset it

---

### Post by Uncle Spellbinder on 2006-09-05
I'm not having problems switching views. I just switched from default to small to normal and party mode and back again. Also tried the 3 browser views with no problem.

---

### Post by hanzomon4 on 2006-09-05
Can you listen to audio cds.
I checked the source from svn and their were some files that mentioned audio cds.
When I compiled the 5.0v it said something like "Audio cd = no", like I could have compiled with audio cd support. 
But their was only a make file.

[EDIT]this is what 5.0v says
```
No musicbrainz2 support
No musicbrainz2 support
No Audio cd support
0 songs and 3 playlists loaded
0  in pl  Master
0  in pl  Podcast
0  in pl  iRadio
load took 2.826ms
start monitoring
Update Context
```

---

### Post by hanzomon4 on 2006-09-05
Yay, I got audio cd support by downloading some optional libs.

By the way does anyone no how to build 5.0 with musicbrainz support i got all the optional libs

---

### Post by hanzomon4 on 2006-09-05
Ok I built it from svn and had an issue with it not reading my m4a files.
I checked the deb in the repo and it has the same issue.
I can play m4a files off my ipod so listen can play them, I filled a bug for the problem.

Now I got all the optional stuff compiled(Audio-cd Musicbrainz) in the svn version(when I checked the one in the unstable repo it was the same as mine so..)

To my surprise it had
1.Audio cd support
2.A single button to download all missing album covers
3.All the panels were resize able
4.It played the m4a music files off my ipod
5.It played my mp4 [COLOR="Red"]VIDEO FILES[/COLOR] off my ipod as well

Theirs someother stuff that I haven't played with yet, but Its nice can't wait tell its finished

---

### Post by ayoli on 2006-09-05
the 0.5beta from Uncle Spellbinder's howto works fine for me and do/play everything i need, many thx. the scan of my mp3 folder was quicker than before indeed.
i just need to find howto start on library view instead of context view. 
regards.

---

### Post by hanzomon4 on 2006-09-05
Did it catch your mp4/m4a files(if you have any)

---

### Post by ayoli on 2006-09-05
> **hanzomon4 said:**
> Did it catch your mp4/m4a files(if you have any)

actually i havent got any mp4 files :)

---

### Post by Dr. Nick on 2006-09-05
My view problems are fixed now, their was a new update today and Ive yet to have issues

---

### Post by hanzomon4 on 2006-09-05
How do you add songs to playlist on an ipod

---

### Post by Hairy_Palms on 2006-09-07
i cannot get 0.5 to play m4a files, i get the no musicbrainz2 error even though i have all the updated files from the musicbrainz repo whereas 0.4.3 playsthem perfectly, i compiled it and installed it in /usr/local so i can have both at the same time. has anyone got m4a files to play in the latest release?

---

### Post by Coolit on 2006-09-07
What a great little program :) 

0.5 started ok but I was unable to add to the library (fresh install, no older version installed), so I removed 0.5, installed the latest stable version, then upgraded to 0.5 and it works fine now. Weird bug :(

Anyway, great program, I've moved from Rhythmbox to it:)

---

### Post by Tritan on 2006-09-08
My iPod mini (fat32) doesn`t get detected - any idea`s? It has been marked under *View > Middle view > iPod*, so it should show, right?

---

### Post by jkroto on 2006-12-14
> **hanzomon4 said:**
> How do you add songs to playlist on an ipod

Did you get an answer for this?  I can't make it add songs either.

---

