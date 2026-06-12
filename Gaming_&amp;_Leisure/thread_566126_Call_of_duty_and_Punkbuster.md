---
title: "Call of duty and Punkbuster"
date: 2007-10-03
forum: Gaming &amp; Leisure
---

### Post by Hightide on 2007-10-03
Hi All
punkbuster kicks me when on multiplayer.  Doent seem to recognise Ubuntu.

any ideas to get around tghis

regards
:)

---

### Post by Circus-Killer on 2007-10-03
sorry for posting a question in your thread hightide. i was just curious, are you running call of duty through wine?

---

### Post by Hightide on 2007-10-03
Hi Circus Killer

no. I used a loki installer

hope this helps

---

### Post by Circus-Killer on 2007-10-03
that sort of helps. i'm still trying to understand this whole loki installer thing. in its own homepage it often refers to the installer as a single thing, but then also refers to multiple installers for different games.

i'm also confused as what the loki installer does. does it allow you to run the game in question natively? anywyas, thanks for the reply. will have to look into that loki installer thingum.

edit: sorry, i just took at the loki homepage and i cant find the download for call of duty.this is the page i went to [http://www.liflg.org/?catid=6](http://www.liflg.org/?catid=6)

any ideas where i get this installer from?

---

### Post by psiu on 2007-10-03
not sure what the loki thing is but....part of the Punkbuster regimen is a couple of background services in Windows, they need to be running or you will be kicked.

As an aside...I hate PB. It's also decided to not play nice with most of the graphics card tweaking tools sometime over the summer--I run on ATITool on the WinXP machine. Very nice, completely random hard locks...*sigh*.

---

### Post by Circus-Killer on 2007-10-03
thanks again. yeah, it appears that nobody is 100% sure whats with these loki installers. i think they might just make installation of games under wine a little easier. but i could be wrong.

i also find it strange that half the installers (ones that are considered old) are not available from the loki projects home page. i mean, even if they created an archive page for the old downloads, would of been better than nothing at all. but alas, what can you do. i ended up just downloading it from another site.

as for punkbuster, its only great if you run windows and if the server you connecting to is 100% up to date. just connecting to my local enemy territory server was a nightmare because the server i was connecting to had an old version of PB running, and i had the latest.

i actually have given up on internet gaming from the pc in all honesty. the only time i play  online anymore is when im playing xbox. the only games i play on my linux box now is single players.

---

### Post by Hightide on 2007-10-03
Hi Guys

i am not a Loki expert but i asked forums for advice in stalling COD on ubuntu. I got this great advice ([http://ubuntuforums.org/showthread.php?t=561938&highlight=call+of+duty](http://ubuntuforums.org/showthread.php?t=561938&highlight=call+of+duty))

The game works well and is not based on wine.

Yes dont like PB. It seems to prefer Windows thus ny query about playing online with ubuntu

regards

---

### Post by brennydoogles on 2007-11-03
> **Circus-Killer said:**
> thanks again. yeah, it appears that nobody is 100% sure whats with these loki installers. i think they might just make installation of games under wine a little easier. but i could be wrong.

i also find it strange that half the installers (ones that are considered old) are not available from the loki projects home page. i mean, even if they created an archive page for the old downloads, would of been better than nothing at all. but alas, what can you do. i ended up just downloading it from another site.

as for punkbuster, its only great if you run windows and if the server you connecting to is 100% up to date. just connecting to my local enemy territory server was a nightmare because the server i was connecting to had an old version of PB running, and i had the latest.

i actually have given up on internet gaming from the pc in all honesty. the only time i play  online anymore is when im playing xbox. the only games i play on my linux box now is single players.

From looking at the loki installer itself,i believe it actually installs the game in wine, and then creates a launcher in your path to run it from linux.

---

### Post by groovomata on 2007-11-03
Here is a list of loki game installers I found. I can play Call of Duty and United Offensive both single player and online no problem, however I am, as well, getting kicked because of a punkbuster problem.
[http://mirrors.ecology.uni-kiel.de/games/liflg/wine/](http://mirrors.ecology.uni-kiel.de/games/liflg/wine/)
Additionally I found good advice from the Winehq site. Just look up 'Call of Duty'. Also, this site gave me some good advice running. Yes, loki installed programmes do use wine to run. 
[http://gaming.gwos.org/doku.php/wine:winestuff](http://gaming.gwos.org/doku.php/wine:winestuff)
All the best,
Erik.

---

### Post by Frak on 2007-11-03
I've learned from many issues of this, just forget multiplayer on Linux, or play it on Windows. I'ven't seen anyone get PB to work under Wine.

---

### Post by groovomata on 2007-11-04
Actually there is a site: [http://www.punkbuster.com/index.php?page=pbsetup.php](http://www.punkbuster.com/index.php?page=pbsetup.php)
It has a linux update for punkbuster called pbsetup.run. I can't seem to install it though. I have been able to play on some servers successfully however I've been getting kicked of many. The interesting thing is that until I installed the same punkbuster update for Vista, I was getting kicked off on Vista too. 

To install it I changed to the directory and tried: sudo sh pbsetup.run but it didn't work. If anyone can figure out how to install that file please post back, as I'd really like to give it a try. 
Thanks,
Erik.

---

### Post by Frak on 2007-11-04
Try just running sudo pbsetup.run in the terminal.

Great find also.

---

### Post by groovomata on 2007-11-04
I tried 'sudo pbsetup.run' and I get the response: command not found. What is interesting is that pbsetup.run has a similar name to other files with a .run extension but the icon looks different, which indicates that it is a different kind of file and needs to be handled differently. Does anyone know how to launch or install this file?
[IMG]http://www.flickr.com/photos/86733040@N00/1856654448/[/IMG]

---

### Post by Frak on 2007-11-04
try
```
sudo bash pbsetup.run
```
I suspect its wanting a shell.

---

