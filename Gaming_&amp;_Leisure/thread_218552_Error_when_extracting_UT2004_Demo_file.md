---
title: "Error when extracting UT2004 Demo file"
date: 2006-07-18
forum: Gaming &amp; Leisure
---

### Post by fatsheep on 2006-07-18
I have downloaded the demo file and put it on my desktop, when I try to extract the .run file out of the .gz archive it gives me this error:

> gzip: /tmp/fr-K1VxUU/UT2004-LNX-Demo3334.run.gz: unexpected end of file

What do I need to do to install it? 

thanks,

-sheep

---

### Post by gerbman on 2006-07-18
Looks like the .gz file is corrupt/incomplete...did you try downloading another (possibly from a different location)?

---

### Post by fatsheep on 2006-07-18
Alright I'll try downloading the one from gamespot.

---

### Post by vem0m on 2006-07-19
go [HERE]("http://www.3dgamers.com/dlselect/games/unrealtourn2k4/ut2004-lnx-demo3334.run.html") and download that demo file goto terminal, navigate to the directory u downloaded it to, then type "chmod +x ut2004-lnx-demo3334.run" then type "./ut2004-lnx-demo3334.run" and it should start the installer enjoy!

---

### Post by fatsheep on 2006-07-19
> **vem0m said:**
> go [HERE]("http://www.3dgamers.com/dlselect/games/unrealtourn2k4/ut2004-lnx-demo3334.run.html") and download that demo file goto terminal, navigate to the directory u downloaded it to, then type "chmod +x ut2004-lnx-demo3334.run" then type "./ut2004-lnx-demo3334.run" and it should start the installer enjoy!

Thanks alot I have installed UT2004 and it works, however I have a question.  
Is there any way I can create a shortcut to UT2004?  Right now to run the game I have to go into the terminal and type "./UT2004".  It works but it's more convienant to have a desktop shortcut. 

Thanks,

-sheep

---

### Post by TFBW on 2006-09-18
The root cause of this error appears to be that the **web server** is misconfigured such that the file is treated as a text file. This corrupts the file in transit. If you use "wget" (or similar) as your client, it will tell you what MIME type the file has. Something like "Length: 288,790,354 [_application/x-gzip_]" is a good sign that the transfer will work.

---

### Post by Giblet5 on 2006-09-28
No, that's not it.

```
wget [http://data.unrealtournament.com/UT2004-LNX-Demo3334.run.gz](http://data.unrealtournament.com/UT2004-LNX-Demo3334.run.gz)
```

Length: 81,049,007 (77M) [application/x-gzip]

The type is fine, the retrieved file is not:

```
gzip -d < UT2004-LNX-Demo3334.run.gz > UT2004-LNX-Demo3334.run
```

produces:

```
gzip: stdin: unexpected end of file
```

---

### Post by Giblet5 on 2006-09-28
And then, you get it running. Yea!

Has anyone noticed that it steps all over Cairo apps under Beryl?  I think it's an issue betwixt AIGLX and the Damage extension?  How appropriate is that?

Cairo-Clock is really messed-up when UT2004 exits.  UT2004 should play the "Muh-Muh-Muh-MONSTER KILL!" audio clip when it exits.

The fix is to grab the clock, give it a good shake (to make the Beryl wobbly-windows plugin repaint the whole thing) and then put it back.

---

