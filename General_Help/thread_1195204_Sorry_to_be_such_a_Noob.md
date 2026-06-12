---
title: "Sorry to be such a Noob"
date: 2009-06-23
forum: General Help
---

### Post by InkedScales on 2009-06-23
right a few questions, dont know where to put all the different ones in different parts of the forum so this should be a good  place to start, sorry for the flurry of questions and as the title dictates, being a noob.

Ok I have recently rebuilt my PC after stealing bits of my mums old one to get extra hard drive space etc.

I have it all partitioned up, now Ive been reading this thing about ubuntu and how to use it as a beginner theres just a few things I have to ask, 

1. is it worth having windows on aswell?

2. can I access files on hardrives formatted for windows?

3. I know it said that u dont use .exe files. does that mean you dont tend to? or that you actively cant? cos if you cant what if the program you want isnt available in any other format?

4. I use mediaplayerclassic as I prefer it as a media player and use it for all my MKV files

5. do those sort of files work the sane ubuntu?

6.I have all my files like that on an external hard drive, even if it was used with my pc on windows will I be able to get the files off and use them on ubuntu?

7. I could install vista on my smaller hardrive as it predates vista and isnt compatible so I had to install it on the larger and use the smaller as extra hardrive space... will this be an issue putting ubuntu on it?

thats all I can remeber for now, any help at all will be appreciated, thanks

---

### Post by SuperSonic4 on 2009-06-23
1. Depends what you use windows for. Tell us what you do in windows and we'll get back to you

2. Yes, Ubuntu (and GNU/Linux) can read ntfs without a problem

3. Wine works with some exe files but it's nowhere near guaranteed. Crossover is paid software but there is better compability. If the program is in no other format then it's best to look for a similar program in the Synaptic package manager or compile from source. As a last resort try wine.

4. Fair enough. I prefer VLC. I can't remember what WMP classic looks like but someone else might

5. Yes, drag and drop into a compatible player and they should work. You will need to install codecs first from the medibuntu site

6. Yes (see point 2)

7. If you repartition any partition then you'll lose the data that was on that partition, whether it was data or OS, windows or linux. If you put it on a blank partition then all should be good

---

### Post by Celauran on 2009-06-23
1. In the beginning, it probably isn't a bad idea.

2. Yes

3. .exe files are Windows executables. If there is something you need that does not have a suitable Linux version, you can run these through Wine. You should find most of what you need natively.

4. Umm... and?

5. You can play .mkv files in Linux

6. Yes, that will work (see 2)

7. It shouldn't be a problem unless you're talking about a very small drive. Windows does sometimes complain if it's not installed on the first physical drive, or so I've heard.

---

### Post by Idefix82 on 2009-06-23
Hello and welcome!
> **InkedScales said:**
> 
1. is it worth having windows on aswell?

It depends on what you want to do with the computer. If you are a heavy gamer then yes. If not then personally, I can't think of anything you would want to do with Windows once you know your way round Ubuntu. One thing though: before you actually install Ubuntu, test it by booting form the CD and see if all your hardware is recognised. If it's not, come back here and we'll help you sort it out. Once you know that you will get a fully functioning OS when you install, go ahead and don't worry about not having Windows.

> **InkedScales said:**
> 
2. can I access files on hardrives formatted for windows?

Yes, no problem with that.

> **InkedScales said:**
> 3. I know it said that u dont use .exe files. does that mean you dont tend to? or that you actively cant? cos if you cant what if the program you want isnt available in any other format?

Linux just doesn't know what to do with .exe files. There are native Linux programs for almost anything you would ever want to do with your computer. If you desperately need to use a program, sometimes a Windows emulator will help. The main department where this will be a problem is games.

> **InkedScales said:**
> 4. I use mediaplayerclassic as I prefer it as a media player and use it for all my MKV files

5. do those sort of files work the sane ubuntu?


There are plenty of very good media players for Ubuntu and many of them will play mkv files. In fact, it being an open source format, it is likely to be much better supported under Linux than under Windows.

> **InkedScales said:**
> 6.I have all my files like that on an external hard drive, even if it was used with my pc on windows will I be able to get the files off and use them on ubuntu?

Yes, you can just plug it in and work away.

> **InkedScales said:**
> 7. I could install vista on my smaller hardrive as it predates vista and isnt compatible so I had to install it on the larger and use the smaller as extra hardrive space... will this be an issue putting ubuntu on it?


You can resize the Vista partition from within Vista and the install Ubuntu into the free space. That should be no problem.

---

### Post by nmaster on 2009-06-23
> **InkedScales said:**
> right a few questions, dont know where to put all the different ones in different parts of the forum so this should be a good  place to start, sorry for the flurry of questions and as the title dictates, being a noob.

Ok I have recently rebuilt my PC after stealing bits of my mums old one to get extra hard drive space etc.

I have it all partitioned up, now Ive been reading this thing about ubuntu and how to use it as a beginner theres just a few things I have to ask, 

1. is it worth having windows on aswell?

2. can I access files on hardrives formatted for windows?

3. I know it said that u dont use .exe files. does that mean you dont tend to? or that you actively cant? cos if you cant what if the program you want isnt available in any other format?

4. I use mediaplayerclassic as I prefer it as a media player and use it for all my MKV files

5. do those sort of files work the sane ubuntu?

6.I have all my files like that on an external hard drive, even if it was used with my pc on windows will I be able to get the files off and use them on ubuntu?

7. I could install vista on my smaller hardrive as it predates vista and isnt compatible so I had to install it on the larger and use the smaller as extra hardrive space... will this be an issue putting ubuntu on it?

thats all I can remeber for now, any help at all will be appreciated, thanks



1. It depends on what you need Windows for.  Some people dual-boot with windows so that they can use games, tax software, or just to have a different option.  I'm currently dual-booting with Wubi, because while not new to unix, I am new to ubuntu.  I would highly suggest using wubi for a while until you feel comfortable with ubuntu.
[http://wubi-installer.org/](http://wubi-installer.org/)

2. Ubuntu can be used with NTFS and FAT (I'm fairly certain), but from my understanding its better to use ext3 (or maybe ext4).  There's a lot of reading you can do about ext3 vs. ext4, but I would suggest using ext3 since its more stable.  However, ext4 is standard for Fedora 11, so it is an option.

3.If you need to run a Windows application, you have some options. You could choose to dual-boot.  You could use an emulator like Wine.  Wine sounds good to me but many applications aren't supported.  I use a virtual machine (VirtualBox) on wubi even though I'm dual-booting.  I plan on removing windows soon and I really like the virutal machine.  If you want a few links showing how to do this easily I have a few really good guides.  *.deb is the Ubuntu equivalent to *.exe. Its much easier, however, to use the repositories (apt-get, aptitude, Synaptic, Add/Remove ...)

4&5.  Software is different on Ubuntu, but I'm sure that you can find something in the repositories that can do the job you want.  VLC, for example, should do what you want.

6. You shouldn't have a problem.

7. Could you explain that a little more?  I'm not sure exactly what you mean.

DON'T BE SORRY! There are a lot of noobs here and to a significant extend that includes me :)  Read the forums. Read psychocats.net.  There's a lot of information out there and it can sometimes be like trying to drink from a firehose, but be persistent.  You'll learn a lot about Linux and computers in general by using Ubuntu.

---

### Post by InkedScales on 2009-06-23
> **neal.m.master said:**
> 1. It depends on what you need Windows for.  Some people dual-boot with windows so that they can use games, tax software, or just to have a different option.  I'm currently dual-booting with Wubi, because while not new to unix, I am new to ubuntu.  I would highly suggest using wubi for a while until you feel comfortable with ubuntu.
[http://wubi-installer.org/](http://wubi-installer.org/)

2. Ubuntu can be used with NTFS and FAT (I'm fairly certain), but from my understanding its better to use ext3 (or maybe ext4).  There's a lot of reading you can do about ext3 vs. ext4, but I would suggest using ext3 since its more stable.  However, ext4 is standard for Fedora 11, so it is an option.

3.If you need to run a Windows application, you have some options. You could choose to dual-boot.  You could use an emulator like Wine.  Wine sounds good to me but many applications aren't supported.  I use a virtual machine (VirtualBox) on wubi even though I'm dual-booting.  I plan on removing windows soon and I really like the virutal machine.  If you want a few links showing how to do this easily I have a few really good guides.  *.deb is the Ubuntu equivalent to *.exe. Its much easier, however, to use the repositories (apt-get, aptitude, Synaptic, Add/Remove ...)

4&5.  Software is different on Ubuntu, but I'm sure that you can find something in the repositories that can do the job you want.  VLC, for example, should do what you want.

6. You shouldn't have a problem.

7. Could you explain that a little more?  I'm not sure exactly what you mean.

DON'T BE SORRY! There are a lot of noobs here and to a significant extend that includes me :)  Read the forums. Read psychocats.net.  There's a lot of information out there and it can sometimes be like trying to drink from a firehose, but be persistent.  You'll learn a lot about Linux and computers in general by using Ubuntu.

sorry I meant that because the hardrive that predates vista wouldnt let me install vista on it, will it not let me install ubuntu on it as it may predate the version???

---

### Post by InkedScales on 2009-06-23
was only saying aboutb the media player as I know it plays the files I use and was asking if u could use it on ubuntu but some people have answer the question (thank you)

I used to game but now i dont am selling WoW, all I would be doing really is stuff like photoshop, can I get that? oh and can I use utorrent and stuff??? also can I get microsoft offfice or macromedia suite etc?

I would probably get rid of windows

ive got an x-fi soundblaster sound card and an asus something or other graphics card, i can try find ther full names if needs be lol

---

### Post by InkedScales on 2009-06-23
oh and can you use opera instead of internet exploer and firefox etc?

---

### Post by Subban on 2009-06-23
> **InkedScales said:**
> I used to game but now i dont am selling WoW

WoW works great in wine or Cedega (I play it far to much in Cedega myself)

> all I would be doing really is stuff like photoshop

The Gimp is Linux's Photoshop, it can do most things Photoshop can, but depending on how fully you used Photoshop will depend on how well you get on with The Gimp I think, I used to use Photoshop for freelance work, leaflets, logo's, web designs, banners, magazine advertisments even and I have found it harder to work in the Gimp but still very very managable.

> oh and can I use utorrent and stuff???

uTorrent I believe will work in wine also, but there are many torrent applications native to Linux, Azureus or my preference is Transmission, I am certain you will find one to replace uTorrent rather than run it in wine, but at least you will have that option if necessary

> also can I get microsoft office

Unless you have a particular reason for using MS Office, then Open Office is just as capable and most likely for more suitable. If there was a very particular reason for using MS Office then Codeweavers CrossOver is probably the best choice to run MS Office in, but I find it unlikely that Open Office wouldn't be suitable, I have yet to personally find anyone who *must* have MS Office. 

> I would probably get rid of windows
I would, but it might be prudent to keep your Windows partition for now in case of teething troubles. Lets say you get a problem that nukes your Ubuntu install, you will be able to just boot to Windows and readily download fixes/help. At a later date you can wipe Windows if you feel like it and use that space for filling with the above mentioned torrents (linux ISO's ofc)

---

### Post by Subban on 2009-06-23
> **InkedScales said:**
> oh and can you use opera instead of internet exploer and firefox etc?

Yes, Opera for Linux is available to run natively, and free I believe rather than having to pay for it like on Windows ;)

---

### Post by ikacer on 2009-06-23
photoshop, microsoft office, and utorrent don't run natively in Ubuntu. There are, however, good open source programs that do the same thing. GIMP is an excellent photoshop-like program, and OpenOffice does just about everything microsoft office does. As for utorrent, I think it runs fine in WINE, but I'm not sure. There are also a lot of excellent bittorrent clients that run natively in Linux, you might want to look at ktorrent, deluge, transmission, and my personal favorite, rtorrent. There are a number of excellent media players for linux as well. I recommend SMplayer, which I honestly prefer to MPC.

I think you'll find that there are excellent programs for just about anything you want to do in Linux. What's more, they are all free, and very easy to install using Synaptic package manager.

---

### Post by nmaster on 2009-06-23
> **InkedScales said:**
> sorry I meant that because the hardrive that predates vista wouldnt let me install vista on it, will it not let me install ubuntu on it as it may predate the version???


I'm not exactly sure what you mean by "predate" or it will "not let me."  I'm sorry, but why don't you put the LiveCD in and see what happens.  You can use the LiveCD to check what space is available for installation.

---

### Post by InkedScales on 2009-06-23
> **Subban said:**
> Yes, Opera for Linux is available to run natively, and free I believe rather than having to pay for it like on Windows ;)
:O pay?? :o I never paid for opera lol

but thanks

---

### Post by InkedScales on 2009-06-23
> **ikacer said:**
> As for utorrent, I think it runs fine in WINE, but I'm not sure. There are also a lot of excellent bittorrent clients that run natively in Linux, you might want to look at ktorrent, deluge, transmission, and my personal favorite, rtorrent. There are a number of excellent media players for linux as well. I recommend SMplayer, which I honestly prefer to MPC.

thanks Ill have to look into these as I use HDbits and they only allow membership for people with certain bittorrent clients so Ill have to see, thanks alot btw to everyone,all of this has been a great help, thanks

---

