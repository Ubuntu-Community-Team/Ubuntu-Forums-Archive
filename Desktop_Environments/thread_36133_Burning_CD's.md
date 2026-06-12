---
title: "Burning CD's"
date: 2005-05-22
forum: Desktop Environments
---

### Post by SpEcIeS on 2005-05-22
I seem to have found my first complaint about Ubuntu, but it is not that big. I was trying to burn a CD using GnomeBaker, Graveman, and the Nautilus CD Burning feature. All were sadly met with failure. :( 

Now, it would seem that GnomeBaker started to burn my ISO, but it stopped at thirty percent, then fixated, then quit. Whenever I tried to Blank a CD/RW Graveman would work, but GnomeBaker failed, nautilus would not even recognise the fact that a CD was in the drawer. Upon coming to these wonderful events, I decided to compile the latest Graveman 0.3.12, which the current Ubuntu comes with 0.3.10, however this did not make any difference.

Well to sum this up so it is shorter, I ended up tainting my wonderful Gnome GUI with a KDE application, nevertheless K3B saw me through. :) Worked seamlessly. :)

Ok, this has finally come to my question, what is going on with my Gnome environment which prevents an easy CD burn?  :roll: It would evidently not be the cdrecord or cddao software, due to the K3B success. I am very interested in finding out what configurations must be applied in order to successfully burn CD's either with nautilus or GnomeBaker.

Thank-you for any help.  :smile:

---

### Post by jeremy on 2005-05-22
I can't offer any help, I'm afraid, but wanted to let you know that I had exactly the same problem, and that kubuntu fixed it for me too.

---

### Post by tread on 2005-05-22
Try enabling burnproof in gnomebaker settings.

Application->System Tools->Configuration Editor, go through apps to find gnomebaker.

---

### Post by Dax0r on 2005-05-22
I have the same problem!

> CD/RW Graveman would work, but GnomeBaker failed, 

Yeah,Gnomebaker failed for me too...I think that's a bug

---

### Post by SpEcIeS on 2005-05-22
Well at least I know that I am not alone, and for now it would seem that K3B will have to do the trick.  ](*,) However, I will try the burnproof option that **tread** suggested, and I will also try and apply it to the nautilus cd burning, since I remember seeing it there also.

Thanks. :)

---

### Post by SpEcIeS on 2005-05-22
Ok people I have one answer to this problem, or at least on my machine.  :) Now I have had no success with nautilus, but I downloaded coaster, see here: [Coaster](http://www.coaster-burner.org/), and it seemed to burn, on my CD/RW, with no problems. 

When I tried, again, to use the nautilus cd-burning feature it kept telling me to insert a CD with more that one megabyte of storage, however the CD/RW was clean. After I applied the above method and was met with success.  \\:D/  Does the nautilus cd-burning feature accept CD/RW's? I am not willing, at this time, to waste a dollar on using a CD-R. It is the Scotsman in me.  ;-)

---

### Post by tread on 2005-05-22
In that case, try to explicitly blank the cd-rw through gnomebaker even if its clean?

---

### Post by mobile.army on 2005-05-31
Gaining inspiration from tread, I used the Nautilus CD Burner by going:

Applications>System Tools>Configuration Editor.

I found nautilus-cd-burner under apps and enabled burnproof and overburn (you just click those boxes...it's easy!)

Now everything is fine.

---

### Post by SpEcIeS on 2005-05-31
[QUOTE=mobile.army]Gaining inspiration from tread, I used the Nautilus CD Burner by going:

Applications>System Tools>Configuration Editor.

I found nautilus-cd-burner under apps and enabled burnproof and overburn (you just click those boxes...it's easy!)

Now everything is fine.[/QUOTE]
I found the same thing, but I forgot about this post. Nautilus seems to work well now that overburn is enabled, and it even will burn ISO's well.  :grin:
Thanks for the help though. :)

---

### Post by kwennemar on 2005-06-02
I have tried an awful and I do mean awful lot of burner programs.  KB3 is the best in the Linux world.  And I fail to see why a good programer doesn't reverse engineer it to be gtk / gnome based.  Since it uses the same actual background programs, wouldn't it be a matter of making good screens like baker and then useing the scripts from say KB3 to tell the actual proc's what to do.  And Nautilus, well, I have the darndest time getting it to work with cdrw's that I want to over write.  There is no simple erase cd option that I have found and it doesn't make multi-session cds easy either.  How do you do that with Nautilus anyways?

I am not a programer, I just work with them.  But this is seems to be the core of the problem.  Gnome doesn't have a good all around native cd burning program that handles most iso formats, copying cds or dvds etc...

My answer was to download a copy of nero for linux and a serial number.  It works just as good as KB3, well almost as good, and doesn't require qt and kde to work.  I am a  pirate and I am trying to be good using GPL software, but I keep finding reasons to go back to my bad ways.  Damn I feel like a junkie!

---

### Post by tread on 2005-06-02
I agree with getting a good cd burning programme for Gnome, and someday gnomebaker will surely become as powerful as k3b. Still, you must ask yourself: would you rather use 20mb or so to download k3b and dependencies or become a pirate and do something illegal?

---

### Post by stevenyu on 2005-06-02
Can anyone give me any suggestion regarding to why I can only burn files from HD to CDR, but can't do CD to CD copy???

I have try bothe gnome baker, and k3d, but both of them failed when I try to burn a normal data CD as well as music CD :neutral:

---

### Post by SpEcIeS on 2005-06-02
[QUOTE=tread]I agree with getting a good cd burning programme for Gnome, and someday gnomebaker will surely become as powerful as k3b. Still, you must ask yourself: would you rather use 20mb or so to download k3b and dependencies or become a pirate and do something illegal?[/QUOTE]
I agree with this. There was a time when I was involved in keygens and cracks, building and using, but then came linux.  :smile: One issue that helped stop me was  that I was really getting tired of the disgusting banners these types of site supported.  :mad: Nothing needs to be stolen, even if the companies that are making the software are greedy. It is still wrong to steal.

Open source offers people whoe participate in this activity to break free and not have to think about theft, and you get to use a real, secure, OS. 

LIke **tread** pointed out, really, what is twenty megs, or so. It is just a drop in the bucket compared to stealing and going against self, however if you are using linux now, you maybe at a cusp in your choices regarding theft.  :grin: 

Good luck and remember...  there is K3B, which is a great software piece.  :wink:

---

