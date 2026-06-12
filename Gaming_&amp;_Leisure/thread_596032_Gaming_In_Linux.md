---
title: "Gaming In Linux"
date: 2007-10-29
forum: Gaming &amp; Leisure
---

### Post by Prometheus7 on 2007-10-29
Why are we so negative all of a sudden? I've seen tons of posts and blogs saying that linux is not meant for gaming and blah blah blah. You mean to tell me that I should dual boot xp/vista just because I want to play my made-for-windows games in their full potential? Screw that. I love ubuntu and am willing to have to tweak my games and fiddle with wine. I am also willing to code and test to help with any development/porting. It is the least that I can do for a much better OS which makes my life so much better.

---

### Post by cogadh on 2007-10-29
Right on, brother (or sister)! =D>

BTW - Love the avatar pic, where did you find it?

---

### Post by Baby Boy on 2007-10-29
Ditto.

I am also willing to work and tweak so I could play games in Ubuntu. If I said that to a Windows-er, he'd think we're all crazy, but I actually think it's kinda fun.

IMO, Ubuntu doesn't need to have ALL the games native/playable to beat Windows in every area, just a couple more good titles would suffice (like Black Isle games for example, or KOTOR, or an Elder Scrolls).

---

### Post by Prometheus7 on 2007-10-29
Avatar pic from xkcd comic: [http://xkcd.com/149/](http://xkcd.com/149/)

It is fun to make games work on linux. Putting in that extra effort is almost as fun as playing the game itself. It's just that wherever I go on the forums/web theres a bunch of ppl that like to be the naysayers and forget that Linux itself was created by ppl that stood up and said "I don't want to have to use a black box, I want to be able to tweak and change my programs to my liking". Why do I want to use a windows black box or buy some stupid gaming console just to have fun?

---

### Post by Baby Boy on 2007-10-29
I'm down with you on this one. It makes you appreciate the value of each and every game you play more knowing that you made it work. Besides, I don't like how aggressive the gaming market for Windows and consoles is. It only makes you want to buy more and more and more games and hardware, leaving you no time to do other things (of course, no one is *making* you do all that, but we all know what it's like when a sequel to your favorite game comes out). I like to take my time and do casual gaming.

---

### Post by cogadh on 2007-10-29
> **Baby Boy said:**
> ... (like Black Isle games for example, or KOTOR, or an Elder Scrolls).
Both KotOR games run perfectly through Wine (it's not native, but hey, it's something). Elder Scrolls 3 and 4 barely work and I don't know about Black Isle games.

---

### Post by Ripfox on 2007-10-29
I just tried Baulders Gate 2 with latest wine and it works almost flawless.

---

### Post by Baby Boy on 2007-10-29
> **ripfox said:**
> I just tried Baulders Gate 2 with latest wine and it works almost flawless.

Really? I always had problems with it. Still, BG1 doesn' work well if I'm not mistaken, neither does ID: Heart of Winter, not to mention the one and only best game in the world Planescape: Torment :D. BTW, I really think those games deserve to run with no probs through Wine or native.

With my previous post I was trying to say this - get **a few** games of this value working close to what they would in Windows and Ubuntu gaming experience would increase substantialy. Whether it's through Wine or natively, doesn't really matter, those who want those in Ubuntu wouldn't care much IMO.

---

### Post by Ripfox on 2007-10-29
Whoops my bad, it was Icewind Dale 2. :oops:

---

### Post by eaglesfan17 on 2007-10-30
I can't believe how far Wine has come along, I have Half-Life 2 and the Insurgency mod running perfectly, without any tweaking at all. It was as easy to install as it was in that legacy operating system.

---

### Post by Crafty Kisses on 2007-10-30
> **Prometheus7 said:**
> Why are we so negative all of a sudden? I've seen tons of posts and blogs saying that linux is not meant for gaming and blah blah blah. You mean to tell me that I should dual boot xp/vista just because I want to play my made-for-windows games in their full potential? Screw that. I love ubuntu and am willing to have to tweak my games and fiddle with wine. I am also willing to code and test to help with any development/porting. It is the least that I can do for a much better OS which makes my life so much better.
That was inspirational.

---

### Post by ohmycar on 2007-10-30
yeah it was heh, btw I liked that avatar. I am going to say it to my girlfriend and see if she slaps me.

---

### Post by Sethalos on 2007-10-30
Maybe one of you Linux Gaming Geniuses could help me get a simple game like PKR ([www.pkr.com](www.pkr.com)) to work in Linux. hehe.

I just haven't been able to do so, I keep getting an IE error, so I followed some instructions to install IE in Wine, and then tried to install PKR again, and no joy.

I love Ubuntu (Linux) and never want to have to go back to Wincrap, but I will end up duel booting to spend my leisure time playing the games I enjoy.

I also play World of Warcraft, and have that running flawlessly through Ubuntu, so there is hope.

Seth

---

### Post by cogadh on 2007-10-30
I believe that PKR requires ActiveX functionality, which doesn't work very well, if at all, in Wine. You might be able to get it working if you install the Mozilla ActiveX control:
[list=1]
[*]Download the Mozilla ActiveX control from  downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz
[*]Extract it to your fake Wine "C:\" drive, e.g. ~/.wine/drive_c/Program\ Files/mozcontrol.
[*]Now open a terminal, cd to that directory, and run wine regsvr32 mozctlx.dll.
[*]Go to the site by running the command "winebrowser http://www.pkr.com/"
[/list]

Ack, this is really a pet peeve of mine: 
> **duel**:
- noun
1.	a prearranged combat between two persons, fought with deadly weapons according to an accepted code of procedure, esp. to settle a private quarrel.
2.	any contest between two persons or parties.
–verb 
3.	to fight in a duel.

**dual**:
- adjective
1.	of, pertaining to, or noting two.
2.	composed or consisting of two people, items, parts, etc., together; twofold; double: dual ownership; dual controls on a plane.
3.	having a twofold, or double, character or nature.

---

### Post by ZylGadis on 2007-10-30
"duel booting" is actually a pretty good description of having GNU/Linux and Windows installed on the same computer.

---

### Post by Prometheus7 on 2007-11-05
> **ZylGadis said:**
> "duel booting" is actually a pretty good description of having GNU/Linux and Windows installed on the same computer.

Agreed. I almost killed myself a couple of weeks ago when I tried to install windows xp again. I had to install every single driver - for my sound card, for my graphics card, ahhh! I did it to see whether Half Life 2 Episode 2 played any better in XP than in wine. Yeah, not really. Maybe a little bit better because I was using the latest directx in windows and I only was using directx 8 in wine. I was a little frustrated in wine that the water effects were so miserable, but I can definitely deal with that.

Time to delete that xp partition :). Maybe I'll keep it a little longer so that I can finish playing the bioshock demo.

---

### Post by Baby Boy on 2007-11-05
> **Prometheus7 said:**
> Agreed. I almost killed myself a couple of weeks ago when I tried to install windows xp again. I had to install every single driver - for my sound card, for my graphics card, ahhh! I did it to see whether Half Life 2 Episode 2 played any better in XP than in wine. Yeah, not really. Maybe a little bit better because I was using the latest directx in windows and I only was using directx 8 in wine. I was a little frustrated in wine that the water effects were so miserable, but I can definitely deal with that.

Time to delete that xp partition :). Maybe I'll keep it a little longer so that I can finish playing the bioshock demo.
Tell me about it. It's funny how we didn't notice it before, Ubuntu sure is an eye-opener. I even have the Dell CD with all the drivers needed for my laptop and it's still a pain. Now I can only remember my woes with my custom-built desktop - why isn't my sound card working, what driver is the best for my graphic card, don't install drivers for your motherboard or they'll screw up your system...:lolflag:

---

### Post by Vitamin-Carrot on 2007-11-05
As gamers we shouldnt have to put up with using wine ... while no offence to the legends that DEV it, we should demand more linux native games like the titles epic and id release ... it is however a growing trend as i cant wait to play x3 on linux and ET:QW is just awesome.

We need a good solid count of linux users and more importantly gamers and if we think we dont have enough we have to convert some more over to linux.

I pulled 3 in the past week and they are all MOHAA players
:-P

---

### Post by almostlinux on 2007-11-05
'gaming on linux' is not moving FORWARD when you run games with wine.

As gaming gets better and 'as good as windows' when you run on wine, less people will want to do native linux port. And we surely don't want that, right?

In light of that, YES! :  Linux is not  good enough for gaming.

---

### Post by JusticeZero on 2007-11-06
Couldn't someone make a game that ran natively in Linux - and was packaged with a Linux quick-boot CD for Windows users?

---

### Post by cogadh on 2007-11-06
> **JusticeZero said:**
> Couldn't someone make a game that ran natively in Linux - and was packaged with a Linux quick-boot CD for Windows users?
Already done many times over, with several different distros and games. In fact, there is a great Linux game sampler live DVD you can get at [www.linux-gamers.net](www.linux-gamers.net).

---

### Post by Depressed Man on 2007-11-06
> **JusticeZero said:**
> Couldn't someone make a game that ran natively in Linux - and was packaged with a Linux quick-boot CD for Windows users?

Ideally yes..(but do you mean a live CD, with a game session running on it?). It'd be hell on RAM since the CD would have to load the OS into RAM, then the game itself lol.

---

### Post by saintlostone on 2007-11-06
> **Prometheus7 said:**
> 

Time to delete that xp partition :). Maybe I'll keep it a little longer so that I can finish playing the bioshock demo.

Um...sorry that this is slightly out of place, but how do you delete the xp partition?  Do you need to sudo or use synaptic?  I think I'm going to take the plunge...Thanx in advance

On topic, I think its awesome that Ubuntu supports some games natively, good that wine makes others possible, and crappy that the software producers don't make installers for Linux as well as windows.  They might be in the MAN's pocket, though.  After all, the less that works in Linux, the more you can make people depend on windows.

---

### Post by Prometheus7 on 2007-11-07
> **almostlinux said:**
> 'gaming on linux' is not moving FORWARD when you run games with wine.

As gaming gets better and 'as good as windows' when you run on wine, less people will want to do native linux port. And we surely don't want that, right?

In light of that, YES! :  Linux is not  good enough for gaming.

Gaming on linux IS moving forward when you run "made for windows" games with wine. The whole strategy is to convert Windows users to Linux users. When there is a bigger market for linux gaming, native linux games will follow. 

The problem is this -- making games is risky enough as it is. Companies are not willing to take the plunge and invest unless they know that the market is there for them. Unless you are suggesting that people make open source games (which is a great idea, btw) we will have to convince companies like EA and Valve etc that it is worth it to make linux-native games.

I'm not sure how Valve collects their stats -- if they can somehow tell the OS even if someone is using wine. But even if companies can't, if we have large communities of people playing the games on a non-windows OS (using wine, cedega, etc) then there will be enough noise for the companies to hear us.

---

### Post by Prometheus7 on 2007-11-07
> **saintlostone said:**
> Um...sorry that this is slightly out of place, but how do you delete the xp partition?  Do you need to sudo or use synaptic?  I think I'm going to take the plunge...Thanx in advance


Use the Ubuntu Live CD...
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

"Uninstalling Windows XP

If you decide after a while that this dualbooting situation is no good and you wish to scrap Windows XP, it’s actually very easy.

Go through the process outlined above to modify the MENU.LST and remove the Windows boot entry.

Then boot off the Ubuntu Live CD and go into GNOME Partition Editor. Right-click the Windows partition (/dev/hda2) and select Delete."

---

### Post by tech9 on 2007-11-07
> **Prometheus7 said:**
> Why are we so negative all of a sudden? I've seen tons of posts and blogs saying that linux is not meant for gaming and blah blah blah. You mean to tell me that I should dual boot xp/vista just because I want to play my made-for-windows games in their full potential? Screw that. I love ubuntu and am willing to have to tweak my games and fiddle with wine. I am also willing to code and test to help with any development/porting. It is the least that I can do for a much better OS which makes my life so much better.

I agree! I am trying to leave windows by the waste-side:)

---

### Post by Redenbacher on 2007-11-07
Blizzard releases all of its games now in both Windows and Mac. 
There is no reason they can not release it for Linux as well, or at least some kind of linux installer, am I right? 

Like it was said earlier, there just has to be a big enough market for it. I think Linux users are approaching that threshold rapidly. 

Do you think that the number of Linux distributions are perhaps a discouragement?

---

### Post by cogadh on 2007-11-07
Yes, there is no reason that Blizzard couldn't release a linux client for many of their games, especialy WoW. During the WoW beta, there actually was a Linux client which was scrapped before retail release.

I don't think the large number of distros really affects anything, since all distros are basically the same at the core. They use the same kernel and the same libraries, but possibly different versions of them. The multiple versions could be a problem, but just like Windows games can require certain versions of drivers and DirectX, there is nothing stopping Linux games from requiring the same of Linux users (i.e. a minimum kernel version, minimum driver version, minimum SDL version, etc.).

---

### Post by stuart.crouch on 2007-11-07
> **Prometheus7 said:**
> Use the Ubuntu Live CD...
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

"Uninstalling Windows XP

If you decide after a while that this dualbooting situation is no good and you wish to scrap Windows XP, it&#8217;s actually very easy.

Go through the process outlined above to modify the MENU.LST and remove the Windows boot entry.

Then boot off the Ubuntu Live CD and go into GNOME Partition Editor. Right-click the Windows partition (/dev/hda2) and select Delete."

Out of interest if you actually did this does it re-allocate the space?
I was just thinking anyone as beginner to computers doing this - they wouldnt know to do anything after they remove the windows partition, potentially leaving them with half a hard disk they can't access (unless they start rtfm'ing and figure out how to format and assign the partition to linux)

Edit: Just re-read the fine article. Its not just click a button, you have to follow the steps in the article itself (which says "and now we'll reclaim the space").  Nice find :D sorry for being a dumb-tard.

---

### Post by Prometheus7 on 2007-11-07
> **stuart.crouch said:**
> Out of interest if you actually did this does it re-allocate the space?
I was just thinking anyone as beginner to computers doing this - they wouldnt know to do anything after they remove the windows partition, potentially leaving them with half a hard disk they can't access (unless they start rtfm'ing and figure out how to format and assign the partition to linux)

Edit: Just re-read the fine article. Its not just click a button, you have to follow the steps in the article itself (which says "and now we'll reclaim the space").  Nice find :D sorry for being a dumb-tard.

Not entirely sure, but I think it does reallocate. Haven't done this so you might want to post at the web site I linked to.

---

### Post by Prometheus7 on 2007-11-07
> **cogadh said:**
> Yes, there is no reason that Blizzard couldn't release a linux client for many of their games, especialy WoW. During the WoW beta, there actually was a Linux client which was scrapped before retail release.

I don't think the large number of distros really affects anything, since all distros are basically the same at the core. They use the same kernel and the same libraries, but possibly different versions of them. The multiple versions could be a problem, but just like Windows games can require certain versions of drivers and DirectX, there is nothing stopping Linux games from requiring the same of Linux users (i.e. a minimum kernel version, minimum driver version, minimum SDL version, etc.).

The kernel and most of the libraries are the same, but yes you might run into problems due to the different distros. This is why the ultimate goal would be for the games themselves to be open source. So that anyone can compile them on any distro.

---

### Post by cogadh on 2007-11-07
A Linux distribution is just a collection of prepackaged software built on top of the same basic Linux core. From Slackware to Fedora to Suse to Ubuntu, underneath they are all the same. The visual style and software selection that make up a distro don't change that. Since any game running on Linux just cares about the core libraries, the kernel and the drivers, what possible problem could there be with making a game to run on different distros? Like I said, they might have to put in certain minimum requirements just to ensure compatibility, but that is not unreasonable at all. In fact, the few Linux native games I have already do that (i.e. kernel 2.4.x or higher, OpenGL 1.4 or higher hardware capability, etc.).

---

### Post by Prometheus7 on 2007-11-08
Wouldn't you have to have rpms for redhat, debs for debian, etc? After having to compile numerous programs on my own, I'm just saying that some differences are there and they make it difficult for someone to write a program for every linux distro. The safest bet is usually to offer the source code so that anyone can compile it on their own against their own libraries.

---

### Post by cogadh on 2007-11-08
Developers would only need to do that if they chose to create their install files compatible with specific package managers. They don't actually need to do that when they could simply release it as a generic .run file that will work on any distro. Id already does that with their Linux installers (Doom 3, ET: Quake Wars, etc.), as do many other Linux native game developers. The only downside to that is the installer won't automatically install or update any dependencies like a DEB package will, but it can alert the user when a dependency is not met. It would be the responsibility of the user to make sure they satisfy those dependencies, then run the installer again. 

It's no worse than a Windows game installer alerting you to out of date drivers or DirectX. In fact, in most cases, the resolution of dependency problems is easier to deal with on Linux than on Windows due to the use of package managers.

---

### Post by &#12465;&#12452;&#12488; on 2007-11-08
If the installer is such a huge problem, maybe [MojoSetup](http://icculus.org/mojosetup/) will make it easier for developers to package GNU/Linux versions of their games.

---

### Post by ricanelite on 2007-11-08
shoot, I'm trying to get World of Warcraft installed and running. On Cedega. For some reason it wont install. I do not know if it is because I installed XGL/Compiz and that is what is making it not work right. Do not know whats up. If anyone has any suggestions, Please let me know. Because I would hate to have put back Windows Vista on this machine.

Because I came to love Ubuntu especially now I could watch Youtube and videos on the web without having to pull out my hair. Using a OS which I do not have to worry about virus. So come one. So please guide me. I'm new to Linux and already I love it. What made me love it more was XGL and Compiz WOW! Just amazing

---

### Post by Prometheus7 on 2007-11-08
Why are you using cedega for WoW when wine works just fine? 

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922)

From what I've read, you just need to do some OpenGl hack.

---

