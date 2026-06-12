---
title: "Question for all you DVD makers - VOB -&gt; DVD-R?"
date: 2005-06-08
forum: Desktop Environments
---

### Post by dolson on 2005-06-08
Hey all.

I got a DVD burner not too long ago, and so I decided that I wanted to try making a DVD-Video. I figured I'd do it with the original (non-Director's Cut) Donnie Darko movie, since it's my favorite movie of all time, and I could use a backup (I already ripped it successfully to Divx5, but I wanna make an actual DVD this time).

Ok, so I read stuff in these forums, LinuxQuestions, various other places on Google and I can't seem to find exactly what I'm trying to do...

Basically, although my burner is a dual-layer burner, I only want to burn the movie itself - no menus, no deleted scenes, no extras, only put the DVD in, it plays, that's it. The full DVD is just over 5GB, but the VOB files for just the movie are about 4.3 or 4.4GB. That should be perfect!

If I rip like this: dvdbackup -n "Donnie Darko" -i/dev/hdb -F -o ddarko/

It will give me the VTS_01_0.IFO file, but no VTS_VIDEO.IFO. Besides, this also creates VTS_01_0.VOB, which is the startup menu and chapter selection, which I don't want.

That is why I specify the start and end chapters like so: dvdbackup -n "Donnie Darko" -i/dev/hdb -t1 -s1 -e28 -o ddarko/

This gives me:
VTS_01_1.VOB  VTS_01_2.VOB  VTS_01_3.VOB  VTS_01_4.VOB  VTS_01_5.VOB

But there are no IFO files there!

I do not need to shrink the VOBs because they should fit as is, so please don't tell me to use some shrinking utilities (especially not Wine and DVD Shrink). I am not asking this! I am asking how to get the IFO files needed to burn this as a single movie file. I don't need chapters or anything fancy either, just a straight single-track DVD.

I tried using dvdauthor -o ddarko/ -T or whatever it was, but that didn't work. I thought that it would, but I must've read it wrong...

Can anyone help me out here?

---

### Post by kurtwisener on 2005-06-08
Not trying to be at all rude here, but what you are asking is, frankly illegal.  Your odds of getting an answer here are very slim.  If you are curious about DVD ripping see [http://www.dvdripguides.com/](http://www.dvdripguides.com/), but before you go crazy with what you learn there, see [http://www.riaa.com/default.asp](http://www.riaa.com/default.asp) as well as [http://www.mpaa.org/anti-piracy/](http://www.mpaa.org/anti-piracy/), and while you're at it check out [http://www.fbi.gov/ipr/](http://www.fbi.gov/ipr/) and finally [http://www.access.gpo.gov/uscode/uscmain.html](http://www.access.gpo.gov/uscode/uscmain.html).  I personally believe that backing up media you possess and can demonstrate ownership of is an inherant right of ownership but I seem to be joining a shrinking minority.  The information you want is, at least, problematic for, if not absolutely inappropriate to, these forums.  I am not saying you are an idiot or insensitive or anything like that at all, I just think that we should do everything we can to keep Canonical/Ubuntu's hands clean in these times of digital rights confusion.  Please see all of the above links and make an informed, responsible decision.  Thank you for taking the time to read this and please remember not to be offended by my tone.  Its impetus is the present tension over the politics of free software, not any mistake on your part.

-Kurt

---

### Post by kurtwisener on 2005-06-08
Just noticing that you hail from Canada, as such please refer to [http://laws.justice.gc.ca/en/C-42/index.html](http://laws.justice.gc.ca/en/C-42/index.html) and [http://www.wipo.int/copyright/en/](http://www.wipo.int/copyright/en/)
-Kurt

---

### Post by brickbat on 2005-06-08
Hi,

Ok. I am in The Netherlands and backing up your own DVDs is perfectly legal here as it is in most countries in the world.  In fact, even in the USA, it is not against the copryright law but the far more recent DMCA.  Can you please answer the question for me because I have exactly the same problem.  It is not against any international copyright agreements.

ciao
bb

---

### Post by mtron on 2005-06-09
he guys just for you to know:
In most of the European Union member states it is legal to make private copies of your owned DVDs. Even when they are protected with CSS. (except Germany, but in Spain, France, Austria, ect. it's ok)

By law, you are not allowed to crack "appropriate copy protection", but due to it's major design faults CSS (the protection used for most DVDs) is not considered to be an appropriate protection.

And: if for legally owned copyright protected material on a medium like CD or DVD it is always good to make a backup of it, because everybody knows how fast a DVD can get scratches. The right of making a private copy for legally owned software is protected by the Directive 2001/29/EC of the European Parliament and of the European Council of 22 May 2001 on the harmonisation of certain aspects of copyright and related rights in the information society, see [here](http://europa.eu.int/eur-lex/lex/LexUriServ/LexUriServ.do?uri=CELEX:32001L0029:EN:HTML)

---

### Post by dolson on 2005-06-09
Cracking the encryption is illegal you say, so fine... Then, forget that this is Donnie Darko, which I own both versions of, but anyhow. That's not what I was asking. I was asking how to burn VOB files to a DVD-R, not how to crack and rip a DVD.

Say that this is a DVD that my brother made with a digital video camera and Windows XP. With no encryption.

I copied his DVD to my hard drive.

How do I burn the VOB files?

---

### Post by mtron on 2005-06-09
see [http://dvdstyler.sourceforge.net/index.html](http://dvdstyler.sourceforge.net/index.html)

if you wanna install the deb you need the marillat repos in your sources.list

## Marillat
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

then "sudo apt-get update && sudo apt-get install dvdstyler"

---

### Post by kurtwisener on 2005-06-09
Sorry Dolson, 

I really did not mean to irritate or offend.  The copyright climate in the US is VERY hot right now and as a result, I believe I overeacted.  As to the information on how to actually do what you want to do all the links provided should be of great assistance.  Good luck to you, it is rather fun actually.  As to the DMCA, we here in the states are frankly, terrorized by the thing.  It has a lot of us running scared.  In conjunction with certain deliberately vague terms of the USA PATRIOT act, it has been getting people into very serious trouble.  I realize that the rest of the world has yet to feel the effects of it.  That said, it would be good to remember that US Copyright law strongly effects international Copyright law, the DMCA/PATRIOT act provisions are becoming more and more integrated into our copyright law.  Elements of the DMCA/PATRIOT act are already strongly evident in the substance of the emerging Software Patent measures in the EU.  There is a very organized and concerted effort to harrass, threaten and outright apprehend people who engage in casual copyright infringement in the US and I believe that this is emerging in the rest of the world.  Look to Germany and the others not so much as anomalies but possible prophecies.  To close this, I am a firm believer in the right to crack and burn what you rightfully own, else why own it?  Unfortunately, ownership is becoming a very hazy subject.  I did not mean to piss anybody off, Ijust wanted to give fair warning and beg caution in our discussions on this forum.

Thanks again,

-Kurt

---

### Post by hal8000 on 2005-06-09
Try this link :

[http://dvd.chevelless230.com/](http://dvd.chevelless230.com/)


let me know if that helps as I have just bought a Philips DVD writer; my immediate use will be to back up my linux partitions, but later I will  copy one of my own DVD collection (currently 3)  to avoid scratches.

---

### Post by dolson on 2005-06-09
I actually read the chevelless stuff yesterday, but I just can't make this do what I want to.

I thought that a VOB was the same as an MPEG2 so I tried our some dvdauthor commands using the VOB instead of the MPG file, and that didn't work.

I see no easy way to generate a working IFO file for a given VOB or VOB set. Unless my utilities are way out of date.

So I tried extracting the M2V and the AC3 from the VOB and then simply multiplexing them back together, but that didn't work either, it gave me some error (can't recall, I tried it while I was at work).

Anyhow, long story short, I found dvd9to5.pl and that seems to have worked, and if so, then I'm going to dissect it tonight and see exactly how they do it.

Thanks for the replies, and I wasn't offended by you, Kurt. I understand where you're coming from and the patent laws are scary shit to me... It's actually really pretty f*cked up if you ask me. I don't even know why they sell DVD burners, CD burners, VCRs, etc. when almost every single thing out there is copyrighted and people aren't allowed to back things up anymore. They shoulda foreseen this, and did something about it. But anyhow, I guess that arresting people for watching DVDs in Linux is a worthy cause.

I think it's just another sign that the end of the world is coming, or at the very least a sign that 1984 will become a reality, although the book was probably off by somewhere between 25 to 50 years, give or take.

---

### Post by MetalMusicAddict on 2005-06-09
In the end I would choose tools on XP rather than linux. There ALOT of tools to do what your asking. DVDDecrypter and DVDShrink are about the best. If you dont want to get too involved Ide go the DVDShrink route.

I have alot of experience with ripping/encoding in XP. PM me if you want info. 

Also Doom9 is the best site for info on this subject.

---

### Post by dolson on 2005-06-10
Yeah, do you have info on where I can get Windows XP for free?

Seriously, I haven't run Windows on my system since August 2002, and I'm not about to start. I would sooner use Wine (*shudder*) than go back to that steaming pile.

Anyhow, it seems that dvd9to5.pl worked as expected.

---

