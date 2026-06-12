---
title: "Flash + Jaunty + Hulu = Problems"
date: 2009-06-03
forum: General Help
---

### Post by Shr00mSter on 2009-06-03
I have 2 systems runing 9.04. One version installed is a x64 version and the other version installed is a netbook remix 9.04.

I have the x64 version of Flash 10 libflashplayer.so in my home/.mozilla directory and firefox is reporting v10.0 r22. I can play YouTube videos fine. (Another guy with the exact same system as mine running the exact same version of Ubuntu in my office is having the exact same problem). This box has an Nvidia card running proprietary drivers v180.

I also have the netbook remix (x32) installed on a acer 1000he with the adobe-flashplugin 10.0.22.87-2jaunty1 version installed through synaptic package manager. Firefox also reports v10.0 r22.

BOTH instances of the ubuntu fail to load Hulu videos. I can go to hulu.com and pick a video and it says Loading and sits there. After a LONG while I either get an error saying that a script in the movie is making adobe take a long time to load or I get the commerical to play but nothing else.

I've followed this post to get my intel 945gm vga working better on the netbook:
[http://ubuntuforums.org/showthread.php?t=1130582&highlight=i915+jaunty](http://ubuntuforums.org/showthread.php?t=1130582&highlight=i915+jaunty)

And I've also tried the following to remove all packages associated with flash:
$ sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree adobe-flashplugin
$ sudo apt-get install adobe-flashplugin

Of course, on the x64 box I had to substitute the adobe-flashplugin install and just copy the libflashplayer.so file back into my home directory.

Is this something I've done wrong on both machines or is this a bug?
Thanks for your help.

---

### Post by tekkitan on 2009-06-04
I am having this EXACT same issue myself. Running Ubuntu 9.04. Every other flash site works such as YouTube, Anime stream sites, etc. The only thing that does not work for me is Hulu. It will say "Loading" then firefox will freeze, turning the screen grey. After a while, it will load the intro commerical, then go back to "Loading" to start loading the show/movie. Then it will freeze up again. After a while, it will come back and say that the video took too long to load.

I have tried numerous suggestions found on these forums to uninstall and reinstall flash, same thing happens. I've tried downloading the flash package from Adobe, tried the nonfree package in apt, etc etc. I have no other 3rd party flash players installed, this is a fresh install of Ubuntu. 

I had no problems with Hulu in 8.10 (even in x64) on this same computer.

---

### Post by Shr00mSter on 2009-06-04
Just an addition to this problem (for searching),
Boxee does the same thing for Hulu video's. Obviously because it uses mozilla to play them.

---

### Post by Shr00mSter on 2009-06-08
> **Shr00mSter said:**
> Just an addition to this problem (for searching),
Boxee does the same thing for Hulu video's. Obviously because it uses mozilla to play them.

Can anyone else verify this besides myself and Tekkitan? Just wondering if it is a bug or not.

Thanks.

---

### Post by daxdog on 2009-06-08
I am running Kubuntu 9.04 on a Dell XPS M1330 using an Nvidia video card.  I can watch Hulu videos in a window, but when I try to watch it full screen Mozilla totally locks up.  I have to reboot to get it working again.

---

### Post by Therion on 2009-06-08
I've had this same exact issue a FEW times.  

What worked for me was, AFTER installing the Abobe plugin, going into Synaptic and searching on "SWF" (no quote marks obviously).

If Synaptic comes back showing you have a package installed by the name of (and I'm going by memory here) **swf-mozilla-plugin** *...  Mark that package for removal* and go back and try Hulu again after removing it.  Worked for me.

---

### Post by tekkitan on 2009-06-08
> **daxdog said:**
> I am running Kubuntu 9.04 on a Dell XPS M1330 using an Nvidia video card.  I can watch Hulu videos in a window, but when I try to watch it full screen Mozilla totally locks up.  I have to reboot to get it working again.

There is another thread on your problem I believe. We can't watch hulu in window or full screen. 

There does not seem to be any packages matching "swf", looked at all packages relating to mozilla and firefox as well with no luck.

Unfortunately Shr00mSter and myself seem to be the only ones having this problem? I have not found anything else on it by searching here and Google. Very frustrating.

---

### Post by iiyohnewb on 2009-06-08
idk if anyone mentioned this before but i got it to work, using this thing 

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) on the forums just, unlock your accoutn so it can change root stuff under user and groups

and then do this in the terminal

[B]sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar


it worked for me and now i can use hulu on fullscreen and anything and whatnot
[/B]

---

### Post by tekkitan on 2009-06-11
> **iiyohnewb said:**
> idk if anyone mentioned this before but i got it to work, using this thing 

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) on the forums just, unlock your accoutn so it can change root stuff under user and groups

and then do this in the terminal

[B]sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar


it worked for me and now i can use hulu on fullscreen and anything and whatnot
[/B]

Didn't have any of the packages it wanted to remove installed. Also no package named non-free-codecs. I am trying this on 8.10 as well and it is still freezing, so it isn't a Jaunty only thing. 

Let me reiterate that we can't watch Hulu at all, it does not work in regular browser size or full screen. It freezes firefox then the video times out.

---

### Post by tekkitan on 2009-06-15
I find it hard to believe that only two people are having this problem on multiple computers. Unless we are missing something completely obvious :-)

---

### Post by tekkitan on 2009-06-19
Okay I think I found the issue! It isn't Linux, and it isn't Flash. It isn't Hulu (well, not a "problem", just the way they do things).

Apparently Hulu isn't the normal Flash site. When trying to access Hulu here at work, in the firewall logs I am seeing RTMP (tcp/1935) being dropped. This is the Real Time Messaging Protocol which is used (primarily by Adobe) to stream audio/video over the internet. More info at the link below:

[http://en.wikipedia.org/wiki/Real_Time_Messaging_Protocol](http://en.wikipedia.org/wiki/Real_Time_Messaging_Protocol)

The answer? Open this port (tcp/1935) in your firewall. If you are in a corporate environment, this may not be possible.

---

### Post by Chronon on 2009-06-19
I have Jaunty on my desktop system and on my netbook (UNR).  Hulu plays just fine on my netbook.  It plays, but with no sound on my desktop machine.  All other flash sites work fine on both machines.

Strangely, if I click through to "Collections" those videos all play fine with sound on my desktop machine as well.  Recently, I briefly (for about a week) had sound working on my desktop machine on other areas of the site.  It also worked when I first installed Ubuntu last summer.  

-- 
tekkitan: Interesting find.  I wonder how this fits with my observations.  My netbook has no problems when connecting through my home network.

---

### Post by jwm93k on 2009-07-13
Hello,
13 July 2009, Loading Ubunty UNR on Asus EEE 901. Main reason is that the Wireless on Xandros was very slow.   Now the wireless on UNR is  as fast as the wired LAN, but I can not run HULU. It first complains I need Flash 9.xxxx. If I use the "install needed drivers" in the pop upwindow, the pluggis are loaded and then I don't get the complaining, but I don't get any video on Hulu. I tried loading Flash 10 to no avail. I tried unloading and reloading Flash plugings. I'm stuck. Yes others have the same problem.

---

### Post by Fire-Eyes on 2009-07-17
I just got an Acer netbook
loaded the netbook version of Ubuntu
now I have no audio, no flash, no Hulu
any help would rock
thank you

---

### Post by Fire-Eyes on 2009-07-17
ok...update
I have audio now
I installed Gstream (I think that was what it was called)

but still no HULU

---

### Post by mjstelly on 2009-07-17
> **Shr00mSter said:**
> Can anyone else verify this besides myself and Tekkitan? Just wondering if it is a bug or not.

Thanks.

I'm a n00b to Ubuntu, so I cannot validate whether or not this issue is a bug. I can tell my experience to date, though. I use Facebook, which depends heavily on Flash, every day. On my Gnome setup, I have the CPU monitor located on my top  panel so I can quickly determine the source of the egregious lag I've been experiencing.

First, I thought it was a memory issue, so I added a gig for a total of 1.5GB. That helped overall performance somewhat, but not for Facebook. I can make the CPU spike to 100% merely by clicking links, typing in a textbox and even scrolling the mouse wheel. I didn't believe what I saw. I've never seen anything like this before. When I stopped input, usage dropped back down below 10%.

I read this thread just now and thought I'd see if I could replicate the problem. I went to hulu and selected a video. It started to play, then about 10 seconds later the entire browser froze completely. I had to force quit to exit.

I, too, have tried many suggestions found on this forum and elsewhere. To be quite honest, I'm sick of trying. I no longer have the patience to figure it out like I did 10 years ago with earlier versions of Linux. Ubuntu prides itself on being the OS the "just works." I didn't see any subtext that said, "...for everyone except you." :confused:

So, Ubuntu demigods, should I fall back to the last release of version 8?

I'd really appreciate a response that makes my version "just work."

Thanks.

Update: Hoped that the issue would be Firefox or a Firefox/Flash problem. Wrongo! The same problem occurs with Opera 9.64. I surmise then that it is definitely a Jaunty/Flash bug. Still wondering if I should downgrade to version 8.

Update: I performed a clean install with 8.04, went to youtube, and ran a video. I then watched the cpu rocket straight to 100% and remain there until immediately after the video ended. It then plummeted to below 10%. I'm going to perform the same test with browsers other than firefox. Hopefully, I'll see some improvement.

Final update: I found the definitive word from Adobe about the problem. Follow this link 
**[Linux Flash web streaming fullscreen video consumes too much CPU, tears and drops frames ]("http://bugs.adobe.com/jira/browse/FP-1692")**

No workaround is known.

---

### Post by mjstelly on 2009-07-21
> **tekkitan said:**
> Okay I think I found the issue! It isn't Linux, and it isn't Flash. It isn't Hulu (well, not a "problem", just the way they do things).

Apparently Hulu isn't the normal Flash site. When trying to access Hulu here at work, in the firewall logs I am seeing RTMP (tcp/1935) being dropped. This is the Real Time Messaging Protocol which is used (primarily by Adobe) to stream audio/video over the internet. More info at the link below:

[http://en.wikipedia.org/wiki/Real_Time_Messaging_Protocol](http://en.wikipedia.org/wiki/Real_Time_Messaging_Protocol)

The answer? Open this port (tcp/1935) in your firewall. If you are in a corporate environment, this may not be possible.

If you get that "script not working" error message on hulu, then yes, your network admin has that port blocked. Trust me, there's no chance that they will open it. Try to explain why you want to watch hulu at work. :)

However, the jaunty + flash problem is real nonetheless.

---

### Post by jwm93k on 2009-07-23
Greetings.
Every load of 9.04 I have done had this problem. One, or two of these things always seems to work for me. Downloading the deb of Flash 10 has never worked for me. I can't remember the exact name, but there is a synaptic load for "ubuntu restricted" files bundled into one package. It has stuff for MP3 and other formats. Then in symantic I select all the swf_xxx (flash) files, (about 2 to 4 packages)and fully uninstall them. Reboot and reinstall these same exact packages and magic it works. The only thing I can figure is the Flash install with 9.04 is either messed up or loads old flash files. Now My desktop and ASUS 901 Netbook can run Hulu and Pandora well. Also since I moved from the default Asus 901 Xandros to UNR my network hookup and speed is much faster. I had to load atomic tanks from synaptic because add/remove did not list it on my Asus 901. If I try to make a movie with my built-in wedcam the system will crash. That is a pain, but I don't make many movies. The Asus 901 with UNR also connected well to my windows system and share drives and connected to my phone thru bluetooth well. The bluetooth headset connected but I had no sound.  Happy Trails.:)

---

### Post by sharrah on 2009-08-27
to get flash and sound working:
```

sudo apt-get flashplugin-nonfree ubuntu-restricted-extras
```

I also had the same problem with hulu. I fixed it using the following: 

```
sudo apt-get purge swfdec-mozilla libswfdec-0.8-0
```

Also, make sure you only have adobe flash plugin installed. This means no gstreamer plugin, no sfwplayer, etc.

Hope this helps.

---

### Post by Fire-Eyes on 2009-08-28
I tried it all
it dose not work
so I went to Linux Mint Gloria
guess what it worked
Now, what I want to know is why is an OS based on Ubuntu working and Ubuntu not work? I know this sounds cheesy but I feel like I have been betrayed by a friend.

---

### Post by oldos2er on 2009-08-28
Using the latest 64-bit Flash works. [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)

---

### Post by fballem on 2009-10-04
Can someone please give me specific instructions on how to open port 1935?
I'm running Karmic at the moment.

---

