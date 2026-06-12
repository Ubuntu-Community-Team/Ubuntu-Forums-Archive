---
title: "Sopcast. .deb that works perfectly."
date: 2006-09-15
forum: Desktop Environments
---

### Post by jbodell on 2006-09-15
[http://linuxtoy.org/archives/gtk_sopcast.html]("http://linuxtoy.org/archives/gtk_sopcast.html")

There you can find the .deb for gtk-sopcast 0.1.1. 

If anyone is having any trouble:

Download this, untar it and place sp-sc into /usr/local/bin/ :[http://download.sopcast.org/download/sp-sc.tgz]("http://download.sopcast.org/download/sp-sc.tgz")

Download the [gtk-sopcast.deb]("http://linuxtoy.org/deb/gtksopcast_0.1.1-1_i386.deb") and use gdebi to install it. 

That should work out of the box. MPlayer wouldnt work for me, it may for others, but Kaffeine worked perfectly. 

Now I can watch premiership football on my linux box as well as my xp box. Nice. For anyone who hasnt tried Sopcast, its incredible. You can watch most soccer games without any interruption totally free. Quality is not amazing, but good enough to watch fullscreen. Took me a while to find this for linux, hope it helps someone.

---

### Post by damu on 2006-09-15
thanks bunch for the info....it works great...

For others which would be in the same than me, I previously installed a version of sopcast which didn't work, but the icon "sopcast" is still in my menu under internet.
Using Accessories/A la carte menu editor, I selected the poscast icon, right clicked on it and chose property.
I changed the command for "sopcast" (the same than the one used in a terminal window to launch it). Now I can launch Sopcast from the menu :)

---

### Post by llamakc on 2006-09-15
Many thanks!

---

### Post by hulet on 2006-09-17
Thank you, this works.

---

### Post by davey.moore on 2006-09-27
It doesnt work for me.
I installed gtk-sopcast and copied the sp-sc file to the /usr/local/bin directory.

I can run gtk-sopcast and it seems to wrok fine, it even starts to load the channel. It says:

"Connecting... 0 seconds elapsed"

and the time starts going up but then that message dissapears but nothing happens.

Hope someone will have the answer!

Thanks.

---

### Post by gmcm1979 on 2006-10-01
i have installed gtk-sopcast but when i click on a channel all it shows is connecting and counter keeps going up and doesnt connect. can anyone help

---

### Post by jbodell on 2006-10-03
> **davey.moore said:**
> It doesnt work for me.
I installed gtk-sopcast and copied the sp-sc file to the /usr/local/bin directory.

I can run gtk-sopcast and it seems to wrok fine, it even starts to load the channel. It says:

"Connecting... 0 seconds elapsed"

and the time starts going up but then that message dissapears but nothing happens.

Hope someone will have the answer!

Thanks.

Sounds like the problem I had with mplayer. Go into the config in sopcast and try swapping mplayer with something xine based. xine will do fine, I used kaffeine and that worked. 

Let me know if that solves the issue.

---

### Post by gd1984 on 2006-10-05
So if you wanted to change it to Kaffeine for example, you would go to sopcast then config and then simply put "kaffeine" after Player or do you have to put more stuff after writing Kaffeine. Because I wrote Kaffeine by itself and still it doesn't work.

Thank You!!!

---

### Post by declaration on 2006-10-09
Thanks so much for this thread- no longer need my VMware Windows installation so much.
Very cool.

@ gd1984-
try the following in the player config- 
> xterm -e xine

You'll need to apt-get xine first.

Cheers again.

---

### Post by KiXeR on 2006-10-13
GTK-sopcast 0.2.8 works great. Thx!

---

### Post by phabulosa on 2006-10-19
Oh my God, it works so SMOOTHLY!!!!!!!!!!!!!!!!1

I love it!!!

:p

---

### Post by t3ddyg on 2006-10-23
This is decent - but I have nothing to compare it to.  I used to use TVUplayer (viidoo.com) on windows.  I felt like it had better channel selection.  Can that be run on linux?

Edit:  Is there a way to configure this to cap the upload speed?  This program runs up the upload so high that it gets choppy, and then rebuffers.  Rinse and repeat.  It's annoying.

Is there any way to correct my audio losing sync, other than restarting the program?

---

### Post by phabulosa on 2006-10-25
> **t3ddyg said:**
> 

Is there any way to correct my audio losing sync, other than restarting the program?

Try to press the player button. It will restart the mplayer window and fix the audio sync problem.

---

### Post by omac on 2006-10-27
This player works perfectly, and you're instructions were precise and easy to follow. Thanks jbodell.  Also, thanks to declaration for the xine syntax, much appreciated.  :)

---

### Post by moon_dog on 2006-10-29
is the quality due to sopcast or is that the quality the stations broadcast at?  it's great that there's finally something like TVUplayer for linux.

---

### Post by t3ddyg on 2006-10-29
Weird.... After I installed edgy off cd, I installed gsopcast again.  I can launch the program just fine, but now I'm having the same issue where i choose a channel, it says "connecting .." and no media player ever opens.  I tried installing both xine and kaffeine, and configuring gsopcast to use them as described in this thread.  Even when i click the player button, the player never pops up?  Any suggestions?

Edit:  I decided to scratch everything i did and start over.  So i uninstalled the non-working gsopcast-0.2.8 and redownload the tar, and began the commands.  I realized that when i ran the make command, a ton of errors occured!  This must be what is causing my issues.  The first time I ran make on the non-working install it didn't work, so i just did sudo apt-get install for all the packages that were required.  I think maybe I messed up what g++ it is using to make, because i remember apt-get installing some 4.x version.  Can someone instruct me on how to fix this?  Here is the output:
```
ted@teg:~$ tar jxf gsopcast-0.2.8.tar.bz2
ted@teg:~$ cd gsopcast-0.2.8/src
ted@teg:~/gsopcast-0.2.8/src$ make
g++ -O2 -Wall `pkg-config --cflags gtk+-2.0`  -c callbacks.cc -o callbacks.o
g++ -O2 -Wall `pkg-config --cflags gtk+-2.0`  -c hardware.cc -o hardware.o
g++ -O2 -Wall `pkg-config --cflags gtk+-2.0`  -c iosignal.cc -o iosignal.o
g++ -O2 -Wall `pkg-config --cflags gtk+-2.0`  -c main.cc -o main.o
g++ -O2 -Wall `pkg-config --cflags gtk+-2.0`  -c channel.cc -o channel.o
g++ -O2 -Wall `pkg-config --cflags gtk+-2.0`  -c iochannel.cc -o iochannel.o
g++ -O2 -Wall `pkg-config --cflags gtk+-2.0`  -c iostatistics.cc -o iostatistics.o
g++ -O2 -Wall `pkg-config --cflags gtk+-2.0`  -c socket.cc -o socket.o
g++ -O2 -Wall `pkg-config --cflags gtk+-2.0`  -c fork.cc -o fork.o
g++ -O2 -Wall `pkg-config --cflags gtk+-2.0`  -c iorecord.cc -o iorecord.o
g++ -O2 -Wall `pkg-config --cflags gtk+-2.0`  -c loadsave.cc -o loadsave.o
g++ -O2 -Wall `pkg-config --libs gtk+-2.0` -o gsopcast callbacks.o hardware.o iosignal.o main.o channel.o iochannel.o iostatistics.o socket.o fork.o iorecord.o loadsave.o

```

---

### Post by t3ddyg on 2006-10-29
Funny story - I'm dumb.  I didn't unzip sp-sc before putting it in /usr/local/bin.  Has anyone been successfull compiling gsopcast-0.2.9?  It's posted on the author's webpage: [http://lianwei3.googlepages.com/home2](http://lianwei3.googlepages.com/home2)

When I tried to use 'make' it gave a bunch of errors.  Perhaps someone with more experience could figure it out?

---

### Post by one_stinky_bum on 2006-10-30
I'm using 0.2.8 on edgy and it works fine. VLC is a great media player that works flawlessly with my setup here.

---

### Post by gmcm1979 on 2006-11-03
i have installed sopcast and i am using xine but i get the following error when trying to launch a channel with xine player

the stream [http://localost:32496](http://localost:32496) use an unsupported codec:

video codec: MS WMV9 (win32) (WMV3)

Start playback anyway?

if i click yes the audio streams ok but there is no video

---

### Post by t3ddyg on 2006-11-05
I don't know much - I'm new to linux, but are you sure you installed the proper codecs?  I would give you instructions - but like I said, I have no clue.  I just had automatix2 install the codecs for me.  
Try This:
[Ubuntu Guide Instructions]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs")

Warning: The guide says something about WMV not working right, but I know it works with Automatix2 - That's how i installed my codecs.

[Installing Automatix2 with Apt]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_Automatix2_with_Apt")

Hopefully that helps!

---

### Post by t3ddyg on 2006-11-06
My sopcast stopped working.  Perhaps sopcast underwent an update, and left the linux people behind?  Is everyone else still up and running?

---

### Post by jharbert on 2006-11-08
Try downloading the recent version of sopcast from sopcast.org.
Unzip, copy sp-cp to usr/bin/.  It worked for me at least.

---

### Post by jetpeach on 2006-11-11
unfortunately the most recent version i could get working was the command line version, and it's very unfriendly... it took time figuring out the commands and is a real pain when you are trying to find stations from the website.

i tried the most recent version with the gui, but couldn't get it to work - dependency errors.  the earlier gtk deb version worked somewhat better though, but I didn't see that many channels listed.

---

### Post by jbtito03 on 2006-11-14
Oi... works perfectly... 

Can someone tell me here to get more channels and how to import them?

Thx

JB

---

### Post by bionnaki on 2006-11-15
wow works great for me...mplayer is fine.

I just wish there were more american channels like comedy central, history channel, ABC/CBS/NBC, etc. Anyone know how to get those channels?

---

### Post by Shane11 on 2006-11-29
Using Edgy.

Sopcast can anybody help?

I downloaded the sp-sc.tgz but when I try to extract it to usr/local/bin i'm told I don't have the permissions to do it. How do I do this in a terminal?

Can anyone provide a step by step idiots guide?

Thanks
Shane (Scarborough UK).

---

### Post by Jussi01 on 2006-12-02
Yeah, Go to terminal and type
```

gksudo nautilus
```

(as long as your using ubuntu not kde)

or for kde

```
kdesu konqueror
```

this will then open a window where you are a super user. simply navicate to the folder, the go and find your extacted sp-sc file elsewhere in your pc, and drag and drop into the desired place :)

---

### Post by rado2402 on 2006-12-03
Really thanks I had a command line version but this gui is just great :D ... i wish it would be something like that for TVU player because I am NHL fan :(

---

### Post by cube3x3 on 2006-12-28
Sopcast is not working at now for me... 
Please can anyone tell whose sopcast is working...
even its website is also not loading.

---

### Post by PetePete on 2007-01-13
Thanks, works fine for me straight out hte box!

---

### Post by ubunter1 on 2007-02-10
ive put the sp-sc in the  right place now what do i do with the next file(extracted) gsopcast-0.2.10.thanks.

---

### Post by tombott on 2007-03-13
A new version of Sopcast has been released.
A updated DEB can be found [here]("http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb")

Save it, right click and 'Open with GDebi Package Installer'

Works a treat on Edgy. Will put icon in Sound & Video Menu

Regards,

Tom

---

### Post by fred_yu_job on 2007-03-13
I'm feeling so luck, just wanted to install Sopcast, and saw this newest package just posted 3 hours ago!
you'da man ! thanks!

---

### Post by max69 on 2007-03-16
Thanks a lot!! The last .deb works perfectly. Do not forget to uninstall the previous version if you had it, it did not work for me before I did. Lets enjoy the footie!!!

---

### Post by pt123 on 2007-03-17
Thanks this is great.

It's a pity TVU player has no Linux version but they have a broadcast version for Linux.

---

### Post by wildlifer on 2007-03-19
Thanks for the link! 
I tried it out in the 64bit version. Needed to download the .deb and use the following command 

sudo dpkg -i --force-architecture gtk-sopcast_0.2.8-1_i386.deb 

Works perfectly.

---

### Post by Mets on 2007-03-23
Well, it doesn't work for me.  I installed the newest version of sopcast and the newest version of the .deb.  I open up gsopcast and I see the channel list.  I double click on a channel and nothing happens.  It just says Connecting... and that's it.  I tried changing the player option to "xterm -e xine" and "xterm -e vlc" and that doesn't work either.  I hit the player button too and nothing happens.  Any ideas?  sp-sc is installed in /usr/bin

---

### Post by Mets on 2007-03-23
Nevermind, all of a sudden everything worked lol...anyway

mplayer just plays audio for me, no video.  GMplayer crashes with an "enable_cache" error.  Totem (go figure) won't play anything.  GXine plays audio but no video.  But VLC does the job just fine.

Also, if you are using VLC and the audio/video are out of sync, use ctrl+L and ctrl+K to lag the audio or video.  I needed to lag the audio by 500ms to get it to sync, but now it looks beautiful and it plays a lot smoother on Ubuntu with VLC than on windows with the sopcast player.

---

### Post by pt123 on 2007-03-24
Mets you need to have the w32codecs I think to get mplayer to play the video

--
Does gsopcast take in path parameters like the windows version.
Because I am trying to get it to open the channels from a webpage through firefox.

But it just opens gsopcast, than opening the channel.

---

### Post by zba78 on 2007-03-28
Installed the .deb file and extracted the contents of the tar.gz file. All works flawlessly. Thanks for the info & files.

BTW, I just changed the player command to **xine** and it worked fine

---

### Post by uggeli on 2007-03-30
Damn I don't get it, maybe just too stupid (same head at summers and winters :P), anyway here's what I've done so far. I copied sp-sc to /usr/bin/ and have installed that newest deb mentioned in this thread. I have Mplayer, Totem-gstreamer and VLC (all from Edgys repos).

Gsopcast seems to work ok, I get channel list but I can't get video to see no matter what. The player button at gsopcast didn't have any effect at all at first. Then I changed to config tab => Player: vlc (no any options, just plain vlc) and now Player button shoots up vlc at [http://localhost:53090](http://localhost:53090) (when trying to watch Star Sports), but no picture or sound.

If I try to record, gsopcast records an .asf file nicely. Only player managed to play it was vlc ( I have codecs installed ok ). Could someone help me please?

---

### Post by Mets on 2007-04-01
that's weird it records the asf file but you can't play it.  Try a few other players to see if they will work.

I think I actually did a restart and then everything worked, so I know that's more of a way to fix things in windows, but try a restart.

Make sure your channel URL header is sop:// and that you installed sopcast (not the deb file) to /usr/bin.  I found it works better if it's in /usr/bin instead of /usr/local/bin even though they should do the same.

---

### Post by uggeli on 2007-04-01
Thanks for tips, I will try those next time in ubuntu (not in ubuntu right now). I don't actually know what is the best way to try other players, since I don't know what extra commands I shoud use. That default didn't even launched mplayer up, so I switched it to vlc. Oh and just to explain it little clearer (I hope), I can play that recorded asf with vlc, but just can't play anything without first recording it to asf, so no "live" picture here.

What comes to that  sp-sc, I actually copied it to /usr/local/bin but when I try command "locate sp-sc" it says it's in /usr/bin.

---

### Post by Kramxel on 2007-04-04
Hi guys!
I've set up sopcast and now use it regularly with no problems. :)

The problem I have concerns TVU, i found this Linux based version, but I can't get it to run...
I'm searching for someone who can put it to work.

This is the download location:
[http://www.tvunetworks.com/download.htm?id=bdl_us](http://www.tvunetworks.com/download.htm?id=bdl_us)

Thanks

---

### Post by nottingham on 2007-04-04
Thanks for the clear instruction anyway. HOWEVER:

I am using Edgy. I extracted sp-sc to both /usr/bin and /usr/local/bin. I installed the sopcat-0.2.8 deb package successfully with a item showing up in the Sound & Video menu. 

My problem is I ran the gsopcat and saw the channel list. I double clicked at tany channels and the program said "Connecting..." and then show at the same place "  0%,ur= 0k,dr=  0k,us= 0k,ds=  0k,peers= 0". I pressed Player button and nothing happens (already tried with different players, mplayer/gxine/kaffeine, in the config tab).

Is there anyone suffering this problem? Is there anyone who could shine it up?

By the way, I did not use the file libstdc++.so.5.0.1 as my Ubuntu Edgy has libstdc++.so.5.0.7. Is it necessary to use the former file?

---

### Post by nottingham on 2007-04-05
Sorry !!! Suddenly, it starts to work nicely. Anyway, I think I have the answers.

1st: I tried the soft quite late at night. Thus, somehow now viewers (peers) was found and gsopcast did not fire up the player as no data was received.

2nd: libstdc++.so.5.0.7 in Edgy works fine.

---

### Post by pt123 on 2007-04-13
uggelli can you get mplayer to work by itself?

You need to have that working  correcty first.

Kramexel the Linux version is a server not the player

---

### Post by Buffaloed on 2007-04-25
> **tombott said:**
> A new version of Sopcast has been released.
A updated DEB can be found [here]("http://linuxtoy.org/deb/gtksopcast/gtk-sopcast_0.2.8-1_i386.deb")

Save it, right click and 'Open with GDebi Package Installer'

Works a treat on Edgy. Will put icon in Sound & Video Menu

Regards,

Tom

Thanks, that works great and installed without a hitch, :)

The only issue I'm having now is that many of the channels I prefer don't show up on the channel list so I have to launch them manually from terminal as described [here.]("http://ubuntuforums.org/showpost.php?p=2308906&postcount=8")

I mainly use it to watch sports. Does anyone know how to make it so when I click on channel links in the sop:// format in my browser (Opera or Firefox) it launches the sopcast client? You'll find lots of them listed here:
[http://www.myp2p.eu/index.htm](http://www.myp2p.eu/index.htm)

---

### Post by 71CH on 2007-04-27
Hello
I was hoping I could get some assistance.  I followed all the instructions and can get the program running but I don't hear any audio nor do I see video/video screen.  It tells me that its connecting but nothing else happens.  Can somebody please help this noob out?  Thanks.

---

### Post by rabidphage on 2007-04-29
> **Mets said:**
> 
I think I actually did a restart and then everything worked, so I know that's more of a way to fix things in windows, but try a restart.


:lolflag: 

If someone can figure out how to set the ports, a lot of problems could potentially be resolved. I cant find anything via google.

---

### Post by webbie180 on 2007-05-01
Can anyone teach me how to make a .deb version out of rpm in the download page of sopcast?  Seems like the .deb version hasnt been updated for a while.

---

### Post by javierfh on 2007-05-13
> **webbie180 said:**
> Can anyone teach me how to make a .deb version out of rpm in the download page of sopcast?  Seems like the .deb version hasnt been updated for a while.

Hello,

did you ever managed to create the ,deb version?
I have tried to use the previous one linked here in this thread, but didnt work,said that file was corrupted..
So anyone know where to get a newer .deb? or how to build it?

Thanks in advance,

Javi

---

### Post by PetePete on 2007-05-13
There is also a qt version of sopcast (qsopcast) which is much more updated and nicer/easier to use GUI.

I dont know how to make a .deb but I've compiled the source and made the executable (no idea if it will run on others PCs). You'll need to have qt libs installed and sp-sc which is gsopcast works you will already have. (you can download sp-sc from sopcast.org)

anyway attaced it the file and a screenshot.... you'll need to extract it, then run
chmod 755 qsopcast

then ./qsopcast

---

### Post by tombott on 2007-05-14
> **PetePete said:**
> There is also a qt version of sopcast (qsopcast) which is much more updated and nicer/easier to use GUI.

I dont know how to make a .deb but I've compiled the source and made the executable (no idea if it will run on others PCs). You'll need to have qt libs installed and sp-sc which is gsopcast works you will already have. (you can download sp-sc from sopcast.org)

anyway attaced it the file and a screenshot.... you'll need to extract it, then run
chmod 755 qsopcast

then ./qsopcast

That works without any problems on my PC, just extracted and ran!

Cheers

---

### Post by tombott on 2007-05-17
I've updated the link to Sopcast in my original post as the URL had moved.

It can be found [here]("http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb")

---

### Post by kleeman on 2007-05-27
If anyone wants an amd64 qsopcast deb get it here:

[http://www.yourfilelink.com/get.php?fid=336393](http://www.yourfilelink.com/get.php?fid=336393)

It is checkinstall but works very well for me....

---

### Post by snifer on 2007-06-05
You can get a newer version from [http://dengpeng.name/blog/2006/12/07/gsopcast/](http://dengpeng.name/blog/2006/12/07/gsopcast/)

---

### Post by neilbmehta on 2007-06-30
Thanks for the info....I followed the instructions and it worked great.,....just had to change the default player to vlc....

---

### Post by neilbmehta on 2007-07-01
Can anyone tell me how to uninstall my version of sopcast from ubuntu 7.04....I tried Add/Remove Programs but it doesnt show up over there.....

---

### Post by iamiso on 2007-07-01
Just a note to say THANKS for the pointer to the deb package! Awesome work especially as footballon.net is no more!

---

### Post by neilbmehta on 2007-07-06
i tried launching sopcast from the terminal and this is the problem i get....

neil@neil-desktop:~$ /usr/bin/gsopcast 
--21:59:11--  [http://www.sopcast.com/xchtml/](http://www.sopcast.com/xchtml/)
           => `-'
Resolving [www.sopcast.com](www.sopcast.com)... 124.243.201.115
Connecting to www.sopcast.com|124.243.201.115|:80... connected.
HTTP request sent, awaiting response... 404 /xchtml/
21:59:13 ERROR 404: /xchtml/.

Can anyone please help me out with this one???

---

### Post by ubunter1 on 2007-07-07
how do i get more channels? or my original channel path,i deleted it from the config while trying to put other addresses in there.thanks.

---

### Post by feasy on 2007-08-15
Hi, I have been trying to figure out how to get Sopcast running on my Ubuntu box.I have feisty

I followed all the instruction but the channels will show up and shows it buffering even up to 100% but it never bring out the mplayer.

I have checked the player configuration and all seems perfect,i have tried with the defualt mplayer and also change to Kaffeine but no luck. I will appreciate any assistance of a step by step how to get it running 
cheers

---

### Post by feasy on 2007-08-15
I figured it out
cheers

---

### Post by nowashburn on 2007-08-17
hmm... this is in a different language. i just switched to Ubuntu  and the biggest difficulty is installing programs. i think i am going to switch back to my mac. Linux isn't easy to use at all, and even though the programs are free.... they aren't that good. no wonder they are free. take this for example, there is a whole forum where people are confused on how to install a video player. weird.

---

### Post by nowashburn on 2007-08-17
forgot to mention... this didn't work. i am not a hater of Linux or any other OS. in fact, at least I have tried them all. its just Linux / Ubuntu seems way harder to do just the simplest things (like install software). and there is a 50/50 chance it wont work. so then you spend hours reading TONS of threads and if you are lucky, you get a half functional program. whats up with that? (also, the spell checker that came with Ubuntu just picked up that i spelled the word "get" wrong. If anyone else knows how to spell "get", please let me know)

---

### Post by tombott on 2007-08-18
> **nowashburn said:**
> forgot to mention... this didn't work. i am not a hater of Linux or any other OS. in fact, at least I have tried them all. its just Linux / Ubuntu seems way harder to do just the simplest things (like install software). and there is a 50/50 chance it wont work. so then you spend hours reading TONS of threads and if you are lucky, you get a half functional program. whats up with that? (also, the spell checker that came with Ubuntu just picked up that i spelled the word "get" wrong. If anyone else knows how to spell "get", please let me know)

If you actually try and explain what is not working then you may get some help.
If you want to moan about Ubuntu / Linux and installing software then this thread isn't really the place to do so.

I have just downloaded and installed the DEB in this thread and Sopcast is working without any problems.

---

### Post by m4rk6 on 2007-08-18
BUMP

how do i set what port sopcast uses?

no one? things were a lot easier with windoze, and people had answers too

---

### Post by PetePete on 2007-08-19
you shouldn't need to set a port, just run the program, click on the channel and mplayer will pop up with the stream.

I'm running it behind a router/firewall with no special settings and it goes fine.

> 
things were a lot easier with windoze, and people had answers too

Stop whining and go back to Microsoft Windows then.

---

### Post by tombott on 2007-08-20
> **PetePete said:**
> you shouldn't need to set a port, just run the program, click on the channel and mplayer will pop up with the stream.

I'm running it behind a router/firewall with no special settings and it goes fine.


Stop whining and go back to Microsoft Windows then.

Second this post, you don't need to do any port forwarding etc.
This should just work.
If it does not maybe you should look at your Router / Firewall or what your ISP may block.

I use SopCast at home, and my internet router is setup for specific port forwarding but nothing is added in for SopCast and it just works.
I can also use SopCast on my work network, and our firewall blocks pretty much everything.

---

### Post by Tom B on 2007-08-23
> **feasy said:**
> Hi, I have been trying to figure out how to get Sopcast running on my Ubuntu box.I have feisty

I followed all the instruction but the channels will show up and shows it buffering even up to 100% but it never bring out the mplayer.

I have checked the player configuration and all seems perfect,i have tried with the defualt mplayer and also change to Kaffeine but no luck. I will appreciate any assistance of a step by step how to get it running 
cheers
> **feasy said:**
> I figured it out
cheers

Would you mind sharing? I'm having the same problem.

---

### Post by ntlam on 2007-08-25
sopcast 0.2.8 works fine with my Mplayer

---

### Post by ntlam on 2007-08-25
any one knows the schedules for English, spanish and italian leagues on sopcast?

---

### Post by mikkohuo on 2007-08-26
> **ntlam said:**
> any one knows the schedules for English, spanish and italian leagues on sopcast?

[http://www.myp2p.eu](http://www.myp2p.eu)

---

### Post by ntlam on 2007-08-26
> **mikkohuo said:**
> [http://www.myp2p.eu](http://www.myp2p.eu)

Thanksssss a lot

---

### Post by tremans on 2007-09-09
> **Tom B said:**
> Would you mind sharing? I'm having the same problem.

I too am having this problem. I'm trying to run sopcast for the first time, and the status in the lower section reads that I'm getting 100% of the stream, but no video player ever launches. I tried switching config > player to simply "vlc" - with no luck. I'm sure I'm just doing something wrong that can (hopefully) be easily fixed.

Anyone have a suggestion for this new guy? :)

---

### Post by Heis on 2007-10-01
> Sport channel 1 - Sopcast (channel 887 or 20036)

Also Possible on Sky Sports 1 - Sopcast. (Channels 29703 or 29704)

To get the channels on sopcast manually try this in the server add bar:
copy a link.

sop://broker.sopcast.com:3912/ADD CHANNEL Number
sop://202.184.158.190:3912/ADD Channel Number
sop://202.71.98.173:3912/ADD Channel Number
sop://broker.100vod.com:3912/ADD Channel Number
sop://broker1.sopcast.com:3912/ADD CHANNEL Number

How can I do this with gsopcast? I can't find channel 887, 20036, 29703 or 29704.

Please help.

---

### Post by zenacim on 2007-10-02
i have the same problem

how to launch a sop://broker1.sopcast.com:3912/6029 

thx u

---

### Post by begemot1 on 2007-10-08
I have the same problem: I have 2.8 running well when I click on the channels listed in gsopcast, but I haven't been able to figure out how to add channels or to paste in links.  In another thread someone said something about pasting the sop://broker.sopcast.com:3912 etc. into the bottom box and then pressing launch, but gsopcast won't _let_ me paste anything in there (or type anything in there).

Suggestions, anyone? (for a complete n00b).

---

### Post by tombott on 2007-10-08
You cannot type into that box.

You cannot click into the box and do Ctrl-V to paste.

You have to right click on box, you will then get the option to paste

[IMG]http://freetowatchtv.co.uk/images/ubuntu/gsopcast1.png[/IMG]

Once you have pasted click on Launch.

[IMG]http://freetowatchtv.co.uk/images/ubuntu/gsopcast2.png[/IMG]

---

### Post by begemot1 on 2007-10-08
> **tombott said:**
> You cannot type into that box.

You cannot click into the box and do Ctrl-V to paste.

You have to right click on box, you will then get the option to paste

[IMG]http://freetowatchtv.co.uk/images/ubuntu/gsopcast1.png[/IMG]

Once you have pasted click on Launch.



Thank you so much for your quick reply!  But alas when I do this gsopcast quits and terminal tells me that there is a "Segmentation Fault."  What does this mean?

---

### Post by tombott on 2007-10-08
Just to add with [qsopcast]("http://ubuntuforums.org/showpost.php?p=2648111&postcount=53") you can paste into the top as shown here:

[IMG]http://freetowatchtv.co.uk/images/ubuntu/qsopcast.png[/IMG]

Tom.

---

### Post by tombott on 2007-10-08
> **begemot1 said:**
> Thank you so much for your quick reply!  But alas when I do this gsopcast quits and terminal tells me that there is a "Segmentation Fault."  What does this mean?

I am getting the same.
have just tried with qsopcast and it works fine.
Read my previous post for a link.

---

### Post by tombott on 2007-10-08
For channel links use this [site]("http://www.sopcast.com/channel/")

The Copy URL link won't work, but right click it and select Copy Link Location.

Paste this into a text editor.

You only need to paste in part of the link that starts sop://

i.e

[http://www.sopcast.com/player/index.jsp?chURL=](http://www.sopcast.com/player/index.jsp?chURL=)**sop://broker1.sopcast.com:3912/6029**&chName=Star+Sports

So you should paste something like this into Sopcast - sop://broker1.sopcast.com:3912/6029

Hope this helps.

---

### Post by begemot1 on 2007-10-08
> **tombott said:**
> I am getting the same.
have just tried with qsopcast and it works fine.
Read my previous post for a link.

Thanks, will give it a try and see if I have better luck.  Your help is much appreciated.

---

### Post by Naegling23 on 2007-10-09
hmmm, I enter the channel in qsopcast, and it just sits on waiting.  It works fine if I pick a channel that is listed though.

nevermind, bad feed, tried it again and it was fine.

---

### Post by ubunter1 on 2007-10-13
my channels don't work is it possible to uninstall then reinstall?,how can i do this?.thanks.

---

### Post by din on 2007-12-13
Hi. 
I did this steps :
Download this, untar it and place sp-sc into /usr/local/bin/ :[http://download.sopcast.org/download/sp-sc.tgz](http://download.sopcast.org/download/sp-sc.tgz)
Download the gtk-sopcast.deb and use gdebi to install it. 

After installation a have sopcast tv player in applications but its not work.
I clicking on it - nothing happens. Whats wrong? How i run it? :confused:

---

### Post by tombott on 2007-12-13
> **din said:**
> Hi. 
I did this steps :
Download this, untar it and place sp-sc into /usr/local/bin/ :[http://download.sopcast.org/download/sp-sc.tgz](http://download.sopcast.org/download/sp-sc.tgz)
Download the gtk-sopcast.deb and use gdebi to install it. 

After installation a have sopcast tv player in applications but its not work.
I clicking on it - nothing happens. Whats wrong? How i run it? :confused:

I tried following your link, but it appears to be dead.

I would download and install this [deb]("http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb")

This will put a Sopcast icon under your Sound & Video menu.

This is the current release I am using and it works without any problems.

---

### Post by din on 2007-12-13
OK. When i double click on it i have option reinstall package.
I tried simply to reinstall the package, but it still not work.

Then i tried to uninstall old gtk-sopcast_0.2.8-1_i386.deb with sudo dpkg -r * 
and install again. But still program is not running. 
Whats wrong?

---

### Post by nbayiha on 2007-12-16
Download this, untar it and place sp-sc into /usr/local/bin/ :[http://download.sopcast.org/download/sp-sc.tgz](http://download.sopcast.org/download/sp-sc.tgz)


this link is dead please can u reupload it?

---

### Post by tombott on 2007-12-16
> **nbayiha said:**
> Download this, untar it and place sp-sc into /usr/local/bin/ :[http://download.sopcast.org/download/sp-sc.tgz](http://download.sopcast.org/download/sp-sc.tgz)


this link is dead please can u reupload it?

Use this [deb]("http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb"). This works on my Gutsy PC's without any problems.

---

### Post by sirdilznik on 2007-12-16
> **tombott said:**
> Use this [deb]("http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb"). This works on my Gutsy PC's without any problems.
I don't suppose there is an amd64 version?

Edit: I tried copying the link location and looking in the parent directory.  No dice.

Edit 2:  Nevermind, solved it.  Doing: ```
sudo dpkg -i --force-architecture gtk-sopcast_0.2.8-1_i386.deb
``` did the trick.  Note on my system I had to ```
sudo apt-get install libstdc++5
``` first to satisfy a dependency.

---

### Post by tombott on 2007-12-18
This will install the latest version of Sopcast,  GSopcast GUI and the QSopcast Gui and set-up Firefox to open Sopcast Channels with Sopcast

# Get the GSopcast GUI deb file
wget [http://freetowatchtv.co.uk/images/ubuntu/gtk-sopcast_0.2.8-1_i386.deb](http://freetowatchtv.co.uk/images/ubuntu/gtk-sopcast_0.2.8-1_i386.deb)
# Install the deb
sudo dpkg -i gtk-sopcast_0.2.8-1_i386.deb
# get the newest version of sopcast
wget [http://freetowatchtv.co.uk/images/ubuntu/sp-auth.tgz](http://freetowatchtv.co.uk/images/ubuntu/sp-auth.tgz)
# extract it
tar xzf sp-auth.tgz
# move the sopcast executable to the directory where the GUI requires it to be and renaming it (the newest version from sopcast is named sp-sc-auth and not sp-sc)
sudo cp sp-auth/sp-sc-auth /usr/bin/sp-sc
# root should own the sp-sc executable - probably not required
sudo chown root:root /usr/bin/sp-sc

#Download the QSopcast GUI and Extract
wget [http://freetowatchtv.co.uk/images/ubuntu/qsopcast.tar.gz](http://freetowatchtv.co.uk/images/ubuntu/qsopcast.tar.gz)
tar xzf qsopcast.tar.gz
#Copy to /usr/bin and change ownership
sudo cp qsopcast /usr/bin/
sudo chown root:root /usr/bin/qsopcast
#Create shortcut to qsopcast
sudo gedit /usr/share/applications/qsopcast.desktop

Enter the following into the blank text document, then save and close

[Desktop Entry]
Name=QSopcast
Comment=Sopcast TV Player
Exec=/usr/bin/qsopcast
Icon=/usr/share/pixmaps/gsopcast.xpm
Terminal=false
Type=Application
Categories=Application;AudioVideo;

You should now have QSopcast and Sopcast TV Player icons under Sound & Video in your menu.

I find that QScopast is much better if you want to manually add in sopcast channels.

To get Firefox to open Sopcast links with QSopcast do the following:

Go into firefox and enter URL: "about:config".
 Right click, select new and string. 

Set string name to:
*network.protocol-handler.app.sop*

Set value to:
*qsopcast*

Now when clicking on a Sopcast url (from [http://www.myp2p.eu/]("http://www.myp2p.eu/") for example) Qsopcast should launch

If you prefer to use GSopcast follow the above steps but substitute *qscopast* with *gsopcast*

Some people will also need to install the following (If you don't already have and KDE applications installed)

sudo apt-get install qt3-apps-dev vlc build-essential

sudo apt-get install libqt3-mt

Thanks to h0me5k1n

Tom.

---

### Post by din on 2007-12-18
Hi
When i try to run qsopcast i get : 

error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

Any ideas?  :confused:

---

### Post by tombott on 2007-12-18
> **din said:**
> Hi
When i try to run qsopcast i get : 

error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

Any ideas?  :confused:

Sorry I have loads of KDE apps installed, so this is already loaded for me.

Try

sudo apt-get install libqt3-mt

Tom.

---

### Post by din on 2007-12-19
Yes> It works... thanks :)

---

### Post by rykel on 2008-01-03
> **jbodell said:**
> [http://linuxtoy.org/archives/gtk_sopcast.html]("http://linuxtoy.org/archives/gtk_sopcast.html")

There you can find the .deb for gtk-sopcast 0.1.1. 

If anyone is having any trouble:

Download this, untar it and place sp-sc into /usr/local/bin/ :[http://download.sopcast.org/download/sp-sc.tgz]("http://download.sopcast.org/download/sp-sc.tgz")



Hi,

The sp-sc file is no longer available?   :confused:

---

### Post by tombott on 2008-01-04
> **rykel said:**
> Hi,

The sp-sc file is no longer available?   :confused:

Try here - [http://download.sopcast.com/download/sp-auth.tgz](http://download.sopcast.com/download/sp-auth.tgz)

---

### Post by coffinsupply on 2008-01-09
ok what's the ssh commad to end the program?

---

### Post by jonno on 2008-01-12
> **tombott said:**
> This will install the latest version of Sopcast,  GSopcast GUI and the QSopcast Gui

# Get the GSopcast GUI deb file
wget [http://freetowatchtv.co.uk/images/ubuntu/gtk-sopcast_0.2.8-1_i386.deb](http://freetowatchtv.co.uk/images/ubuntu/gtk-sopcast_0.2.8-1_i386.deb)
# Install the deb
sudo dpkg -i gtk-sopcast_0.2.8-1_i386.deb
# get the newest version of sopcast
wget [http://freetowatchtv.co.uk/images/ubuntu/sp-auth.tgz](http://freetowatchtv.co.uk/images/ubuntu/sp-auth.tgz)
# extract it
tar xzf sp-auth.tgz
# move the sopcast executable to the directory where the GUI requires it to be and renaming it (the newest version from sopcast is named sp-sc-auth and not sp-sc)
sudo cp sp-auth/sp-sc-auth /usr/bin/sp-sc
# root should own the sp-sc executable - probably not required
sudo chown root:root /usr/bin/sp-sc

#Download the QSopcast GUI and Extract
wget [http://freetowatchtv.co.uk/images/ubuntu/qsopcast.tar.gz](http://freetowatchtv.co.uk/images/ubuntu/qsopcast.tar.gz)
tar xzf qsopcast.tar.gz
#Copy to /usr/bin and change ownership
sudo cp qsopcast /usr/bin/
sudo chown root:root /usr/bin/qsopcast
#Create shortcut to qsopcast
sudo gedit /usr/share/applications/qsopcast.desktop

Enter the following into the blank text document, then save and close

[Desktop Entry]
Name=QSopcast
Comment=Sopcast TV Player
Exec=/usr/bin/qsopcast
Icon=/usr/share/pixmaps/gsopcast.xpm
Terminal=false
Type=Application
Categories=Application;AudioVideo;

You should now have QSopcast and Sopcast TV Player icons under Sound & Video in your menu.

I find that QScopast is much better if you want to manually add in sopcast channels.

Thanks to h0me5k1n

Tom.


I followed these instructions and everything seems to be in the right place. However when I try to start sopcast or qsopcast from the launchers I get nothing. I've check and both qsopcast and sp-sc are in usr/bin but when I try to run them it tells me "no such file or directory"!!!

Am I insane? Now I am running 64bit and installed the gtk-sopcast deb using this, "sudo dpkg -i --force-architecture gtk-sopcast_0.2.8-1_i386.deb"

More specifically:
bash: /usr/bin/qsopcast: No such file or directory or
bash: /usr/bin/sp-sc: No such file or directory

---

### Post by sonofabics on 2008-01-12
Still working with gutsy :guitar:

Trick for newbies like me. configure player in config /mplayer/koffeinr/totem etc. and launch player before shopcast, 

thanks for the package

---

### Post by jonno on 2008-01-12
I just learned you gotta put this "./" in front of a script to run it. I swear I didn't need this before on my Ubuntu desktop. Anyway, Sopcast is working for me now.

---

### Post by csulok on 2008-01-18
when i select a channel from the channel list, qsopcast and gsopcast work fine, however when i paste an url like this sop://broker1.sopcast.com:3912/6274 and press launch, gsopcast throws a segmenation fault, and qsopcast does nothing but 'connecting...'

is there a way to fix this?

---

### Post by tombott on 2008-01-19
> **csulok said:**
> when i select a channel from the channel list, qsopcast and gsopcast work fine, however when i paste an url like this sop://broker1.sopcast.com:3912/6274 and press launch, gsopcast throws a segmenation fault, and qsopcast does nothing but 'connecting...'

is there a way to fix this?

I have never been able to paste links into GSopcast without it crashing out.
However when you paste a link into QSopcast you must then click on 'Launch'
Try using the following link - sop://broker.sopcast.com:3912/22508
I have used this, this morning and it has worked without any problems.

---

### Post by csulok on 2008-01-19
> **tombott said:**
> I have never been able to paste links into GSopcast without it crashing out.
However when you paste a link into QSopcast you must then click on 'Launch'
Try using the following link - sop://broker.sopcast.com:3912/22508
I have used this, this morning and it has worked without any problems.

indeed, there must have been some problem with the link i tried to play.

thanks for your reply.

---

### Post by jonno on 2008-01-21
Well I had gsopcast working for a  short while but I messed something up in the Config section and now it doesn't show anything in the channels list when I launch and also crashes immediately when I paste in a url and then click Launch.

Can someone tell me what is the url supposed to be in Channels Url in the Config page?

---

### Post by Tom B on 2008-01-21
Mine is

[http://www.sopcast.com/gchlxml](http://www.sopcast.com/gchlxml)

---

### Post by yeev on 2008-01-22
i need helpppp:(
[http://ubuntuforums.org/showthread.php?t=608175&highlight=sopcast](http://ubuntuforums.org/showthread.php?t=608175&highlight=sopcast)

---

### Post by jonno on 2008-01-22
> **Tom B said:**
> Mine is

[http://www.sopcast.com/gchlxml](http://www.sopcast.com/gchlxml)

Thanks. That got the channels back.

---

### Post by gangstamini on 2008-01-22
:KS   Great tutorial. it works right out the box. Thanks alot. 
Now to catch up on some football :popcorn:

---

### Post by tC_Crazy on 2008-01-23
Hey all, I need some help. I made an old laptop (P3 600mhz, 192mb RAM) an Xubuntu machine and now I need to run sopcast. I installed sp-sc-auth to /usr/bin, and I installed the libstdc++5 libraries. However, when I try any channel, I get this:

```
cpq@cpq-laptop:/usr/bin$ ./sp-sc-auth sop://broker.sopcast.com:3912/22508 3908 8908
detect MTU=4c4
Connection=11   Connection=11
i=0   11
ipExternal:6500a8c0  Internal:6500a8c0  portLocal:37240    portExternal1:63031    External2:63031  linkType:11
tm4.sopcast.com proto=17
adv=914
TD1=231-4294967065:  1201135253:914:2839376271
tm4.sopcast.com proto=17
adv=827
TD1=231-4294967065:  1201135253:827:2839376358
Average difference=231
231
231
3dbedaf0 28ba0b0d
Not valid ID
55186096 b0fb5605
sop://broker.sopcast.com:3912/99
system channelID=99
detect MTU=4c4
localaddr:      c0a80065:22342, externaladdr:c0a80065:22342
broker connection closed retv=-13
channel ID=22508
tk:00000000 00000000
streamID=57ec
STOP QUIT
retv = 0
        spsc_cleanup_sysch
sopch2_schedule_sc_misc_sysch retv=0
CHLST blockSize=0
2839378595:2839376594
detect MTU=4c4
Start cache thread.
retv = -108
        spsc_cleanup

```

I've tried 4-5 different channels. And these channels work well on my windows machine. 

Any ideas??

---

### Post by idiefouru on 2008-01-24
THIS IS AN AWESOME ADDITION...great!

---

### Post by tim183 on 2008-01-27
both q sopcast and sopcast tv player are working well for me, both able to buffer to 100%!

how do I get the video to stream in mplayer or vlc?

I followed the instructions and opened the player before the sopcast client.

I was not getting any response from mplayer so i tried using VLC so i changed the player name to VLC in config, but still no response. I've reset it to mplayer again now but I'm still not getting anything..... ideas?

how do I find the local host address for the sopcast client?

thanks

---

### Post by tim183 on 2008-01-27
still no luck!

---

### Post by cherry316316 on 2008-01-28
i got a problem, i watch cricket (a kinda sport if you don't know what it is) on the internet.

i get the link for this from some websites, the websites asks to open the page in 
IE, and then it run the channel inside the website, only thing needed is sopcast 
has to be installed before hand.

now , when i am in linux, the website i open is in firefox, so the firefox doesn't use the sopcast and nothing happen.

is there a way , i can get the channel from website to my sopcast
this is the website from where i get link
[http://www.niharsworld.com/2007/12/22/india-vs-australia-20072008-live-cricket-streaming-links-sopcast-links-tvu-links/](http://www.niharsworld.com/2007/12/22/india-vs-australia-20072008-live-cricket-streaming-links-sopcast-links-tvu-links/)
(channel may be off depending upon match)
but how can i use those links which says open in IE to play in linux ?

thanks

---

### Post by flebber on 2008-02-02
I must be the only person that cannot get this to work. I followed your instructions, the deb is a slightly newer version than the one you have listed installed using gdebi. Sopcast doesn't really give any errors it just freezes on the channel selection screen  everytime you choose a channel.

Because that failed I thought I would try the vlc version followed the notes in the readme from sp-auth package. But again this didn't work. 

Is this package still current and working ? My goal was to watch this [http://livefooty.doctor-serv.com/sat2.2/Tottenham_ManU.html](http://livefooty.doctor-serv.com/sat2.2/Tottenham_ManU.html)

IS there a way to get firefox to show the streams in the browser ?

---

### Post by MaindotC on 2008-02-12
> **tombott said:**
> Try using the following link - sop://broker.sopcast.com:3912/22508
I have used this, this morning and it has worked without any problems.

Just installed Gutsy and installed this via the instructions a few posts up.  Oh man it is beautiful!  Only prob is it takes up A LOT of bandwidth (can't even navigate web pages while displaying a channel) and my school's bandwidth manager caps my wireless connection :(  Still sweet.  Thank you all for your instructions and support!

---

### Post by splittter on 2008-02-14
Just tried following the guide to setup the various sopcast programmes

With sp-sc itself I can run it from the command line and then launch VLC to watch the stream, but only if i'm in /usr/bin ... otherwise i get "No such file or directory" is that normal?

With Qsopcast I'm getting similar error, it claims:

error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

Even though I've installed the libqt-mt package via synaptic, and i've browsed /usr/lib and libqt-mt.so.3 is there

Any ideas?

---

### Post by MaindotC on 2008-02-14
There was nothing in the tutorial about this but the first thing that comes to mind is permissions.  I'm actually having a majour pain issue w/ named finding my zone file - same issue but I can't figure out what the problem is.

Another suggestion regarding being in the /usr/bin directory - I think you can put it in the respective directory but beginning with a period - for example I believe there's a <program name> directory and a .<program name> directory - the latter being accessible from anywhere.  If you do ```
 ls -a 
``` I believe it will show you what I mean.  I'm in winblows right now and I don't yet know how to mount the existing partition in VMWare so I have to dual-boot (otherwise I'd check it for you).  Hope that points you in the right direction.

---

### Post by Blastomorpha on 2008-02-21
Hi guys. I succesfully managed to get sp-sc work via command line:

```
sp-sc sop://broker1.sopcast.com:3912/6029 3908 8908
```

but when i try to "catch" the stream using vlc (by opening http//:localhost:8908 or http//:localhost:8908/tv.asf etc.)  i get only the audio! Any ideas? :confused:

---

### Post by MaindotC on 2008-02-21
When you start the stream, open a command prompt and type ```
netstat -n
```  Actually, I'm not sure if it's -n (I'm in winblows right now and it's -n in winblows) but it's whatever option that will show you all connections and their associative port.

The reason I mention that is my streams usually come in a different port - 8912 I believe.  I sincerely doubt you would get anything at all on the incorrect port but just want to make sure that's correct.  And of course, if you see the connection to the sopcast link coming in on a different port you'll have to adjust vlc accordingly.

Another suggestion would be to use "add/remove software" and download all the gstreamer plugins (if you haven't already).  Let me know if you've done these already.

---

### Post by Blastomorpha on 2008-02-25
> **strAlan said:**
> When you start the stream, open a command prompt and type ```
netstat -n
```  Actually, I'm not sure if it's -n (I'm in winblows right now and it's -n in winblows) but it's whatever option that will show you all connections and their associative port.

The reason I mention that is my streams usually come in a different port - 8912 I believe.  I sincerely doubt you would get anything at all on the incorrect port but just want to make sure that's correct.  And of course, if you see the connection to the sopcast link coming in on a different port you'll have to adjust vlc accordingly.

Another suggestion would be to use "add/remove software" and download all the gstreamer plugins (if you haven't already).  Let me know if you've done these already.

Thanks for the advises, but I still have the same problem!
However, I have an old Ati 9500pro, with its drivers properly installed after a very long process about a year ago...
Maybe it's time to upgrade (not my VG :lolflag: ) from 6.06 to 7.10?

---

### Post by MaindotC on 2008-02-25
I don't like the idea of just upgrading because that doesn't really help you understand the problem, but if it comes gametime and you want it to work and don't have time to mess around disassembling code, I would advise you upgrade to 7.10.  For a long time I was angry that they took netplay out of Zsnes in 7.10 and I wouldn't budge from 7.04, but then again w/ 7.04 you had to jump through hoops to get Beryl working.  I saw someone using 7.10 with the new compiz-fusion installed and I instantly said to hell with Zsnes.

If you do, I advise you make a backup image of your current hard drive just in case you don't like Gutsy or Gutsy doesn't like your hardware.

I really don't see how it could have anything to do with Gutsy but that's probably the best a newb like me could suggest to you (which you actually suggested lol)

---

### Post by guevara on 2008-02-28
Thank you guys. I will watch now soccer. When i moved from XP i just worried it's solved cheers.

---

### Post by bash on 2008-03-04
> **tombott said:**
> This will install the latest version of Sopcast,  GSopcast GUI and the QSopcast Gui

# Get the GSopcast GUI deb file
wget [http://freetowatchtv.co.uk/images/ubuntu/gtk-sopcast_0.2.8-1_i386.deb](http://freetowatchtv.co.uk/images/ubuntu/gtk-sopcast_0.2.8-1_i386.deb)
# Install the deb
sudo dpkg -i gtk-sopcast_0.2.8-1_i386.deb
# get the newest version of sopcast
wget [http://freetowatchtv.co.uk/images/ubuntu/sp-auth.tgz](http://freetowatchtv.co.uk/images/ubuntu/sp-auth.tgz)
# extract it
tar xzf sp-auth.tgz
# move the sopcast executable to the directory where the GUI requires it to be and renaming it (the newest version from sopcast is named sp-sc-auth and not sp-sc)
sudo cp sp-auth/sp-sc-auth /usr/bin/sp-sc
# root should own the sp-sc executable - probably not required
sudo chown root:root /usr/bin/sp-sc

#Download the QSopcast GUI and Extract
wget [http://freetowatchtv.co.uk/images/ubuntu/qsopcast.tar.gz](http://freetowatchtv.co.uk/images/ubuntu/qsopcast.tar.gz)
tar xzf qsopcast.tar.gz
#Copy to /usr/bin and change ownership
sudo cp qsopcast /usr/bin/
sudo chown root:root /usr/bin/qsopcast
#Create shortcut to qsopcast
sudo gedit /usr/share/applications/qsopcast.desktop

Enter the following into the blank text document, then save and close

[Desktop Entry]
Name=QSopcast
Comment=Sopcast TV Player
Exec=/usr/bin/qsopcast
Icon=/usr/share/pixmaps/gsopcast.xpm
Terminal=false
Type=Application
Categories=Application;AudioVideo;

You should now have QSopcast and Sopcast TV Player icons under Sound & Video in your menu.

I find that QScopast is much better if you want to manually add in sopcast channels.

Thanks to h0me5k1n

Tom.

I followed this guide and it works well. Only thing is I have a 64-bit system. After a bit of searching I found the svn of gsopcast hosted over at google code (Source: [Link](http://code.google.com/p/gsopcast/) | How to compile: [Link](http://dengpeng.name/blog/2007/06/25/how-to-compile-lastest-gsopcast-via-subversion/)). So I compiled a 64bit from the latest svn. The program is now btw version 0.4 and not 0.2.x anymore. So someone with a 32bit might want to create a new .deb for that platform as well.

---

### Post by MaindotC on 2008-03-04
> **bash said:**
> I followed this guide and it works well. Only thing is I have a 64-bit system. After a bit of searching I found the svn of gsopcast hosted over at google code (Source: [Link](http://code.google.com/p/gsopcast/) | How to compile: [Link](http://dengpeng.name/blog/2007/06/25/how-to-compile-lastest-gsopcast-via-subversion/)). So I compiled a 64bit from the latest svn. The program is now btw version 0.4 and not 0.2.x anymore. So someone with a 32bit might want to create a new .deb for that platform as well.

You know just because you have a 64 bit processor doesn't mean you HAVE to install 64-bit OS.

---

### Post by skiwithpete on 2008-03-13
I get this error

```

gsopcast: sound.cc:47: Sound::Sound(): Assertion `pcm_element' failed.
Aborted (core dumped)

```


Am running a laptop Compaq X1000.

---

### Post by reality_hunter on 2008-03-16
> **tombott said:**
> This will install the latest version of Sopcast,  GSopcast GUI and the QSopcast Gui

# Get the GSopcast GUI deb file
wget [http://freetowatchtv.co.uk/images/ubuntu/gtk-sopcast_0.2.8-1_i386.deb](http://freetowatchtv.co.uk/images/ubuntu/gtk-sopcast_0.2.8-1_i386.deb)
# Install the deb
sudo dpkg -i gtk-sopcast_0.2.8-1_i386.deb
# get the newest version of sopcast
wget [http://freetowatchtv.co.uk/images/ubuntu/sp-auth.tgz](http://freetowatchtv.co.uk/images/ubuntu/sp-auth.tgz)
# extract it
tar xzf sp-auth.tgz
# move the sopcast executable to the directory where the GUI requires it to be and renaming it (the newest version from sopcast is named sp-sc-auth and not sp-sc)
sudo cp sp-auth/sp-sc-auth /usr/bin/sp-sc
# root should own the sp-sc executable - probably not required
sudo chown root:root /usr/bin/sp-sc

#Download the QSopcast GUI and Extract
wget [http://freetowatchtv.co.uk/images/ubuntu/qsopcast.tar.gz](http://freetowatchtv.co.uk/images/ubuntu/qsopcast.tar.gz)
tar xzf qsopcast.tar.gz
#Copy to /usr/bin and change ownership
sudo cp qsopcast /usr/bin/
sudo chown root:root /usr/bin/qsopcast
#Create shortcut to qsopcast
sudo gedit /usr/share/applications/qsopcast.desktop

Enter the following into the blank text document, then save and close

[Desktop Entry]
Name=QSopcast
Comment=Sopcast TV Player
Exec=/usr/bin/qsopcast
Icon=/usr/share/pixmaps/gsopcast.xpm
Terminal=false
Type=Application
Categories=Application;AudioVideo;

You should now have QSopcast and Sopcast TV Player icons under Sound & Video in your menu.

I find that QScopast is much better if you want to manually add in sopcast channels.

Thanks to h0me5k1n

Tom.

thanks for these instructions ...they work very well......only thing I change was in qsopcast -> config -> ...and change the mplayers to just "vlc"

thanks again

---

### Post by tekDragon on 2008-03-16
> **splittter said:**
> Just tried following the guide to setup the various sopcast programmes

With sp-sc itself I can run it from the command line and then launch VLC to watch the stream, but only if i'm in /usr/bin ... otherwise i get "No such file or directory" is that normal?

With Qsopcast I'm getting similar error, it claims:

error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

Even though I've installed the libqt-mt package via synaptic, and i've browsed /usr/lib and libqt-mt.so.3 is there

Any ideas?

I had the same issue, solved by following the instructions here:
[http://onlyubuntu.blogspot.com/2008/02/sopcast-with-gui-and-sop-urls-in-ubuntu.html](http://onlyubuntu.blogspot.com/2008/02/sopcast-with-gui-and-sop-urls-in-ubuntu.html)

more specifically...  this is what fixed it.

```
sudo apt-get install qt3-apps-dev vlc build-essential
```


I have everything working...  well almost eveything. When I route sopcast through VLC I get audio and video that are out of synch...  the audio is about 15 secs behind and so that's really not usable. Seems to work fine under mplayer except that some streams seem to require VLC.

Any ideas?

---

### Post by tekDragon on 2008-03-16
Actually closing vlc crashed sound altogether and forced me to restart. But I seem to be able to get most of the streams working under mplayer anyway.

---

### Post by nstamoul on 2008-03-23
> **skiwithpete said:**
> I get this error

```

gsopcast: sound.cc:47: Sound::Sound(): Assertion `pcm_element' failed.
Aborted (core dumped)

```


I second that.Any solutions?

P.S.: I am on hardy beta.Might it be that pulseaudio is messing with it?

---

### Post by bogdy72000 on 2008-03-25
i installed tor today and after that sopcast stoped  displaying the channel list. i'm sure is something about the way applications connect to the internet now. i tried reinstalling and no success. pages in opera could not be displayed after installing tor. after I reinstalled opera and figuring out that all I had to do was to turn of the proxy.  I googled for a fix for this for about the whole day today, and I'm fed up. There must be someone who know a lot more than I do and can help.tanks in advance.i really like the wAy sopcast works on ubuntu gutsy, but now i'm left with tor and :popcorn:

---

### Post by tekDragon on 2008-03-26
Is there anyway to get the video controls to appear when qsopcast launches mplayer?

---

### Post by mocha on 2008-03-27
> **bogdy72000 said:**
> i installed tor today and after that sopcast stoped  displaying the channel list. i'm sure is something about the way applications connect to the internet now. i tried reinstalling and no success. pages in opera could not be displayed after installing tor. after I reinstalled opera and figuring out that all I had to do was to turn of the proxy.  I googled for a fix for this for about the whole day today, and I'm fed up. There must be someone who know a lot more than I do and can help.tanks in advance.i really like the wAy sopcast works on ubuntu gutsy, but now i'm left with tor and :popcorn:

You need to look into Vidalia to control how Tor works easily.

---

### Post by tombott on 2008-03-29
> **tekDragon said:**
> Is there anyway to get the video controls to appear when qsopcast launches mplayer?

Get it to use VLC instead mate.
Go into QSopcast - Config - Config
And change all mplayer to vlc
I also take out all the switches.

i.e

Replace - mplayer -ontop -geometry 100%:100%
with - vlc

Tom

---

### Post by tombott on 2008-03-29
> **bogdy72000 said:**
> i installed tor today and after that sopcast stoped  displaying the channel list. i'm sure is something about the way applications connect to the internet now. i tried reinstalling and no success. pages in opera could not be displayed after installing tor. after I reinstalled opera and figuring out that all I had to do was to turn of the proxy.  I googled for a fix for this for about the whole day today, and I'm fed up. There must be someone who know a lot more than I do and can help.tanks in advance.i really like the wAy sopcast works on ubuntu gutsy, but now i'm left with tor and :popcorn:

Check that under Config the Channel URL is set to - [http://www.sopcast.com/gchlxml](http://www.sopcast.com/gchlxml)

I have just installed Sopcast and QSopcast on a new PC following my instructions and the channel lists are showing in Sopcast and QSopcast without any problems.

---

### Post by tombott on 2008-03-29
To get Firefox to open Sopcast links with QSopcast do the following:

Go into firefox and enter URL: "about:config".
 Right click, select new and string. 

Set string name to:
*network.protocol-handler.app.sop*

Set value to:
*qsopcast*

Now when clicking on a Sopcast url (from [http://www.myp2p.eu/]("http://www.myp2p.eu/") for example) Qsopcast should launch

If you prefer to use GSopcast follow the above steps but substitute *qscopast* with *gsopcast*

I have edited my original instructions to reflect these changes.

---

### Post by mocha on 2008-03-29
> **tombott said:**
> To get Firefox to open Sopcast links with QSopcast do the following:

Go into firefox and enter URL: "about:config".
 Right click, select new and string. 

Set string name to:
*network.protocol-handler.app.sop*

Set value to:
*qsopcast*

Now when clicking on a Sopcast url (from [http://www.myp2p.eu/]("http://www.myp2p.eu/") for example) Qsopcast should launch


This is weird, I have a gutsy box that this procedure works on, I click a sop link and qsopcast opens and has the link in its address bar.  On my Feisty box however, the qsopcast program opens but the link doesn't appear in the qsopcast address bar.  Any ideas what might be wrong?  I'm using the same versions of sopcast on both machines.

EDIT:  Never mind.  I had an older version of qsopcast on the Feisty box, installed the newer one with URL handling and all is fine.

---

### Post by RamR on 2008-03-30
This looks very promising.  However, I have a small problem.  It is with direct linking the program to sopcast internet links.  When a link to a sopcast stream is clicked the program begins but nothing happens.

Thanks in advance for any assistance.

---

### Post by mocha on 2008-03-30
> **RamR said:**
> This looks very promising.  However, I have a small problem.  It is with direct linking the program to sopcast internet links.  When a link to a sopcast stream is clicked the program begins but nothing happens.

Thanks in advance for any assistance.

This is exactly the same problem I had in the post before yours.  You are using the wrong version of qsopcast, you are supposed to use the version with URL handling, I attached it here.

---

### Post by Stonekeeper on 2008-04-20
I put together a package for sopcast and soplaunch. It's for gutsy and was built using nixstaller. Hope it's useful for someone.

[http://www.megaupload.com/?d=B6XQ3G6J](http://www.megaupload.com/?d=B6XQ3G6J)

---

### Post by johnmc on 2008-04-22
> **RamR said:**
> This looks very promising.  However, I have a small problem.  It is with direct linking the program to sopcast internet links.  When a link to a sopcast stream is clicked the program begins but nothing happens.

Thanks in advance for any assistance.

got the same problem - only with gsopcast, not qsopcast.
Any idea where the problem is?

---

### Post by mocha on 2008-04-30
After upgrading to Hardy, the sopcast URLs no longer opened up qsopcast from Firefox 3.  In order to get it to work again you have to type in "about:config", change the "network.protocol-handler.warn-external.sop" to "true".  Then go to a webpage that has a sop URL, click it, a dialog box should popup asking what app you want to open the URL with.  Navigate to /usr/local/bin and select qsopcast, also check the box to "make this a bookmark" or whatever it said (I don't remember now).  And that should do it.  Now if you go to Edit - Preferences - Applications, you will see a content type "sop" with the action "use qsopcast".  :popcorn:

---

### Post by filthy on 2008-05-05
Please excuse me being a complete noob. I have been trying to copy the file in post 141 into /usr/local/bin but I keep getting the same response that I cannot do it as I dont have permission. I get this even when I use terminal for nautilus. I am quite inexperienced inlinux and would really appreciate an idiots guide to installing the sopcast programme. I am using Hardy Heron and I am finding it generally simple to use but this is evading me. Please help me so my linux experience isnt soured. I would love to leave windows behind.

---

### Post by tombott on 2008-05-05
If you follow this [post]("http://ubuntuforums.org/showpost.php?p=3972826&postcount=94") you should not have any problems installing Sopcast.
Let me know how you get on.

---

