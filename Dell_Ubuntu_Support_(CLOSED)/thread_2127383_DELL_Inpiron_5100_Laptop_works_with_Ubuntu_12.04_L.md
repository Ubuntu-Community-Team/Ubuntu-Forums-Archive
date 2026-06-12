---
title: "DELL Inpiron 5100 Laptop works with Ubuntu 12.04 LTS installed"
date: 2013-03-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ITBeast on 2013-03-19
To the Ubuntu Community,

For those who may still have a DELL Inspiron 5100 I just wanted to post what flavor and version of Linux worked for me in getting my 10 year old laptop back to usable condition (Or as I called it Raising the Titanic). Along with the hardware specs I will summarize what parts of the laptop worked with my version of Linux and which parts did not (Which was very few). Along with that I will also briefly post what other flavors of Linux was tried but did not work. I am doing this since my search was painful in finding if any Linux Versions would work on this Dell, Luckily I finally found one person that had been successful with Ubuntu with a slightly older version (8.04 LTS) which finally gave me something to work on.

_**What Versions of Linux that did not work**_
- CentOS 6.3 both 32 bit and the 64 bit versions: The 64 bit did not processor did not work for obvious reasons (It was an old 32 bit only Processor P4). I had a little more luck with the 32 bit version of CentOS 6.3 that would allow the CentOS install get as far as getting ready to actually installing the CentOS OS but then would just lock. Believe the problem to be because the P4 processor was not natively PAE supported (Due to age)
- Linux Mint 14.1 32 bit version only: No go from the start on either LIVE CD Session or Install, It would just error out and say wrong operating system. The Linux Mint Page explicitly states while 32 bit is supported that PAE had to be enabled for it to work, which I found odd since Linux Mint is an off shot of Ubuntu but I guess that is one of the differences between the 2 flavors.

**_What Version Did Work_**
- Ubuntu 12.04 LTS 32 bit version only: This worked from the get with both the Live CD and then the Install. From what I can tell is the Ubuntu OS "simulates" the PAE support for those processors that do not support the natively.

[B][U]DELL Inspiron 5100 Laptop Hardware specs and brief explanation
[/U][/B]- Linux Ubuntu 12.04 LTS 32bit Operating System (formerly Windows XP)
- Pentium 4/2.53 ghz processor:This processor does not natively support PAE but Ubuntu simulates the functionality
- 1GB PC133-so-dimm RAM: works fine
- 32 MB ATI Rage Video Card with VGA out port: Both the interal Display connected to the display (1024x768 max resolution for the internal LCD Display) and the VGA out port (Tested at 1368 X 768 Resolution on a 32inch Vizo T.V. Screen), Can also extend the Desktop Display to other monitor
- 15 inch built-in XVGA LCD Display:  (1024x768 max resolution for the internal LCD Display)
- 80GB IDE Hard Drive - works fine
- 2 USB 2.0 Slots - works fine
- Combo CD/DVD Drive (24x CDRW Read/Burn and 6x DVD-ROM Read only): works fine, Reads CD's and DVD's without a hitch (Have not tested the burning capabilities but I am sure it will work) However there are some issues regarding Video playback (See Deficiencies below)
- Panda Ultra Wifi (b/g/n) 150Mbps Wireless-N 2.4GHz USB Adapter: Works out of the Box on Ubuntu 12.04 LTS
- 100MB Broadcom Wired NIC: Works Fine (My particular NIC Works intermittently but this is a hardware problem and not a Linux Driver problem)
- 56k Dial up modem (No supported drivers in Linux): Is not supported on Ubuntu (Besides who uses Dial Modems anymore anyways)
- PCMIA Slot (No supported drivers in Linux)          : Not supported in Ubuntu, to bad I have an Linksys Wi-fi card that is now just a paperweight, but the before mentioned Panda Ultra Wifi (b/g/n) 150Mbps Wireless-N 2.4GHz USB Adapter works just fine.

**_Overall Performance of Ubuntu 12.04 LTS on a DELL Inspiron 5100 Laptop: _**
The overall performance is acceptable to good. I'm not going to lie to you and say that it runs like a Chevy Corvette but will say it moves more like a Toyota Prius. We must remember that this is a 10 YEAR OLD piece of machinery however with that in mind does work great. I'm able to do the following in it and get good response time in execution of the applications...

- Firefox 19.0.2 with K12 Blackboard teleconferencing and Web Browsing
- Liberoffice 4.0.1.2 (Formerly Open Office) For Word Processing and so forth
- View documents and files within a Windows Network (Samba is installed by default)
- Spotify (The Linux software is still in beta with Spotify)
- Remote Desktop using the Windows RDP Desktop protocol. 

**_Modifications made to Default software _**
I  made some modifications to the software that was already installed or   upgraded the existing ones that was not in the per-defined  repositories. This also includes enabling root and getting rid of the  "Guest Session".

- _** Getting Rid of the guest session.**_ Ubuntu is easy enough  to break into  without leaving the front door wide open and post a sign  "Break Into  Me", So I followed this link to change that deficiency.  Thanks to an [article]("http://www.liberiangeek.net/2012/03/remove-the-guest-session-from-ubuntu-12-04-precise-pangolin/") posted by the Liberian Geek that is no longer a problem in Ubuntu 12.04 LTS
-  _**Enabling Root as a Login**_. For those who wants to have access to Root  which is not available in Ubuntu by default please read this [article]("http://www.liberiangeek.net/2012/05/login-as-root-in-ubuntu-12-04-precise-pangolin/") posted by the Liberian Geek. Please be warned there are dire consequences if you are not careful, proceed with caution.
-_**  Installing/upgrading LibreOffice version 4.0**_. For those who either want to  install or Upgrade to LibreOffice 4.0 (formley openoffice) please read  this [article]("http://www.webupd8.org/2013/03/install-libreoffice-40-in-ubuntu-1204.html")   from Web UPD8, it goes over how to modify your current repositories to   either upgrade or install. The current Ubuntu repositories only have   LibreOffice 3.5.7 .
- _**Installing Adobe Reader**_. While Ubuntu has it's own  version of a .pdf reader I still prefer the good old reliable Adobe  Reader which can be installed in Ubuntu. Once again the Liberian Geek  was kind enough to provide an [article]("http://www.liberiangeek.net/2012/10/install-adobe-reader-in-ubuntu-12-10-quantal-quetzal/") on how to do so, while it says for Ubuntu 12.10 this will also work work for Ubuntu 12.04 LTS as well.
- _**Installing Google Chrome**_. For those who want  Google Chrome instead of the Ubuntu offered Chromium you can now  follow the steps from this [article]("http://www.krizna.com/ubuntu/install-google-chrome-ubuntu-12-04/") offered by krizna(.)com have Google's version of this popular web browser.
-  _**Installing Spotify on Ubuntu**_. While Spotify is not  officially supported  on Linux as of yet (Officially only Windows and  Mac att) the developers  over at spotify have been working on a client  version for the Debian  releases of Linux like [Ubuntu]("https://www.spotify.com/us/download/previews/"). As of right now it is only in pre-release status and not officially supported. It worked just fine on Ubuntu 12.04 LTS.
- _** Streaming Netflix on Ubuntu.**_ The kind folks of the  Ubuntu community  developed a in house application using wine to be able  to view Netflix  using a Firefox plugin. PLEASE NOTE THIS IS NOT  SUPPORTED BY NETFLIX,  with that being said I did get this working well  in my Ubuntu Virtual by  following the instructions provided by [How-To-Geek.com]("http://www.howtogeek.com/130372/how-to-watch-netflix-on-ubuntu-with-the-netflix-desktop-app/")   . This unfortunately did not work on my Dell Inspiron 5100 with  Ubuntu,  do not believe had anything to do with the app just my  hardware. I'm  sure it would work fine with a newer processor. 				

**_Deficiencies using Ubuntu 12.04 LTS on a Dell Inspiron 5100 Laptop: _**
2 of these are insignificant (for me anyways) and 2 minor/major issue that is frustrating but most likeliy due to age of the hardware, anyways here they are...

- PCMIA SLot, No Linux Drivers: Insignificant since I have a USB Wi-Fi Adapter that works perfectly
- 56K Dial Up Modem, No Linux Drivers: Again Insignificant since I don't use Dial up and I don't think anybody else does either.
- Play Any type of Movie Files (Whether it may be on a CD, DVD, or a file on a hard drive: This includes and DVD Movies on a DVD (Yes the codecs were loaded correctly) or any MP4 or other relayed Video File. Audio Files seem to work fine. While this is frustrating everything else works fine.
- Netflix (not supported by NetFlix but the Ubuntu Community has developed an application using wine that does work) However, while this worked in a virtual the video on the Inspiron 5100 was effected the same the other video files mentioned previously. Only the Audio Files worked.

_**Overall satisfaction with Ubuntu 12.04 on my Dell Inspiron 5100**_
Overall I could not be happier. The original Operating System that came with it (Windows XP SP1) Had overtime become to resource intensive with all the patches and service packs which made it very painful to use, I had even downgraded the OS to Windows 2000 SP4 but it was only slightly better and the other negative was in upgrading the software was no longer supported (Windows 2000 support ended in July 2010). This had pretty much had sat on a shelf for almost 3 years until I finally came upon this solution.

If anybody has any questions or ways I can improve what has been down feel free to reply back to this thread and I will answer.

I will update if anything changes.

I want to thank everybody in the Ubuntu Community for making this possible.

---

### Post by mörgæs on 2013-03-20
Thanks. Please post a brief summary in the thread [http://ubuntuforums.org/showthread.php?t=1543006](http://ubuntuforums.org/showthread.php?t=1543006) , possibly linking to the detailed explanations here.

I would recommend Lubuntu on such old hadware.

---

### Post by ITBeast on 2013-03-20
I went ahead and posted at the link you mentioned with a link back to this thread giving the full explanation and details of my laptop in this thread.

As I said in my original post I ended up with using Ubuntu after doing some extensive research on Google and coming up with a post from someone back in 2008 that had used Ubuntu 8.04 on there Dell Inspiron 5100 hardware. Did not now of the other Ubuntu flavors until I started installing and playing with Ubuntu.  

When I get home tonight I will download Lubuntu 12.10  and try it on a Live CD, If it supports my processor I will do a test run on a Virtual 1st to see if Lubuntu will support my wife's needed applications and browser. If that all pans out I will then proceed to installing on my Laptop, Until then I will keep her on the 12.04 LTS. Like I said in my last post it is at least usable at this point and not collecting dust anymore However, Would not mind see it move a little faster :D.

Thanks for you advice and reply post, I will reply back in this thread or another concerning my Lubuntu results.

---

### Post by ITBeast on 2013-03-21
**_Modifications made to Default software _**
I  made some modifications to the software that was already installed or  upgraded the existing ones that was not in the per-defined repositories. This also includes enabling root and getting rid of the "Guest Session".

- _** Getting Rid of the guest session.**_ Ubuntu is easy enough to break into  without leaving the front door wide open and post a sign "Break Into  Me", So I followed this link to change that deficiency. Thanks to an [article]("http://www.liberiangeek.net/2012/03/remove-the-guest-session-from-ubuntu-12-04-precise-pangolin/") posted by the Liberian Geek that is no longer a problem in Ubuntu 12.04 LTS
-  _**Enabling Root as a Login**_. For those who wants to have access to Root  which is not available in Ubuntu by default please read this [article]("http://www.liberiangeek.net/2012/05/login-as-root-in-ubuntu-12-04-precise-pangolin/") posted by the Liberian Geek. Please be warned there are dire consequences if you are not careful, proceed with caution.
-_**  Installing/upgrading LibreOffice version 4.0**_. For those who either want to  install or Upgrade to LibreOffice 4.0 (formley openoffice) please read  this [article]("http://www.webupd8.org/2013/03/install-libreoffice-40-in-ubuntu-1204.html")  from Web UPD8, it goes over how to modify your current repositories to  either upgrade or install. The current Ubuntu repositories only have  LibreOffice 3.5.7 .
- _**Installing Adobe Reader**_. While Ubuntu has it's own version of a .pdf reader I still prefer the good old reliable Adobe Reader which can be installed in Ubuntu. Once again the Liberian Geek was kind enough to provide an [article]("http://www.liberiangeek.net/2012/10/install-adobe-reader-in-ubuntu-12-10-quantal-quetzal/") on how to do so, while it says for Ubuntu 12.10 this will also work work for Ubuntu 12.04 LTS as well.
- _**Installing Google Chrome**_. For those who want  Google Chrome instead of the Ubuntu offered Chromium you can now  follow the steps from this [article]("http://www.krizna.com/ubuntu/install-google-chrome-ubuntu-12-04/") offered by krizna(.)com have Google's version of this popular web browser.
-  _**Installing Spotify on Ubuntu**_. While Spotify is not officially supported  on Linux as of yet (Officially only Windows and Mac att) the developers  over at spotify have been working on a client version for the Debian  releases of Linux like [Ubuntu]("https://www.spotify.com/us/download/previews/"). As of right now it is only in pre-release status and not officially supported. It worked just fine on Ubuntu 12.04 LTS.
- _** Streaming Netflix on Ubuntu.**_ The kind folks of the Ubuntu community  developed a in house application using wine to be able to view Netflex  using a Firefox plugin. PLEASE NOTE THIS IS NOT SUPPORTED BY NETFLIX,  with that being said I did get this working well in my Ubuntu Virtual by  following the instructions provided by [How-To-Geek.com]("http://www.howtogeek.com/130372/how-to-watch-netflix-on-ubuntu-with-the-netflix-desktop-app/")  . This unfortunately did not work on my Dell Inspiron 5100 with Ubuntu,  do not believe had anything to do with the app just my hardware. I'm  sure it would work fine with a newer processor.

---

### Post by ITBeast on 2013-03-23
I have tried Lubuntu as per the moderator and I am very pleased with the results, please follow this [link]("http://ubuntuforums.org/showthread.php?t=2128700&p=12571192#post12571192") for further analysts.

---

### Post by ITBeast on 2013-03-29
After having my wife test out Lubuntu 12.10 for the last week there was some deficiencies in using the web browsers (Both Firefox and Chrome). The speed was very slow in response and if you used the tab browsing or had more than one browser open. Once again it seems that the culprit was the processor. I am going to try reloading Lubuntu and not use the Netflix Wine Emulater plug-ins on the web browser and see if this will correct the deficiency. If not I maybe forced into re-installing Ubuntu 12.04LTS, while my wife like the windows feel, Having the video work, and the other apps moving faster the browser capabilities was just not acceptable to her.

I will update the status concerning this later.

---

### Post by mörgæs on 2013-03-30
Have you tried adding Flashblock or similar plug-ins to the browsers? 

Tried xxxterm or another light-weight browser?

Does **top** give any indication as to what exactly is slowing down the browsing (CPU or memory constraints)?

---

### Post by ITBeast on 2013-04-01
Hi morgaes,

It was the processor that was getting eaten up by the browser, Memory was fine. I also ended up slicking the hard drive and reloading Lubuntu again without the Netflix Wine emulator and the browsers worked like a champ with multiple tabs opened and switched (more than 3).

I will give your other plugins a try as well, thanks for the advice.

I will keep this thread as well as the Lubuntu thread updated with my progress.

---

