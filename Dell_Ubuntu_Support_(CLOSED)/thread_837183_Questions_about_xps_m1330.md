---
title: "Questions about xps m1330"
date: 2008-06-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by CodeSamurai on 2008-06-22
Hello all.  I'm thinking about getting a Dell xps m1330 here soon and had a few questions.  I've scoured the forums and internet and only found half-answers, so I'm coming to you guys.  

1. What kind of battery life will I be looking at under ubuntu?  To answer this question, it'd be helpful to have your specs including screen configuration, battery size, and processor clock.  As well as which video card you are running.

2. How well do the media keys work?  Do you have to wait for a response before you can touch it again (such as volume) or can you treat it like a normal media key?

3. How well does wifi work?  Are you using ndiswrapper or madwifi?

4. Any quirky things or strange bugs I should know about? 

Thanks in advance.  Sorry about all the questions, I just really need straightforward answers and not, "My friend told me that his buddy had one and it got one million hours of batter life..." before I buy this laptop.  Thanks!

Trent out

---

### Post by akniss on 2008-06-22
I have the m1330 with the LED backlight display, X3100 graphics, 2.2 GHz cpu, 32GB solid state drive, and Intel 4965ABG wireless, running 32-bit Hardy (8.04).

> **CodeSamurai said:**
> 
1. What kind of battery life will I be looking at under ubuntu?  

With the 4 cell battery, I get right at 2 hours of battery life on my m1330.  This is with the wireless on, compiz running, and very basic usage (internet browsing, document viewing and editing.  Nothing cpu or graphics intensive (other than compiz).  I also purchased the 9 cell battery for use when I need more time, but haven't ever used my laptop long enough to know how much time it would actually give me.  I've used it for at least 4.5 hours without problems.

> **CodeSamurai said:**
> 
2. How well do the media keys work?  Do you have to wait for a response before you can touch it again (such as volume) or can you treat it like a normal media key?

Media keys seem to work fine for me.  I don't use the stop/play/previous/forward keys, so I can't comment directly on those.  Volume and mute buttons work just as one would expect.

> **CodeSamurai said:**
> 
3. How well does wifi work?  Are you using ndiswrapper or madwifi?

Wifi worked perfectly out of the box after a fresh install of 8.04 (also worked with Gutsy).  It uses the iwl4965 driver by default, and I've not had any trouble connecting to unprotected or WEP networks.  I've not tried WAP, however, so can't comment on that.

> **CodeSamurai said:**
> 
4. Any quirky things or strange bugs I should know about? 

The 9-cell battery provides substantial life, but is quite large.  It actually sits underneath the back of the laptop so that it sits at an angle when plugged in.  Not a big deal for me, but might be undesireable for the ultimate road-warrior.  

It took a little fiddling to get suspend working perfectly, but it is now flawless.  I can suspend/resume numerous times and wireless and display come back everytime.  This was not the case with Gutsy, but things work splendidly on Hardy.

Overall, I'm happier with my m1330 than any other laptop I've ever owned, at least now that I've got ubuntu 8.04 on it.  I initially ordered it with Vista (no ubuntu option at that time, I got one of the first ones off the shelf).

---

### Post by engineer on 2008-06-23
I can report a battery life of at least 5 hours with the 9-cell battery. I only tried it once so far. Most of the time I had wireless turned off, but I did some monte carlo simulations, so the cpus had to work a lot.

Media keys work fine, as reported from akniss.

---

### Post by sdennie on 2008-06-23
With LED backlight, nvidia 8400M GS, 2.5Ghz T9300 CPU and Intel 3945 wireless Hardy installs fine out of the box.  With some tweaking, I get 6-7 hours of battery on the 9 cell battery while doing things like IM and browsing.  As long as you stick to intel wireless, you should have no problem with any of the XPS m1330 configurations.

---

### Post by PsychedelicReaction on 2008-06-30
> **vor said:**
> With LED backlight, nvidia 8400M GS, 2.5Ghz T9300 CPU and Intel 3945 wireless Hardy installs fine out of the box.  With some tweaking, I get 6-7 hours of battery on the 9 cell battery while doing things like IM and browsing.  As long as you stick to intel wireless, you should have no problem with any of the XPS m1330 configurations.

which tweaks have u done? my 9 cells can't resist more than 4/4:30 hours (wifi on+nvidia). and i tried most of the tweaks from lesswatts but i didn't notice much improvement.

---

### Post by sdennie on 2008-07-01
> **PsychedelicReaction said:**
> which tweaks have u done? my 9 cells can't resist more than 4/4:30 hours (wifi on+nvidia). and i tried most of the tweaks from lesswatts but i didn't notice much improvement.

1) I use something like this: [http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644) to automate the powertop/lesswatts.org tips for switching to/from battery

2) I aggressively reduce disk activity using [http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998) but adapted for the link in #1.

3) Rather than use the PerfLevelSrc hack to get decent compiz performance, I use: [http://ubuntuforums.org/showthread.php?t=828369](http://ubuntuforums.org/showthread.php?t=828369)

4) I use the nvidia OnDemandVBlankInterrupts option in /etc/X11/xorg.conf and have a script that toggles compiz sync to vblank depending on whether or not I'm on battery.

5) I completely removed the uvcvideo webcam driver (I never use it).  It may be sufficient to just modprobe -r it though.

6) Contrary to what lesswatts.org says, I find it necessary to explicitly set the iwl3945 power savings mode

7) I don't keep a gmail tab open in Firefox but instead use Evolution.  This saves a surprising amount of power

8 ) I keep the backlight as low as possible

9) On battery, I only have Firefox, Evolution, Pidgin and a few terminals open.

That's all I can think of off the top of my head.

---

### Post by LibertyShadow on 2008-07-01
I have an XPS M1330 running Hardy x64 with 4GB Shared Dual Channel DDR2 SDRAM at 667MHz, Intel Core&#8482; 2 Duo T8300 (2.4GHz/800Mhz FSB/3MB cache), Slim and Light LED Display with VGA Webcam, 128MB NVIDIA® GeForce&#8482; 8400M GS, 250GB SATA Hard Drive (5400RPM),Intel Next-Gen Wireless-N Mini-card.

I bought the 6-cell battery - with wifi on, I get just over 2 1/2 hours (after configuring with powertop)

The media keys work as they are mean to, other than the eject button.  See: [https://bugs.launchpad.net/ubuntu/+bug/180866]("https://bugs.launchpad.net/ubuntu/+bug/180866")  However, I did not fix this myself because I would sometimes eject the media by accident when trying to hit F10 in the dark.

Intel wireless works flawlessly, although not at N-speeds (greatest is 54mbps).  I have tested it with both WPA and WPA2.

It might be a while before you get used to the keyboard.  I hit "|" countless times during shift-enters in Mathematica. It has good feedback, but the space bar is too flimsy for my taste.  The touchpad is on the small side.

One quirk: the M1330 runs a little hot.  I updated to Bios version A11 and enabled Powermizer (nvidia driver version 173.14.05), and since then things have been a little better.

Second quirk: []("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695") 
Setting Advanced Power Management to disabled (255) does not work for my hard drive.  I had to use 254.

---

### Post by bubbalouie on 2008-07-01
> **CodeSamurai said:**
> Hello all.  I'm thinking about getting a Dell xps m1330 here soon and had a few questions.  I've scoured the forums and internet and only found half-answers, so I'm coming to you guys.  

I have an Aussie delivered model, I've installed Kubuntu 8.04 with a fair few power saving tweaks in place (I have also undervolted the CPU), also I have no special effects enabled.
> 
1. What kind of battery life will I be looking at under ubuntu?  To answer this question, it'd be helpful to have your specs including screen configuration, battery size, and processor clock.  As well as which video card you are running.

Geforce 8400m, T9300, LED backlight, no cell devices or USB gadgets plugged in, Wifi on (BT off), I get about 3-3.5 hours from the standard 56 watt battery, that's just with Kopete (IM), Opera, Firefox,  Kate, SSH and a Konsole & file browser running though... I am sure if you run skype and flash and a bunch of other stuff it'll die in under a 2 hours (like any laptop usage makes a big difference)...
> 
2. How well do the media keys work?  Do you have to wait for a response before you can touch it again (such as volume) or can you treat it like a normal media key?

Everything works very well here, not much else to say (with backports the wifi light even works)... what really impressed me is the Fn keys, all good, even the monitor switching key, I did have to apply a dimmer fix to make the bbacklight jumps smaller though (one line in a config file).
> 
3. How well does wifi work?  Are you using ndiswrapper or madwifi?

All from the standard install and it works a treat, I can see quite a few AP's in my area...
> 
4. Any quirky things or strange bugs I should know about? 

The bluetooth can get a bit flakey unless your mouse is very close (less than 45cm), it starts out fine but oddly begins to degrade after a little while, oddly with a mobile phone it's all good.

The fan tends to run quite a bit, reducing power consumption helps with the fan though (all in all it isn't as bad as some other laptops, but not as good as a Sony). It does idle very cool compared to many laptops though, which I guess is a good thing.

The HDMI audio doesn't work too well, if you are watching a movie and Skype pops up a toaster box you can say goodbye to digital audio. The analog outputs are free of this issue, however, you can only use one of the headphone outputs (I think Linux treats it like a 5.1 card :) ), there may be a tweak to get stereo x2 but to be honest this is a non issue for me.

> 
Thanks in advance.  Sorry about all the questions, I just really need straightforward answers and not, "My friend told me that his buddy had one and it got one million hours of batter life..." before I buy this laptop.  Thanks!

Trent out

All in all, I can say it is a nice laptop, the build quality does leave a bit to be desired.... but then again, $2500 for a 13" laptop that has more features than most 15" laptops, something's gotta give, and to be honest, the build quality is as good as any other Dell I've used...

---

### Post by CodeSamurai on 2008-07-01
Thanks everyone.  Your suggestions and answers are really helping.  My dillema is this:  

I currently have a penryn macbook pro. (Didn't buy it, I actually won it in a university contest) and I think it's great, but for me it's 

1. Too big
2. Doesn't play well with Linux
3. It's apple...just not my style I guess.

I do enjoy the battery life however.  I can get close to 4 hours most of the time.  I've wanted to switch completely to Linux for years and seeing as how this is my last year of college, I'd like to go out with some style, haha.  I think I'm going to go with an xps m1330 with an LED screen, 8400m gs, and possibly a penryn processor, depending on price.  If I sell this macbook pro (which is super new) I have the potential to make 500-800 dollars off the deal.  

What would you guys do in the same situation? Would you keep the macbook pro or sell it and buy the dell?  Decisions, decisions.  I love linux, and especially ubuntu, but with so much power at hand, how does one decide?  Help me out ubuntu community!

Trent out

---

### Post by flakrat on 2008-07-01
A couple options with the Macbook
 1. Reinstall it with Ubuntu, or some other Linux
 2. With MacOS, install Virtual Box (free) and then create a Ubuntu virtual machine

Outside of that, if you really do not like the Macbook hardware, go for the XPS, I really like mine.

---

### Post by CodeSamurai on 2008-07-01
@flakrat

Yeah, I've done both already.  Thanks for the reply though!  It was just hard as heck to get things working on the macbook pro and I consider myself fairly well versed in the workings of Ubuntu.  I could get things to work, but in the end, I was just better off using OS X with this machine.  Especially considering the battery life.  That is a huge thing for me because of how much I am in class.  Ubuntu on this machine pulls maybe 2.2 hours with backlight low ad wifi on.  I'm in class for 4+ hours a day.  Even after using powertop and throttling, but if what I'm seeing on this thread is correct, the m1330 will give me better battery life on ubuntu than what I'm getting on OS X with this Macbook Pro.  Thanks for the reply!

Trent out

---

### Post by checksum_101 on 2008-07-03
I've run gusty and now hardy on my m1330 and would never go back to m$

only real quirk I've noticed is external dual LCD configs can be a little fiddly & over time I sometimes get redraw issues with the external lcd.

As a developer I still need do a little Flash from time to time so VirtualBox resolves that.

---

### Post by CodeSamurai on 2008-07-04
Happy 4th everyone!  I'm still having trouble deciding...I do have one more question:

How is the speaker quality?  I know laptops in general have pretty poor built-in speakers, but comparatively, how are they?  I listen to music quite a bit on the go.  The speakers on this Macbook Pro are pretty rockin' compared to my old toshiba satellite.  

Help me out Ubuntu community!  Thanks!

Trent out

---

### Post by sultanoswing on 2008-07-04
> **CodeSamurai said:**
> Happy 4th everyone!  I'm still having trouble deciding...I do have one more question:

How is the speaker quality?  I know laptops in general have pretty poor built-in speakers, but comparatively, how are they?  I listen to music quite a bit on the go.  The speakers on this Macbook Pro are pretty rockin' compared to my old toshiba satellite.  

Help me out Ubuntu community!  Thanks!

Trent out

The speaker's a bit tinny for my liking, but then I'd use headphones or external speakers for any serious listening anyway...I can't compare to other laptops, since this is the first I've owned, but I'm sure there are better out there - although the small form factor has an effect here.

My other experiences are similar to those above - a great little laptop - stylish and compact, with great stability and usability under Hardy (x64 in my case). Bluetooth a little on and off, wireless (intel) flawless incl. WPA2, build quality OK (although it doesn't quite sit flat on a flat surface - some little rubber feet are probably in order). 

Good battery life: more 2.5 hrs on 6-cell with the power saving fixes above under light use - I haven't actually had it run out yet. Although I may tone back the hard drive tweaks a little, since the drive spins up before scrolling, resulting in lag.

I was in the same quandry - buy a Macbook - similar price / performance and can run all three OS's. But then again, you only need one - and I'm very happy with linux these days, so felt a bit bad buying OSX only not to use it - whereas I had no such quandaries about wiping Vista without even booting it (although it hurt to pay the M$ tax).

In short - I am very happy with the purchase.

---

### Post by Poohbuntu on 2008-07-06
I, too, am planning to purchase an M1330.  In my first inquiry, however, the Dell rep claimed that they don't package the T9300 Penryn CPU with an M1330 running Ubuntu.  Anyone know the logic behind this assertion? :confused:

---

### Post by sdennie on 2008-07-06
> **Poohbuntu said:**
> I, too, am planning to purchase an M1330.  In my first inquiry, however, the Dell rep claimed that they don't package the T9300 Penryn CPU with an M1330 running Ubuntu.  Anyone know the logic behind this assertion? :confused:

I don't know the logic behind this and, in fact, this is the exact reason why I had to buy my XPS m1330 with Vista instead of Ubuntu.  When I bought mine the T9300 processor wasn't available for the Ubuntu machine and it sounds like it still isn't.  There is no apparent logic in this because Ubuntu runs fine with a T9300 CPU.

---

### Post by sultanoswing on 2008-07-07
> **Poohbuntu said:**
> I, too, am planning to purchase an M1330.  In my first inquiry, however, the Dell rep claimed that they don't package the T9300 Penryn CPU with an M1330 running Ubuntu.  Anyone know the logic behind this assertion? :confused:

There is no logic, and I fear (without having access to Dell's finances and Microsoft 'deals') that the T9300 is cross-subsidised by the crapware which comes with the Vista option.

Dell: if you're listening, there's not much point in having Ubuntu / Linux options if they're crippled, pared-down, low-option versions of the rest of the product line. I too was forced to buy Vista, but promptly wiped it. What a waste of cash, but even more galling is the fact that Ballmer can add one more to the tally, when it's simply not true.

---

