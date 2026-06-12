---
title: "PS3 media sever install"
date: 2009-02-05
forum: General Help
---

### Post by jinxs1591 on 2009-02-05
Hello

I'm still very new to ubuntu and was hoping would anyone know how to install the ps3 media server and please go easy I'm still a command line noob

---

### Post by mb_webguy on 2009-02-05
If you're talking about a UPnP server to stream music and videos to your PS3, then there are several applications that will do the job.  I personally use [MediaTomb]("http://mediatomb.cc/").  It's not fancy, but it's easy to set up and it does the job, and it's in the Ubuntu repositories.  [uShare]("http://ushare.geexbox.org/") and gMediaServer are a couple of other UPnP servers available in the repositories, but I don't know anything about them.  

If you're specifically talking about [PS3 Media Server]("http://code.google.com/p/ps3mediaserver/"), then I can't help much.  I looked at it, but it's severely lacking on installation instructions.  It also doesn't seem as mature an application as the others.  

----------

To set up MediaTomb on Ubuntu to stream media to your PS3:

**1) Install MediaTomb.**  Open the terminal and type "sudo apt-get install mediatomb".

**2) Run MediaTomb once to create the configuration file.**  Type "mediatomb".  Wait for the output to stop -- it should give you a URL for connecting to MediaTomb.  Press Ctrl-C to stop MediaTomb.

**3) Edit the configuration file.**  Enter the command "gedit ~/.mediatomb/config.xml".  Make the following changes:

Find this line:```
<protocolInfo extend="no"/><!-- For PS3 support change to "yes" -->
```
Change "no" to "yes".  Then find the following lines:```
<!-- Uncomment the line below for PS3 divx support -->
<!-- <map from="avi" to="video/divx"/> -->
```
Remove "<!--" and "-->" from the second line.  Now scroll up to to this line:```
<extension-mimetype ignore-unknown="no">
```
Directly below that line, paste these lines:```
<map from="avi" to="video/x-divx"/> 
<map from="divx" to="video/x-divx"/>
```
Save and exit.

**4) Start MediaTomb.**  Type "mediatomb".  Take note of the address it gives you (though you probably won't need it).

**5) Add your media directories.**  Look in Applications->Sound & Video for a launcher for MediaTomb.  This will open a page in your web browser.  (If this doesn't work, type the address MediaTomb gave you in your browser's address bar.)  In the left pane, click "Filesystem" and locate the media you want to share.  At the top of the right pane, click the plus symbol with the arrows around it.  Select "Timed" and "Full", check "Recursive", and then click the "Set" button.  Do this for each directory you want to share with your PS3.  Now when you click "Database" in the left pane, it will show the media you're sharing.  (It will take a few minutes to add large numbers of files, so if your media doesn't show up immediately, give it some time.)

That's it.  To run MediaTomb, type "mediatomb" in the terminal (although at this point, it's already running).  I created a launcher for my panel by right-clicking on the panel, selecting "Add to Panel" and then "Custom Application Launcher", and using the command "gnome-terminal -x mediatomb".  (You could just use the command "mediatomb", but you wouldn't be able to close it without killing the process.) The MediaTomb icon is found in "/usr/share/pixmaps/".

You can also set MediaTomb to run at startup by going to System->Preferences->Sessions, clicking the "Add" button, and using one of the above commands, depending on whether you want to have the option of closing the program or not.

NOTE:  Some tutorials say to run MediaTomb using sudo, but there's no reason to do this as long as your user account has read access to the files you want to share.

---

### Post by RAiN2M on 2009-02-13
Thank you very much mb_webguy, this was cake. I got my media server up and running and it only took like 20 mins, haha.

---

### Post by goldleader on 2009-02-18
I have followed these instructions and can't get mediatomb to work on my PS3, when i search for media servers on my PS3 it says it can't see any.  Im using the 64 bit version of Ubuntu 8.10, not sure if that will make any difference.  

My network is a wired connection to my PC from a Linksys WRT54GS and then a wireless connection to my PS3.  

I have no ports forwarded though on the router and wonder if this is the problem.  

Also i have to say that i have had media servers working before on this same network using tversity on Windows Vista.  Please help.

---

### Post by mb_webguy on 2009-02-18
If the router is handling both the wired and wireless connections, then port forwarding shouldn't come into it.  That's only for external connections.

HOWEVER, some routers do not have UPnP enabled by default, even if it is supported by the router.  Check your router's settings and see if you can find the setting for UPnP, and make sure it's enabled.  

If your router has UPnP enabled, you made the appropriate changes to the Mediatomb config file, and Mediatomb is running, the PS3 should detect it.

---

### Post by goldleader on 2009-02-20
Thanks for the reply.

I have checked on the router and UPnP is enabled so thats not the problem.  Any other ideas before i totally start again with a new box?

Thanks

---

### Post by mb_webguy on 2009-02-20
Nope, sorry.  I'm running Mediatomb on two different computers, and both are detected by my PS3 without any problem.  If UPnP is enabled on your router, and you set up the Mediatomb config file correctly, I don't know what the problem could be.

You're not perhaps running Mediatomb using sudo (as is suggested for some reason by several tutorials I've seen on the web)?

---

### Post by goldleader on 2009-02-21
Great news built a new box using Ubuntu 8.10 32 bit and it worked first time using these instructions.  Which are great by the way, thanks.  Im very happy now i have a server that i can remotely manage.

I think the problem i was having on my first box was that when i ran Mediatomb it would assign an ip address of 192.168.11.103 and my network is 192.16.1.* so it wouldn't work.  Not sure why it did this but on my new box it assigns the right ip address so all is good.

Thanks for the help.

---

### Post by philinux on 2009-02-21
Should just add fuppes, which I use, is another alternative.
[http://fuppes.ulrich-voelkel.de/](http://fuppes.ulrich-voelkel.de/)

---

### Post by Axess_Denied on 2009-03-19
Okay...

My PS3 sees MediaTomb. My media is all located on an external drive, how do I get MT to look at that drive instead of PC Directory? 

:) That would be a big help. I like to keep my media off of my machine. Can I have it look at my library for Rythymbox?



[SOLVED]

---

### Post by madhi19 on 2009-04-04
You have to share the folder where your media is located first. To do that you right click on the folder you want to share than click on Properties/Share. 
When you done that you start mediatomb and use the web interface to add and scan the right folder.

---

### Post by mb_webguy on 2009-04-04
> **madhi19 said:**
> You have to share the folder where your media is located first. To do that you right click on the folder you want to share than click on Properties/Share. 
When you done that you start mediatomb and use the web interface to add and scan the right folder.

Samba has nothing to do with UPnP.  I don't have any of the media I share with Mediatomb shared with Samba.  As long as the media you're trying to share is readable by the account running Mediatomb, and you have it shared in Mediatomb, it should be available to UPnP clients on the network.

---

### Post by sdowney717 on 2009-11-14
error, database is locked
I had installed it before, then uninstalled then reinstalled
and i suppose mediatomb is trying to open a database 

> scott@scott-desktop:~$ sudo apt-get install mediatomb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libffmpegthumbnailer3 libmozjs0d mediatomb-common mediatomb-daemon
The following NEW packages will be installed:
  libffmpegthumbnailer3 libmozjs0d mediatomb mediatomb-common mediatomb-daemon
0 upgraded, 5 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B/1,533kB of archives.
After this operation, 4,059kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libffmpegthumbnailer3.
(Reading database ... 190743 files and directories currently installed.)
Unpacking libffmpegthumbnailer3 (from .../libffmpegthumbnailer3_1.5.4-1build1_i386.deb) ...
Selecting previously deselected package libmozjs0d.
Unpacking libmozjs0d (from .../libmozjs0d_1.8.1.16+nobinonly-0ubuntu1_i386.deb) ...
Selecting previously deselected package mediatomb-common.
Unpacking mediatomb-common (from .../mediatomb-common_0.12.0~svn2018-4ubuntu1_i386.deb) ...
Selecting previously deselected package mediatomb-daemon.
Unpacking mediatomb-daemon (from .../mediatomb-daemon_0.12.0~svn2018-4ubuntu1_all.deb) ...
Selecting previously deselected package mediatomb.
Unpacking mediatomb (from .../mediatomb_0.12.0~svn2018-4ubuntu1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for sreadahead ...
Processing triggers for desktop-file-utils ...
Setting up libffmpegthumbnailer3 (1.5.4-1build1) ...

Setting up libmozjs0d (1.8.1.16+nobinonly-0ubuntu1) ...

Setting up mediatomb-common (0.12.0~svn2018-4ubuntu1) ...
Setting up mediatomb-daemon (0.12.0~svn2018-4ubuntu1) ...
 * Starting upnp media server mediatomb                                  [ OK ] 

Setting up mediatomb (0.12.0~svn2018-4ubuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
scott@scott-desktop:~$ mediatomb

MediaTomb UPnP Server version 0.12.0 - [http://mediatomb.cc/](http://mediatomb.cc/)

===============================================================================
Copyright 2005-2008 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2009-11-14 16:02:46    INFO: Loading configuration from: /home/scott/.mediatomb/config.xml
2009-11-14 16:02:46    INFO: Checking configuration...
2009-11-14 16:02:46    INFO: Setting filesystem import charset to UTF-8
2009-11-14 16:02:46    INFO: Setting metadata import charset to UTF-8
2009-11-14 16:02:46    INFO: Setting playlist charset to UTF-8
2009-11-14 16:02:46    INFO: Configuration check succeeded.
2009-11-14 16:02:46    INFO: Initialized port: 49154
2009-11-14 16:02:46    INFO: Server bound to: 192.168.110.1
2009-11-14 16:02:46    INFO: Adding HTTP header "X-User-Agent: redsonic"
2009-11-14 16:02:47   ERROR: SQLITE3: (5) database is locked
Query:UPDATE "mt_autoscan" SET "touched"=0 WHERE "persistent"=1 AND "scan_mode"='timed'
error: database is locked
scott@scott-desktop:~$ 


---

### Post by benerivo on 2009-11-15
I think you could just remove the database. Try doing```
sudo updatedb
```then```
locate mediatomb.db
```to find the right file to delete.

---

### Post by Brilock on 2009-12-21
> **mb_webguy said:**
> If you're talking about a UPnP server to stream music and videos to your PS3, then there are several applications that will do the job.  I personally use [MediaTomb]("http://mediatomb.cc/").  It's not fancy, but it's easy to set up and it does the job, and it's in the Ubuntu repositories. 


You rock webguy, kudos to great descriptions and clear instruction.  And the MediaTomb folks too!

Just 1 transcoding away from watching myth recordings on the ps3... :P

---

### Post by Bradj47 on 2009-12-22
Thanks a lot webguy. I had no idea I could do this. It really freed up a lot of space on my PS3. I can read all the music and picture files I added to MediaTomb without a problem. But I'm having a problem playing WMV, MOV, and FLV video files. Is there some codec in the config file to enable or something?

---

### Post by Bradj47 on 2009-12-22
Now I'm having another problem with it: 
[https://sourceforge.net/projects/mediatomb/forums/forum/440751/topic/3224259/index/page/1](https://sourceforge.net/projects/mediatomb/forums/forum/440751/topic/3224259/index/page/1)

---

### Post by mb_webguy on 2009-12-28
> Thanks a lot webguy. I had no idea I could do this. It really freed up a lot of space on my PS3. I can read all the music and picture files I added to MediaTomb without a problem. But I'm having a problem playing WMV, MOV, and FLV video files. Is there some codec in the config file to enable or something?I generally avoid Windows Media and Quicktime files, partially because they're not as widely supported as other formats (such as an avi with divx/xvid video and mp3 audio), and partially because they're occasionally DRM'ed.

As of firmware update 2.10, the PS3 will play wmv files, but you might have to enable it.  On the PS3, go to Settings > System Settings > Enable WMA Playback.

The PS3 won't play Quicktime (a.k.a. ".mov") or Flash video (".flv") files, so you'll have to transcode them on the media server.  MediaTomb supports on-the-fly transcoding using external encoders, but I haven't really played with it enough to walk you through it.  [Here]("http://mediatomb.cc/pages/transcoding")'s MediaTomb's documentation page for transcoding.

---

### Post by Brilock on 2009-12-29
> **mb_webguy said:**
> 
The PS3 won't play Quicktime (a.k.a. ".mov") or Flash video (".flv") files, so you'll have to transcode them on the media server.
I can see media tomb on my ps3, and all the directories I've set up as well but none of the videos show up.  I had assumed that my recordings were in a bad format, but I've got all mpgs.  I can view all of the recordings' thumbnails under the photo viewer, so that strikes me as odd.  The router has UPnP enabled too, are there any other settings I may have forgotten?  I'm pretty sure I followed the config file instructions but I'll double check...

Also, I've set up crontab to create links using mythrename.pl.  There aren't any issues with that are there?  I'll paste it here in case there's a mistake.  Otherwise maybe it can help others

*/10 * * * * sudo perl /usr/share/doc/mythtv-backend/contrib/user_jobs/mythrename.pl --format "\%T/\%Y-\%m-\%d  \%H\%i \%- \%T \%-\%S" --link /mythtv/readable-recordings

---

### Post by oliver.greg@gmail.com on 2009-12-30
Are you familiar with tcpdump?  If so, from your mediatomb server, use: (assuming you ethernet interface is eth0)

tcpdump -i eth0 -w ~/mediatom.cap -s 1500 host ip.of.your.ps3 and port 49152 (unless you changed your mediatomb port)

After you try to browse your collection, stop the dump and open it with wireshark.  You should see your media list sent in the format your config.xml prepares.

If not, there is something wrong.  Does netstat -rn show the proper multicast route on the right interface?

In /etc/default/mediatomb, under options, place "-D" to enable more verbose logging for mediatomb.

-Greg

---

