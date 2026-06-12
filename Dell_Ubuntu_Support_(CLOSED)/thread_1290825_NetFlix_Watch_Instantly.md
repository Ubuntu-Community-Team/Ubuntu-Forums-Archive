---
title: "NetFlix Watch Instantly"
date: 2009-10-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by goofynewf on 2009-10-13
This may be an odd question.  I love Netflix and watching movies instantly.  

Watching instantly with Ubuntu is not available.  

From the Netflix website: "Our apologies — streaming is not supported for your operating system.  Note that your current Internet browser is fully compatible with adding titles to the Instant Queue for later watching on compatible devices." 


Does anyone know of any plug ins that would allow an Ubuntu user to use Nextflix watch instantly feature.  



Thanks.

---

### Post by jessiebrownjr on 2009-10-18
> **goofynewf said:**
> This may be an odd question. I love Netflix and watching movies instantly. 
 
Watching instantly with Ubuntu is not available. 
 
From the Netflix website: "Our apologies — streaming is not supported for your operating system. Note that your current Internet browser is fully compatible with adding titles to the Instant Queue for later watching on compatible devices." 
 
 
Does anyone know of any plug ins that would allow an Ubuntu user to use Nextflix watch instantly feature. 
 
 
 
Thanks.
 
Im not on my ubuntu box so I can't tell you what it might be missing but do you see anywhere on there a "requirements" page? If its something like Flash or something you will see it..

---

### Post by Brandon Williams on 2009-10-19
To the best of my knowledge, Netflix "Watch Now" uses Microsoft silverlight for streaming. Novell (I think) has been working on a port of silverlight for linux, called moonlight. However, moonlight is still not capable of handling most silverlight content, at least, it wasn't the last time I played with it. You could give it a try, but it's unlikely to work.

I haven't tried, but it's possible that you might be able to get silverlight working by running IE with wine. This is very new functionality, so it falls into the category of app that is unlikely to work very well in wine.

---

### Post by ghostborg on 2009-11-02
I am interested too but I got one of those ROKU boxes.
You can use Virtualbox for now.
I have not tried the IE wine thing as above.
The problem with the ROKU box is that you need to go to a computer to add
content to your watch instantly queue.
My favorite way was using the Windows MCE with a MCE remote. This allows you to use the Netflix watch Instantly and browse movies to watch which the ROKU box does not allow. BTW they have three box choices now and the $79 dollar one cannot stream HD content.
I guess they have some issue with Linux that potentially violates copyright laws.):P

---

### Post by maruchan on 2009-11-06
If you have a Windows XP, Windows Vista, or Windows 7 CD, you can do what I did: Install VirtualBox, then install the Windows OS of choice, then watch Netflix Instant Watch titles from there. Works great...I have a Roku player too, and love it, but sometimes I want to watch at my PC.

---

### Post by jaqrah on 2009-11-06
> maruchan  	
Re: NetFlix Watch Instantly
If you have a Windows XP, Windows Vista, or Windows 7 CD, you can do what I did: Install VirtualBox, then install the Windows OS of choice, then watch Netflix Instant Watch titles from there. Works great...I have a Roku player too, and love it, but sometimes I want to watch at my PC. 

Really?  Although I haven't tried this in three or four months, my experience was horrible at best.  Usually, the sound would not synch with picture and the picture would stutter in super slow mo or just stop altogether.  I have not had **any** success using Netflix from inside a virtual environment.

What settings are you using in Vbox to accomplish your success?

---

### Post by maruchan on 2009-11-06
I get a slower framerate on Windows 7 and Vista, but in XP it's hardly noticeable. Either way, it doesn't really hurt the watching experience.

As for my settings: XP Pro / 1195MB RAM (2022 for Windows 7)/ 128MB video RAM, 3D accel enabled, AC97 audio, PCnet-FAST III(NAT) adapter.

I noticed that the machines listed in your sig may not be beefy enough. I'm doing this stuff on a Q8300 with 8GB RAM...but then again I'm also running an XP VM on a T7200 laptop with 2GB RAM and playback there is fine.

---

### Post by maruchan on 2009-11-06
[Oops, dupe]

---

### Post by jaqrah on 2009-11-06
Thanks Maruchan


As I suspected, you are offering up a fair amount of host ram to get your results.  I was going to max out my ram at 4gb on one of my desktops, so that would surely help.

---

### Post by SpikeBoycom on 2009-11-09
I've installed firefox for windows through wine and silverlight through wine hoping that would work, but when I go to the movie page it displayed an error message "We could not load the movie player. Please visit our help page for more details." It gives "ErrorCode: 1001" which is displayed as if the font required to display it isn't installed (you can't read it, but when you copy it that's the text that gets copied).

The link to more details suggests that this could be caused by a missing font, so I checked the C:\windows\Fonts directory (which was empty) so I copied the msttcorefont Arial to the c:\windows\Fonts directory:

```
cp /usr/share/fonts/truetype/msttcorefonts/Arial*.ttf ~/.wine/drive_c/windows/Fonts/
```Then I restarted firefox, navigated to the movie page and it started loading silverlight like it's supposed to (it had those dots that are in a circle) but then the whole app froze up (you could tell because the entire window dimmed and after a few minutes of doing nothing when I closed it ubuntu told me that it was not responding).

That's the closest I've gotten to getting netflix movie player to work without a full windows emulation. Hopefully moonlight will start to support silverlight 2.0 soon so we can just use moonlight and change the firefox useragent to trick netflix into thinking we're using firefox on windows so we can watch netflix movies without a full emulation.

---

### Post by snowpine on 2009-11-09
> **SpikeBoycom said:**
> That's the closest I've gotten to getting netflix movie player to work without a full windows emulation. Hopefully moonlight will start to support silverlight 2.0 soon so we can just use moonlight and change the firefox useragent to trick netflix into thinking we're using firefox on windows so we can watch netflix movies without a full emulation.

You are wasting your time (but hopefully having fun in the process :)). Netflix could support Linux tomorrow if they wanted to; they choose not to for business reasons. Netflix is one of the only reasons I keep Windows around (does anyone know if Netflix works with Mac?)

---

### Post by SpikeBoycom on 2009-11-09
Netflix claims to support mac (although I've never tried it)

---

### Post by chewbakker82 on 2009-11-09
It does work with Mac, my girlfriend has a mac laptop and that's what I've had to use to watch Netflix instant ever since my xbox got the Red Ring of Death for the second time. Until I get it back from Microsoft that's all I can use. I was hoping there was a way to watch it on Ubuntu but like someone stated before I'm sure it's a business desicion that netflix doesn't support linux.

---

### Post by RaygionsSumta on 2009-11-13
> **snowpine said:**
> You are wasting your time (but hopefully having fun in the process :)). Netflix could support Linux tomorrow if they wanted to; they choose not to for business reasons. Netflix is one of the only reasons I keep Windows around (does anyone know if Netflix works with Mac?)

I use Netflix on my MacbookPro running Snow Leopard.  Works great!

---

### Post by dy-namo on 2009-11-15
[SIZE=3][SIZE=2]Yea I can say that this is the one thing I miss about windows. Netflixs works flawlessly there. For now I can always stream on my laptop while chilling at my desk or boot up vista if I wanted to.  It'll be nice to use ubuntu for all my needs. ;)

Question? Is there a way to toggle between vista and ubuntu without rebooting ? I'm new at this, hadn't really researched yet.[/SIZE] 
[/SIZE]

---

### Post by maruchan on 2009-11-16
You can watch Netflix movies in Ubuntu, just use VirtualBox or another VM software package. See page 1 of this thread. Other than that, you will have to reboot to use both OS's.

---

