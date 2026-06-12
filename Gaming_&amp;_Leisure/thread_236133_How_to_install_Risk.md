---
title: "How to install Risk?"
date: 2006-08-14
forum: Gaming &amp; Leisure
---

### Post by zorkerz on 2006-08-14
I've been trying to run the risk version found [here]("http://jrisk.sourceforge.net/") and have run into various problems.  The applets work great but I would like to be able to play offline.  Has anyone been able to run this game?  If so please tell me how you got it going.
elias

---

### Post by ricardisimo on 2007-02-03
I'm wondering if you'd managed to get the game up-and-running, and if so, I'll gladly pick your brain.

---

### Post by Waappu on 2007-02-03
Hi

This works for me

- I downloaded [Risk ]("http://linux.softpedia.com/progDownload/Risk-Download-4922.html")
- Then I install java 1.5 using [Automatix2]("http://www.getautomatix.com/").
- Right click downloaded file and select Open with "Sun Java 5.0 runtime"

---

### Post by Perfect Storm on 2007-02-03
Perhaps I should write a howto to this game as well. I'll report back when it's done.

---

### Post by teddybairs on 2007-02-03
You may find similar problems with any java game you come across. I've never been able to run them right with the deb Java packages. What I had to do was go to Sun's website and download the JRE for Linux as a bin file and then run it. It will put a folder in your user folder. After that, I had to manually go in and change the script files to point to the Java folder sitting in my home file. For Risk.sh it looks something like this:

#!/bin/sh
cd /home/frallen/Risk
/home/frallen/jre1.5.0_07/bin/java -jar Risk.jar

Basically you just have to tell the sh file where the Risk data files are, and where the java binary is. After this, it should run without a problem.:)

---

### Post by ricardisimo on 2007-02-03
> **Waappu said:**
> Hi

This works for me

- I downloaded [Risk ]("http://linux.softpedia.com/progDownload/Risk-Download-4922.html")
- Then I install java 1.5 using [Automatix2]("http://www.getautomatix.com/").
- Right click downloaded file and select Open with "Sun Java 5.0 runtime"

OK. So it's installed now, and supposedly the install added a Risk launcher to my menu, but I certainly can't find it. The faq says to double-click the risk.jar file in the game folder, but that just launches archive manager. How do you launch? Thanks again.

---

### Post by klytu on 2007-02-03
> **ricardisimo said:**
> OK. So it's installed now, and supposedly the install added a Risk launcher to my menu, but I certainly can't find it. The faq says to double-click the risk.jar file in the game folder, but that just launches archive manager. How do you launch? Thanks again.

Try double-clicking the file Risk.sh in the game folder.  If you then get a GUI dialog box that says "Do you want to run Risk.sh or display its contents?", select Run.

If you have Sun java installed, you can right-click the Risk.jar file and open it with java.

---

### Post by ricardisimo on 2007-02-03
Thanks! That worked great. I am, however, having another problem. This last time I launched, I got a popup announcing that "an error has occurred!!!", that I should copy and paste the displayed text and mail it to [email]yura@yura.net[/email] (which I couldn't do since I couldn't interact with the text in the box). There is also a "button" at the bottom of this box that allows me to save the error log to file, which I did and I sent it along its merry way. The problem is that the popup won't close, even after I shut Risk down. I'm trying to find it in System Monitor so that I can shut it down from there, but it doesn't have any obvious name or much (if any) memory footprint. I'd appreciate any help in shutting this down.

P.S. - I'm sure I could just restart, but I'm twenty minutes into downloading the Feisty ISO... I'd prefer not interrupting it.

---

### Post by ricardisimo on 2007-02-03
Never mind... it was java. I should have guessed that right away. :rolleyes:

---

### Post by zorkerz on 2007-02-03
Slightly unrelated but i was wondering if anyone could find a picture of the europe map from Risk: The Game of World Domination.  This was one of the earliest risk video games for windows published by Hasbro and developed by Blue Sky Entertainment.  It had a great giant europe map including North Africa, Turkey, and some of the Middle East.  There were hundreds of territories and i think 9 continents.  Anyways it has great sentimental value for me, I've lost probably 3 cds of the game and don't want to spend a couple bucks to play it in windows.  I would like to try and make the map playable in this java risk.  If anyone can find an image of the map on the cd or online it would be much appreciated.  Thankee
elias

---

### Post by ricardisimo on 2007-02-04
Is this what you were looking for? I'd send it full-sized, but it's 2+MBs, and UbuntuForums won't have it. Give me an email and it's yours.

P.S. - You're going to need all of the other images on the disk as well, the map "overlays" and "underlays" or what-have-you, if you really want to try to make it work on the other Risk.

---

### Post by zorkerz on 2007-02-04
Yes! Thats it.  My email is [email]zorkerz@gmail.com[/email] If I'm correct it looks like i will need that image and another all in gray scales.  Unless someone could find one already done in gray scales I was going to try and make it in gimp from the main map.  If anyone has other ideas I'm all ears, but ive been searching for a project for myself anyways.  Thankyou ricardisimo!
elias

---

### Post by zorkerz on 2007-02-06
So there is currently a resolution requirement of 677 X 425.  However I am talking with Yura to see on the feesability of changing that.  I am also playing around with the image shrunk to 677 X 425 however I think this might create a very cramped map.  More as I know it.
elias

---

### Post by ricardisimo on 2007-10-07
Hey there... did anything ever happen with those maps? This is one game I do miss for just passing the time, and this smaller version is nice, but I'd love to see that Europe map working again. Has anyone gotten the original Hasbro disk to work via wine? If so, I'd appreciate a tutorial on that and Civ II in wine.

---

### Post by zorkerz on 2007-10-07
I never got a full reply form the guy who wrote jrisk he said that he would look into my request of changing the maximum resolution of a map higher.

I cant believe its too hard to set the maximum resolution of a map higher. I however do not know how to.

If anyone does or can find someone who can code for this. Its java right? (jrisk)

Im the first to admit i dont know what im doing but i wonder what it would take to got more people into coding for this program. I don't even know where to begin.

ricardismo glad to see your still interested
cheers

---

### Post by ricardisimo on 2007-10-10
Oh, I'm still very much interested. Unfortunately, I know less than nothing about hacking, coding, you name it. I normally remember where the power button is... normally. I wish I could help out more with the project.

I'm still wondering, though, if you or anyone else has managed to get the Hasbro version to run via wine. There's something I'm not getting, because i can't seem to get any of my old Windows game discs to install properly. I'd love a tip or two.

Thanks.

---

### Post by zorkerz on 2007-10-10
I no longer have the hasbro version of risk. Have owned at least 3 copies over the years and all have been lost or broken. If it worked I would also love to know.

Its very hard to find these days. I have never been able to succesfull burn a copy of it or make an iso or find it online or download a no cd crack (my computer now has no internal cd player). 

Thats what brought me to jrisk in the first place, as a replacement to the original hasbro risk.

Thats where I stand.
cheers

---

### Post by tjtillman on 2008-02-07
Hey I actually just installed the old Hasbro Risk today via wine and it worked! 

Now, it was using the disc hasbro printed in 1997, as opposed to those in 1996. From what I understand, the ones in 1996 had a compatibility problem, not allowing you to install Risk on anything higher than Windows 95. In Windows XP, this is circumvented with Win95 compatibility mode, but I guess it would still work in wine if you have it set to Windows 95 mode.

Mine was a 1997 disc so it installed fine, and it played fine. The only tweaking I had to do was either change the symbolic link of "Z:" in .wine/dosdevices to point to the CD drive, OR (like what I did), to whatever folder you copy the Risk CD into.

Im not really a terribly advanced user and I was able to get it working so it shouldn't be too tough, but if you have any questions that I can help with, feel free.

---

### Post by zorkerz on 2008-02-07
man thats awsome where did you get the disc? No chance its new form somewhere?

I have had trouble finding it again after my 2 or 3 copies broke.

I still dream of finding someone/learing myself how to modify jrisk so it can take bigger maps and bringing the europe map into it.

Im glad people are still into this great game.
cheers

---

### Post by markharding557 on 2008-02-08
> **Waappu said:**
> Hi

This works for me

- I downloaded [Risk ]("http://linux.softpedia.com/progDownload/Risk-Download-4922.html")
- Then I install java 1.5 using [Automatix2]("http://www.getautomatix.com/").
- Right click downloaded file and select Open with "Sun Java 5.0 runtime"

why are you installing java 1.5 from automatix when it is in the repository?see link [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=sun&searchon=names&subword=1&version=gutsy&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=sun&searchon=names&subword=1&version=gutsy&release=all")
this could cause problems

---

### Post by ricardisimo on 2008-02-09
Now it's in the repositories. At the time I can't say that it was. Besides, for every one person that has had a serious issue with Automatix, there are 100 newbies on their hands and knees thanking the developers for their work.

I never understood the antagonism towards Automatix. It's a tool, just like any other.

---

### Post by ricardisimo on 2008-02-09
> **tjtillman said:**
> Hey I actually just installed the old Hasbro Risk today via wine and it worked! 

Now, it was using the disc hasbro printed in 1997, as opposed to those in 1996. From what I understand, the ones in 1996 had a compatibility problem, not allowing you to install Risk on anything higher than Windows 95. In Windows XP, this is circumvented with Win95 compatibility mode, but I guess it would still work in wine if you have it set to Windows 95 mode.

Mine was a 1997 disc so it installed fine, and it played fine. The only tweaking I had to do was either change the symbolic link of "Z:" in .wine/dosdevices to point to the CD drive, OR (like what I did), to whatever folder you copy the Risk CD into.

Im not really a terribly advanced user and I was able to get it working so it shouldn't be too tough, but if you have any questions that I can help with, feel free.

Are you on Feisty or Gutsy?

---

### Post by Waappu on 2008-02-10
> **markharding557 said:**
> why are you installing java 1.5 from automatix when it is in the repository?see link [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=sun&searchon=names&subword=1&version=gutsy&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=sun&searchon=names&subword=1&version=gutsy&release=all")
this could cause problems

Hi

If I remember correct java wasn't in repo back then when first post is writen. Now it is I and I agree install java from there and not use Automatix2

---

### Post by markharding557 on 2008-02-14
> **Waappu said:**
> Hi

If I remember correct java wasn't in repo back then when first post is writen. Now it is I and I agree install java from there and not use Automatix2

java 1.5 is in dapper drakes repos,this was released june 2006 before the first post in this thread

---

### Post by zorkerz on 2008-03-05
Hey all, I just got an email from Yura the creator of jrisk. Version 1.0.9.5 of jrisk has just come out supporting full screen and bigger maps!

Don't know if this matters to others but this is exactly what i have been waiting for. Now hopefully I can import the hasbro europe map and play again.

good day

a link might be nice [http://jrisk.sourceforge.net/]("http://http://jrisk.sourceforge.net/")

---

### Post by zorkerz on 2008-03-09
what version of java are people using for this?

---

### Post by ricardisimo on 2008-03-12
Has anyone tried [this version]("http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/TBS/PHP-RiSK-35623.shtml")? If so, please send me a step-by-step, because I'm useless without a .deb file. Tarballs just make a sticky mess in my brain. Thanks in advance.

---

### Post by ricardisimo on 2008-03-18
I'll take that as a "no"... and use this as a bump. ;-)

---

### Post by zorkerz on 2008-03-19
I imagine you have gotten this far already... 
I downloaded the packages and extracted it. Then there is a readme and also and install file in the install folder both of which give some directions.

The install file at least gives some system program requirements. I don't have everything so did not pursue  it any farther. 

It also has only been tested on firefox 1 so i don't think much work is being done on it.

good luck

---

### Post by ricardisimo on 2008-03-19
Thanks! Any progress on the Hasbro maps?

---

### Post by zorkerz on 2008-03-19
I just barely got the swing gui to open for the first time. This apparetly provides a better interface for making maps, but i have not looked at it at all. I have a paper due tomarrow and one next week, so hopefully all find some time in the near future to put it all together.

Im very excited to be able to play the europe map again. I will be sure to let everyone know how it progresses.

---

### Post by zorkerz on 2008-03-21
So im currently adding in all the continents and countries in the map editor. Especially for the countries i am going to use numbers for now. Does the hasbro risk game label all the countries?

If so i would love to get all the names somehow. 

I really need to just get a 4th copy of it.

Updates: oh and also really most importantly how many armies do you get for controlling each of the 16 continents at the beginning of your turn?

-sardina and corsica are one country belonging to the southern italy continent?
-are denmark and southern sweden one or two countries
-cyprus is part of turkey rather than egypt?
-which country in turkey does the island of crete connect two?

---

### Post by zorkerz on 2008-03-22
So I have the europe risk map all made out except for the image map that tells jrisk where each country is.

The swing gui does not have a good way to fill in the areas for each country so i have been trying to use gimp (which i am very inexperienced in). 

Im trying to take the color code map from hasbro and convert it to greyscale (same value for red, green, and blue). Each territory needs to have a different greyscale number (1-255 jrisk can't use 0).

I don't think i understand how to make an image map for jrisk though because i keep getting an error message on small test maps *image map uses colors that do not match any country

does anyone know how this works?

Other questions to solve still:
-# of armies each continent is worth
-where in turkey does crete connect to
-is cyprus part of the continent of turkey or egypt
-country and continent names

---

### Post by starksandclarks on 2008-11-15
I'm gonna try to raise this topic from the dead and ask whether anyone here knows of public servers for this or people who congregate to play online.

The computer AI makes some dumb choices even when set to hard.  I've never played before and started on a whim when I stumbled upon this game.  Now though it makes me feel like I'm getting good at beating the AI instead of beating good players.  Not faulting the developers, just saying there's a big difference between the two and I wonder if anyone actively sets up games on this.

---

### Post by zorkerz on 2008-11-15
I don't know. It would be nice to be able to play against real people thats for sure. I have just always ended up playing hot seat games with friends on a single computer. Have you checked the games website? I seam to remember something along those lines there.

---

### Post by starksandclarks on 2008-11-15
> **zorkerz said:**
> I don't know. It would be nice to be able to play against real people thats for sure. I have just always ended up playing hot seat games with friends on a single computer. Have you checked the games website? I seam to remember something along those lines there.

Yeah the website is peculiar because it has very little info other than the download link.  Even the game manual is pretty sparse on details.

Seems a shame for the multiplayer component to be programmed in but be under-utilized so much.  It shouldn't be that hard to have a web page that says "Here are servers with people looking to play right now."

Hm....

---

### Post by zorkerz on 2008-11-15
To be fair to the developer. Ive talked to him a few times about the map I worked on. He made the game in his spare time and to my knowledge has no help at all. I think he has made a great game overall.

---

### Post by starksandclarks on 2008-11-15
Well, it wasn't my intention to fault the developer, though it may have come across that way.  I think the game is great.  

Having worked with Java a little bit I'm interested to see how he coded the logic behind it and I may poke around the code a bit.

On the other hand, having worked with Java before, I may not. Haha.

---

### Post by potterbond007 on 2008-12-19
> **ricardisimo said:**
> Thanks! That worked great. I am, however, having another problem. This last time I launched, I got a popup announcing that "an error has occurred!!!", that I should copy and paste the displayed text and mail it to [email]yura@yura.net[/email] (which I couldn't do since I couldn't interact with the text in the box). There is also a "button" at the bottom of this box that allows me to save the error log to file, which I did and I sent it along its merry way. The problem is that the popup won't close, even after I shut Risk down. I'm trying to find it in System Monitor so that I can shut it down from there, but it doesn't have any obvious name or much (if any) memory footprint. I'd appreciate any help in shutting this down.

P.S. - I'm sure I could just restart, but I'm twenty minutes into downloading the Feisty ISO... I'd prefer not interrupting it.

Ok.. I am stuck in this part of the installation. I closed off the error log.. But I dont know where to progress from here. The error keeps coming and trying to load a map from the default maps available in the map folder does not seem to be working. I have Java 6.0 runtime installed which is what i use to run the risk.jar file.

---

### Post by Mattymadhatter on 2010-04-16
Hi all,

Hasbros Risk 1997 had to be one of my favorite games to waste time on. 

I lost the cd a long time ago. Recently I found a copy and downloaded it, after not being able to find a cd sold anywhere.

The version I have is asking for a CD. The crack exe file that came with this version doesnt do its job.

Can anyone either suggest a fix, or provide me with a version I can use? I see these threads are old, but would greatly appreciate someone giving this rookie in gaming hacking some advice.

All I want to do is play an old game I bought and lost a long time ago...

---

### Post by ricardisimo on 2010-10-13
> **zorkerz said:**
> So I have the europe risk map all made out except for the image map that tells jrisk where each country is.

The swing gui does not have a good way to fill in the areas for each country so i have been trying to use gimp (which i am very inexperienced in). 

Im trying to take the color code map from hasbro and convert it to greyscale (same value for red, green, and blue). Each territory needs to have a different greyscale number (1-255 jrisk can't use 0).

I don't think i understand how to make an image map for jrisk though because i keep getting an error message on small test maps *image map uses colors that do not match any country

does anyone know how this works?

Other questions to solve still:
-# of armies each continent is worth
-where in turkey does crete connect to
-is cyprus part of the continent of turkey or egypt
-country and continent names

Did you ever get a reply to this? I'm having an odd issue with my Risk CD. New computer, and suddenly there is no way to make the exe files on the installer disc executable for Wine. Been too long... how the hell did I do this before?

---

### Post by zorkerz on 2010-10-13
I don't know that I ever got a direct response. I was able to eventually import the europe map into jrisk (now called dominion). Its not perfect last I checked there are a few bugs. I have not used it though because you need to manually place all your armies one at a time alternating players at the beginning of the game and that just takes too long.

---

### Post by ricardisimo on 2010-10-21
Interesting... I didn't put it together until just recently. The Hasbro disc works just fine under wine, but only if one uses the open source "nv" graphics driver, and not the proprietary "nvidia" driver. Any idea as to why that might be?

For the longest time I could figure out why I could use it on some of my machines but not others.

---

### Post by francois.e on 2010-12-25
Trying to install Domination. Automatix is no longer available. Java is needed to run Domination.

1) installed java :
root@MSIX340:/home/fl# apt-get install openjdk-6-jdk
2) downloaded risk installer or Domination_install_1.1.0.1.jar from:
[http://risk.sourceforge.net/download.shtml](http://risk.sourceforge.net/download.shtml)
3) right click on Domination_install_1.1.0.1.jar after making the file executable, and open with JavaJDK java 6 runtime.
4) then follow the instructions to get the game installed, you will find Domination under Games

---

### Post by ricardisimo on 2010-12-27
By the way, someone (zorkerz?) got a version of the Big Europe map up and running on Domination. Nice work! Still some tweaks needed - countries connected which shouldn't be, and others with long borders that miraculously don't touch, etc. - but it looks quite good.

I'm not understanding how to work the map editor, so if someone can give me some tips and tricks, I'd be glad to help. Secondly, the AI on Domination is OK, but there is at least one major flaw. Whether the computer player is working with 3 armies or 100, they ***all*** occupy their conquered countries. They never move just three in, which leads to some really bizarre placements, and wasted armies that never wind up back in play.

---

### Post by ekjsim on 2011-01-03
> **francois.e said:**
> Trying to install Domination. Automatix is no longer available. Java is needed to run Domination.

1) installed java :
root@MSIX340:/home/fl# apt-get install openjdk-6-jdk
2) downloaded risk installer or Domination_install_1.1.0.1.jar from:
[http://risk.sourceforge.net/download.shtml](http://risk.sourceforge.net/download.shtml)
3) right click on Domination_install_1.1.0.1.jar after making the file executable, and open with JavaJDK java 6 runtime.
4) then follow the instructions to get the game installed, you will find Domination under Games

still works :)

---

