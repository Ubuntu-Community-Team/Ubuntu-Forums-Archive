---
title: "Another Neverwinter nights problem."
date: 2010-10-31
forum: Gaming &amp; Leisure
---

### Post by Stylesmarino on 2010-10-31
Hey folks.

I am currently fighting with the installation process of Neverwinter Nights. 
I am very new to Ubuntu, Lucid. Noob etc...

I have been following this guide: [http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html)
I have downloaded and extracted the 
Resources (nwresources129.tar.gz), 
Linux Client (English_linuxclient169_orig.tar.gz)
 and the 1.29 Update (English_linuxclient169_xp2.tar.gz)

The update seemed to add nothing that was not in the client or the resources.

I have also installed from deluxe edition disk in WINE.

I want to use the client.
The Wine install was broken. 

Here is the problems.
1) fixinstall does not run from the terminal. 
I suspect that is because it is not there.  I have no executable called fixinstall to run. 

2) The guide says ./nwn to start the app.
But I don't have an executable called nwn. I have nwmain and nwserver.

[s]3) When I try to run nwmain (./nwmain) it tells me that I am missing libmss.so.6:[/s]
Edit: have this one sussed. Why don't I have nwn executable?

I assume there is stuff missing.
Is this true? Anybody know how I can fix such?
I want to play....

---

### Post by Perfect Storm on 2010-10-31
Never failed me: [http://gwos.org/doku.php/guides:64bit:nwn](http://gwos.org/doku.php/guides:64bit:nwn)


Just pay close attention, as there are many commands.

---

### Post by Stylesmarino on 2010-10-31
Thanks.

I'll check it out.

---

### Post by Stylesmarino on 2010-10-31
Sorted now, sort of.

Its running. 
Seems I had somehow downloaded part of the client.

However I can't see the text on the key input. 
I can see a bit of the first letter thats all.

Anybody any experience with this?

---

### Post by oldrocker99 on 2010-10-31
By the way, the last update for the client is 1.69, which is ~450 MB and includes horse riding, plus a whole heck of a lot more.

:guitar:

---

### Post by Stylesmarino on 2010-10-31
Yeah, cheers I got that.

Not finding anything on this text problem.
I wonder is it a graphics card problem?

---

### Post by Stylesmarino on 2010-11-07
Bump.

Still can see the text in the key input screen.

Have tried the stuff from this guide: [http://nwn.bioware.com/forums/viewtopic.html?topic=347606&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=347606&forum=72)

Apparently it was an issue with "dialog.tlk".

I did the checksum thing. Found dialog.tlk failed.
Extracted in a new version.
Did the chown and chmod on dialog.tlk.
re ran the checksum thing and 
ran nwn.

Still no text.
Anybody suggest anything different? My head is wrecked.....:)

---

### Post by applejuicekiss on 2011-01-01
i have had the same missing text problem since i upgraded from ubuntu 8.10.  it is the same in ubuntu 9.4, 9.10, and 10.4.  not sure about 10.10.  havn't been able to find much info about this issue and havn't been able to play.  a new dialog.tlk did not fix the problem.  neither new install of ubuntu nor nwn fix the problem.  i suspect it has to do with the the open source drivers for my radeon card, because the ati drivers stopped supporting my x1950 for ubuntu 9.4, which was when the game stopped working.  any info would be much appreciated.

---

### Post by oldrocker99 on 2011-01-04
I had the same thing happen to me with my x1200 laptop. I finally decided to go on with 9.04 when it happened to me, and I figured that the open-source drivers would only get better, and that is what happened. The open-source drivers, the 'radeon' ones, are certainly good enough for me to play at 800X600 full speed.  I just downloaded a most interesting set of modules from Neverwinter Vault called Vis et Virtus, which push the engine pretty fully, and, cutscenes and all, it runs fine on my laptop with a "legacy":mad: ATI chip.

I'm a much happier gamer these days, although there are a number of native Linux games that are too slow to be playable (Aquaria, for one).

I've been playing Neverwinter Nights since it came out in 2002, under XP until '08,  when I discovered that my long-term favorite game had a Linux client=D>.

---

