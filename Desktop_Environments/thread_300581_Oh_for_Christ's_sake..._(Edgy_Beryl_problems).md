---
title: "Oh for Christ's sake... (Edgy Beryl problems)"
date: 2006-11-15
forum: Desktop Environments
---

### Post by Cl1mh4224rd on 2006-11-15
Before I say goodbye to Ubuntu (and Linux in general, most likely) for a very, very long time...

Can anyone *please* explain to me why an attempt to install XGL+Beryl with [this HOWTO](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL) would result in:

1) [When selecting the XGL session] A black desktop, empty panels, and the complete inability to do anything other than wave the mouse around in frustration and whack Ctrl+Alt+Backspace, which itself results in...

2) A *completely* black screen. My monitor goes into standby and the system is unresponsive, requiring a manual restart. As an added bonus, I'm treated to the very same frustrating nothingness when I try to Restart, Shutdown, or Switch Users from a normal GNOME session...

...?

**Distro:** Ubuntu 6.10
**CPU:** AthlonXP 2700+
**Motherboard:** Asus A7N8X Deluxe
**Video card:** Radeon X800 GTO (using the latest proprietary drivers from ATI's website)
**RAM:** 1GB Corsair XMS (2x512MB; dual-channel; underclocked to match FSB)

](*,)

---

### Post by taurus on 2006-11-15
Let me get this right.  You can't get beryl to run with Edgy so you will say goodbye to Ubuntu and Linux in general for a very long time!!!  In case you don't know, beryl is still a beta meaning that it works for some but not for everyone!  If you look around these forums, you would have known that it sometimes crashes people's machines and they have to reinstall the whole thing over or it messes up their X that they need to reconfigure it before they can login into Gnome again...

---

### Post by canadianwriterman on 2006-11-15
Taurus is right, Cl1mh4224rd. You can expect problems when programs are still in the development stage. You do have a couple of options, though. I had bad luck with Beryl, but I did get Compiz working well. Or, you could move to Novell SLED, which has Compiz already configured. Or, you could wait for Feisty, which should have the desktop effects built in. Or, you could go to Windows and have no desktop effect, and all the rest of the security frustrations, limitations and excessive costs associated with it.

---

### Post by canadianwriterman on 2006-11-15
Also, your ID shows you as a Dapper user, but the link you provided for Beryl is for Edgy. I don't know, but maybe there is a difference.

EDIT: Sorry, I see you have Edgy listed at the bottom of your post.

---

### Post by igknighted on 2006-11-15
> **Cl1mh4224rd said:**
> Before I say goodbye to Ubuntu (and Linux in general, most likely) for a very, very long time...

Can anyone *please* explain to me why an attempt to install XGL+Beryl with [this HOWTO](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL) would result in:

1) [When selecting the XGL session] A black desktop, empty panels, and the complete inability to do anything other than wave the mouse around in frustration and whack Ctrl+Alt+Backspace, which itself results in...

2) A *completely* black screen. My monitor goes into standby and the system is unresponsive, requiring a manual restart. As an added bonus, I'm treated to the very same frustrating nothingness when I try to Restart, Shutdown, or Switch Users from a normal GNOME session...

...?

**Distro:** Ubuntu 6.10
**CPU:** AthlonXP 2700+
**Motherboard:** Asus A7N8X Deluxe
**Video card:** Radeon X800 GTO (using the latest proprietary drivers from ATI's website)
**RAM:** 1GB Corsair XMS (2x512MB; dual-channel; underclocked to match FSB)

](*,)

I have basically that exact same setup and would be glad to walk you through the beryl install.  A) XGL sucks, since you have an ATI card you don't have to deal with it.  B) Never touch proprietary crap like fglrx, even with a 10 foot pole unless necessary (luckily in this case it is not, the open-source 'radeon' driver is superior).  To get Beryl working with your card, try out this (preferably on a fresh install, not sure what has been done to yours right now), and since your system is nearly identical to mine I can't imagine it would fail: [http://www.ubuntuforums.org/showthread.php?t=290841](http://www.ubuntuforums.org/showthread.php?t=290841)

---

### Post by Cl1mh4224rd on 2006-11-16
> **taurus said:**
> Let me get this right.  You can't get beryl to run with Edgy so you will say goodbye to Ubuntu and Linux in general for a very long time!!!
This is merely one in a long line of disappointing attempts to make Ubuntu "cool". Beyond that, this was also an attempt to improve performance (why does X.org still suck at 2D rendering?).

It's not like I'm new to Linux. I maintain a FreeBSD server at work. (Yes, I know, it's actually Unix.) I've played with Gentoo numerous times. I even tortured myself by attempting to create a Linux From Scratch system (never finished). Aced an introductory class to Red Hat (the only person to get a 100%, but not a surprise given my previous experience.).

> In case you don't know, beryl is still a beta meaning that it works for some but not for everyone!
It worked in Dapper; same hardware. Even that took a few too many tries. "Why not just stick with Dapper, then?" Because I thought I had a choice. For all the talk of choice I see coming from the Linux community, there's an amazing attempt to gloss over (or outright ignore) the sacrifices. I wonder how this is at all different from Windows...

> If you look around these forums, you would have known that it sometimes crashes people's machines and they have to reinstall the whole thing over or it messes up their X that they need to reconfigure it before they can login into Gnome again...
I'm well aware of the issues, but, as I said above, I've had it working before, and I continue to hear an overwhelming majority of people praising its stability. Silly me.


> **igknighted said:**
> I have basically that exact same setup and would be glad to walk you through the beryl install.  A) XGL sucks, since you have an ATI card you don't have to deal with it.  B) Never touch proprietary crap like fglrx, even with a 10 foot pole unless necessary (luckily in this case it is not, the open-source 'radeon' driver is superior).  To get Beryl working with your card, try out this (preferably on a fresh install, not sure what has been done to yours right now), and since your system is nearly identical to mine I can't imagine it would fail: [http://www.ubuntuforums.org/showthread.php?t=290841](http://www.ubuntuforums.org/showthread.php?t=290841)
Yeesh... Another HOWTO. I'll give this a shot, but, seriously... at what point does a HOWTO for each combination of hardware and distro become absurd?

---

### Post by 23meg on 2006-11-16
[QUOTE=Cl1mh4224rd]at what point does a HOWTO for each combination of hardware and distro become absurd?[/QUOTE]At the point where it isn't absolutely needed.

---

### Post by 3rdalbum on 2006-11-16
I've got a Radeon XPress, and I used to run without graphics acceleration.

I know from experience that the proprietry ATI driver is the buggiest thing you can put into kernelspace.

You actually have another option: Use vanilla Compiz instead of Beryl. Less flashy, but more stable.

---

### Post by tubasoldier on 2006-11-16
Its because you chose ATI.

---

### Post by Cl1mh4224rd on 2006-11-19
> **igknighted said:**
> . . .since your system is nearly identical to mine I can't imagine it would fail: [http://www.ubuntuforums.org/showthread.php?t=290841](http://www.ubuntuforums.org/showthread.php?t=290841)
OK. This doesn't seem to be working. With a fresh install, switching the driver from "ati" to "radeon" (plus the options) actually results in *worse* performance.

Additionally, I can't even import the GPG key. I copy/paste the command given and get this:

```
$ wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
Password:--16:53:55--  http://www.beerorkid.com/compiz/quinn.key.asc
           => `-'
Resolving www.beerorkid.com... 208.113.152.130
Connecting to www.beerorkid.com|208.113.152.130|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,692 (1.7K) [text/plain]

100%[====================================>] 1,692         --.--K/s             

16:53:55 (17.89 KB/s) - `-' saved [1692/1692]



```
...and just sits there. I don't get the "OK" that I would expect and I'm not sent back to the command prompt. If I hit Ctrl+C I get:

```
sudo: pam_authenticate: Conversation error
```
I seriously doubt the GPG issue has anything to do with the changes I had made, though. I had installed the available distro updates immediately after installing the OS, and right before modifying xorg.conf and rebooting. When I logged back in, I no longer had any sound.

Weeee...

Edit: I've reposted this in the actual thread.

---

### Post by Cl1mh4224rd on 2006-11-19
> **tubasoldier said:**
> Its because you chose ATI.
So much for choice, ay?

---

### Post by Cl1mh4224rd on 2006-11-19
> **igknighted said:**
> . . .since your system is nearly identical to mine I can't imagine it would fail: [http://www.ubuntuforums.org/showthread.php?t=290841](http://www.ubuntuforums.org/showthread.php?t=290841)
OK. I finally got everything "working", but overall performance is actually worse. While the window drawing isn't quite as horrid (switching tabs in Firefox preferences still reveals noticeable drawing), the animation when creating windows for new applications is chunky.

Also, it sometimes takes up to two seconds for a window to close once I hit the close button on the titlebar.

Edit: Oh, and the screen darkening and lightening for gksudo makes me want to claw my eyes out now...

---

### Post by CatKiller on 2006-11-19
> **Cl1mh4224rd said:**
> So much for choice, ay?

Actually, I think you're supposed to be enjoying **informed** choice. So if you pick the wrong thing, then it's your own fault and you have to live with it. And if you don't take the trouble to become informed, then it's your own fault and you have to live with it.

I could be wrong, of course.

---

### Post by Cl1mh4224rd on 2006-11-20
> **CatKiller said:**
> Actually, I think you're supposed to be enjoying **informed** choice. So if you pick the wrong thing, then it's your own fault and you have to live with it. And if you don't take the trouble to become informed, then it's your own fault and you have to live with it.

I could be wrong, of course.
Oh, right... yes... let me just go out and buy a new video card so I can run Linux "properly". Or, rather... go out and buy an *old* video card.

I'm well aware that nVidia cards are "better" for Linux. I have what I have.

It seems more more apparent to me that there is a significant disconnect between what Linux enthusiasts believe and claim their OS is capable of, and what it is actually capable of in reality. And I wonder more and more how this is any different from what we see coming out of Redmond.

I'm certainly not a Microsoft fanboy, but I do seem to be quickly turning into a Linux basher... and that's a damn shame. :???:

Alright. I'm sorry, but there really is no reason to keep this thread open any longer. Linux in general has a long way to go on the desktop, in my opinion. A very long way.

I think I'm done here.

---

### Post by CowzRule on 2006-11-20
I noticed an improvement in Beryls performance when I installed the latest svn snapshot of Beryl.
See this page:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/SVN_Snapshots_Repository]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/SVN_Snapshots_Repository")
The only "bug" I've run into so far is sometimes windows and dialog boxes will open underneath already opened windows. To fix-it I just right click the Beryl icon in the Notification Area and click "Select Window Manager - Metacity" then do it again only selecting "Beryl". Basically restarting the Beryl window manager.
Give it a try.

---

### Post by BLTicklemonster on 2006-11-20
I feel your pain, Cl1mh4224rd. I tried over and over to get beryl to behave right in edgy, and got random results and clocklike precision when it came to glitches. So I removed it. I never was one for eye candy anyway. I kept having the "missing borders" thing every other time I used it, and half the time I tried changing settings (like the water thingy) it didn't work. Yes, I know it's beta, but still, it wasn't up to snuff for me. 

So if you really really really have to have beryl, either wait for ati to start making decent drivers, or get an nvidia (I used ati for a while in linux, and went out and purchased an nvidia and am happier now), and wait for beryl to get stable.

But I like that you appeared to be sticking it out! Way to go. Kudos to you, now just don't go overboard and leave. Ubuntu is still great no matter if beryl doesn't work.

---

### Post by orb9220 on 2006-11-21
Thanks BLTicklemonster on hitting it on the head.

> So if you really really really have to have beryl, either wait for ati to start making decent drivers, or get an nvidia (I used ati for a while in linux, and went out and purchased an nvidia and am happier now), and wait for beryl to get stable.

What he doesn't seem to understand that beryl is NOT ubuntu. So why is he dissing ubuntu for what is obvious an ati-beryl issue.

As for ati they suck for windows too unless you do the extra labor. I only install nvidia on windows or linux. And now I have alot less support questions related to graphic problems.

And to his it is what I have ati. Live with it or change it. I know alot of younger ones that will buy new video card just cuz they want to play some new game is thier only motivation. So if you are not willing to pay to get the best hardware for the job then don't point the finger at ubuntu saying it their fault.

There are many here with ati that got it working great with alot of tweaking and adjusting but it is alot more work.

I hope it is something that you did or not doing that way it can be fixed.
Otherwise you are stuck unless you are willing to get a nvidia card.

Sorry I couldn't help you.

---

### Post by infoseeker on 2006-11-21
I have an nvidia btw. I have installed both Kubuntu 6.10 and Ubuntu 6.10 on two different partitions and I have nothing but total happiness from both installations.  Beryl is running on the Ubuntu install without even a murmur.   May it progress to even greater heights. For beta software I find it amazing.

---

### Post by ShadowVlican on 2006-11-21
> **igknighted said:**
> I have basically that exact same setup and would be glad to walk you through the beryl install.  A) XGL sucks, since you have an ATI card you don't have to deal with it.  B) Never touch proprietary crap like fglrx, even with a 10 foot pole unless necessary (luckily in this case it is not, the open-source 'radeon' driver is superior).  To get Beryl working with your card, try out this (preferably on a fresh install, not sure what has been done to yours right now), and since your system is nearly identical to mine I can't imagine it would fail: [http://www.ubuntuforums.org/showthread.php?t=290841](http://www.ubuntuforums.org/showthread.php?t=290841)
if XGL and fglrx are sh!t, then all those guides out there MUST BE DELETED... they are guiding the noobs like ME WRONGLY. setting up stuff like this is difficult enough as it is, no need for dumb guides

> **tubasoldier said:**
> Its because you chose ATI.
don't go there ;) 

> **BLTicklemonster said:**
> I feel your pain, Cl1mh4224rd. I tried over and over to get beryl to behave right in edgy, and got random results and clocklike precision when it came to glitches. So I removed it. I never was one for eye candy anyway. I kept having the "missing borders" thing every other time I used it, and half the time I tried changing settings (like the water thingy) it didn't work. Yes, I know it's beta, but still, it wasn't up to snuff for me. 

So if you really really really have to have beryl, either wait for ati to start making decent drivers, or get an nvidia (I used ati for a while in linux, and went out and purchased an nvidia and am happier now), and wait for beryl to get stable.

But I like that you appeared to be sticking it out! Way to go. Kudos to you, now just don't go overboard and leave. Ubuntu is still great no matter if beryl doesn't work.
i have nvidia, wasn't easy to setup either... in fact i just made a thread about my problems.. lol

i have the missing borders problem... actually they are missing but they flash.. hahaha

---

### Post by BLTicklemonster on 2006-11-21
Yes, the flashing ones, too! I forgot all about that!

Actually, I still have it going in dapper, and it works fine. It's just in edgy where I had the problems. (I rarely use the dapper. It's my fallback os in case I screw edgy up too bad again)

---

### Post by ShadowVlican on 2006-11-22
my success story:
[http://ubuntuforums.org/showthread.php?t=304266](http://ubuntuforums.org/showthread.php?t=304266)

no problems so far... hope i don't jinx it :D

---

### Post by jrevillini on 2006-11-26
I feel kind of bad for adding to this post.  On one hand, I want to help.  On the other hand, as I stumbled through at least 20 different how-to guides, trying anything and everything to get beryl working on my system, I kept wishing there were fewer suggestions because there's no telling which one is going to work for you.

But I know that if everyone had that philosophy,. no guide would be written.  So anyway, here are a few things that could be stopping beryl form working on a system:

1) Let's say you get to the point that you can select the Beryl session styles when you're loggin in, you log in, notice that things look different, but none of the effects are running.  You might need to run the /usr/bin/beryl-manager script.  I don't think that just installing beryl puts this into your session start-up programs. So go to system>preferences>sessions and add it to your start up progs.

2) Beryl is running but you have no window decorations; before i realized that i should be running beryl-manager, i was running beryl-glx.  this seems to get all the effects loaded, but the windows decor is missing.

I wish i could be more helpful but I'm a stumbler as I said.  I have no idea what I'm doing in Linux most of the time.  I just follow guides until i get to the point I wanted to be at.  I really think that if we all spent more time at the command prompt understanding our system, we'd be better off in the GUI.  I definitely found that to be the case with Windows versions 2, 3.1, 95, 98, ME, 2000, and XP - my knowledge at the command prompt helped me clear up frustrating problems that the gui sheilded from me.

Not to get off topic, but is there a way to have an open terminal window where you can watch the things going on in the background as you interact witht he gui?  I know you can go to terminal, execute an app and watch it log things ot the console, but can ubuntu show what's going on with it?

Peace,
Jim

---

