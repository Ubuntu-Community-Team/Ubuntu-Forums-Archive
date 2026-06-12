---
title: "Unreal Tournament 2004 Demo for Linux; Doesn't read"
date: 2006-04-29
forum: Gaming &amp; Leisure
---

### Post by TheIdiotThatIsMe on 2006-04-29
For some reason, I cannot seem to install a demo of UT2004 no matter where I download it from. I've downloaded the demo 3334 version of UT2004 (as far as I know it's the latest version) from at least four different sites and I keep running into the same error. Someways during the installation, I get "Error: Read failure on ut2004demo.tar.bz2. What I dont understand is that is passes the archive integrity check, and the download always seems to go fine, so I cant understand why it just crashes like this?

---

### Post by TheIdiotThatIsMe on 2006-04-30
I'm guessing it's a problem with the way things are downloading now? I've tried downloading a zip of Enemy Territory, and it cant open the package. I downloaded a 3120 version of UT2004 compressed and it wont read that archive either. I've tried downloading a .run installer of UT2004 linux and it gets the read error. What is going on all the sudden ](*,)

---

### Post by Denta on 2006-04-30
I'm having problems too...
denta@datorn:~$ gzip -d UT2004-LNX-Demo3334.run.gz
gzip: UT2004-LNX-Demo3334.run.gz: unexpected end of file

---

### Post by Adrian_b on 2006-04-30
Try downloading it with WGET?
Maybe it's just Firefox handling it wrong..

---

### Post by TheIdiotThatIsMe on 2006-04-30
[QUOTE=Adrian_b]Try downloading it with WGET?
Maybe it's just Firefox handling it wrong..[/QUOTE]

Thought that too, so I had downloaded one with Konqueror. Same error. Will try with wget though.

---

### Post by Perfect Storm on 2006-05-01
You could try with D4x

---

### Post by Leigh on 2006-05-04
I had exactly the same problem, but I found a working copy here ( [http://videogames.yahoo.com/download?eid=332005](http://videogames.yahoo.com/download?eid=332005) )

---

### Post by TheIdiotThatIsMe on 2006-05-05
Leigh, thanks for the link I'll try it when I get home today. Also, Artificial Intelligence, what is D4x?

---

### Post by Perfect Storm on 2006-05-05
It's a downloader manager (D4X = Downloader for X). It's like Get-right for windows, just without all the sluggyness.
If you have universe enable in your sourcelist.
```
sudo apt-get install d4x
```

---

### Post by TheIdiotThatIsMe on 2006-05-10
I downloaded it with D4X and once again got the same error. Has anyone else had this much trouble unarchiving/installing packages?

---

### Post by JoeMetal on 2006-05-11
I just downloaded the .run file and it worked fine for me.

---

### Post by TheIdiotThatIsMe on 2006-05-11
[QUOTE=JoeMetal]I just downloaded the .run file and it worked fine for me.[/QUOTE]

Would be kind enough to give me the link you downloaded it from?

---

### Post by mtron on 2006-05-11
i downloaded it from the link posted above without a problem. 

open a terminal and copy: 
```
wget http://us.rd.yahoo.com/games/buzz/downloads/332005/SIG=13bgptr6m/*http%3A//h.yimg.com/download2.games.yahoo.com/games/buzz2/content/p/2/332005/ut2004-lnx-demo-3120.run.bz2

```

---

### Post by TheIdiotThatIsMe on 2006-05-15
I have tried that code again and still get errors. I've tried downloading in different DE's with different browsers and even D4X and the terminal. I have also downloaded three other games that are all .run files, and none of them work. Is there a way to diagnose the problem? Or also is there a way to reinstall Ubuntu back to default without messing with data files (like .ogg files in user created folders?)

---

### Post by lakosked on 2006-10-07
I too have run into the same problem.  As of today Atari still has not updated the broken gzip demo file for UT2004 Linux.   I have found a source for a slighty older build 3120 the link is [http://videogames.yahoo.com/download?eid=332005](http://videogames.yahoo.com/download?eid=332005) But the download stalled for me so I would use the command wget [http://h.yimg.com/download2.games.yahoo.com/games/buzz2/content/p/2/332005/ut2004-lnx-demo-3120.run.bz2](http://h.yimg.com/download2.games.yahoo.com/games/buzz2/content/p/2/332005/ut2004-lnx-demo-3120.run.bz2)

I have also found a uk link to the latest build 3334 [http://www.downloads.jolt.co.uk/getdownload.php?id=4011](http://www.downloads.jolt.co.uk/getdownload.php?id=4011)
This too stalled after 97% download. (using debian KDE & konqueror)
Fortunately when I tried to download again, my browser saw the unfinished file and asked if I wanted to resume the download.  Unfortunately it resumed the downlaod with a 90kb file of the download page.  So I've started over and hope this time it wont stall.

I am curious though...does anyone know how to use wget with a php as the url?  I tried the address above but it just downloads the php web page not the actual file.  Ive also tried the source address that the download gives me during the download.  wget [http://213.208.119.22/getfile.php?dlid=3305034](http://213.208.119.22/getfile.php?dlid=3305034)
But that too gives me just the webpage and not the file.

---

### Post by anthro398 on 2006-10-11
wget [http://data.unrealtournament.com/UT2004-LNX-Demo3334.run.gz](http://data.unrealtournament.com/UT2004-LNX-Demo3334.run.gz)

---

