---
title: "Flash in firefox slow (on a fast computer)"
date: 2007-12-22
forum: Desktop Environments
---

### Post by oddworld on 2007-12-22
I have a fairly fast computer - Dell inspiron e1405 with a core 2 duo cpu @ 2.0 ghz, 2 gigs of DDR2 ram, onboard intel graphics. Compiz works great, but it turned off at the moment.

When trying to do anything in firefox using flash, it is quite slow and choppy.
This includes youtube, shockwave games, etc...
I have disabled ipv6 (which sped up non-flash firefox a decent bit), but it did not affect youtube and shockwave games.
In other operating systems I have had no trouble getting youtube to play smoothly, so I know it must be a simple setting in ubuntu or perhaps a bad driver.

Installed is flash 9,0,115,0 which is the most recent.

Any help is much appreciated, thanks!

---

### Post by solarwind on 2007-12-22
Try using swiftfox.

Latest swiftfox 2 branch: 2.0.0.11

View the links here: [http://getswiftfox.com/tarballs.htm](http://getswiftfox.com/tarballs.htm)

Find your CPU and replace all occurances of the version in the link with the one above for the 2 branch (works with all your plugins).

Then run this:

sudo ln -s /usr/lib/mozilla/plugins/* . while in your swiftfox plugins directory

---

### Post by oddworld on 2007-12-22
So which would I pick for that?
I dont see core 2 duo, 
just Core Solo/Duo\
Core 2 is very different from Core 1

Ideally I would like to fix the problem in just firefox, but I suppose if I could integrate everything (google browser sync, adblock plus, fireftp) then I may be satisfied.

Any other ideas / what cpu to use on swiftfox?

---

### Post by solarwind on 2007-12-22
> **oddworld said:**
> So which would I pick for that?
I dont see core 2 duo, 
just Core Solo/Duo\
Core 2 is very different from Core 1

Ideally I would like to fix the problem in just firefox, but I suppose if I could integrate everything (google browser sync, adblock plus, fireftp) then I may be satisfied.

Any other ideas / what cpu to use on swiftfox?

Swiftfox is the **same thing** as firefox, it's just an optimized build. Also, I believe you want the "prescott" builds.

---

### Post by oddworld on 2007-12-22
ok so I downloaded the prescott, unzipped it
Ran "swiftfox"
A brower quickly pops up, named "mozilla firefox" is this indeed swiftfox?
Help -> about states I am using 2.0.0.11, the same version as my firefox build

Is it the same browser or is it swiftfox?

---

### Post by solarwind on 2007-12-22
> **oddworld said:**
> ok so I downloaded the prescott, unzipped it
Ran "swiftfox"
A brower quickly pops up, named "mozilla firefox" is this indeed swiftfox?
Help -> about states I am using 2.0.0.11, the same version as my firefox build

Is it the same browser or is it swiftfox?

Yes, that is swiftfox, trust me. Now run my command from your swiftfox plugin directory to get all your plugins working...

---

### Post by solarwind on 2007-12-22
```
cd <your swiftfox plugins directory>
sudo ln -s /usr/lib/mozilla/plugins/* .
```

Run that and you're good to go.

Also, here's a nice icon you can use if you decide to make a shortcut/launcher to your new browser ;)

[IMG]http://img150.imageshack.us/img150/9210/iconkm3.png[/IMG]

---

### Post by oddworld on 2007-12-22
I like the icon, and I like the browser
I will probably use this in the future.
Unfortunately though, the flash game I am trying to play is still slow.
I have downloaded the .swf for the game, any idea how to run it outside of firefox/swift ?

---

### Post by solarwind on 2007-12-22
> **oddworld said:**
> I like the icon, and I like the browser
I will probably use this in the future.
Unfortunately though, the flash game I am trying to play is still slow.
I have downloaded the .swf for the game, any idea how to run it outside of firefox/swift ?

Which game are you trying to play? I'll see if it's lagging for me.

---

### Post by oddworld on 2007-12-22
[http://onslaught.playr.co.uk/](http://onslaught.playr.co.uk/)

Click the link, let it sit there for like 2 minutes. The demo will show the computer playing.
You dont have to click anything after going to the link.
I did this with standalone flash player too, its slow as well.
You try it.

---

### Post by oddworld on 2007-12-22
So, back to the main idea...
Why is flash slow on my computer, and how do I fix it?

---

### Post by solarwind on 2007-12-22
Wow, this is a pretty fun game and it's working fine for me! I can't understand why it's slow for you. Did you install the drivers for your video card?

---

### Post by oddworld on 2007-12-22
No, I have not done anything yet to my video card. 
What drivers I have on the card now, are what booted up with ubuntu.
I have the intel 945? 955 ? 950 ? Something like that. 
glxgears runs smoothly, gets ~900 fps.
Any ideas?

---

### Post by skullhead on 2007-12-23
ya i think im having the proble as you ive tryed multiple browsers and all slow and what i mean by slow is my video is 3 secs ahead of my audio i dont know if thats the kind of problem your having?

---

### Post by oddworld on 2007-12-23
My video and audio arnt out of sync, but I am having problems with flash.
I don't really understand what would be wrong, I have the latest version.
Anyone have any ideas?

---

### Post by oddworld on 2007-12-23
I have an idea, but I need some advice.
I am using the "intel experimental modesetting" driver for my intel 945 graphics card
What if I used the i810 driver - "intel integrated graphics chipsets, including i810 ....blah blah ...915GM and 945 GM"?
I am very cautious to just try this, because I am not sure what will happen when I choose it.

I have a Dell e1405 with an intel 945 graphics card.
I am in the "Screen and Graphics preferences".
Everything works well with my computer, just slow flash.
900 fps with glxgears, I have even played a few games such as pingus.

I would like to know what might happen, and why I have the choice between these two drivers, and which might work best.
Thanks

---

### Post by oddworld on 2007-12-23
So I tried using the i810 drivers given, logged off. 
Upon trying to log back in I got that friendly black screen.
Booted into recovery mode, used 
```
 sudo dpkg-reconfigure -p high xserver-xorg 
```
to recover my xorg settings / driver.
So that didn't work.

Is there any way of updating my "intel experimental modesetting" driver, or is that handeled automatically within the update manager?
Also: still have that flash problem, looking for ideas.
Thanks

---

### Post by jargoman on 2008-01-07
I find if I move my mouse non stop flash will run smoother.

I'm running 1400 fps with my nvidia card and it's still choppy.

hmmm... perhaps adobe is slacking on linux support.

---

### Post by Big_Croc7 on 2008-01-30
I'm getting the exact same problem.. unfortunately, no solution, as yet.  I've checked the cpu, and it's pegged at 100% whenever flash things are playing in a browser, with slow, jerky playback.  Download the same file and play it in MPlayer, though, and it works fine - this may be a temproary fix you can try, but it's hardly ideal.

---

### Post by raucous1 on 2008-02-06
Same kinda problem here. Flash works ok when  viewing "normal sized" videos, but when I try to fullscreen a video, it becomes unbearable choppy. 

Im running a dell computer with a nvidia card (using the restricted drivers).  I have tried installing/uninstalling the different types of flash plugins (non-free, swf etc) but nothing seems to work. Whats the deal with this? My other computer (much older and slower) running Fedora has no problems with this.

---

### Post by antelopepoop on 2008-02-20
Same issue here.  Running a Dell 600m with an ATI Mobility 9000 on Gutsy.  I haven't messed with my video drivers or with my flash drivers (I used the one recommended by firefox (the Adobe ones)).  I get a 100% cpu usage when youtube is maximized, then it drops to 13% if I go to google.com

Btw - I am having issues with gtxgears.  First of all, where do you see your framerate?  Or is my issue that severe?  Whenever I try to move the window, the video will keep playing in its original spot for a little bit.  If I try to slide it across the cube to another desktop it really fritzes out and detaches into video chunks.
Secondly, [Noob Alert!] where do you find the launcher for the program?  I used synaptics, and found that it was already installed, then had to search for it using the desktop search tool.  I found it and launched it from there, but is there an easier way to launch it?

---

### Post by revolutio on 2008-02-23
I have the same problem.  Also glxgears says it is running at 800 fps but I can still see snags in it.  When I expand the window to fullscrean (like the flash videos that are causing me problems) it virtually freezes yet the console is still claiming 40 fps.

Like others have said, playing in VLC or SMPlayer causes no problems when in fullscreen.

antelopepoop, just run your console and just type in glxgears.  The framerate is displayed in the console so I suppose if you launched it by itself you wouldn't see the output.  Normally you will type in glxgears in the console and a new window with the gears will open up and then every few seconds a new line in the console will output your fps.

---

### Post by zxscooby on 2008-02-23
I had a similar problem with an older laptop, slow, jerky flash and other video problems, firefox would scroll very slowly.
i found that powernowd was causing the performance problem. i disabled it from the start up services. i used another power management app , dont remember wich one though.

---

### Post by madjr on 2008-02-25
this is a flash 9,0,0,115 issue

> For users of Flash CS3 Professional, an update including all Debug and Release versions of this new Flash Player and a new Video Playback component supporting H.264

since adobe hasnt ported flash cs3 (dev tool) to linux or any other version, we are f*cked, thanks adobe...


adobe been implementing a bunch of crap that is not fully compatible with linux and makes it extremely slow (also hardware acceleration is not really supported).

get the last one 9,0,0,48 which works extremely better with dual-core in comparison (even still it doesnt go as smooth as in other OSs in single core procesors, thanks ADOBE.....)

get it here (flash 9 zip file, has linux versions too inside)
[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1)

install 9,0,0,48 anyway it should fix your problem

---

### Post by revolutio on 2008-03-14
> **madjr said:**
> install 9,0,0,48 anyway it should fix your problem
No luck, same issue except now it isn't really fullscreen, just a large window.  

Any other ideas folks?  Right now Windows is beating Linux in terms of functionality. :confused:

---

### Post by samandiriel on 2008-03-15
Odd.  I don't have any problems at all, either with the game link or with playing video from youtube.  In fact, video is smoother with flash on my homer Gutsy install (Dell Dimension 9200) than it is on my work XP box (Dell XPS400).  

I have no clue what the issue actually is with your flash, but I'm definitely not experiencing it myself.  Not sure if that's because I have a high powered machine with pretty well supported hardware or not.

My flash plugin in FF 2.0.0.12:  Shockwave Flash 9.0 r115.

---

### Post by shea241 on 2008-03-15
I can confirm the slowdown when watching the demo mode of that flash game.  I don't have a fast CPU, a P4 2.8, but it's certainly fast enough to render some vectors on a small screen area.  I doubt the video card is truly the problem, since flash doesn't really use any hardware acceleration last I checked (with the exception of some acceleration of video rendering, and I don't even know if that's implemented in released versions of flash yet.)  I also doubt it's the video drivers, since I can make the frame rate much higher by picking the 'low quality' graphics setting in flash.  It's still updating the same screen rectangle, but it's doing it without any antialiasing.  So, I think the problem must lie in Flash's rasterizer itself.  I don't understand why it would be much slower under Ubuntu than any other OS, since I [naively] would assume that rasterization code is mostly platform-indepdent.  But I can't pretend to know anything about the inner workings of Flash.  It's probably more complicated than that.

The flash game certainly started off nice and fast, and the frame rate dropped somewhat linearly as more things were being drawn to the screen.  So sad!

---

### Post by revolutio on 2008-03-15
Processor certainly isn't a problem: Athlon 64 3400+

Video card certainly isn't a problem: Radeon 9800 pro

My thoughts are that it could be a problem with the ATI restricted drivers.  They have given me trouble before.  Though the issue is strange since there is **no** lag until the video is expanded, so the issue is with expanding flash video, not with basic running of flash.  Unless for some reason expanding causes an exponential increase in processor load, such that I really wouldn't notice sluggishness beforehand.

The problem exists in Firefox, Epiphany, Opera, and Firefox 3.0b3.

Updating the version of flash didn't seem to have an effect.  The Add-Ons tab in firefox still says 9.0 r115 though I installed 9.0 r48.

---

### Post by mazingerZ on 2008-03-15
I've got the same problem, I think.  Flash video on places like youtube "stutters." I'm using a dual boot and it doesn't do that under XP, so I think it's a software issue.

Using an AMD XP 1700+, Geforce 6, Gutsty Gibbon, Shockwave Flash 9.0 r115 w/ Firefox 2.0.0.12.

---

### Post by scimitar123 on 2008-03-16
I'm having the same problem also. In a small window flash is fine, but full screen is very jurky and jumpy. This is a particular problem with bbci ([www.bbc,co.uk/iplayer](www.bbc,co.uk/iplayer))

Alan

---

### Post by revolutio on 2008-03-21
I got 9.0.0.48 installed and the problem still exists on Firefox 2.  On Firefox 3b4 I can't actually get it to open a full-screen window.

---

### Post by Big_Croc7 on 2008-03-31
So basically, after reading around other threads and forums, it looks like there's no way to get it to work properly - Adobe can't/won't provide a version of flash that works properly under Linux.  There are open-source alternatives, such as Gnash, but these don't play Flash 9 yet (Gnash is up to v7, although there is a new version from a couple of weeks ago that may work with some v9 content).  

A lot of people find that adobe's v48 is smoother than v115, but then you don't get fullscreen.  The best solution for now is to write to the sites that use flash and ask them to release the content in a sensible (i.e. supported and open) format; the second best is probably to use a stand-alone player like MPlayer and a Firefox plugin like Fast Video Download to grab the flash file and play it from your hard drive.

---

### Post by Tomatz on 2008-03-31
I had this problem on my eeepc.

I just turned off hardware acceleration in the flash settings.

Just r click on the game/animation you are trying to play and click settings

Works fine now :)

---

### Post by geoken on 2008-03-31
> **Big_Croc7 said:**
> 
  The best solution for now is to write to the sites that use flash and ask them to release the content in a sensible (i.e. supported and open) format; the second best is probably to use a stand-alone player like MPlayer and a Firefox plugin like Fast Video Download to grab the flash file and play it from your hard drive.

What sensible format can the game be ported to? Java?

---

### Post by wdev on 2008-04-07
> **Tomatz said:**
> I just turned off hardware acceleration in the flash settings.

Just r click on the game/animation you are trying to play and click settings

Works fine now :)

Thanks!! I had the same problem as many of you - flash freezing my FireFox on YouTube and some games. Turning off hardware acceleration did it's job - everything's fine now :) Give it a try ;)

---

### Post by TRANQU111TY on 2008-04-25
Disabling Hardware Acceleration seemed to produce less lag but it is still a problem for me.

---

### Post by Ben C on 2008-04-30
I have the same problem. It's very annoying.

Disabling hardware acceleration doesn't work very well for me. It produces streaks, and doesn't look like the entire frame is updating at the same time.

---

### Post by uraldinho on 2008-05-13
This issue was the single most annoying problem with my ubuntu/firefox settings. It was getting unbearable, I've been using Opera without flash for some time now. 

After reading a few forums, I disabled hardware acceleration in flash. This made a big difference. Just to give you more details, apparently I'm using flash version 9.0.124.0...  

My graphics card is ATI with proprietary fglrx drivers, as a measure I also changed my fglrx settings to performance settings, rather than quality. 

At the moment, I'm happy that firefox is usable again. I'll see if my "browsing experience" improves. If not, back to the forums to do more reading.

---

### Post by PrimoTurbo on 2008-05-14
One of the reasons why I am back on Windows XP is because Linux has  horrible support for flash. On a low end system you cannot enjoy watching youtube. Firefox is also much slower under Linux for me then under Windows.

---

### Post by uraldinho on 2008-05-14
> **PrimoTurbo said:**
> One of the reasons why I am back on Windows XP is because Linux has  horrible support for flash. On a low end system you cannot enjoy watching youtube. Firefox is also much slower under Linux for me then under Windows.

Dude, don't give up :) 

Disable hardware acceleration and see if it gets any better. I was close to giving up firefox rather than ubuntu (need linux for work), but disabling hardware acceleration made a difference. 

I've also installed flashblock add-on for firefox. Saves me time and bandwidth, the add-on simply puts a play button where the flash file is supposed to be. This way you have a choice of loading or not loading the file. 

But, I do agree with you, I don't like the performance of firefox in ubuntu.

---

### Post by jackwhite on 2008-06-05
> **uraldinho said:**
> Dude, don't give up :) 

Disable hardware acceleration and see if it gets any better.

How do you do this?

---

### Post by Tomatz on 2008-06-05
> **jackwhite said:**
> How do you do this?

Try this:

> UBUNTU FAMILY 8.04 HARDY HERON USERS ONLY


Install the Flash plugin manually by downloading the tar archive of Adobe Flash v10 beta. Simply open the tar archive, then find the file named "libflashplayer.so and place it on your desktop. Next, execute this command in the terminal:

32-Bit Ubuntu Family Users Only:

sudo apt-get purge flashplugin-nonfree && sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplugin-alternative.so

You may now restart Firefox and use the plugin.

64-Bit Ubuntu Family Users Only:

sudo apt-get purge flashplugin-nonfree && sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo nspluginwrapper -i /usr/lib/flashplugin-nonfree/libflashplayer.so && sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so && sudo rm -f /usr/lib/firefox/plugins/npwrapper.libflashplayer.so

You may now restart Firefox and use the plugin.


PRE-UBUNTU FAMILY 8.04 HARDY HERON USERS ONLY


Install the Flash plugin manually by downloading the tar archive of either Adobe Flash v9 or Adobe Flash v10 beta. Simply open the tar archive, then find the file named "libflashplayer.so and place it on your desktop. Next, execute this command in the terminal:

32-Bit Ubuntu Family Users Only: 

sudo apt-get purge flashplugin-nonfree && sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/firefox/plugins/libflashplayer.so

You may now restart Firefox and use the plugin.

64-Bit Ubuntu Family Users Only: 

sudo apt-get purge flashplugin-nonfree && sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo nspluginwrapper -i /usr/lib/flashplugin-nonfree/libflashplayer.so && ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox/plugins/libflashplayer.so && sudo rm -f /usr/lib/firefox/plugins/npwrapper.libflashplayer.so

You may now restart Firefox and use the plugin.



All credits go to **reasuringlyoffensive** so if it works go thank him here:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by delamere on 2008-07-13
First of all apologies for bumping this thread.

I was having the same problem as many of you but resolved it by disabling the Shockwave flash player plugin. I am using the latest version of Firefox with Ubuntu 8.04, I think. Hope that helps :).

---

