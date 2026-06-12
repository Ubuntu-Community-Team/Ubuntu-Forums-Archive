---
title: "no sound on Packard bell laptop"
date: 2006-02-26
forum: Desktop Environments
---

### Post by jmpmjmpm on 2006-02-26
Hello Guru's,

I have a small problem after installing ubuntuon my packard bell easynote.

The packard bel support page with all the details for my laptop is here

[http://support.packardbell.com/uk/mypc/?PibItemNr=PB30S00001#show](http://support.packardbell.com/uk/mypc/?PibItemNr=PB30S00001#show)

I've cheched in device manager and is shows my sound "card" as detected and seems to have drivers loaded for everything. Also everything looks fine in sound manager.

I have to say tha Ubuntu has done a great job of detecting almost everything out of the box. My in-built wifi was configured easily and even the function buttons (volume, brightness, sleep, etc) work.

Just no sound...

Also if someone would like to point me in the direction to a good howto on setting up those non-free software thingy's like mp3, dvd, type stuff that would be great.

and is there an altenative to frontpage for ubuntu? I have a website that has been built using fp2003 that I would like to maintain under linux.

Has anyone figured out a way to get the 5th gen Ipod to work with linux yet? 

thanks for all your time guys!

---

### Post by jmpmjmpm on 2006-02-26
this is what dmidecode says, both disabled? is this the root of the sound problem?


Handle 0x000D, DMI type 10, 6 bytes.
On Board Device Information
        Type: Video
        Status: Disabled
        Description: ATI M10

Handle 0x000E, DMI type 10, 6 bytes.
On Board Device Information
        Type: Sound
        Status: Disabled
        Description: AC97 Audio

---

### Post by cdsboy on 2006-02-26
well is your video working fine? like full res and stuff? because if it is then thats not the problem because you video card says its disabled too lol. oh and with the frontpage thing there is a program called Crossover office. it runs ms office 2003 suite almost flawlessly. there is a fee but i am pretty sure it is less and $30. that program can get all your ms office programs up and running.

---

### Post by akniss on 2006-02-26
[QUOTE=jmpmjmpm]
and is there an altenative to frontpage for ubuntu? I have a website that has been built using fp2003 that I would like to maintain under linux.
[/QUOTE]


you might take a look at Nvu. 
[http://www.nvu.com/](http://www.nvu.com/)
Its not quite as feature-rich as frontpage, but at least it uses correct standards.  I use it for my webpages, but i don't do anything too fancy.

---

### Post by jmpmjmpm on 2006-02-26
thanks for the advice guys, very useful.

Actually, the video card doesn't seem to be working properly, I can only get 1024x768 when the native re for this screen is 1280x768 (i think) it's one of these widescreen types. Also everything looks too smooth, to the point of almost looking a bit blurry.

I am trying to make sense of another thread that mentions a potential problem with the intel 915GM chipset that is in these centrino notebooks. It's about time manufacturers srarted addressing cross-platform compatibility isntead of using the "designed for windows" get out.

I am using the flight 4 dapper drake version but I had more issues (including the above) with hoary which led to me returning to window until dapper seemed to be stable enough for me to try. So I don't think dapper is the problem here.

Does anyone know how to address the ipod thing? because it's only that and World of warcraft that stops me dumping the windows partition totally.

Cheers

---

### Post by jam'ez on 2006-03-09
Well i have the the same laptop. i have the sound problem too, trying hard to configure it or find a way to! 
For your graphics go into synaptic and search for 915resolution and download the 915resolution. 
Follow the readme file, its pritty easy. its in  /usr/share/doc/915resolution/README.Debian when you have it installed!
I have the full res and everything, looks much better. the only thing i did different was when you are configuring it i went for the closed res it has which was 1280x1024. i just didnt put 1024 i put the correct 768. it work great. just got to sort my sound problem. if it dont work im going to get a USB or PCMCIA sound card.

Good luck :D 

James

---

### Post by jam'ez on 2006-03-15
still no news on the sound front. annoying! works on most laptops with Intel ICH6 card!!!
Did u try the video installation i said last?

---

### Post by pompeyjohn on 2006-05-07
hi guys I have the same machine :D , and the same problems :sad: 

I couldnt find the 915resolution package in synaptic - do you know if it has been renamed?

---

### Post by jmpmjmpm on 2006-05-12
Hi, just an update to say as of now there is still no solution to this here, I have posted multiple threads across multiple forums, but nothing. The red light cmes on in the headphone jack and I can make the sound "click" by fiddeling with volumes but no actual sounds. This realllly does make me think this is a codec issue with the connexant sound (connexant id31) codec. Those that have got this working seem to have a realtek chip and so possibly a diffferent codec

---

### Post by dsokus on 2006-05-12
Hey, I also have a Packard Bell Easynote and I had the same problem when I first started... At first I thought it was just Ubuntu but then I started up in Windoze and that did it too, I was like... hmm! As far as I can recall, there was a setting in the BIOS which centrally muted the entire thing - for me it works beautifully since then. But then I have an Easynote A and it might not work the same way for you guys. I can't get around my resolution either though, so we're in the same boat there. :p

---

### Post by dsokus on 2006-05-12
Hey, I also have a Packard Bell Easynote and I had the same problem when I first started... At first I thought it was just Ubuntu but then I started up in Windoze and that did it too, I was like... hmm! As far as I can recall, there was a setting in the BIOS which centrally muted the entire thing - for me it works beautifully since then. But then I have an Easynote A and it might not work the same way for you guys. I can't get around my resolution either though, so we're in the same boat there. :p

---

### Post by jmpmjmpm on 2006-05-16
The sound works fine in windows, always has. I'm convinced that my chip uses a "strange" codec that isn't supported and alsa doesn't seem to want to support it. Probably because it's fairly rare, which makes it no better than than the hardware vendors that doesn't support linux for the same reason.

Or

There is a major conflict between the modem and sound card and linux is thinking the modem is the sound card.

What model is your easynote?

Mine is A8202

---

### Post by bluenova on 2006-05-16
Packard Bell + Linux = Head ache

They use custom hardware, even it windows you have to use Packard Bell drivers to get it to work. May advice = stay clear.

---

### Post by cwalte on 2006-07-12
I got 915resolution to work after rebooting, it's made a great difference as my laptop (EasyNote A series). No sound and no idea how it's going to get resolved. Guess I'll have to get a PCcard, which will be better than the poor internal one.

Chris

---

### Post by pompeyjohn on 2006-07-30
I have the same machine guys (an A series, 8 i think)

I have got the widescreen working lovely - using 915resolution, drop me a line if you need a hand with that.

still not working yet,...

wireless, card reader and ... sound.

I have tried all the tips on here about muting channels, etc.. and the best I can get is a popping sound.

Such a shame!

Anyone have an update with happy news?

---

### Post by cwalte on 2006-08-04
I managed to get wireles working with help from this post, it took a bit of time but it worked. Made my Saturday morning (that does sound sad, doesn't it?). 

No joy on the sound, might have to give up and get that Creative PC soundcard, £99,though...

C

[http://www.ubuntuforums.org/showthread.php?p=703020#post703020]("http://www.ubuntuforums.org/showthread.php?p=703020#post703020")

---

### Post by pompeyjohn on 2006-08-23
I still have no sound...... anyone know if this works in Edgy? or other Linux distro's?

It would be a shame to leave Ubuntu....

---

### Post by michellez on 2006-09-17
Packard Bell A8 550 here, same problem. Got graphics and wifi ok, but the same popping/no sound problem.

There is some kind of conflict going off here. Can anyone make more sense than I can of the following errors I found in dmesg?

> PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
PCI quirk: region 1180-11bf claimed by ICH6 GPIO


> PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0


ls pci shows 1c as:
> 0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)

cat /proc/asound/cards shows:
>  0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with unknown codec at 0xb0040800, irq 169


Surely that should show ac97?

lsmod|grep snd shows:
> snd_intel8x0           34076  5
snd_ac97_codec         96804  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec


Cheers guys! :cool:

---

### Post by pompeyjohn on 2006-10-02
somebody... anybody... please!!

who knows... perhaps this will work in edgy!! :D

---

### Post by pompeyjohn on 2006-10-06
ok, well it doesnt work in edgy either.

That looks like it for me and ubuntu then.

I am very saddened by this, to those of you who know me I love the idea of free software. I am absolutely gutted right now.

Oh well, maybe in six months or a year it'll be sorted. I have done all I can, and it looks like everyone else has as well.

Check out the bottom for [the sound of a nail being smacked into a coffin]("http://www.linuxreality.com/forums/index.php?PHPSESSID=ccd827efa603194fb9cabf6c28d28568&topic=137.msg740").

---

### Post by jmpmjmpm on 2007-01-05
just an update, I was fortunate enough to have this notebook refunded back in august '06, bought an acer with the money and edgy is sweet. Alsa is still working on this issue with some success in recent days tho so keep your fingers crossed for sound after your next distro upgrade. 

The alsa bug page for this issue is here [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1134](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1134)

---

### Post by cwalte on 2007-01-08
Just found 
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1134](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=1134) and 
[http://www.howforge.com/benq-joybook-s52-built-in-sound-card-partially-work-with-alsa](http://www.howforge.com/benq-joybook-s52-built-in-sound-card-partially-work-with-alsa)

Will try them tonight...

C

---

### Post by pompeyjohn on 2007-01-08
thank you very much jmpmjmpm (and well done on the cross posting, hopefully all interested in this will be kept informed. 

I am glad to hear you have sound working now.

I am sure the ALSA folks are doing all they can. I tried to put some pressure on PB to release info, but who knows what is happening......

Fingers crossed for the next release :)

---

### Post by cwalte on 2007-04-24
It  works! Follow the steps here
[http://ubuntuforums.org/showthread.php?p=2526861#post2526861](http://ubuntuforums.org/showthread.php?p=2526861#post2526861)
and get sound on your easynote!!!

---

### Post by michellez on 2008-02-09
Got the Ubuntu 7.10 out the other night.. all worked straight off with no messing. Sound and Wifi with WPA. Now installed and happily running Ubuntu Linux :-D

---

