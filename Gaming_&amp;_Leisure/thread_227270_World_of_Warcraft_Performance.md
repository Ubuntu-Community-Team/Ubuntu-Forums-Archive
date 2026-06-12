---
title: "World of Warcraft Performance"
date: 2006-08-01
forum: Gaming &amp; Leisure
---

### Post by AngryKidJoe on 2006-08-01
[b]Linux Distribution = Kubuntu 6.06 Dapper Drake (686)
Wine version = 0.9.18
Graphics make/model/memory/driver version = NVIDIA/6600/256MB/8762
CPU model / CPU Memory = AMD 64 3200+ / 1GByte[/b]

No matter what I set the graphic settings to, they stay the same. About 30 in indoor areas and 10-20 outdoors. The only thing to change anything is Terrain distance. Is it the emulation that's halting my FPS or is there any other options I have to improve them?

Like I said, the ingame options do little to nothing to alter FPS.

There was a command somewhere "eselect nvidia opengl" or something or other but all it did was give me an error which I do not recall. 

Insight?

---

### Post by alynx on 2006-08-02
I know , but you will be stuck with lower FPS in Wine than Windows generally.  I had 97 FPS in RFK actually :p

I recommend that you turn off vertical sync and trilinnear filtering in the grapichs ingame , that boosted my FPS anyways. Dont really know if it works for you , but we got the same Computer spec except the Processor.

---

### Post by AngryKidJoe on 2006-08-02
I have all that stuff off. There's probably something in the Config.wtf that I can turn off to fix it.

---

### Post by AngryKidJoe on 2006-08-02
<double post>

---

### Post by alynx on 2006-08-03
I only added the following in the Config.wtf

SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxApi "OpenGL"

But i guess you have allready tried that?

---

### Post by AngryKidJoe on 2006-08-03
Correct. It's gotta be with how something is configured I'm sure. I'm going to play around for a little while. Hell, if I can get it up to 30 fps consistantly, I'll be more comfortable playing WoW in Linux. Right now I'm switching back and forth (XP is running w/ OpenGL as well) to test some tweaks and see if I can find equals in Kubuntu.

---

### Post by ilmorris on 2006-08-04
> **AngryKidJoe said:**
> Correct. It's gotta be with how something is configured I'm sure. I'm going to play around for a little while. Hell, if I can get it up to 30 fps consistantly, I'll be more comfortable playing WoW in Linux. Right now I'm switching back and forth (XP is running w/ OpenGL as well) to test some tweaks and see if I can find equals in Kubuntu.

I am very interested in hearing your findings.  I have never been able to get comparable performance for WoW thru wine or cedega on my system.  My experience is very similar to what your original post states... 9-12 fps outdoors, 21-25 fps indoors.  My windows performance is almost exactly twice the listed fps i.e. 19-24 fps outdoors, 38-43 fps indoors.  I have tried multiple distros with similar results.  As it stands WoW is the only reason I still have a Windows partition on my personal computer.  I am beginning to think that my system is just too underpowered to run comparably via wine.

Athlon XP 2100+
1GB DDR 2100 Ram
120GB Seagate Barracuda SATA HD
nVidia GeForce 5500FX 256MB

---

### Post by alynx on 2006-08-04
I'll get to work at mine aswell ;)

---

### Post by nalthien on 2006-08-04
One thing that helped me somewhat is turning on triple buffering in the Config.wtf file:

SET tripleBuffer "1" 

I believe is the line--I'm at work so I don't have my Config.wtf in front of me.

---

### Post by cabugi on 2006-08-06
Alright I used to get a decent framerate until I tried that eselect opengl set nvidia thing.  Now it just crashes immediatly and doesnt let me launch it in opengl mode.  I've been trying to find out a way to change whatever I did back to default.  Can anyone help me?

---

### Post by toasterofirony on 2006-08-06
This was something I hoped someone might advise me on, too. I'm running an FX5600 256MB card and though it was happy enough in Windows, I've only acheived reasonable FPS by turning everything down to minimum. I did the first two bosses of AQ20 last night and was nearly lagged to death :\

One thing that struck me as odd was that even though it claimed to be running with 2xAA and all the bells and whistles when I was first playing around with the graphics, it blatantly wasn't.

Also, I forced my desktop to 60hz, rather than 75 which it seemed to prefer despite my requests to the contrary, and now WoW won't recognise this change.

That said it's certainly playable, it's just annoying I can't make it perfect :P

---

### Post by lmandrake on 2006-08-14
Do you guys get the same fps while looking / moving around? When I run straight ahead and just look up and down my framerate is fine, but as soon as I start looking around or change the view with the mouse I get around 1-2 fps and this is not really  playable.

I have an AMD XP2500+ with an ATI 9600XT running the latest ATI drivers (fgl_glxgears gives me around 650fps) and I tried both opengl and d3d (with opengl being a little bit faster). I attached my Config.wtf; maybe there is a false set parameter.

---

### Post by ilmorris on 2006-08-14
> **lmandrake said:**
> Do you guys get the same fps while looking / moving around? When I run straight ahead and just look up and down my framerate is fine, but as soon as I start looking around or change the view with the mouse I get around 1-2 fps and this is not really  playable.

From my own experience, I have not found a playable experience as of yet with wine or cedega.  That is not to say that I can not play the game, just the FPS that I am observing makes the game unplayable if a lot of action is going on.  Of course this may be related to my older hardware, (ASUS A7N8X-E Deluxe Mobo, Athlon XP 2100, 1GB Ram, 120GB SATA HD, GeForce FX5500 256MB).  I have noticed a lot of the people posting comparable performance seem to have fairly new hardware as compared to my existing hardware.  I might try a base comparision and post the results that I see using a plain no mod install of WoW on both sides of my system.  Just to show the results I am observing.  If there is anyone out there seeing 'comparable' performance that can post performance screenshots from their Windows machine and Linux systems, along with their config files that I think would be very helpful.  I really would love to get WoW running smoothly under Linux if at all possible.

---

### Post by gremeth on 2007-02-05
[FONT="Tahoma"]
Concerning FPS when running WoW under wine 9.3 or later...
[LIST=1]
[*]Make sure you have the most recent version of wine.  I used the winehq.org debs. [http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb").
[*]Follow the relevant portions of the WineHQ HOWTO making sure to install the .dll files and add the registry key. [http://appdb.winehq.org/appview.php?iVersionId=6482]("http://appdb.winehq.org/appview.php?iVersionId=6482") 
[*]Edit your Config.wtf to suit your machine.
[/LIST]
That should be it.  On my system, World of Warcraft performs just as well in Wine as in Windows XP Pro.  I would even say it is more responsive, but I attribute that to opengl mode.  Good Luck!
[/FONT]

---

### Post by Sammi on 2007-02-05
This is all that most Ubuntu users need to get WoW up and running: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by abzolutxero on 2007-02-06
concerning the first tweak in that howto, i had a hard time creating the registry key in wine's regedit.  for some reason, it wouldnt allow me to rename the key once i created it, so i made a .reg file you can just import.


***USE AT YOUR OWN RISK.  I CANT OFFER MUCH SUPPORT IF THIS DOES OR DOES NOT WOR***

all will say is that it worked like a charm for me, and i saw a significant FPS increase... 


1-download the attached file
2-open terminal
3-run the following: "wine regedit"
4-backup your registry (file>export....)
4-import attached registry file (file>import....)
5-close regedit

hope this helps out for anyone having any difficulty.  the second tweak on that howto, i saw no FPS increase, so i just dont use it.

---

### Post by Sammi on 2007-02-07
I've already added info to the howto on how to bypass the bug that stops some people from editing that key. You shouldn't need to import that file.

---

### Post by dspari1 on 2007-04-26
I got the best performance by turning down tarrain distance to a minimum **AND** turning off vertical sync. Because of this, I'm now running the game at 38fps outside on my P4 2.4ghz, 1gb of ram, and Geforce 6600GT 128mb. 

Changing any of the other settings did not impact my performance at all. (I turned up my rez to 1280x1024, turned on all the options to the highest, I even turned up AF up a notch; my performance stayed at 38fps regardless of what I did). 

I am also running 
Beryl /w
Texture from Bitmap
COW - OFF
Force AIGLX
XGL Binding
XGL Rendering
Blur - OFF
Wine legacy windows - ON (for proper fullscreen)

Note: I am running CrossOver Linux instead of Wine or Cedega because I like the fact that I can change the settings in OpenGL without crashing.



here is a quick screenshot that I took:

---

