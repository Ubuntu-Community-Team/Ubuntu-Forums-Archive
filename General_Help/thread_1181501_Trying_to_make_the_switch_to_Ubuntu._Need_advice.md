---
title: "Trying to make the switch to Ubuntu. Need advice"
date: 2009-06-08
forum: General Help
---

### Post by krstofer on 2009-06-08
Hey Guys,

I am new to linux and recently installed ubuntu on an old desktop just for fun. Then I installed it on my laptop (secondary PC). I really like it. I want to use more of it. Now I want to install it on my primary PC to be a windows free home. However, there are certain things I use my PC for that I absolutley need. The main thing is a media server.

I currently use tversity on my windows PC, This lets me have access to my multimedia, anywhere. I stream to my xbox, dvd player, G1, and my work PC. I have tried many software packages so far (gstreamer, boxee, xmbc, and a few others) but I have yet to even make a connection to my xbox.

Second, I need adobe premiere level video editing software for home movies and work videos.

Third, MP3 ripping and editing software (I'm sure I can find this).

Last, I need to find out how to remote desktop into my home PC. I currently use windows remote desktop.

I just need to know that I will be able to do all these things with my ubuntu desktop. If I know I can get what I need, then I will be able to convert my primary desktop and my wife's laptop to become a windows free home.

FYI, this was all brought about by a recent virus I got on my windows machine.

Thanks
Krs.

---

### Post by steveneddy on 2009-06-08
Everything but the video editing can be found by searching these forums or Google.

I would search each item individually, get that working, then move on.

I am not sure if you can run Adobe video editing software effectively in WINE.

There is Avidemux, but I'm not sure how that compares to Adobe's product.

---

### Post by pastalavista on 2009-06-08
You could, with some work, do all that on Ubuntu.. and only you can decide if all the work is worth it. To get a big jump on the work, it mught be best if you started with [Mythbuntu]("http://www.mythbuntu.org/").

---

### Post by roharme on 2009-06-08
One big thing that is stopping me from switching to linux completely is Gaming

---

### Post by logos34 on 2009-06-08
adobe premiere (6.0) on wine = a big [maybe]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=128")

---

### Post by roharme on 2009-06-08
Adobe Premier in Wine

Kidding or what!!!

Even Counter Strike Source wont run properly in my 2GB System

:(:(

---

### Post by logos34 on 2009-06-08
> **roharme said:**
> Adobe Premier in Wine

Kidding or what!!!

Even Counter Strike Source wont run properly in my 2GB System

:(:(

I said big maybe -- read the link.  4 testers

---

### Post by bear24rw on 2009-06-08
I think uShare can stream to xbox (i think it's called ushare, can someone confirm?)

---

### Post by krstofer on 2009-06-08
I was just reading about mythbuntu. I didn't know there was so many flavors of  ubuntu. Will I be able to stream to my xbox360 with that?

Regarding adobe premiere, id doesn't have to be that software, but something of it's caliber would work.

BTW, I thought of another thing, ripping DVD's and converting to divx. Can that be done? I saw that divx didn't even have software for linux.

---

### Post by Legace on 2009-06-08
> **krstofer said:**
> BTW, I thought of another thing, ripping DVD's and converting to divx. Can that be done? I saw that divx didn't even have software for linux.

Yes, it can be done :)
[https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs)

---

### Post by rizman on 2009-06-08
To stream to the XBOX, you can either use uShare or Fuppes. I tried both.

uShare is pretty easy to setup and it is in the Ubuntu repos. However, I couldn't get it to display folders on the Xbox. I had 1000's of MP3's in one big list.

Fuppes is harder to setup. You need to compile from source etc... But, is displays your media in a folder like structure.

Both work fine with DivX/Xvid movies. I can even stream 720p mp4 files, although at some moment it will start to stop playing and buffering before continuing. But I'd guess that's because my media is stored on an NAS which is connected wirelessly to my Laptop, which stream wirelessy to the 360.

If you have an Xbox (not an Xbox 360) you could also try MediaTomb. Apparently it works pretty good. It does not yet support the 360.

---

### Post by krstofer on 2009-06-08
Yipes!! I couldn't possibly use uShare, I ripped almost all my CD's. Looks like Fuppes it is.
 
I tried media tomb, but couldn't figure out why I couldn't get it to show on my xbox360. It seems that a lot of the media server software are for pc's connected directly through televisions.
 
I just saw something about malware in ubuntu. Are viruses and malware as prominent on ubuntu as windows? I'm a pretty good windows user and can usually spot a virus pretty quickly. I'm afraid I wouldn't be able to spot a virus in ubuntu being I don't really know te ins and outs of the software.

---

### Post by krstofer on 2009-06-09
Ok, I downloaded fuppes. Now this is probably one of the most newb questions asked but, How do I install something outside of synaptics?

---

### Post by krstofer on 2009-06-11
Is that too newb of a question?

---

### Post by Troublegum on 2009-06-15
Did you try the installation instructions on the website?



[LIST]
[*]download fuppes and extract it to
[*]go to that folder and run:
```

./configure
make
sudo checkinstall

```
[/LIST]

make sure to install checkinstall before you do that. checkinstall creates a .deb package so you can uninstall the software via synaptic later.

---

### Post by Bigtime_Scrub on 2009-06-15
> **krstofer said:**
> Hey Guys,

I am new to linux and recently installed ubuntu on an old desktop just for fun. Then I installed it on my laptop (secondary PC). I really like it. I want to use more of it. Now I want to install it on my primary PC to be a windows free home. However, there are certain things I use my PC for that I absolutley need. The main thing is a media server.

I currently use tversity on my windows PC, This lets me have access to my multimedia, anywhere. I stream to my xbox, dvd player, G1, and my work PC. I have tried many software packages so far (gstreamer, boxee, xmbc, and a few others) but I have yet to even make a connection to my xbox.

Second, I need adobe premiere level video editing software for home movies and work videos.

Third, MP3 ripping and editing software (I'm sure I can find this).

Last, I need to find out how to remote desktop into my home PC. I currently use windows remote desktop.

I just need to know that I will be able to do all these things with my ubuntu desktop. If I know I can get what I need, then I will be able to convert my primary desktop and my wife's laptop to become a windows free home.

FYI, this was all brought about by a recent virus I got on my windows machine.

Thanks
Krs.

1st of all welcome to linux. You can stream to your xbox. In fact you can do everything you want as long as you are willing to put in the work and be open minded in the way linux works. 

For the xbox, [http://ubuntuforums.org/showthread.php?t=794489]("http://ubuntuforums.org/showthread.php?t=794489") click this to get started.

For editing home videos, you can try Avidemux, k9copy, and DeVeDe. I use all three as they are each good at different things. They are available in ubuntu repositories and you can install them with Synaptic Package manager or with the command line from terminal. Know this however, no one program in Linux can replace everything a do-all Windows program does, you can however, get multiple programs together to get the same functionality. Linux in general leans towards a one-program one-task sort of approach. So if a program doesn't give you everything you need find a task specific program that fills in the gaps.

I suggest grip and audacity for your mp3/cd needs. (also in repositories)


I don't use Ubuntu, but I believe it has remote desktop already installed.:popcorn:

Good luck.

---

### Post by bobnutfield on 2009-06-15
If you need SERIOUS video editing in Linux, there is really only one choice at this time:

[http://cv.cinelerra.org/]("http://cv.cinelerra.org/")

I have used Adobe Premier Pro and Cinelerra extensively in the past.  Cinelerra can be very frustrating because it is not as intuitive as APPro.  But, it is very powerful.

---

### Post by krstofer on 2009-06-15
> **Troublegum said:**
> Did you try the installation instructions on the website?



[LIST]
[*]download fuppes and extract it to
[*]go to that folder and run:
```

./configure
make
sudo checkinstall

```
[/LIST]

make sure to install checkinstall before you do that. checkinstall creates a .deb package so you can uninstall the software via synaptic later.


Yeah, I followed the instructions, but I got an error that something was missing. I couldn't find any answers. So I decided to install WINE and install play-on and tversity. It totally screwed up my system and I had to reinstall ubuntu on saturday. I decided to install mythTV and it streams to my xbox. Now I have to find out how  to get all my other internet feeds (HULU, Youtube, Netflix, ETC) to my xbox.

---

### Post by krstofer on 2009-06-15
Thanks for the welcome Scrub. I am totally open minded about Linux. I know it's going to be hard to learn, but I printed out the getting started guide, and got some general linux books. I also have a DEC OSF/1 Command and SHell users guide that I got in college when I first wanted to learn about UNIX and it's commands.

One of my biggest problems is installing apps not knowing if they have a gui front end or not. I installed open-vm-tools and thought it was a gui interface, but I don't know where it is or where the documentation is.

So far, my biggest gripe is the right-click drag. That is the way I move files in windows, and I can't do it in Linux. I need to find an easy way to move (not copy) other than cut and paste.

---

