---
title: "Lubuntu 12.10, A  Slightly better Fit for my DELL Inspiron 5100 Laptop"
date: 2013-03-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ITBeast on 2013-03-23
To the Ubuntu/Lubuntu Community,

For those who may still have a read my original [post]("http://ubuntuforums.org/showthread.php?t=2127383") on my Dell Inspiron 5100 I ended up trying Lubuntu at the suggestion of on of the Moderator's of this forum. As I stated in my earlier post while Ubuntu 12.04 LTS did get my laptop from off the shelf and moving again I was still have some lag issue concerning the Video with the processor. For the most part Ubuntu 12.04 LTS did almost everything  I wanted within a fair response time but light resource functionality of Lubuntu I felt did up the usability of my old Laptop overall. I will again go into what worked and did not work along with modifications made.

_**What Versions of Linux that did not work**_
- CentOS 6.3 both 32 bit and the 64 bit versions: The 64 bit did not  processor did not work for obvious reasons (It was an old 32 bit only  Processor P4). I had a little more luck with the 32 bit version of  CentOS 6.3 that would allow the CentOS install get as far as getting  ready to actually installing the CentOS OS but then would just lock.  Believe the problem to be because the P4 processor was not natively PAE  supported (Due to age)
- Linux Mint 14.1 32 bit version only: No go from the start on either  LIVE CD Session or Install, It would just error out and say wrong  operating system. The Linux Mint Page explicitly states while 32 bit is  supported that PAE had to be enabled for it to work, which I found odd  since Linux Mint is an off shot of Ubuntu but I guess that is one of the  differences between the 2 flavors. 

**_What Versions of Linux that Did Work_**
- Ubuntu 12.04 LTS 32 bit version only: This worked from the get with  both the Live CD and then the Install. From what I can tell is the  Ubuntu OS "simulates" the PAE support for those processors that do not  support the natively. Response time with most apps was fair to good, the only problems I had was any Video playback and Netflix Streaming.
- Lubuntu 12.10 32 bit version only: Worked as well and in some areas better than Ubuntu 12.04 LTS. Response time was good to very good, hardly used any RAM (The most I saw was maybe 400mb but usually hovered around 170mb to 200mb).

[B][U]DELL Inspiron 5100 Laptop Hardware specs and brief explanation
[/U][/B]- Linux Lubuntu 12.10 32bit Operating System (formerly Windows XP and Ububtu 12.04 LTS)
- Pentium 4/2.53 ghz processor:This processor does not natively support PAE but Ubuntu simulates the functionality
- 1GB PC133-so-dimm RAM: works fine
- 32 MB ATI Rage Video Card with VGA out port: Both the interal Display  connected to the display (1024x768 max resolution for the internal LCD  Display) and the VGA out port (Tested at 1368 X 768 Resolution on a  32inch Vizo T.V. Screen), Can also extend the Desktop Display to other  monitor
- 15 inch built-in XVGA LCD Display:  (1024x768 max resolution for the internal LCD Display)
- 80GB IDE Hard Drive - works fine
- 2 USB 2.0 Slots - works fine
- Combo CD/DVD Drive (24x CDRW Read/Burn and 6x DVD-ROM Read only):  works fine, Reads CD's and DVD's without a hitch (Have not tested the  burning capabilities but I am sure it will work) However there are some  issues regarding Video playback (See Deficiencies below)
- Panda Ultra Wifi (b/g/n) 150Mbps Wireless-N 2.4GHz USB Adapter: Works out of the Box on Ubuntu 12.04 LTS and Lubuntu 12.10
- 100MB Broadcom Wired NIC: Works Fine (My particular NIC Works  intermittently but this is a hardware problem and not a Linux Driver  problem)
- 56k Dial up modem (No supported drivers in Linux): Is not supported on Lubuntu (Besides who uses Dial Modems anymore anyways)
- PCMIA Slot (No supported drivers in Linux)          : Not supported in Lubuntu, to bad I have an Linksys WiFi card that is now just a  paperweight, but the before mentioned Panda Ultra WiFi (b/g/n) 150Mbps  Wireless-N 2.4GHz USB Adapter works just fine.

**_Overall Performance of Lubuntu 12.10 on a DELL Inspiron 5100 Laptop: _**
The overall performance is good to very good. While again it does not run like a Chevy Corvette but will say it moves now like a Toyota Corolla Sports Edition.  I'm able  to do the following in it and get good response time in execution of the  applications...

- Firefox 19.0.2 with K12 Blackboard teleconferencing and Web Browsing
- Liberoffice 4.0.1.2 (Formerly Open Office) For Word Processing and so forth
- View documents and files within a Windows Network (Samba is installed by default)
- Spotify (The Linux software is still in beta with Spotify)
- The Lubuntu Video Player can now play any form of pre recorded Video
- Remote Desktop using the Windows RDP Desktop protocol. 

**_Modifications made to Default software _**
I  made some modifications to the software that was already installed or    upgraded the existing ones that was not in the per-defined   repositories. This also includes enabling root and getting rid of the   "Guest Session". While these are all aimed at Ubuntu 12.04 LTS It does and will work in Lubuntu 12.10, any modifications made to the orginal links are listed with the link.

- _** Getting Rid of the guest session.**_ Ubuntu is easy enough   to break into  without leaving the front door wide open and post a  sign  "Break Into  Me", So I followed this link to change that  deficiency.  Thanks to an [article]("http://www.liberiangeek.net/2012/03/remove-the-guest-session-from-ubuntu-12-04-precise-pangolin/") posted by the Liberian Geek that is no longer a problem in Ubuntu 12.04 LTS or Lubuntu 12.10. There is a deviation in this from Ubuntu 12.04 LTS to Lubuntu 12.10, for Lubuntu 12.10 please type the following 1st CLI in the command console below instead of sudo gedit /etc/lightdm/lightdm.conf (As described in the link)...

sudo abiword /etc/lightdm/lightdm.conf

Then follow rest of the link, the reason for this is gpedit is not an available text editor in Lubuntu 12.10 however abiword is and will do the same job as gpedit.

-  _**Enabling Root as a Login**_. For those who wants to have access to Root  which is not available in Ubuntu by default please read this [article]("http://www.liberiangeek.net/2012/05/login-as-root-in-ubuntu-12-04-precise-pangolin/") posted by the Liberian Geek. Please be warned there are dire consequences if you are not careful, proceed with caution.
-_**  Installing/upgrading LibreOffice version 4.0**_. For those who either want to  install or Upgrade to LibreOffice 4.0 (formley openoffice) please read  this [article]("http://www.webupd8.org/2013/03/install-libreoffice-40-in-ubuntu-1204.html")    from Web UPD8, it goes over how to modify your current repositories  to   either upgrade or install. The current Ubuntu repositories only  have   LibreOffice 3.5.7 .
- _**Installing Adobe Reader**_. While Ubuntu has it's own   version of a .pdf reader I still prefer the good old reliable Adobe   Reader which can be installed in Ubuntu. Once again the Liberian Geek   was kind enough to provide an [article]("http://www.liberiangeek.net/2012/10/install-adobe-reader-in-ubuntu-12-10-quantal-quetzal/") on how to do so, while it says for Ubuntu 12.10 this will also work work for Ubuntu 12.04 LTS as well.
- _**Installing Google Chrome**_. For those who want  Google Chrome instead of the Ubuntu offered Chromium you can now  follow the steps from this [article]("http://www.krizna.com/ubuntu/install-google-chrome-ubuntu-12-04/") offered by krizna(.)com have Google's version of this popular web browser.
-  _**Installing Spotify on Ubuntu**_. While Spotify is not   officially supported  on Linux as of yet (Officially only Windows and   Mac att) the developers  over at spotify have been working on a client   version for the Debian  releases of Linux like [Ubuntu]("https://www.spotify.com/us/download/previews/"). As of right now it is only in pre-release status and not officially supported. It worked just fine on Ubuntu 12.04 LTS.
- _** Streaming Netflix on Ubuntu.**_ The kind folks of the   Ubuntu community  developed a in house application using wine to be able   to view Netflix  using a Firefox plugin. PLEASE NOTE THIS IS NOT   SUPPORTED BY NETFLIX,  with that being said I did get this working well   in my Ubuntu Virtual by  following the instructions provided by [How-To-Geek.com]("http://www.howtogeek.com/130372/how-to-watch-netflix-on-ubuntu-with-the-netflix-desktop-app/")    . This unfortunately did not work on my Dell Inspiron 5100 with   Ubuntu or Lubuntu,  do not believe had anything to do with the app just my   hardware. I'm  sure it would work fine with a newer processor.                 

**_Deficiencies using Ubuntu 12.04 LTS on a Dell Inspiron 5100 Laptop: _**
2 of these are insignificant (for me anyways) and 1 minor/major issue  that is frustrating but most likely due to age of the hardware, anyways  here they are...

- PCMIA SLot, No Linux Drivers: Insignificant since I have a USB Wi-Fi Adapter that works perfectly
- 56K Dial Up Modem, No Linux Drivers: Again Insignificant since I don't use Dial up and I don't think anybody else does either.
- Netflix (not supported by NetFlix but the Ubuntu Community has  developed an application using wine that does work) However, while this  worked in a virtual the video on the Inspiron 5100 was effected. Only the Audio Files  worked.

_**Overall satisfaction with Lbuntu 12.10 on my Dell Inspiron 5100**_
Overall happier now than I was with Ubuntu (and I was pretty happy with Ubuntu). The original Operating System that came  with it (Windows XP SP1) Had overtime become to resource intensive with  all the patches and service packs which made it very painful to use, I  had even downgraded the OS to Windows 2000 SP4 but it was only slightly  better and the other negative was in upgrading the software was no  longer supported (Windows 2000 support ended in July 2010). This had  pretty much had sat on a shelf for almost 3 years until I finally came  upon using Ubuntu. Now using Lubuntu 12.10 has really made that experience much better with it's less resource intensive demands and my wife likes that feel of that Windows 2000 like desktop than the unity on Ubuntu. My only real grip for Lubuntu is there is no LTS version (Long Term Support) as there is in Ubuntu as to having to upgrade every 18 months which I would prefer just to do it every 5 years, Hopefully Lubuntu will correct this in later versions. Again overall, could still not be happier.

If anybody has any questions or ways I can improve what has been down feel free to reply back to this thread and I will answer.

I will update if anything changes.

---

### Post by ITBeast on 2013-03-29
After having my wife test out Lubuntu 12.10 for the last week there was  some deficiencies in using the web browsers (Both Firefox and Chrome).  The speed was very slow in response and if you used the tab browsing or  had more than one browser open. Once again it seems that the culprit was  the processor. I am going to try reloading Lubuntu and not use the  Netflix Wine Emulater plug-ins on the web browser and see if this will  correct the deficiency. If not I maybe forced into re-installing Ubuntu  12.04LTS, while my wife like the windows feel, Having the video work,  and the other apps moving faster the browser capabilities was just not  acceptable to her.

I will update the status concerning this later.

---

### Post by ITBeast on 2013-04-01
I ended up slicking the hard drive and reloading Lubuntu again  without the Netflix Wine emulator and the browsers worked like a champ  with multiple tabs opened and switched (more than 3) between.

I will keep this thread updated with my progress.

---

### Post by mörgæs on 2013-05-20
Well, what do you know: Now I happened to get involved in bringing a 5100 to life. Thanks for the guide, here's a little [addition]("http://ubuntuforums.org/showthread.php?t=1543006&page=140&p=12660560#post12660560").

Did you try using faster memory than 133 MHz, and if so did you face any problems?

---

### Post by WoundedWolf on 2013-06-03
I just performed an install of Peppermint Three OS on my old Inspiron 5100 over the weekend. I was looking to resurrect it as a netbook for mostly browsing and hopefully a little video streaming. It took about 4 re-installs to get everything running that I wanted, but overall I am pretty impressed with the speed and responsiveness so far. Just a couple of comments, the PCMCIA support took a little digging. I have a funky Belkin Wireless G card that I have used forever and it didn't get picked up automatically in the install. After a few BSODs, re-installs, and a couple of hours of searching I finally found the magic drivers, so I performed another re-install and had the PCMCIA wireless card running in minutes thanks to this info (see Ubuntu install section about half-way down the page):

[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

I also got Netflix-Desktop running, thanks to the simple install instructions here:

[http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html](http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html)

Now, I have had an interesting experience with the video streaming. When I browsed to Hulu and YouTube while on the 10/100 ethernet wire I was very impressed with the playback quality. A slight lag here and there, but the sound was synced with the video and it was definitely watchable. However, over wireless G, the playback was very choppy. Not really watchable. I have other wireless G devices in my home that stream video no problem, so I can only assume it is a hardware issue with the old Inspiron 5100.

As for Netflix-Desktop, the video played over both ethernet and wireless, but it was so choppy over both that it was pretty much un-watchable. I had upgraded the video card on this laptop a few years ago to the Mobility Radeon 9000 (M9) 64MB, and I have 1GB of RAM installed, but I think the streaming video is just a little too much for this old fogey. Running Netflix-Desktop with Wine in the background is a little beyond its abilities. But normal browsing is very quick, which is as much as I can hope for from a 10-year old laptop. I was also very pleased with the ease of install, simplicity, and speed of Peppermint OS. Being a Linux n00b, it was fairly painless to get it installed and running like I wanted.

---

