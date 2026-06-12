---
title: "minecraft on ubuntu 10.10 - java?"
date: 2011-03-16
forum: Gaming &amp; Leisure
---

### Post by sssecure on 2011-03-16
Hello, im running ubuntu 10.10, graphics AMD Radeon HD 6850 w/ proper drivers and 3D acceleration. I have dualboot, with w7, where i play minecraft on a serv, but on linux, i can't simply start a game, the same in smp. Everytime i launch minecraft, login and try to play in multiplayer/ try to create a world in SP, it crashes. The log file is here:[http://goo.gl/NHfAw](http://goo.gl/NHfAw). I'm using java6, i tried the same with the open one available in the ubuntu software center, still the same. I tried to run minecraft on windows 7 in virtualbox, there it says "OpenGL not found" or somethingl ike that, although i installed the last drivers from AMD. googled for hours, tried hundreds of fixes and scripts, nothing helped. i love this game so much.. please help me. :)
Maybe this could help?
[http://goo.gl/hQF20](http://goo.gl/hQF20)

[http://getsatisfaction.com/mojang/topics/ubuntu_minecraft_issue_probably_java](http://getsatisfaction.com/mojang/topics/ubuntu_minecraft_issue_probably_java)

I copy-pasted this text from getsatisfaction [where i also wrote, but still no reply]

---

### Post by BbUiDgZ on 2011-03-16
i've always had problems with ATI cards and linux (not just ubuntu)
I just always buy nvidia now

---

### Post by sssecure on 2011-03-16
yeah, i found this out too. 
i will change my gtk in the future, still i want to run minecraft here. any idea?

---

### Post by flaak_monkey on 2011-03-16
Yeah I'm running Minecraft on Ubuntu 10.10 just fine. Perhaps try reinstalling java and/or launching Minecraft from its icon (in other words don't use the terminal)

---

### Post by sssecure on 2011-03-17
well, i did try that in the first step. didn't work.
im about to reinstall ubuntu, so wish me luck please .)

---

### Post by shmup on 2011-03-18
You really didn't have to reinstall Ubuntu, but I fear I'm too late.

---

### Post by sssecure on 2011-03-18
[FONT=Lucida Sans Unicode]okay, you were actually late.
now im screwed, i formatted the w7 partition accidentally and set it as a swap space for my 9.10 ubuntu i just installed.
now i can't even install the proper drivers, why does this stuff always happen to me?
it keeps on giving this error:

aticonfig: No supported adapters detected

googled, nothing.
it would be nice if anyone would help.. -__-

/// ok i think i will just update this one, try minecraft without any drivers [yep guys i know its completely a nonsense, cause it wont work without OpenGL, but anyways, i'll give it a try] and upgrade my ubuntu to 10.04.1 LTS. hope the drivers will work on that one.
[/FONT]

---

### Post by sssecure on 2011-03-18
omg.
i got minecraft to work here, slow as hell but working.
and im afraid that if i upgrade my system and install the proper drivers, it wont work. 
still im going to do that.
thank u guys for support [though im not getting any]

---

### Post by burton247 on 2011-03-18
I have minecraft running fine on my ubuntu laptop, but I now just run a server on that but I think I have proprietary ati drivers on it.

My desktop has an ati and I run minecraft on it under crunchbang. Took me a while to get it to work as there was an issue with openGL2 but once I sorted that it was fine, runs perfectly on it with the open source drivers. 

Got it running on my mates laptop too and it works better under ubuntu than windows.

Have you disabled all the fancy desktop effects? That could be slowing it down

---

### Post by MasterNetra on 2011-03-18
This might help, once you get to it, make sure Java Runtime is installed or OpenJDK. 

> 
*snip!*

Procedure:

   1. Make sure minecraft alpha has been run at least once so it can download the gamedata.
   2. Download the latest version of the game engine: [COLOR="Navy"][http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.5/lwjgl-2.5.zip/download](http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.5/lwjgl-2.5.zip/download)[/COLOR]
   3. Open zip file in Archive Manager and open jar/ directory
   4. Navigate to the minecraft game data directory in nautilus: /home/user/.minecraft/bin
   5. Drag jinput.jar lwjgl.jar lwjgl_util.jar from the archive to the minecraft gamedata directory
   6. Open native/linux/ in the archive
   7. navigate to /home/user/.minecraft/bin/natives
   8. Drag everything from native/linux/ to /home/user/.minecraft/bin/natives
   9. Your done! Start the game!

(Source: [http://www.minecraftforum.net/viewtopic.php?f=17&t=57426](http://www.minecraftforum.net/viewtopic.php?f=17&t=57426))

Once the files are properly installed it should run, you will have to run it from the .jar executable of course. If you need the .jar excutable of course goto: [http://www.minecraft.net/download.jsp](http://www.minecraft.net/download.jsp)

---

### Post by sssecure on 2011-03-18
@masternetra: well, the problem is that the actual version is beta, and the files listed in your post are from alpha version, so the game will actually update all those files itself x(

---

### Post by burton247 on 2011-03-18
The alphas will keep being updated.

However, any accounts bought in the beta stage won't get updates, only the final game when it is released.

---

### Post by sssecure on 2011-03-18
so when i bought the game in beta, i wont get the 1.4 beta update?
what a rip-off.
now, i got into the stage where i cant even install the drivers.
wish me luck

---

### Post by sssecure on 2011-03-18
Help PLEASE! :(
[http://imghosting.byl.cz/?v=screenepe.png](http://imghosting.byl.cz/?v=screenepe.png)
[http://imghosting.byl.cz/?v=screenkvk.png](http://imghosting.byl.cz/?v=screenkvk.png)

cant get this to work.. -__-

---

### Post by sssecure on 2011-03-18
started a new thread
[http://ubuntuforums.org/showthread.php?p=10574859#post10574859](http://ubuntuforums.org/showthread.php?p=10574859#post10574859)

---

### Post by burton247 on 2011-03-18
I think that is the case, I'm not sure though, I bought it in alpha and have always got updates

---

### Post by sssecure on 2011-03-19
okay, this problem is finally finished.
minecraft runs perfectly on my ubuntu 10.10  [a fresh xubuntu installation, then switched to ubuntu 10.10 session] 
the only problem.. or glitch is that when i'm walking and gathering wheat [or weed ^^], my character keeps on walking towards -__- and i have to press some more keyboard keys to get it right.

is there any answer to this question? or just a bug, and i should stop gathering anything and killing pigs instead?

---

### Post by sssecure on 2011-03-19
omg..
ubuntu 10.04 LTS x64 
now minecraft crashes like before.
any clue?

---

### Post by Veikk0 on 2011-03-21
> **sssecure said:**
> okay, this problem is finally finished.
minecraft runs perfectly on my ubuntu 10.10  [a fresh xubuntu installation, then switched to ubuntu 10.10 session] 
the only problem.. or glitch is that when i'm walking and gathering wheat [or weed ^^], my character keeps on walking towards -__- and i have to press some more keyboard keys to get it right.

is there any answer to this question? or just a bug, and i should stop gathering anything and killing pigs instead?

It's a known bug and also exists in Windows: [http://getsatisfaction.com/mojang/topics/sticking_keys_linux_only]("http://getsatisfaction.com/mojang/topics/sticking_keys_linux_only")
We'll just have to deal with it until Mojang fixes it :( I've fallen to death multiple times because of this...

> **sssecure said:**
> omg..
ubuntu 10.04 LTS x64 
now minecraft crashes like before.
any clue?
Have you installed the latest drivers from ATI/AMD website? If you haven't, remove the ones provided with Ubuntu before installing the new ones. I think the Ubuntu-provided drivers are older than your video card and thus don't have support for it.

And yeah, ATI's Linux drivers have historically been crap, although there's been some improvement lately. Now that I think about it, it's possible that you're in the same situation as I was a few months ago. I was using the Radeon HD 5450 with the latest drivers, and then I discovered Minecraft. When I started a new single player world it just crashed. It was obviously a bug in the ATI drivers since Minecraft worked with the open source drivers (albeit very slowly, ~5 FPS). I waited a few months for a bugfix but nothing changed: every month when ATI released a new driver version I tested it, and still Minecraft crashed. All other games worked well but Minecraft crashed no matter which Java version and proprietary driver I was using. My solution: sold the card and used my integrated graphics (ATI/AMD 760G). Installed the proprietary driver provided with Ubuntu 10.04 (drivers from ATI homepage didn't work for some odd reason...) and *voilà*! It worked! FPS was under 30 but it worked!!

Then a few weeks ago I got this Radeon X1950 Pro (from 2006) for €20. Installed the latest free drivers from xorg-edgers repository -> running Minecraft with ~40 FPS! :D

Anyway, it could also be because you're using the 64-bit Ubuntu. I'm using the 32-bit even though my processor could do 64-bit because after using the 64-bit version for a few days I came to the conclusion that it was more buggy and had some missing features (well, not features *per se*, but some applications don't have 64-bit versions). I have only 2 GB RAM anyway, and since the main benefit of using 64-bit is the possibility of having more than 4 GB RAM using 64-bit doesn't make much sense to me.

If new drivers don't work, try removing Sun Java and installing OpenJDK. Also, deleting the bin folder in .minecraft might be of help (makes Minecraft re-download the latest updates).

---

### Post by sssecure on 2011-03-21
@veikk0: i seriously love u for responding to my thread. ^^
i officially hate AMD & ATi from this time, and i think im gonna change my card for an nvidia in the future, because this "games" what amd plays with me during installing their damn drivers are starting to annoy me. 
What confuses me is that when i type uname -m into the console [terminal], it says "i686" what means i have a 32bit version of ubuntu. 
So ok, its an driver problem. I installed the latest drivers from AMD.com, via the wiki.ubuntu.cz guide. [yep im from czech republic, i probably mentioned it before, dont be scared when u c that noob language], but when i installed them, [the last line of the install process before the reboot was aticonfig --initial or something like that] the max. resolution was 1600x1200, but my native resolution is 1680x1050 with 60hz. So i had another 2 hour google session how to set it to 1680x1050, with an blinking message from my monitor saying "Input not supported", cos 1600x1200 is a different aspect ratio, right? Well, after those 2 hours of googling, i found some xrandr stuff, typed my own configuration of it and pasted it into .xprofile [or .xprofiles, who cares], rebooted and it was 1680x1050. 
I let this thread open and will check it every day, if anyone would have some ideas. 

But one last question.
What GTK from nvidia would you recommend?
My current specs:
AMD Phenom(tm) II X4 965
Kingston HyperX Genesis 4GB (kit 2x 2GB) 1333MHz
AMD Radeon HD 6850 

the other things aren't important, are they?

The CPU is running great, the gtk too, but that driver stuff is making me want to throw my machine out the window -___-

I want a Nvidia GTK like 2GB, that is able to run cs:s on 1680x1050 like this one, L4D2 as well, tf2, l4d..
and minecraft of course :D

Till then, i solved it this way - i have dualboot, ubuntu &*windows 7 64bit, windows 7 just for games [microsoft sucks, admit it. if it wouldn't be so commercial and pre-installed on all notebooks, machines and such things, games would be on mac & linux.]

---

### Post by sssecure on 2011-03-23
bump

---

### Post by Veikk0 on 2011-03-23
Hiya, I'm back! Sorry for the late answer, but I had my marticulation exam in math today. I just hope I'll pass, math isn't my strongest subject...

So yeah, think it's a driver problem. I googled "Radeon HD 6850 ubuntu" and found _[this 11-page thread]("http://ubuntuforums.org/showthread.php?t=1614444")_. Apparently AMD added official Linux driver support for HD 6850 in February this year, months after the Windows one! WTF?! I knew their Linux drivers weren't good, but over 3 months... that's really something -.- This just confirms what I think about their driver quality: new AMD/ATI video card + Linux = fail. If I ever think of buying a new card from them, kick me!

If you have the latest driver (version 11.2), have tried the stuff I recommended (try different Java, delete bin folder in the hidden .minecraft folder) and it just doesn't work, then I don't think there's anything else you can do but to switch to Nvidia or maybe get an older ATI/AMD card that works. You could try installing the driver one more time using this guide from the unofficial AMD Linux wiki [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually). And if you have the patience, try the 32-bit Ubuntu.

If you're planning to buy an Nvidia video card I'm not sure if I can help, or if you'll need any help at all. :P I don't have much Nvidia experience myself, but I've heard only good things about Nvidia cards in Linux. I have understood that one can buy pretty much any new Nvidia card and have it working without problems. Our old(ish) family computer has GeForce 7600 GT and it's always worked well and reliably. Runs Minecraft at 1280x1024 (max res :D), yay!

Anywhoo, I hope you're able to solve the problem and if you do, post here. I wanna know if this gets a happy ending and you get to play Minecraft. ;)

---

### Post by Mathomatistyx on 2011-03-23
Wow, my first post after a year of Ubuntu! :D

I run 10.04 on my desktop and 10.10 on my laptop. On 10.04, minecraft ran after I installed sun-java6-plugin from synaptic (I had no java at all), so make sure this is installed. On 10.10, I simply had to remove icedtea6-plugin, and it worked! I hope this helps... :)

---

### Post by sssecure on 2011-03-23
oh, thanks for responding. :)
i tried so much things between my last post and now to get minecraft working, but still it acts like notch would hate me.
my ubuntu desktop looks like this right now:
[http://dl.dropbox.com/u/20137117/Screenshot.png](http://dl.dropbox.com/u/20137117/Screenshot.png) -__-
but im going to make a customized install of ubuntu 10.04.2 today, burning it during nite and tommorrow, i will format the whole HDD, install win 7 and then the customized install of ubuntu (with amd drivers pre-installed). Hope it works..

(32bit ubuntu ver.)

by the way, [http://ubuntuforums.org/showthread.php?p=10592445#post10592445](http://ubuntuforums.org/showthread.php?p=10592445#post10592445)

have a nice day (or night)


@math: i've already tried all that stuf.. i did even try minecraft.exe in wine or playitonlinux, did not work. god bless me.. :(

---

### Post by sssecure on 2011-03-26
[font=courier new]please
[/font]

---

