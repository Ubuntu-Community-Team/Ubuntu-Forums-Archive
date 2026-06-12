---
title: "Internet Explorer"
date: 2006-06-30
forum: Desktop Environments
---

### Post by lwr on 2006-06-30
Hi,
I need to run Internet Explorer to test websites I develop - that's the only reason by the way, I've not gone insane. I've tried just installing it with wine, I've tried using sidenet, I've tried IEs4Linux, none of which seem to work. The best I've got so far is being able to open a blank window that claims to be (Wine) Internet Explorer. Any suggestions as to what I'd need to do? Ideally it would be nice to have a native linux app that accurately emulated the way IE rendered a page, but I guess that's wishful thinking right?

Thanks for your help

---

### Post by hda on 2006-06-30
I'd suggest running a full Windows installation in VMware.
Works for me.

hth,
_hda_

---

### Post by th3james on 2006-06-30
[This site]("http://www.anybrowser.com/siteviewer.html") lets you test your site through ANY browser without installing anything!

---

### Post by user1397 on 2006-06-30
[quote=lwr]Hi,
I need to run Internet Explorer to test websites I develop - that's the only reason by the way, I've not gone insane. I've tried just installing it with wine, I've tried using sidenet, I've tried IEs4Linux, none of which seem to work. The best I've got so far is being able to open a blank window that claims to be (Wine) Internet Explorer. Any suggestions as to what I'd need to do? Ideally it would be nice to have a native linux app that accurately emulated the way IE rendered a page, but I guess that's wishful thinking right?

Thanks for your help[/quote]how did you try installing it with wine?

---

### Post by lwr on 2006-06-30
I downloaded the install file and just opened it with wine by clicking on it. Apart from when I tried sidenet, then i just went for option 1.

Thanks for the previous suggestion th3james, but it seems that that site doen't want to show iframes, pictures or anything else with a local path.

---

### Post by user1397 on 2006-06-30
[quote=lwr]I downloaded the install file and just opened it with wine by clicking on it. Apart from when I tried sidenet, then i just went for option 1.

Thanks for the previous suggestion th3james, but it seems that that site doen't want to show iframes, pictures or anything else with a local path.[/quote]man, I don't really know what to tell you, wine worked for me when i tried installing IE.  just some bad luck I suppose **he goes and sits on his la-z-boy, feeling like this: :confused:**

---

### Post by l.tambiah on 2006-06-30
Internet explorer running on Linux...

First install Wine, the one in the repositorys will be fine for Internet explorer. 

```
$ sudo apt-get install wine
``` 
Now go to the site which contains the binary and download it. I have downloaded the binary to my Desktop.

[Ies 4 Linux]("http://www.tatanka.com.br/ies4linux/index-en.html")

Extract the package "ies4linux-2.0beta8.tar.gz" (just right click and select extract).

In Terminal(this presumes you have downloaded binary to desktop):

```
$ cd Desktop/ies*
``` 
Just do a ls command now and ensure the binary "ies4linux" exists.

```
$ ls -l
``` 
If all is well lets install it:

```
$ ./ies4linux
``` 

Now follow prompts in terminal (this is straight forward). After all is installed now you  should see an IE icon pop up on your desktop. First time ie starts it fails to display correctly. Just close it and re-lauch the browser and all will be fine.

---

### Post by Jasper Houtman on 2006-06-30
[Installing IE under WINE]("http://appdb.winehq.org/appview.php?appId=25")
The above is a link to a page on how to get different versions of IE running under WINE.

Edit: I currently have IE 5.0, 5.5 and 6.0 (with flash 8 ) installed and running perfectly in WINE on Ubuntu Dapper Drake.  Use them for webpage testing and for flash 8 files.

---

### Post by lwr on 2006-07-02
I tried doing ies4linux again using the terminal as you suggested and it came up with the following errors:

```

All right! Let's start the installations...

Downloading everything we need
 DCOM98.EXE
 mfc40.cab
 249973USA8.exe
 ADVAUTH.CAB
 CRLUPD.CAB
 HHUPD.CAB
 IEDOM.CAB
 IE_S1.CAB
 IE_S2.CAB
 IE_S5.CAB
 IE_S4.CAB
 IE_S3.CAB
 IE_S6.CAB
 SCR56EN.CAB
 SETUPW95.CAB
 FONTCORE.CAB
 FONTSUP.CAB
 VGX.CAB
 ie55sp2_9x.zip
 ie501sp2_9x.zip
 swflash.cab
[ OK ]

Installing IE 6
 Initializing
 Creating Wine Prefix
 Extracting CAB files
/home/luke/.ies4linux/downloads/ie6/EN-US//ADVAUTH.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/luke/.ies4linux/downloads/ie6/EN-US//CRLUPD.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/luke/.ies4linux/downloads/ie6/EN-US//HHUPD.CAB: WARNING; possible 6720 extra bytes at end of file.
/home/luke/.ies4linux/downloads/ie6/EN-US//IEDOM.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/luke/.ies4linux/downloads/ie6/EN-US//IE_S1.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/luke/.ies4linux/downloads/ie6/EN-US//IE_S2.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/luke/.ies4linux/downloads/ie6/EN-US//IE_S3.CAB: WARNING; possible 1400095 extra bytes at end of file.
ie_3.cab: checksum error
/home/luke/.ies4linux/downloads/ie6/EN-US//IE_S4.CAB: WARNING; possible 697815 extra bytes at end of file.
ie_4.cab: checksum error
/home/luke/.ies4linux/downloads/ie6/EN-US//IE_S5.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/luke/.ies4linux/downloads/ie6/EN-US//IE_S6.CAB: WARNING; possible 143480 extra bytes at end of file.
ie_6.cab: checksum error
/home/luke/.ies4linux/downloads/ie6/EN-US//SCR56EN.CAB: WARNING; possible 806829 extra bytes at end of file.
vbscript.dll: checksum error
/home/luke/.ies4linux/downloads/ie6/EN-US//SETUPW95.CAB: WARNING; possible 473915 extra bytes at end of file.
iemigrat.dll: checksum error
/home/luke/.ies4linux/downloads/ie6/EN-US//VGX.CAB: WARNING; possible 874819 extra bytes at end of file.
vgx.dll: checksum error
An error occured when trying to cabextract some files.

```

I hadn't seen that before as I hadn't used the terminal, but it doesn't mean a lot to me. Any suggestions as to what I need to do? According to synaptic, I've got cabextract installed ok.

---

### Post by kripkenstein on 2006-07-02
If the wine in the repos doesn't work, try the latest (0.9.16, currently).

I also need to test websites on IE (sadly...). I use the latest wine and the latest ies4linux. After installation things are fine, but they sometimes 'break' after a few days. A reinstall of ies4linux fixes things. Annoying, but still workable.

---

### Post by l.tambiah on 2006-07-02
Dont know why your getting problems, follow my solution and it should work fine. I am using it on my desktop and laptop without no issues. The installer I have told you to use will allow you to add IE 5 - 6.

---

### Post by lwr on 2006-09-06
Things still aren't working any better. I really need to get this sorted. Take a look at [my website]("http://www.truthdesigns.co.uk") (still very much in development btw) in Firefox/Konqueror/Opera or anything that can actually render pages and you'll see pretty much what I intend you to see. Have a look again in IE. This is a desperate situation. I can't do any real webdesign until I get IE running. Either that, or I'll have to wait until everyone has IE7.

---

### Post by justaguynpc on 2006-09-06
[FONT="Tahoma"][/FONT]Wow!

Installed GREAT for me, though I won't be using it for any HTML issues.  I have been with linux for years, a sundry of distros.  Just the sight of IE brings back a blast from the past.

Just installed for sh*ts and grins!

Cheers

---

### Post by lwr on 2006-09-11
Quick update:

I've finally got IE working. I posted my problem on the ies4linux forum, and they came up with the solution. It turns out all I had to do was delete both the bin and .ies4linux files, then run the script again. Pretty simple.

It's kind of mixed emotions now I've got it working. On the one hand, it's great that I can actually do website development now, but on the otherhand I'm running what is possibly the worst piece of software ever on my beautiful Ubuntu machine. Oh well, needs must when the devil drives.

---

### Post by Stone123 on 2006-09-11
never mind .

---

### Post by Rob Lindsay on 2006-09-15
I found that the best way out of this problem was to run ./ies4linux in a terminal again - having emptied the .ies4linux folder.

I left the machine to do the download and found that the checksum problems disappeared.

Have loaded IE6 and IE5.5 and they work well for checking web  page displays.

---

### Post by peabody on 2006-09-15
> **lwr said:**
> It's kind of mixed emotions now I've got it working. On the one hand, it's great that I can actually do website development now, but on the otherhand I'm running what is possibly the worst piece of software ever on my beautiful Ubuntu machine. Oh well, needs must when the devil drives.

Amen brother.  Sometimes I think it'd be great to just say f@#$% it and tell people using a site to just install Firefox.

Then I see that Firefox still only has about 28% of the browser market and I sigh.

What really gets me is that IE in Ubuntu is faster than my native firefox!  The right click menu takes a day and a half to pop open, but other than that the thing is super speedy!  Double sigh...

---

