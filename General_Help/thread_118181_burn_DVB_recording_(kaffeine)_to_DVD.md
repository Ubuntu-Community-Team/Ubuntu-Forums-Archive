---
title: "burn DVB recording (kaffeine) to DVD"
date: 2006-01-16
forum: General Help
---

### Post by RikoW on 2006-01-16
Hi everybody,

I have a Cinergy T2 DVB-T TV card which runs great using for example *xine* or *kaffeine*. I use *kaffeine* to record programs of the TV card to my hard disc. Of course, ultimitely I would like to burn them on DVD to watch on the regular TV screen.

However, so far I was not successful to do so.

*Kaffeine* provides 3 output formats for the TV stream: TS, mpeg_PS, mpeg_PES. As far as I understood now, TS stands for "transmission stream" which has insufficient information stored for DVD recording. Instead you need the "programm stream" format, which I assume is one of the above. 

However, no matter how I record the TV program, when using a *dvdauthor* frontend like *tovid* or *qdvdauthor*, I always get the same sort of warning/error and no iso image is created:

```
WARN: System header found, but PCI/DSI information is not where expected
	(make sure your system header is 18 bytes!)
WARN: Skipping sector, waiting for first VOBU...
[ ...repeat millions of time .... ]
WARN: Skipping sector, waiting for first VOBU...
**** dvdauthor : PROCESSUS 2 ****
DVDAuthor::dvdauthor, version 0.6.11.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>
**** mkisofs : PROCESSING ****
INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.
mkisofs: No such file or directory. Faild to open /data/DVB/dvd//VIDEO_TS/VIDEO_TS.IFO
mkisofs: Can't open VMG info for '/data/DVB/dvd/'.

```

I also read about re-multiplexing the mpeg files, but also that did not result in any iso image for the DVD.

I would be very grateful, if anybody has any hint on how to do that properly.

Thanks and cheers,

         Riko

---

### Post by comar961 on 2007-10-03
Actually it is quiet easy:

This method has been tested on (K)Ubuntu Feisty with DVB-T in Austria.
You will need:
1) Kaffeine and DVB working (there are separate howtos for getting DVB to work)
2) Avidemux - install from normal repositories (needs universe and multiverse - there are also howtos for this)
3) Mandvd - you can get it here: [http://www.getdeb.net/app.php?name=ManDVD]("http://www.getdeb.net/app.php?name=ManDVD")
4) Free space on your harddrive
5) A mouse, because all the programs used are just easy click click!
 
Let's get started:
1) Open Kaffeine and select the DVB channel you want to record.
2) Menu DVB -> Configure DVB -> Recording: select MPEG_PS als preffered format and choose recording directory - audio/video will be stored here for further processing.
3) Start recording
4) Stop recording (should save the recoring to a file)
5) Quit kaffeine (or continue watching TV if you like, we won't need much CPU-power)
6) Start avidemux and open the file from the recording directory.
7) Use following settings: audio - copy, video - copy, format - mpeg ps a+v. No video/audio encoding is done so there will be **[COLOR="Blue"][SIZE="4"]NO QUALITY LOSS!!![/SIZE][/COLOR]**. We're doing this just to fix the mpeg-container.
8) Save the file and use .mpg ending. Now you can delete the file from step 4) to get some free space.
9) Open ManDVD
10) Now you can add the file to the project and it won't be reencoded!

---

