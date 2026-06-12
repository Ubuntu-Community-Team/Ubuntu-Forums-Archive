---
title: "Linux alternative for Orb and Mycasting?"
date: 2007-10-03
forum: Gaming &amp; Leisure
---

### Post by teknosexual on 2007-10-03
Here is the offical website: [https://mycast.orb.com]("https://mycast.orb.com")

In a nutshell, this Windows-only application allows you to login to your PC remotely from anywhere and steam your music and videos. Specifically, you can stream them to you Nintendo Wii and Xbox 360.

Upon searching, it looks like no one's had any luck get it to function in Wine. So, I am wondering if anyone knows of a similar application that is Linux friendly?

---

### Post by ibbuntu on 2007-11-20
I'm looking for something like this too.

---

### Post by oxygala on 2007-12-09
can't you do it by vlc too? what is the difference?

---

### Post by Vadi on 2007-12-09
I know you can login to your computer from anywhere with the remote desktop... what do you mean by steaming though?

---

### Post by Mblackwell on 2007-12-10
The point is to be able to go to a web page and stream your music and movies through an embedded flash player (flash 7 compatible) from your machine on to said browser page. The point being this allows you to listen to your music catalogue and watch your movies on your (for example) Nintendo Wii.

In fact, since I got rid of satellite tv I've been looking for just this. I used to use Orb occasionally when I still used Windows, and I haven't seen any Linux equivalent.

---

### Post by karth on 2007-12-10
Double posting, sorry

---

### Post by karth on 2007-12-10
For Linux, I see two main alternatives:

1- MPD + Icecast2: MPD is a music player daemon, that means it runs in the background and responds to shell commands or to GUI commands (i.e. phpmp2), and it is able to accept connections from cliens to send them the audio output (by default, OGG format). Icecast2 is a streaming daemon that's able to connect to audio sources and cast them over the network. Audio apps (Amarok, VLC, whatever) connect to Icecast2 through a http stream and the music plays on your remote computer.

Howto + links to MPD and Icecast2: [http://gentoo-wiki.com/HOWTO_Icecast_OGG_and_MP3_streaming](http://gentoo-wiki.com/HOWTO_Icecast_OGG_and_MP3_streaming)

2- Jinzora: This is a "simple" php script that lives on your webserver. it is secured with login+password, manages a library, and outputs .m3u files to be opened by your fav music app. The stream comes through http, and the format is, I guess, the file's format (mp3, aac, ogg, whatever).

[http://en.jinzora.com/](http://en.jinzora.com/)

---

### Post by Mblackwell on 2007-12-12
Not at all what's needed, since it absolutely *has* to go to an embedded Flash 7 compatible player on a web browser page, so it can be used with the Internet Channel software (which is Opera with Flash 7 build into it).

That's the point. Playing music between computers is easy, the point is to do it from your computer to a Nintendo Wii.

---

### Post by weblordpepe on 2007-12-12
The point is that Orb doesn't run on Linux when it should. Orb is seriously awesome. All thats needed is a web browser+ media player. 

Although I might try that MPD+icecast trick. But Orb is absolutely awesome. Its half the reason why my main file server runs Windows.

---

### Post by Mblackwell on 2007-12-13
The only problem is that streaming movies over it kind of stinks. Playback is slow and the quality is poor. Not that I expect the quality to be great but it's really washed-out looking.

---

### Post by RDV on 2007-12-13
Although this is not a native solution for Orb under Linux here is a quote for somone running ORB under Linux "... currently run XP in a vmware session on my linux box just for ORB, and that's hardly a perfect solution". See [http://forums.orb.com/viewtopic.php?p=20652](http://forums.orb.com/viewtopic.php?p=20652) 

I have not come across anyone successfully running ORB under WINE.

I use ORB to stream audio and video to my PDA and will need this functionality as I move exclusively to Ubuntu.

An area that may be of interest is a Shoutcast server and NSV (NullSoft Video Streaming). Be warned that I have never set up Shoutcast on Linux but the Windows version worked very well for me. There is a  native Linux Shoutcast server and NSV Linux utility. See the following links: 
Shoutcast Linux Download: [http://www.shoutcast.com/download/files.phtml](http://www.shoutcast.com/download/files.phtml)
NSV Linux utility: [http://www.scvi.net/nsv_linux.htm](http://www.scvi.net/nsv_linux.htm)
Shoutcast recommended player - Linux/X Windows users should use XMMS
(What is NSV) [http://www.scvi.net/whatis.htm](http://www.scvi.net/whatis.htm)
How TO NSV - [http://gentoo-wiki.com/HOWTO_NSV_on_Linux](http://gentoo-wiki.com/HOWTO_NSV_on_Linux)

I suspect the downside of using this solution for video streaming is that ORB has the feature of adjusting (manual or auto settings) the stream rates for the target device. For example my PDA must have a lower stream rate (Kbps) than a PC or the video stutters and has buffer delays. I do not know if Shoutcast/NSV can do this.

As I stated I have not tried this solution on Linux yet. This is a project after I get Ubuntu displaying through my component video connection to my HDTV (come on ATI).

---

### Post by weblordpepe on 2007-12-15
Wow ATi. My condolences.

But yeah - the thing with Orb is that its brilliant. I had been trying for months to get realtime streaming and encoding from a web GUI so I could listen to music at work on my PDA :P

When Orb came around it was all problems solved. Its amazing the freedom you get with an Orb server on your idling box at home. Its the same 'aaaaah' kinda freedom you get from an SSH server :P

---

### Post by breaking on 2008-01-02
I too have been looking for this for a long time.  I think I have finally found the solution in Jinzora ([http://en.jinzora.com/]("http://en.jinzora.com/")).

It takes a little bit more knowledge to setup (need to setup a LAMP server) but it works every bit as well.

The only feature that's missing is it won't work if you can't open up a NAT port to it, like on a college campus.  Otherwise, even if your house is on a dynamic IP that changes frequently, there are scripts that you can get to automatically email you when your IP changes.  I hope this is what you were looking for!

---

### Post by weblordpepe on 2008-01-05
oooooooooooooooohhhh!!!!!

---

### Post by teknosexual on 2008-01-16
> **breaking said:**
> I too have been looking for this for a long time.  I think I have finally found the solution in Jinzora ([http://en.jinzora.com/]("http://en.jinzora.com/")).

Thank you, I'll check it out! :KS

---

### Post by mondoUNC on 2008-01-16
Check out Mediatomb, I set it up to stream to my PS3 with [this tutorial]("http://ubuntuforums.org/showthread.php?t=650020&highlight=mediatomb"), I'd imagine it could be set up to stream to Wii or 360. Its got a nice interface and encodes on the fly, I tried Fuppes and a few others and its definitely the best.

---

### Post by jadymitchell on 2008-01-16
Here's another vote for Jinzora.  I actually now prefer it to Orb because I can customize it to suit my needs (basically, simple streaming of music to a Treo 700w).

---

### Post by CrossCrucial on 2008-01-24
I was also looking for an Orb alternative for streaming to my 360. For pointing me in the right direction, here is a tip

dydns.com (among others) offer free links to your dynamic/static IP and support for having your computer automatically update it whenever your ISP changes it. My dlink router has this built in, but there is a linux app(written in perl) which does this. Also a Windows solution is available, of course.

here's the link to the app and you can sign up for their free service on the same site. You get some degree of customization- like "<yourname>@mygameserver.net". Though there are a limited number of domain name choices

[https://www.dyndns.com/support/clients/unix.html](https://www.dyndns.com/support/clients/unix.html)

---

### Post by jms830 on 2008-02-07
A simple mp3 serving program to use, without relying on an external app like jinzora, is gnump3d. It's in the repositories.

[http://ubuntu-tutorials.com/2006/12/28/how-to-setup-gnump3d-for-a-streaming-media-server-ubuntu-510-6061-610/](http://ubuntu-tutorials.com/2006/12/28/how-to-setup-gnump3d-for-a-streaming-media-server-ubuntu-510-6061-610/)

One addition I would make to the guide is to change the "log" locations to somewhere in your home folder in the gnump3d.conf file. That way you don't have to run gnump3d as root. You will understand what I mean after you read the guide above. Then I just add gnump3d to my startup programs and I can access my mp3s from anywhere. There's even a way to password protect it. Also don't forget to open/forward port 8888 on your firewall.

---

### Post by jimmydahl on 2008-02-09
I used to use the GNUmp3d streaming media server and it worked fine and is very simple to get working. But there's one feature i missed in gnump3d - a simple way to protect your music to be accessed by unauthorised people.
GNUmp3d works like a webserver and makes everything in your shared music directory accessible if you now its url. The password protection is only for the page listing your music, not for the stream it self, and this feature is by the way taken away in the latest release.
There is one secure way to solv this though: blocking ip-adresses. You may save all allowed ip-adresses in a file. But this is not the ideal solution if you want to be able to access your media from everywhere, anytime...

Today I switched to useing Jinzora (mentioned several times above) instead. It's a bit harder to install, but just follow some simple LAMP-installation-guide first and then use the Jinzora web-based setup and there shouldn't be no problem.
Jinzora is actually really nice and supports multiuser access control, is fully skinable and has a lot mor features then GNUmp3d.

I don't think you may stream anything to your xbox 360 this way though. Officially you must use a Windows Media Center system or a Windows Media Connect application for this to work. Myself I use a program called tversity for this, but I think it only runs on windows systems...

---

### Post by peher on 2008-03-26
hi

you should also check ampache ([www.ampache.org](www.ampache.org)) in php and subsonic (subsonic.sourceforge.net) in java both nice programs

---

### Post by boakes on 2008-03-29
What if you already have an Orb server running?  How do you get it to play in Linux, every media player I've tried fails.

---

### Post by mgchan on 2008-05-15
With Orb recently releasing a native iPhone viewer, I am seriously considering either running Orb under a slimmed down VMware, or possibly going back to XP MCE for my HTPC device.  I prefer to have ubuntu running mythtv, but being able to easily stream all my movies, tv shows, or live tv to my iphone either over EDGE (works OK) or wifi (works great) would be a deal breaker.

---

### Post by al6042 on 2008-07-02
Hi guys... 
had anybody tried the oxyl-box, which is used to stream from linux to the pinnacle showcenter?

cheers
al

---

### Post by broderboy on 2009-01-27
check out ushare [http://blog.gpowered.net/2008/09/how-to-stream-video-to-xbox-360-from.html](http://blog.gpowered.net/2008/09/how-to-stream-video-to-xbox-360-from.html)

---

### Post by jackharvest on 2009-10-26
Frick, two years of patience since this thread and there still isn't any development with ORB or a simplistic alternative? 

Good grief. 

Isn't there a way to get it working with winetricks?

---

### Post by 569874123 on 2009-10-26
This thread has several alternatives...

---

### Post by brewster1134 on 2009-12-09
i have been using Zina for awhile.
it pretty much rules...  and looks way better than jinzora

[http://www.pancake.org/zina](http://www.pancake.org/zina)

---

### Post by patrickballeux on 2009-12-15
For movie streaming, I am currently working on a new project called JapelServer.  It's default configuration is for the iPhone, but it can be customized to support any devices over the network that can access a webpage and play streams from that webpage.

See [http://sourceforge.net/projects/japelserver/]("http://sourceforge.net/projects/japelserver/") for more details...

---

### Post by commander flatus on 2009-12-15
This whole thing kind of makes me sad.... :(

None of the above solutions work easily for audio and video. In fact, few work for video at all.

If you want iPhone compatibility you're doubly worse off -- ootunes advertises that it works on Linux and it may - but the author has never compiled the full thing on Linux and in its default state it works for music, not video. At least this is what he told me when I asked

MythTV has a streaming plug in for video which is long stagnant in development, but may actually work - I haven't tried it. MythTV also has a flash plugin which makes it OK for streaming over the internets but doesn't help b/c THE Steve decided that Flash wouldn't go in the iphoneses. This plugin makes streaming live TV over the tubes possibly, but only via starting a recording, then streaming that file - which is a PITA.

I have not tried Japel Server. What I would like is simple - and I cannot understand why it's not out there -

Live on demand transcoding to iphone via the iphone safari browser - the video spec is published -- shouldn't be that hard - especially for saved video files.

And (probably somewhat more difficult but certainly not impossible) the same thing for live TV.

Windows has multiple products that can do this - Orb, TVersity, TVU, yada yada yada...

If I didn't work 60 hours a week as a physician and have a 1 year old son I would work on it myself because it's so friggin frustrating. Maybe I should get an Android phone.

NSW

---

### Post by patrickballeux on 2009-12-15
Hi commander,

> **commander flatus said:**
> This whole thing kind of makes me sad.... 

Live on demand transcoding to iphone via the iphone safari browser - the video spec is published -- shouldn't be that hard - especially for saved video files.

NSW

JapelServer does exactly that: Live transcoding.  But since the project is only a few days old, I need some more time to polish the webpage and some minor bugs.  But it is already usable.  Only restriction, no space in the names of the movie for now and files have to be on the local HD. (I will fix that in the next releases...  )

Patrick

---

### Post by commander flatus on 2009-12-15
> **patrickballeux said:**
> Hi commander,



JapelServer does exactly that: Live transcoding.  But since the project is only a few days old, I need some more time to polish the webpage and some minor bugs.  But it is already usable.  Only restriction, no space in the names of the movie for now and files have to be on the local HD. (I will fix that in the next releases...  )

Patrick

I will download and check it out. Thanks for recognizing this shortcoming of our favorite OS. Can you work on streaming live TV next? Just kidding...

Flatulently,

---

### Post by patrickballeux on 2009-12-15
I can stream webcams or any stream from the internet also.  It's just a matter of setting the proper gstreamer configuration for what you want to stream...

---

### Post by EvilGenius007 on 2010-01-10
[SIZE=2]Just checking this out at work, and I can't wait to get home & try installing **[COLOR=#525252]JapelServer [/COLOR]**on my media storage box! I'm a huge Ubuntu newbie, but I will probably try to create some notes as I go & maybe produce some "documentation" to help others get it working.[/SIZE]

---

### Post by gnice3d on 2010-01-17
Use MediaTomb which is in the usual Ubuntu repos .. Synaptic will provide actual app and underlying daemon.

Works quite nicely 8)

---

### Post by mvpereira on 2010-05-28
Well, I didn't try other options than uShare and Wine+Orb.
My main goal is to have my video, music and pics library available to my xbox360.

Orb is perfect because it sorts your media accordingly (pics in dates, music in genre and artist and albums, and videos in folders), which is very helpful to find that special file. Orb can even stream youtube videos (and probably web radios, but I'm not sure). Unfortunately, installation is a bit hard because it shows no characters, just buttons. You should install using a how-to with screenshots. More than that, sometimes it just becomes quiet in the middle of a music. Xbox360 keeps counting music time, but it will never change to the next music. Also, in pictures library, it works just with some small files, and not with the photos...
For videos, the most important feature for me in Orb is the possibility to show subtitles through ffdshow, and the transcoding, because of the poor xbox360 video capabilities.
This is my impression for orb.

uShare worked once, but I don't use it anymore because it shows all my files in a single directory. And it does not transcode video files.

But in the last posts here, I found MediaTomb, which could be an option for me. But reading MediaTomb documentation, it has no support for xbox360.

I just don't know what to do, since there are different options for different jobs that could be done by using just one software. When will we have an Orb port for linux? Does anybody have a newer comment on that? Because the latest release on their site is dated November 2009.

---

### Post by JAS40 on 2010-07-29
I am new to Linux and Ubuntu, using it only for the past month.  I too  also want to stream photos, videos and music to my Wii.  I have  installed the latest version of Wine from the website and also installed  Orb20SetupEnGB.exe using right click and the option to install with  Wine Windows Program Loader.  Orb appears to have installed successfully  and completed a connection test with 2 green ticks suggesting that Orb  will function properly.
However when I login to MyOrb on the Wii and browse to my files, despite  being able to browse all the folders and see all the files on my Ubuntu  computer, I cannot open any files.  I get the message that the files  are not available.
In the system monitor on my computer under processes Orb.exe and  OrbTray.exe are both "sleeping" and under Waiting Channel are  "pipe_wait".  Does anyone have any suggestions and can anyone explain  why I can browse to my computer, see all the file names but not be able  to open them.  Thanks in advance and hopefully there will be a solution  for us all to benefit soon.  Great forums and great OS by the way.

---

### Post by JAS40 on 2010-08-03
I am new to Linux and Ubuntu, using it only for the past month. I too also want to stream photos, videos and music to my Wii. I have installed the latest version of Wine from the website and also installed Orb20SetupEnGB.exe using right click and the option to install with Wine Windows Program Loader. Orb appears to have installed successfully and completed a connection test with 2 green ticks suggesting that Orb will function properly.
However when I login to MyOrb on the Wii and browse to my files, despite being able to browse all the folders and see all the files on my Ubuntu computer, I cannot open any files. I get the message that the files are not available.
In the system monitor on my computer under processes Orb.exe and OrbTray.exe are both "sleeping" and under Waiting Channel are "pipe_wait". Does anyone have any suggestions and can anyone explain why I can browse to my computer, see all the file names but not be able to open them. Thanks in advance and hopefully there will be a solution for us all to benefit soon. Great forums and great OS by the way.

---

### Post by fuzzman54 on 2010-11-18
It's closed source and commercial, but I use Twonkymedia Server. It does everything that Orb and Tversity can, even streaming to a Wii.

[http://twonkymedia.de/products/twonkyserver/tryit.aspx](http://twonkymedia.de/products/twonkyserver/tryit.aspx)

There's a 30 day trial, and it's 30 bucks after that, but I just keep deleting the "~/home/.twonky" directory and the trial resets.

---

### Post by commander flatus on 2010-11-18
> **fuzzman54 said:**
> It's closed source and commercial, but I use Twonkymedia Server. It does everything that Orb and Tversity can, even streaming to a Wii.

[http://twonkymedia.de/products/twonkyserver/tryit.aspx](http://twonkymedia.de/products/twonkyserver/tryit.aspx)

There's a 30 day trial, and it's 30 bucks after that, but I just keep deleting the "~/home/.twonky" directory and the trial resets.


It doesn't do everything Orb does. Not even close. It cannot place-shift video to other computers and iPhones and Android devices. It can serve as a DLNA/uPNP server though. There's lots of software that can do that, though, including the free and very useful MediaTomb.

I own a copy of twonky, myself and I'll say it's great software, but not the same as Orb.

There are, however, some indications that Orb may be coming to Linux. Go to AppBrain.com and look at the listing for the Orb Live software. It says that they're working on a Linux server.

Time will tell.


Flatulently,

---

### Post by acastley on 2013-03-28
I also have this issue nearly 6 years on, still no alternative? I love Linux but want Orb style software

---

### Post by Perfect Storm on 2013-03-29
This is a very old thread. Please start a new one.


Thread closed.

---

