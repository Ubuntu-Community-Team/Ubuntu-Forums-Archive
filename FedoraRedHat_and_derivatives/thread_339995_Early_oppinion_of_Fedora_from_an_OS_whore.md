---
title: "Early oppinion of Fedora from an OS whore"
date: 2007-01-16
forum: Fedora/RedHat and derivatives
---

### Post by Scheater5 on 2007-01-16
The last 6 months since kissing Windows goodbye have, partly, been spent "experimenting."  Ubuntu has, and probably will be for the foreseeable future, my main workstation OS, but no sooner did I become comfortable with Ubuntu did I start "trying out" other OS's (including a disastrous affair with a botched attempt to create a Macintel).  Gentoo, FreeBSD (which I'm still experimenting with), OpenSuSE, Morphix and Santa Fe (neither of which even got installed), older Microsoft incarnations, and most recently, Fedora Core 6.

Well, my affair with Fedora didn't start off well.  At the time I had Herd 2 of Fiesty on my desktop, and apparently the Fedora installer didn't like having to deal with that.  Which, I suppose is not entirely it's fault.  See, the main CD-Rom drive on that comp is a little screwy - however, Ubuntu has never had a problem with it and always installs flawlessly.  Luckily this particular comp has a separate DVD drive, so I tried that, and finally, success.  

Run through the installer with minimal problems, and boot into a working Fedore Core environment with Gnome.  First things first - load up KDE.  Also with seemingly goes off without a hitch.  Reboot into KDE.  Here's where the real trouble starts.  I try to make all my experiments practical, so I figured I'd turn this desktop into a multimedia station.  Unfortunately that includes alot of software not in the main Fedora repo.  So I go to my trusty friend google and look for documentation on enabling extra repos.
And look.
And look. 
And look.  
Buried in there is the answer I'm looking for - the Linva repos and fresh RPMs repos.
Only the site I found didn't mention that they often conflict with each other.  Joy.
So I fire up Add/Remove programs and start grabbing stuff to play DVDs as per the instructions I found on the net (which, mysteriously, I can't come by again).  Now when I open Xine, the whole comp locks up!  
But, knowing Kaffine works with a xine backend, I figure if the instructions say xine will play it, Kaffine should play it - after all, I've got dvds playing fine in Kaffine in Kubuntu.  Sure enough, encrypted DVDs now play in Kaffine - playing a DVD in Kaffine screws up the graphics for everything else on the screen, and the DVD itself is very grainy.  
O yea, the the instructions that enabled the Linva repo forgot to put a header on the config file, so after the reboot Add/Remove programs wouldn't open - I just deleted the file in /etc/yum, figuring it's not worth it.  

So, it's early yet in my experience with FC6.  Alot of things are fine - web browsing, file browsing, got Kopote working fine, Limewire even works on FC6 when I have problems with it on Kubuntu (it's the network at my college, it doesn't like Flash apparently...still troubleshooting that one).  But there's all these little annoying details that make it seem less polished, when honestly I think it would be a very good OS.  And I think I may have an idea of where most of my problems steam from.  
Documentation.
The "official" fedora faq, on the website, is for FC5!!!  I didn't even mention the situation Fedora Frog put me in...I had to delete everything it did, especially my repositories.  It's the documentation, and of course the community, that make Ubuntu the great os it is, and the reason it's surpassed Fedora in apparent popularity in such a short time.  Amazing what a well written how-to will do.

---

### Post by dca on 2007-01-17
Fedora Frog worked great for me.  Just needed to make sure that was the first thing I did after install.  Flash from frog installed on root so it was just as easy to d/l & install flash from adobe's website.

---

### Post by KoRnholio on 2007-01-18
Fedora Frog worked flawlessly for me.  Much better than Automatix ever has (Automatix always kills X on my desktop).

I mainly deleted my FC6 partition because YUM was slow as a bear compared to Synaptic.

The installation is also more of a pain than Ubuntu.  Although, its still not nearly as complicated as, say, Gentoo :)  Just multiple cds can be annoying - especially when I didn't find out till after burning all discs that I didn't even need 4 and 5.  Other than that, I found them remarkably similar.  Actually, Fedora was much better about restoring X when it got borked.

---

### Post by Insomniac20k on 2007-01-18
I didn't have a very good experience with Fedora. 

I moved to it from  Gentoo. After my Gentoo died, I didn't feel like going through the install again so I fired up Fedora 4. It worked well after some configuration and I was happy.

Reluctantly, I moved to FC5 and I was blown away.  It worked great.

Then I went to 6 the day it came out and I could not get it to function properly. My wireless would not work on my laptop, games that used to work fine now lagged, and worst of all when I played DVDs the sound would not be in sink with the video and sometimes it would get all purple.

I had experimented with Ubuntu on another computer and didn't like it too much but after 6 failed me, I gave it another shot and I like it a lot. It worked out of the box and was easy to customize.

---

### Post by Scheater5 on 2007-01-18
Well, I've since trashed that install (couldn't resist trying to get a macintel to work again).  But I've heard alot of mixed things about Fedora, from a pretty wide range of people.  I'm getting the impression that it's a good OS, just a little more finicky with hardware than Ubuntu - and the fact that I along with most people vastly prefer apt to yum.  Later on down the line I'll probably give it another shot (barring the possibility that I get OSX on that desktop...then it'll be Ubuntu and OSX and nothing else!) maybe when 7 comes out.  I just didn't see anything about it that I preferred over Ubuntu - nothing.

---

### Post by cnayak on 2007-02-23
It's very odd that you had to google and google and google for simple stuff.

 [here]("http://www.fedorafaq.org/") is one of the first links I found from google - and there are many around. Given the line-by-line guidance, any dumb **** can set up the OS to be on par with Ubuntu. And every single guide I found, clearly mention the conflict between Livna and freshrpms (in bold too). Next time around, do yourself a favour by going between the lines.

 And FC 6 is by far the best release regarding hardware support. I have a two year old Acer laptop and I never managed to get the battery meter to work under ANY distro. Only Ubuntu 6.04 and FC 6 display the charge correctly. Almost all of my friends run FC 6 and they share between them many different hadware - 64-bit processors, SB Live cards, ATI and Nvidia displayadapters. They have never EVER encountered any hardware related problem. The only trouble I ever faced was to recognize my wi-fi card, and the grea Fedora community helped me out in this regard.

 Mebbe, all that OS hopping has ****** up your system real bad. Go install Windows if you don't find totally free software not up to your standards, or manage to get things working on your own. 

PS: You have waaay too much free time on your hands.

---

### Post by Scheater5 on 2007-02-23
Well, I'm happy that Fedora meets your approval.  The beauty of free software truely is the choice.  It didn't work for me - it does work for you.  Thus the two words *early* and *oppinion* in the thread title.  
But, I'm curious.  I would like to know how you think "OS hopping" could, quote, "**** up" a system?

---

### Post by igknighted on 2007-02-24
> **Scheater5 said:**
> The last 6 months since kissing Windows goodbye have, partly, been spent "experimenting."  Ubuntu has, and probably will be for the foreseeable future, my main workstation OS, but no sooner did I become comfortable with Ubuntu did I start "trying out" other OS's (including a disastrous affair with a botched attempt to create a Macintel).  Gentoo, FreeBSD (which I'm still experimenting with), OpenSuSE, Morphix and Santa Fe (neither of which even got installed), older Microsoft incarnations, and most recently, Fedora Core 6.

Well, my affair with Fedora didn't start off well.  At the time I had Herd 2 of Fiesty on my desktop, and apparently the Fedora installer didn't like having to deal with that.  Which, I suppose is not entirely it's fault.  See, the main CD-Rom drive on that comp is a little screwy - however, Ubuntu has never had a problem with it and always installs flawlessly.  Luckily this particular comp has a separate DVD drive, so I tried that, and finally, success.  

Run through the installer with minimal problems, and boot into a working Fedore Core environment with Gnome.  First things first - load up KDE.  Also with seemingly goes off without a hitch.  Reboot into KDE.  Here's where the real trouble starts.  I try to make all my experiments practical, so I figured I'd turn this desktop into a multimedia station.  Unfortunately that includes alot of software not in the main Fedora repo.  So I go to my trusty friend google and look for documentation on enabling extra repos.
And look.
And look. 
And look.  
Buried in there is the answer I'm looking for - the Linva repos and fresh RPMs repos.
Only the site I found didn't mention that they often conflict with each other.  Joy.
So I fire up Add/Remove programs and start grabbing stuff to play DVDs as per the instructions I found on the net (which, mysteriously, I can't come by again).  Now when I open Xine, the whole comp locks up!  
But, knowing Kaffine works with a xine backend, I figure if the instructions say xine will play it, Kaffine should play it - after all, I've got dvds playing fine in Kaffine in Kubuntu.  Sure enough, encrypted DVDs now play in Kaffine - playing a DVD in Kaffine screws up the graphics for everything else on the screen, and the DVD itself is very grainy.  
O yea, the the instructions that enabled the Linva repo forgot to put a header on the config file, so after the reboot Add/Remove programs wouldn't open - I just deleted the file in /etc/yum, figuring it's not worth it.  

So, it's early yet in my experience with FC6.  Alot of things are fine - web browsing, file browsing, got Kopote working fine, Limewire even works on FC6 when I have problems with it on Kubuntu (it's the network at my college, it doesn't like Flash apparently...still troubleshooting that one).  But there's all these little annoying details that make it seem less polished, when honestly I think it would be a very good OS.  And I think I may have an idea of where most of my problems steam from.  
Documentation.
The "official" fedora faq, on the website, is for FC5!!!  I didn't even mention the situation Fedora Frog put me in...I had to delete everything it did, especially my repositories.  It's the documentation, and of course the community, that make Ubuntu the great os it is, and the reason it's surpassed Fedora in apparent popularity in such a short time.  Amazing what a well written how-to will do.

Yeah, it took them a while to get the new "official FAQ" up, but aside from what they added most of it is the same, so you could have used the FC5 one.  Fedora is a little more consistant than Ubuntu is in this regard.    Overall, I found Fedora to have more polish.  Little things that Ubuntu overlooks like right click -> execute to run a program, no need to run it from a terminal.  I hate to say it in some ways, but Fedora is way ahead of Ubuntu from a technical standpoint.  They have a 3d effects setup program (see beryl), for an OS that came out at the same time as Edgy, they are using the 2.6.19 kernel instead of 2.6.17 the edgy uses, and while RPM's suck, yum is the best RPM package manager I have used (haha, yast and whatever Mandriva uses are its competition, so I guess thats not saying much).  I wish portage worked on any distro, sigh.

To make a long story short, I am using FC6 as my main OS until my new proc/mobo arrives, then its another free-for-all to see what gets installed working the best with the new parts!  Oh my, my grades will suffer lol.

---

### Post by cnayak on 2007-02-24
> **Scheater5 said:**
> Well, I'm happy that Fedora meets your approval.  The beauty of free software truely is the choice.  It didn't work for me - it does work for you.  Thus the two words *early* and *oppinion* in the thread title.
   
 You made many misleading points in your posts. I object them only. Sure, Linux gives us all lots and lots of choices and given the fact that its all free, there is little point in bitching about any shortcomings. 

> But, I'm curious.  I would like to know how you think "OS hopping" could, quote, "**** up" a system?

 'Twas a conjecture :). But trust me on this, properly tweaked, ANY OS will load up pretty fast.

---

### Post by cnayak on 2007-02-24
> **igknighted said:**
> Yeah, it took them a while to get the new "official FAQ" up, but aside from what they added most of it is the same, so you could have used the FC5 one.  Fedora is a little more consistant than Ubuntu is in this regard.    Overall, I found Fedora to have more polish.  Little things that Ubuntu overlooks like right click -> execute to run a program, no need to run it from a terminal.  I hate to say it in some ways, but Fedora is way ahead of Ubuntu from a technical standpoint.  They have a 3d effects setup program (see beryl), for an OS that came out at the same time as Edgy, they are using the 2.6.19 kernel instead of 2.6.17 the edgy uses, and while RPM's suck, yum is the best RPM package manager I have used (haha, yast and whatever Mandriva uses are its competition, so I guess thats not saying much).  I wish portage worked on any distro, sigh.

To make a long story short, I am using FC6 as my main OS until my new proc/mobo arrives, then its another free-for-all to see what gets installed working the best with the new parts!  Oh my, my grades will suffer lol.

 Ubunt u too has many nifty features. For example, there is always a OSD volume meter whenever I change the volume via the keyboard shortcuts on my lapop. Pretty neat and it looks good too.

---

### Post by igknighted on 2007-02-24
> **cnayak said:**
> Ubunt u too has many nifty features. For example, there is always a OSD volume meter whenever I change the volume via the keyboard shortcuts on my lapop. Pretty neat and it looks good too.

Yeah, but its not useful.  Plus I adjust my volume on the speaker directly anyways.  It is a nice touch tho, I hadn't realized that my keyboard shortcuts on my logitech keyboard worked, which apparently they do (in fiesty herd 4), which is a pleasant surprise.

---

