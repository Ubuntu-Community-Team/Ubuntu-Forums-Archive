---
title: "Change screensaver to photo slideshow(?)"
date: 2012-08-15
forum: Desktop Environments
---

### Post by Buntu Bunny on 2012-08-15
I've been trying out various desktops since I installed Ubuntu 12.04; so far I'm really liking Xfce. It's logical and highly customizable. I was also delighted to find that it hadn't abandoned the screensaver. My question is, is there a way to have it do a slideshow from my picture folder? I do a lot of photography and loved this feature with the old Gnome desktop in Ubuntu 10.04. Screensaver Preferences gives me a random mode, but it's all pre-installed stuff.

---

### Post by Toz on 2012-08-15
If you are using xscreensaver, then select the GLSlideshow screensaver, click on the Advanced tab and under Image Manipulation, select "Choose Random Image" and specify the directory to use.

---

### Post by OM55 on 2012-08-15
Hello Buntu Bunny (I remember you from another thread... I'm glad you were able to install Ubuntu 12.04 on your new laptop...)

Here is another option for you:

The default screensaver in Ubuntu 12.04 (gnome-screensaver) does not have the option to show user photos. But you can easily replace it with another one that does, for example XScreenSaver. Not only XScreenSaver allows you to show user photos, it has hundreds of nice screensaver options (including even one with the Windows blue-screen-of-death...).

To do that, first remove the gnome-screensaver:

```
sudo apt-get remove gnome-screensaver
```Then, install XScreenSaver with the additional data for the screensavers:

```
sudo apt-get install xscreensaver xscreensaver-data-extra xscreensaver-gl-extra

```Reboot, and you are done.
You can launch XScreenSaver manually by typing:

```
screensaver
```The option to select a folder with photos is in the 'Advance' tab.

Enjoy!

---

### Post by Buntu Bunny on 2012-08-15
Toz, thanks! It worked.

OM55 (Hi! I remember you too) happily, Xfce comes with the xscreesnaver. :)

---

### Post by ironscf on 2012-09-04
):P Thanks from me too. I should have searched forum sooner. Spent hours looking for a way to display photos from Pictures directory when PC idles.

---

### Post by AnTonyWmM on 2012-12-12
I recently installed the xscreensaver, and have attempted to us GLslideshow to display photos from my Pictures folder.  However, it simply goes to a black screen.  I can see the pictures playing in the settings box, but when I click preview, the screen goes blank, and then a bit of orange script flashes in the upper corner of the screen momentarily, as if it can't find the directory or something.

Any insight?

Thanks,
Anthony

---

### Post by Peter Maunder on 2012-12-12
There were problems with the XSCREENSAVER slideshow picking up the picture folder as there was a missing dependency  libwww-perl in some distributions. I had to download the library for one of my machines. The problem was supposed to be fixed but may still be there. I could see the preview slideshow but GLSlideshow would not find the chosen folder when XScreensaver tripped.

---

### Post by AnTonyWmM on 2012-12-13
Thanks for the info Peter!
Currently using Wallch as a desktop slideshow instead.

---

### Post by Buntu Bunny on 2012-12-13
> **AnTonyWmM said:**
> Thanks for the info Peter!
Currently using Wallch as a desktop slideshow instead.

Is Wallch an actual screensaver? Or is the slideshow on the active desktop as a background?

---

### Post by eldiabolosk on 2012-12-13
TOZ: I do not have the you mentioned under GLSlideshow under advanced settings. All I got is Commandline: glslideshow -root
and Visual: GL

Help please.

---

### Post by eldiabolosk on 2012-12-13
TOZ: I do not have the you mentioned under GLSlideshow under advanced settings. All I got is Commandline: glslideshow -root
and Visual: GL

---

### Post by Toz on 2012-12-13
> **eldiabolosk said:**
> TOZ: I do not have the you mentioned under GLSlideshow under advanced settings. All I got is Commandline: glslideshow -root
and Visual: GL

Help please.

Look on the "Advanced" tab - the one next to the "Display Modes" tab on the main xscreensaver preferences window (not the button you click if you go through "Settings").

---

### Post by Sky Aisling on 2013-01-13
**Peter Maunder** writes: 
 > Re: Change screensaver to photo slideshow(?) 
There were problems with the XSCREENSAVER slideshow picking up the  picture folder as there was a missing dependency libwww-perl in some  distributions. I had to download the library for one of my machines.  The problem was supposed to be fixed but may still be there. I could  see the preview slideshow but GLSlideshow would not find the chosen  folder when XScreensaver tripped. I've found the same issue on the download I took yesterday -**  Ubuntu-12.04-.1-desktop-i386.iso**.  The **libwww-perl** dependency was  missing. 

This site was useful: 
[http://useranswer.com/answer/installing-libwww-perl-on-ubuntu-12-04se/](http://useranswer.com/answer/installing-libwww-perl-on-ubuntu-12-04se/) 

I installed (from a terminal window) this command: 

```
sudo apt-get install libwww-perl 
```This solved the issue. 

[COLOR=Red]Note:[/COLOR] prior to discovering the missing dependency, I had deleted the  Gnome-Screensaver and installed the XScreensaver per the same instructions  that **OM55** gave in the above post of August 15th, 2012 11:47 AM.

---

### Post by marcisim on 2013-01-16
Hi everyboy, 

I have a problem similar to that of AnTonyWmM: I removed gnome-screensaver, installe xscreensaver, selected the slideshow mode, but both in the settings box and in the preview, the application just picks up just one image and repeat it.
The images are in a directory are all in the same directory and are named with numbers (i.e.: 1.jpg, 2.jpg, 3.jpg etcetc)

Thank you in advance for helping

Marcello :)

---

### Post by marcisim on 2013-01-16
Well...it seems that i fixed it. I had a suggestion from [this]("https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/278941") post: by reading the documentation of xcreensaver it seems that the -pan and -duration command line options are involved in choosing the number of time we want an image appearing.

[COLOR=#323232][FONT=monospace]-duration *seconds*
[/FONT][/COLOR]
[COLOR=#323232][FONT=monospace]How long each image will be displayed before loading a new one.
Default 30 seconds.

[/FONT][/COLOR]
[COLOR=#323232][FONT=monospace]-pan *seconds*
[/FONT][/COLOR]
[COLOR=#323232][FONT=monospace]How long each pan-and-zoom should last. Default 6 seconds.
[/FONT][/COLOR]
[COLOR=#323232][FONT=monospace]With the default settings of *-pan 6 -duration 30*, each image
will be displayed five times (30/6), and then a new image will
be loaded. If you want a new image to be loaded at each fade,
then set *-pan *and *-duration *to the same value.
[/FONT][/COLOR]


Therfore I went on "settings" &#8594; "advanced" and in the command line i put both values to 6 seconds (but you can choose another value) and it fixed it.

WOW!

---

### Post by AndyCinDallas on 2013-06-08
I had the right directory of images selected in GLSlideshow (Ubuntu 12.04 LTS), but they weren't showing. The below just worked for me:

> **Sky Aisling said:**
> **Peter Maunder** writes: 
 I've found the same issue on the download I took yesterday -**  Ubuntu-12.04-.1-desktop-i386.iso**.  The **libwww-perl** dependency was  missing. 

This site was useful: 
[http://useranswer.com/answer/installing-libwww-perl-on-ubuntu-12-04se/](http://useranswer.com/answer/installing-libwww-perl-on-ubuntu-12-04se/) 

I installed (from a terminal window) this command: 

```
sudo apt-get install libwww-perl 
```This solved the issue. 

[COLOR=Red]Note:[/COLOR] prior to discovering the missing dependency, I had deleted the  Gnome-Screensaver and installed the XScreensaver per the same instructions  that **OM55** gave in the above post of August 15th, 2012 11:47 AM.

As soon as I installed **libwww-perl** as above, my pics were visible - thank you!

---

### Post by Randymanme on 2013-08-18
I would also like to use a slideshow of my pictures folder for a screensaver, but I don't see how to do it with xscreensaver.  Xscreensaver says "Directory does not exist: 'home/randall/pictures.'  Please see screenshot.  Well maybe not -- I don't see how to add a screenshot from my comcomputer.

What am I doing wrong?  And how do I fix it?  
libwww-perl is already installed.

Any help would be much appreciated.

P.S., One solution, if I could do it, would be to install mate screensaver [but I'd only want mate screensaver and only mate screensaver (not the whole mate desktop)] on Ubuntu.

---

### Post by Toz on 2013-08-18
> **Randymanme said:**
> ....."Directory does not exist: 'home/randall/pictures.'.....
The default pictures folder name is **Pictures** (capital P). Double-check to make sure you have it spelled correctly, Linux is case sensitive.

---

### Post by Randymanme on 2013-08-25
Thank you for the suggestion, but that doesn't work either.  Now I get: "Error: File does not exist /home/randall/Pictures"

---

### Post by Toz on 2013-08-25
> **Randymanme said:**
> Thank you for the suggestion, but that doesn't work either.  Now I get: "Error: File does not exist /home/randall/Pictures"

Can you open a terminal window, type in the following commands, and post back the results:
```
ls -l /home/randall
```
...and
```
ls -l /home/randall/[Pp]ictures
```

---

### Post by Randymanme on 2013-08-25
Thank you for spending time with me on this.  I appreciate it.

```
randall@randall-EL1358G:~$ ls -l /home/randall
total 186576
drwxrwxr-x  3 randall randall      4096 Aug 15 17:30 ~
drwx------  2 randall randall      4096 Aug 15 14:57 black-wallpapers-NoobsLab.com
-rw-rw-r--  1 randall randall      1351 Aug 22 13:59 compiz_backup.profile
-rwxr-xr-x  1 randall randall     20318 Aug 12 00:44 conky-builder.sh
drwxr-xr-x  2 randall randall      4096 Aug 22 14:44 Desktop
drwxr-xr-x  2 randall randall      4096 Aug 25 04:21 Documents
drwxr-xr-x 23 randall randall      4096 Aug 25 13:57 Downloads
drwx------  7 randall randall      4096 Aug 23 12:17 Dropbox
drwxr-xr-x  2 randall randall      4096 Aug 25 16:37 dwhelper
drwxrwxr-x  2 randall randall      4096 Aug 19 04:26 Educational_Vidieos
drwxrwxr-x  5 randall randall      4096 Aug 14 17:10 Extracted_TarBalls
drwxrwxr-x  5 randall randall      4096 Aug 15 13:47 FavoriteTVvideos
drwxr-xr-x  4 randall randall      4096 Aug 17 22:43 Fight_Films
-rw-rw-r--  1 randall randall    786003 Aug 17 18:32 Firefox_wallpaper.png
drwxrwxr-x  2 randall randall      4096 Aug 15 14:57 FlvVideos
drwxrwxr-x  2 randall randall      4096 Aug 12 10:29 gymnastics
drwxrwxr-x  6 randall randall      4096 Aug 12 11:00 ISOs
drwxrwxr-x  2 randall randall      4096 Aug 14 17:10 JW4Sweetie
drwxr-xr-x  2 randall randall      4096 Aug 15 14:57 KindleBoobks
drwxrwxr-x  2 randall randall      4096 Aug 15 13:20 Law and Order Special Victims Unit season 4-JDmaX
drwx------  2 randall randall      4096 Aug 19 04:13 Law and Order SVU - The Complete Season 13 [HDTV]
drwxrwxr-x  2 randall randall      4096 Aug 15 02:40 Law & Order - Criminal Intent - Season 4 Complete
drwxr-xr-x  2 randall randall      4096 Aug 15 14:21 Law&OrderS20
-rw-rw-r--  1 randall randall         0 Aug 12 01:22 libpeerconnection.log
drwxrwxr-x  3 randall randall      4096 Aug 17 18:38 Library_downloads
drwxrwxr-x  7 randall randall     65536 Aug 19 04:22 Lisa'sDwhelper
drwxr-xr-x  2 randall randall      4096 Aug 14 17:10 Me4upload
drwxr-xr-x  3 randall randall      4096 Aug 19 04:29 Miscellania
drwxr-xr-x  3 randall randall      4096 Aug 14 17:09 MoreDownloads
drwxrwxr-x  2 randall randall      4096 Aug 14 17:09 motivation
drwxrwxr-x  2 randall randall      4096 Aug 25 16:37 Movies
-rw-rw-r--  1 randall randall     62878 Aug 25 04:20 mozilla.pdf
drwxr-xr-x  2 randall randall      4096 Aug 12 00:58 Music
drwxrwxr-x  2 randall randall      4096 Aug 14 17:11 NeedToGetBack
drwxr-xr-x  2 randall randall      4096 Aug 12 11:03 Newer_UnseenVideos
drwxrwxr-x  2 randall randall      4096 Aug 19 04:28 newPorn
drwxrwxr-x  2 randall randall      4096 Aug 14 17:11 News videos
-rw-rw-r--  1 randall randall 181706752 Aug 17 15:54 OMG GIRLZ - Performing New Single _Baddie_.mpeg
drwxr-xr-x  2 randall randall      4096 Aug 15 16:09 OtherPictures
drwxr-xr-x  4 randall randall      4096 Aug 25 03:37 Pictures
drwxrwxr-x  3 randall randall      4096 Aug 15 16:09 PicturesMqain
drwxrwxr-x  8 randall randall      4096 Aug 19 04:47 Porn
drwxr-xr-x  2 randall randall      4096 Aug 14 17:20 Post Install Info
drwxr-xr-x  2 randall randall      4096 Aug 12 00:58 Public
drwxrwxr-x  8 randall randall      4096 Aug 14 17:20 RetrievedDociuments
drwxrwxr-x  3 randall randall      4096 Aug 15 14:57 Safe.House.2012.DVDRiP.XviD.AC3-REFiLL
-rw-rw-r--  1 randall randall     99647 Aug 18 04:22 Screenshot from 2013-08-18 04:21:57.png
drwxrwxr-x  2 randall randall      4096 Aug 14 17:13 Serious_Music
drwxr-xr-x 17 randall randall      4096 Aug 15 16:44 SomeWindowsDownloads
drwxr-xr-x  3 randall randall      4096 Aug 14 17:15 Sports_Videos
drwxrwxr-x  2 randall randall      4096 Aug 14 17:20 TarBalls
drwxr-xr-x  2 randall randall      4096 Aug 12 00:58 Templates
-rw-r--r--  1 root    root         8656 Aug 19 12:34 testdisk.log
-rw-rw-r--  1 randall randall   8083456 Aug 16 18:22 The_Greenerator_Rapid_Prototype-_Residential_Green_Energy_Ge.mpeg
drwxr-xr-x  5 randall randall      4096 Aug 14 17:21 ThemeTarBalls
drwxrwxr-x  2 randall randall      4096 Aug 17 16:20 Torrents
drwxrwxr-x  2 randall randall      4096 Aug 20 16:27 Ubuntu One
drwxr-xr-x 12 randall randall      4096 Aug 19 11:35 Videos
drwxrwxr-x  4 randall randall      4096 Aug 17 18:20 Vuze Downloads
randall@randall-EL1358G:~$ 
```
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .. 
```
randall@randall-EL1358G:~$ ls -l /home/randall/[Pp]ictures
total 28044
-rw-r--r-- 1 randall randall    53673 Feb 27 20:30 000016-CulturesSM2MalinPalm-jpg_050705.jpg
-rw-r--r-- 1 randall randall    50337 Feb 27 20:29 00006-WildMomentsRUThomaKokta-jpg_050641.jpg
-rw-r--r-- 1 randall randall    49740 Jan 13  2013 04-WhiteHouse2012Photos_620x413.jpg
-rw-r--r-- 1 randall randall    95208 Nov 25  2011 12300_380474477890_582742890_3890248_2414919_n.jpg
-rw-r--r-- 1 randall randall   191488 Nov 29  2011 12b3e3eb8dc11cd21c81742b231f6640.jpg
-rw-rw-r-- 1 randall randall   149703 Feb  7  2012 144.jpg
-rw-r--r-- 1 randall randall    44289 Jan 13  2013 16-21-WhiteHouse2012Photos_620x413.jpg
-rw-r--r-- 1 randall randall    36451 Nov 25  2011 17571_267487822890_582742890_3444833_5786249_n.jpg
drwxr-xr-x 3 randall randall    12288 Aug 23 02:23 (1) Abigeal Benson_files
-rw-rw-r-- 1 randall randall   585603 Aug 23 02:23 (1) Abigeal Benson.html
-rw-r--r-- 1 randall randall   157383 Nov 29  2011 2011-11-29-024153.jpg
-rw-rw-r-- 1 randall randall    74649 Aug 14 17:24 2013-08-14-172445.jpg
-rw-r--r-- 1 randall randall   307516 Nov 29  2011 21bec8d2423cf50eff5b36fa1f755a88.jpg
-rw-r--r-- 1 randall randall    60786 Jan 13  2013 24B-64-WhiteHouse2012Photos_620x413.jpg
-rw-r--r-- 1 randall randall    54607 Nov 25  2011 250984_10150202066022891_582742890_7157148_7873987_n.jpg
-rw-r--r-- 1 randall randall    51465 Jan 13  2013 26B-66-WhiteHouse2012Photos_620x413.jpg
-rw-r--r-- 1 randall randall    46916 Jan 13  2013 33-38-WhiteHouse2012Photos_620x413.jpg
-rw-r--r-- 1 randall randall    96091 Nov 18  2012 4romAndroid 1258.jpg
-rw-r--r-- 1 randall randall    20045 Nov 20  2012 4romAndroid 1347.jpg
-rw-r--r-- 1 randall randall    27288 Nov 20  2012 4romAndroid 1349.jpg
-rw-r--r-- 1 randall randall    11417 Dec 22  2012 4romAndroid 1621.jpg
-rw-r--r-- 1 randall randall    12813 Dec 22  2012 4romAndroid 1625.jpg
-rw-r--r-- 1 randall randall    72032 Dec 25  2012 4romAndroid 1716.jpg
-rw-r--r-- 1 randall randall   331950 Aug  4  2012 4romAndroid 541.jpg
-rw-r--r-- 1 randall randall   112559 Aug 10  2012 4romAndroid 544.jpg
-rw-r--r-- 1 randall randall    90687 Aug 28  2012 4romAndroid 553.jpg
-rw------- 1 randall randall    50841 Feb 14  2012 5.1.PNG
-rw-r--r-- 1 randall randall   176152 Mar 17 01:25 558906_453037458092511_611078973_n.jpg
-rw-r--r-- 1 randall randall    59239 Jan 13  2013 77-WhiteHouse2012Photos_620x413.jpg
-rw-r--r-- 1 randall randall    36033 Jan 13  2013 83-WhiteHouse2012Photos_620x413.jpg
-rw-r--r-- 1 randall randall    58386 Jan 13  2013 84-WhiteHouse2012Photos_620x413.jpg
-rw-rw-r-- 1 randall randall   130237 Feb  7  2012 Beijing-China-A-square-de-011.jpg
-rw-r--r-- 1 randall randall   683434 Nov 10  2011 beyonceAtLast.png
-rw-r--r-- 1 randall randall    48985 Dec 12  2011 capt.75d9e77faac44c678c3781aceca14625-75d9e77faac44c678c3781aceca14625-0.jpg
-rw-r--r-- 1 randall randall    35116 Dec 12  2011 capt.d18f553d00d743d4a88958e9c41877a3-d18f553d00d743d4a88958e9c41877a3-0.jpg
-rw-r--r-- 1 randall randall   205289 Jan 10  2013 Capture2.PNG
-rw-r--r-- 1 randall randall     3628 Nov 15  2011 certificate.png
-rw------- 1 randall randall    93075 Jun 16  2012 CheapVideoCards.PNG
-rw-r--r-- 1 randall randall    15823 Dec 12  2011 coexist.jpg
-rw-rw-r-- 1 randall randall    40140 Apr 29 00:11 condi rice.jpeg
-rw-r--r-- 1 randall randall   167946 Nov 29  2011 d9e090a2bf91a51e784ed499581fbbdf.jpg
-rw-r--r-- 1 randall randall   835088 Oct 10  2011 Dawes1.png
-rw-r--r-- 1 randall randall   139108 Dec 26  2011 Dazesha.png
-rw-rw-r-- 1 randall randall   401168 Aug 25 03:37 DownloadSetup.exe
-rw-rw-r-- 1 randall randall    15543 Jul 19  2012 DwF9vJ5HMEKIy9umElyteA.jpeg
-rw------- 1 randall randall   283961 Mar 28  2012 Ella2.png
-rw-rw-r-- 1 randall randall  1545536 Aug 14 23:53 Firefox_wallpaper.png
-rw-rw-r-- 1 randall randall 12575448 Aug 23 17:40 google-talkplugin_current_amd64.deb
-rw-r--r-- 1 randall randall   524088 Nov 16  2012 IMAG0127.jpg
-rw------- 1 randall randall   162838 Mar 15 17:44 Image 4528.jpg
-rw-rw-r-- 1 randall randall     8975 Aug 17 18:31 images.jpeg
-rw------- 1 randall randall    91061 Jul 23  2012 i'm.jpg
-rw-r--r-- 1 randall randall     3863 Dec 12  2011 janet1.jpeg
-rw-rw-r-- 1 randall randall    41594 Apr 29 00:11 jesse&halle.jpg
-rw------- 1 randall randall    35010 Feb 11  2012 Me.png
-rw-rw-r-- 1 randall randall    35442 Apr 29 00:11 MJ & Janet Jackson_jpg.jpg
-rw-rw-r-- 1 randall randall    82916 Aug 17 18:30 obama-family-victory-night2.jpg
-rw-r--r-- 1 randall randall   746971 Oct 10  2011 Prince1.png
-rw-rw-r-- 1 randall randall     4364 Jun 24  2012 randall.jpeg
-rw-r--r-- 1 randall randall   107406 Aug  7 17:27 Screenshot-1.png
-rw-r--r-- 1 randall randall   682571 Dec 12  2011 Screenshot-5.png
-rw-r--r-- 1 randall randall  2363851 Nov 24  2011 Screenshot at 2011-11-24 05_44_37.png
-rw-rw-r-- 1 randall randall   289908 Sep 26  2012 Screenshot at 2012-09-26 22:57:36.png
-rw-rw-r-- 1 randall randall   578625 Sep 26  2012 Screenshot at 2012-09-26 23:43:59.png
-rw-rw-r-- 1 randall randall   476768 Jul  9 21:25 Screenshot from 2013-07-09 21:25:46.png
-rw-rw-r-- 1 randall randall   109265 Aug 22 13:29 Screenshot from 2013-08-22 13:29:36.png
-rw-rw-r-- 1 randall randall   286240 Aug 23 02:24 Screenshot from 2013-08-23 02:23:56.png
-rw-r--r-- 1 randall randall   145605 Aug  7 17:26 Screenshot.png
-rw-rw-r-- 1 randall randall   553066 Jan 29  2012 Selection_006.png
-rw-rw-r-- 1 randall randall   496596 Jan 29  2012 Selection_007.png
-rw-r--r-- 1 randall randall     4632 Dec 12  2011 serena2.jpeg
-rw-r--r-- 1 randall randall     3720 Dec 12  2011 serena3.aspx.jpeg
-rw-r--r-- 1 randall randall    26822 May 13  2012 slide_196203_459542_large.jpg
-rw-r--r-- 1 randall randall    35167 Dec 12  2011 swilliams.jpg
-rw-rw-r-- 1 randall randall   159226 Aug 12 01:47 TailgateSavethedateHeader.jpg
-rw-r--r-- 1 randall randall     4165 Dec 12  2011 venus2.jpeg
-rw------- 1 randall randall   102358 Jun 14  2012 VillaVillaKhula.jpg
drwxr-xr-x 2 randall randall     4096 Aug 14 17:24 Webcam
randall@randall-EL1358G:~$
```

---

### Post by Toz on 2013-08-25
I added code tags to your previous post to make it easier to read.

The listings look fine. In the configuration dialog:
- Make sure that only "Choose Random Image" is selected.
- Delete the existing text in text box to the left of the Browse button.
- Click on the Browse button, then the Pictures folder, then OK

Does that help? It seems that there is an issue if you have existing text in the box before clicking on Browse.

---

### Post by Randymanme on 2013-08-26
Thank you very much, Toz; I appreciate your help and consideration.

I continued googling the problem and arrived at [URL="http://a1.blogspot.com/2012/04/ubuntu-1204-explained-setting-up.html"]http://a1.blogspot.com/2012/04/ubuntu-1204-explained-setting-up.html 
[/URL]                         and followed the directions (which included installing kdelibs-bi, kdelibs5-data, kdelibs5-plugins).

So now, xscreensaver works like I wanted it to.

Thank you.

---

### Post by Toz on 2013-08-26
Thats really odd. I don't have those kde libs installed and the GLslideshow works. I can't imagine how a kde lib would be a dependency for an xscreensaver screensaver. (*scratches head*). But anyways, it worked for you.

---

