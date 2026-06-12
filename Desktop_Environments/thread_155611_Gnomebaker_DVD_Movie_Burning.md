---
title: "Gnomebaker DVD Movie Burning"
date: 2006-04-05
forum: Desktop Environments
---

### Post by dpack on 2006-04-05
When I used Windows this is what I would do to make a copy of a DVD movie.
1. Launch DVD Shrink.
2. Rip the whole DVD or just the movie to the hard drive.
3. Open Nero Express and tell it I am burning DVD Video Disc
4. Drop the files created by DVD Shrink in the list and burn the disc.

The DVD I burned would work in any DVD Player I put it in. Now that I am using Ubuntu this is what I have done.
1. Installed latest version of Wine.
2. Installed the DVD codecs needed from Restricted Formats
3. Installed DVD Shrink
4. Enabled DMA on all my optical drives, including my burners
5. I ripped just the movie to the hard drive. Every thing is working perfectly so far.
6. I open Gnomebaker and tell it I am burning a 4.7GB DVD.
7. I drop all the files created by DVD Shrink into the Data Disc tab.
8. I tell it to start creating the DVD and set it to finalize the disc and gave it a title
9. The DVD burns successfully with no errors.

I take the DVD and plop it in my DVD Player and it tell me there is a disc error. So I pop the DVD into the computer and after automatically mounting Ubuntu brings up a window showing all the files I just burned to the disc – even the disc title is right. If I double click on the VOB files it starts playing the movie. So I rebooted into Windows and my DVD playback software (WinDVD) does not recognize a disc.

Being that I had no errors during the creation process, what the hell happened that made it burn me a new coaster? I know someone else out here has done this successfully. What am I doing wrong?

---

### Post by PhoenixP3K on 2006-04-05
I discovered that issue myself... The DVD disc made under Unbuntu did not work on my DVD player and my Playstation 2. However when I put it in either Ubuntu or Windows it's automaticly detected as such and the default DVD player kicks in and plays the movie. I though it was a coding error of somesort and that the PC had the logical power of overcoming it but I took the VIDEO_TS folder and placed it on my Windows partition. Changed OS and burned the same project on Windows using Nero (DVD-Video option).

So it work flawlessly on my TV DVD player...

Why so much info? Just to relate to your experience :p
I'll be starting to look for a DVD Authoring or a way to specify the way baker makes the disc. **Help us please!**

---

### Post by dpack on 2006-04-05
Glad to know I'm not the only one with this issue. But if I have to burn the disc under Windows there is no point in doing the project under Ubuntu at all. Anyone out there successfully burned a DVD Movie using Gnomebaker and it work in DVD Players?

---

### Post by dpack on 2006-04-05
I found out what needs to be done to get DVD Video burning to work in Gnomebaker. I found the missing link here [http://dvd.chevelless230.com](http://dvd.chevelless230.com) but you only need to do one section of it. Here is a start to finish project for those trying to do what I did:

Rip the DVD with DVD Shrink
1. Start DVD Shrink and Open the movie disc
2. Choose whether you want to backup the entire disc or do a re-author
3. Once you have your files ready to rip click Backup
4. Make sure “Create VIDEO_TS and AUDIO_TS subfolders” is checked
5. Rip the DVD to a desired location
6. Close DVD Shrink

Create ISO image of ripped files
If this is the first time you've used this utility and you are not sure it is installed do the following:
1. System > Administration > Synaptec Package Manager
2. Search for **mkisofs** and verify it is installed. My system already had it installed and I can only guess it is from when I installed the DVD Playback codecs from the Restricted Formats wiki.
3. Open Terminal and type the following adjusting the paths for where you want the ISO file placed and the location of where the files you ripped are: **mkisofs -dvd-video -o Desktop/Downloads/movie.iso Desktop/Downloads/dvds**
4. In the above example the Video_TS and Audio_TS folders are under the dvds folder and the ISO file will be placed in the Downloads directory.
5. Once the ISO file has been created you need to verify the ISO file contents and make sure the VIDEO_TS.IFO has the lowest sector number of all files. (The number in brackets.)
6. In Terminal type: **isoinfo -i Desktop/Downloads/movie.iso -l**

Burn ISO file
1. Open Gnomebaker
2. Select the Burn DVD Image button
3. Browse to the ISO file and then start the burn

That's it! You'll now have a DVD Movie that can play in all players. I'm starting to not feel like so much of an Ubuntu noob anymore! LOL :D

---

### Post by PhoenixP3K on 2006-04-05
It seems quite simple and I'll be sure to give it a try on a DVD-RW :p

Now this makes use of mkisofs but why can't gnome baker let you choose the way you create the iso (because it does create one).

'Til that day I'll use the method you described.
Thanks a bunch. You ended up helping others in the end :D

Spirit of Ubuntu is great :p

---

### Post by Didjit on 2006-04-06
Just as a suggestion if you want to stay all native linux:
I use K9Copy [http://k9copy.sourceforge.net/](http://k9copy.sourceforge.net/) burn to ISO. Then use Gnomebaker's Burn DVD ISO option.

I have only done one DVD using this method and so far it worked pertty good.

Didjit

---

### Post by mgmiller on 2006-04-07
Just a quick thought, why not use dvd shrink to rip the movie directly to an iso?  It is a choice in the program.  Once you have an iso, all you need to do is right click it and tell it to write to disk and it will expand it and burn the disk.  Much simpler, unless I'm missing something here.

---

### Post by PhoenixP3K on 2006-04-07
[QUOTE=mgmiller]Just a quick thought, why not use dvd shrink to rip the movie directly to an iso?  It is a choice in the program.  Once you have an iso, all you need to do is right click it and tell it to write to disk and it will expand it and burn the disk.  Much simpler, unless I'm missing something here.[/QUOTE]
Yes, DVD Shrink doesn't make ISO files. It creates a standard DVD architecture files. Now Gnomebaker and Nautilus create an ISO out of those files and then burn it. Now the ripping is flawless as mentionned earlier since thoses files burned using Nero worked on any DVD player.

So the solution brought to our attention is to make an ISO that respects a stand-alone DVD players.

---

### Post by ironphil on 2006-04-07
As mentionned earlier in this tread, k9copy is the equivalent of DVDshrink on linux. If you have problems installing it on breezy, be patient, I recently tried Dapper Drake flight 6 and it is in the repositories, installable with a few clicks...

There is a program also called dvdshrink but it has nothing to do with the dvdshrink for windows, it is a linux software. It also has a gui called xdvdshrink. Info here: [http://dvdshrink.sourceforge.net/]("http://dvdshrink.sourceforge.net/")

---

### Post by dpack on 2006-04-07
I have been using DVD Shrink in Windows for so long I completely forgot it had an ISO feature. So I tried it tonight. I ripped a brand new movie in DVD shrink (Doom Unrated) and told it to create an ISO file. I then burned that ISO file using Gnomebaker onto a DVD-RW. I put the DVD into my stand alone DVD player and "Ta Da!" I was watching Doom! Great! So here are the new instructions:

Rip the DVD with DVD Shrink
1. Start DVD Shrink and Open the movie disc
2. Choose whether you want to backup the entire disc or do a re-author
3. Once you have your files ready to rip click Backup
4. Set "Select Backup Target" to "ISO Image File"
5. Rip the DVD to a desired location
6. Close DVD Shrink

Burn ISO file
1. Open Gnomebaker
2. Select the Burn DVD Image button
3. Browse to the ISO file and then start the burn

Since my player played the movie on a DVD-RW I know it will work for a DVD-R like I usually use. Thanks for reminding me mgmiller!

---

### Post by matthinckley on 2006-04-10
I use DVD Shrink to create video_ts files and I noticed the same problem with GnomeBaker.. 

I use K3B and have no issues at all

---

### Post by discord on 2006-04-15
what kind of read times are you getting when using dvdshrink? I'm getting like 2,983 KB/s read times when ripping with DVD shrink. Is there a native linux program I can rip to iso with first to speed up the process? What kinda speeds are you guys getting?

---

### Post by dpack on 2006-04-16
I don't think if you changed to different software it would speed up the process. I could be wrong though, but I think your transfer rate is all dependent upon how fast your PC's hardware is and how it is setup. When I rip a DVD with DVD Shrink my rate starts out at 2800 KB/s. The rate slowly increases as it is ripping the DVD and continues to increase until it is finished. By the end of the rip the rate has increased on mine to 8200 KB/s. I ripped a whole DVD this morning in 8 minutes 52 seconds. But I am thinking my hardware setup plays a factor in this.

I have dual Ultra320 SCSI hard drives at 10K rpm. When I rip a DVD I write the ISO file to my second hard drive that is not running an OS. It is sitting there doing nothing but the ISO write process. Plus, the DVD-ROM I am ripping from is the only device on IDE channel 1 on the mobo so it has all the bandwidth. In DVD Shrink I also have the check box for the Preview unchecked.

I believe DVD Rip is a native Linux program and you can try it, but again I think it all boils down to the limitations of the hardware in your PC.

---

### Post by discord on 2006-04-19
in the mr.bass guide [http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/) I beleive he mentions using the DVDdecryptor program to rip the data to his hard drive before using dvd shrink. He mentions tha DVDdecryptor is able to use DMA while dvdshrink is not. DVDdecryptor is a windows program though. I wanna use something to get the DVD on the drive faster and then shrink using DVDshrink. I think this would be much faster.

---

### Post by an10ae on 2006-05-30
discord:

1.)vobcopy (it's in the repos) Will decrypt and copy the entire contents over to your drive. It's Fast!

2.)note::(if you are using dual-layer drive and disks 8.4Gb you can move directly to step 3)
Then Use dvdshrink under wine or possibly (haven't tried it yet but excited to try it)k9copy to compress the video to fit on 4.7 Gb disk.

3.)Then use K3B Video DVD option.

---

