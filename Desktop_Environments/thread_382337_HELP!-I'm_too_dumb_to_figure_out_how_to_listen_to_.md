---
title: "HELP!-I'm too dumb to figure out how to listen to streaming audio."
date: 2007-03-11
forum: Desktop Environments
---

### Post by hodad on 2007-03-11
After six months of trying to simply listen to news online, and trying endlessly to follow advice on this site to get something to work, I can only get one or two sites to work, and only if they have a mp3 formatted file for me to download.

I have installed countless programs through Synaptic, apt-get, etc., including Java, RealPLayer 10 Gold, etc. etc., etc.  hese programs have all installed correctly, but none do anything as far as I can tell. Literally weeks of time wasted.  Can anybody suggest a site that explains what the plethora of file formats, file extensions, and programs that I come across in this forum actually do and how they work?  I get snippets here, snippets there, and nothing makes sense.  The guidance given in the forum typically gets me 95% there (even though I don't have a clue what the helper is talking about), but never actually gets any kind of audio working for me at any sites. I guess the typical way to solve this is to keep trying to download reams of programs, repositories, plugins, and whatever else I don't understand until something works, but THERES GOT TO BE A BETTER WAY!  NO SITE that I have visited takes the time to explain what's going on with various media , players, plugins, etc. etc.    They all seem to assume you already know what is going on before explaining it to you (Catch 22 , anyone?).  

I don't need any advice on how to get any of these programs to work, because I have given up in frustration, and know nothing will work.  I  want to start at the beginning and learn how downloading and playing audio works, and perhaps have a basis for how to start going about getting something to work, so I'm not forced to go back to Windows.

Sorry about venting my frustration, I realize that I'm only showing my ignorance. 

 Any help in understanding how to go about getting "streaming audio" or "podcasts" to work would be GREATLY appreciated!!](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by x64Jimbo on 2007-03-11
Ok, so when you download a streaming audio file, you're actually only downloading a file that contains the IP/URL of a streaming audio server, and a specific stream for the player to request. When you open that file, it follows those instructions. Which sites are you trying to access, what formats are they using, and what player are you using to play them?

---

### Post by techstop on 2007-03-11
I don't listen to podcasts, but when you listen to streaming audio (eg. internet radio stations), find the actual server and port number and play that, I don't think Linux handles the .pls files very well. For example, my ISP has this radio station listed;

[http://radio.internode.on.net:8012/listen.pls](http://radio.internode.on.net:8012/listen.pls)

But, to get it working in ubuntu, I need to play the following location;

[http://radio.internode.on.net:8012](http://radio.internode.on.net:8012)

Sometimes the port isn't listed directly, so you need to open the .pls file in a text editor to find the actual server location and port number. eg.

[http://somafm.com/beatblender.pls](http://somafm.com/beatblender.pls)

...open the playlist file to find;

```
[playlist]
numberofentries=3
File1=http://207.200.96.232:8006
Title1=(#1) SomaFM: Beat Blender (128k mp3): A late night blend of deep-house and downtempo chill.
Length1=-1
File2=http://204.15.0.150:80
Title2=(#2) SomaFM: Beat Blender (128k mp3): A late night blend of deep-house and downtempo chill.
Length2=-1
File3=http://204.15.0.150:8388
Title3=(#3) SomaFM: Beat Blender (128k mp3): A late night blend of deep-house and downtempo chill.
Length3=-1
Version=2

```

...so then you could play this location;

[http://207.200.96.232:8006](http://207.200.96.232:8006)

...etc.

I use streamtuner to organise internet radio stations, and rhythmbox also works great. They are both in the ubuntu repos. Also, you might want to make sure all your codecs are installed. Here are some good pages to look at;

[https://help.ubuntu.com/community/Multimedia](https://help.ubuntu.com/community/Multimedia)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/MultimediaApplications](https://help.ubuntu.com/community/MultimediaApplications)

HTH.

EDIT: rhythmbox does podcasts as well!

---

### Post by hodad on 2007-03-11
Thanks for the replies!

I have a bookmark for "PublicRadioFan.com".  Whenever I click on a site, I typically get a webpage that doesn't do anything, or I'll get a green puzzle piece and some kind of message like " need plugin".  Or I will get "Totem" , and it ALWAYS has a message like "Can't play this file format" (never has done anything else).   I've lost count of the number of times, and ways, I have tried to download these "plugins", and, of course, it never works.  Occasionally, if I look hard enough, I find a broadcast listed with an ".mp3" extension, and they play just fine over my pc speakers.  

I have Mplayer, Totem, Real PLayer 10, Java, and a few more things installed.   Perhaps tommorrow, I'll try some of the things  that you have listed.  Thanks for taking the time to help.  I'll try some of the suggestions tommorrow, as I'm starting to fall asleep                ..zzzzzzzzzzz

---

### Post by techstop on 2007-03-12
> **hodad said:**
> Thanks for the replies!

I have a bookmark for "PublicRadioFan.com".  Whenever I click on a site, I typically get a webpage that doesn't do anything, or I'll get a green puzzle piece and some kind of message like " need plugin".  Or I will get "Totem" , and it ALWAYS has a message like "Can't play this file format" (never has done anything else).   I've lost count of the number of times, and ways, I have tried to download these "plugins", and, of course, it never works.  Occasionally, if I look hard enough, I find a broadcast listed with an ".mp3" extension, and they play just fine over my pc speakers.  

I have Mplayer, Totem, Real PLayer 10, Java, and a few more things installed.   Perhaps tommorrow, I'll try some of the things  that you have listed.  Thanks for taking the time to help.  I'll try some of the suggestions tommorrow, as I'm starting to fall asleep                ..zzzzzzzzzzz

OK, well have you tried what I said above? You need to get the server and port number, not the .pls file. I'll spell it out...

For the second link on the publicradiofan.com page at the moment (KGOU), this is the address it links to;

[http://publicradiofan.com/cgi/wrap.pl?s=mms://media1.levanttech.net/kgou](http://publicradiofan.com/cgi/wrap.pl?s=mms://media1.levanttech.net/kgou)

Change that to this in firefox;

mms://media1.levanttech.net/kgou
 and press enter. You will get a prompt about launching an external application, and presto!!!

For the fourth link on the page (WCAI), this is the address it links to;

[http://streams.wgbh.org/wnan.pls](http://streams.wgbh.org/wnan.pls)

Save that file and have a look inside, you will see this;

```
[playlist]
File1=http://64.71.145.107:8002
Title1=WCAI / WNAN Cape and Islands
Length1=-1
NumberOfEntries=1
Version=2
```

Therefore, you will need to play this location in your favourite music player;

[http://64.71.145.107:8002](http://64.71.145.107:8002)

See? I don't know if there is an easier way, but this works for me, and any stations I regularly listen to I just bookmark in streamtuner.

---

### Post by hodad on 2007-03-13
techstop,

Your method actually worked!!!!!!  I'm not surprised that I couldn't figure it out before now.  Why does it need to be so difficult? I still think there must be an app out there that allows you simply to click on a "podcast icon" and just start playing (What a concept!).  I must still be missing something (my brain, perhaps).

I will look at the other links that you listed to try and educate myself; seems like a bewildering array of terminology to wade through to do something so simple.  I'm still waiting for the day when I can turn on a computer and have it work for me rather than the other way around; I guess I'll pass along that dream to my grandchildren.

For now, however, you gave me the ability to listen finally!  Thanks a Heap!

---

### Post by tgalati4 on 2007-03-14
iTunes on a Mac handles podcasts pretty well.  Integrates with the iPod as well.  Multimedia is a little tedious under Linux, but once you get the proper tools and scripts, it works well.

Bashpodder is great for filling your disks with podcasts that you won't have time to listen to.  Xmms is a simple yet expandable media player with all sorts of plug-ins except speed-up.  I have yet to find a podcast plug-in that will speed up playback by 30%.  You can transcode or bring into an audio editor (now we're talking WAV file) but no simple, audiobook fast player.

It's a changing landscape.  If you don't have the patience for Linux than try a Mac.  If you think you have the patience, then the community can help you find a solution that works for you.

Good luck.

---

### Post by techstop on 2007-03-14
> **hodad said:**
> techstop,

Your method actually worked!!!!!!  I'm not surprised that I couldn't figure it out before now.  Why does it need to be so difficult? I still think there must be an app out there that allows you simply to click on a "podcast icon" and just start playing (What a concept!).  I must still be missing something (my brain, perhaps).

I will look at the other links that you listed to try and educate myself; seems like a bewildering array of terminology to wade through to do something so simple.  I'm still waiting for the day when I can turn on a computer and have it work for me rather than the other way around; I guess I'll pass along that dream to my grandchildren.

For now, however, you gave me the ability to listen finally!  Thanks a Heap!

No worries, it took me a little while to figure out....I just add all my favourite stations to streamtuner and go from there. If you want to organise podcasts, please have a look at ryhthmbox. They are both in the ubuntu repos (rb is installed by default I think).

---

### Post by Daniel15 on 2007-03-15
Speaking of streaming audio, can anyone help me with my problem? I'm trying to listen to Fox FM ([http://www.fox.com.au/listen)](http://www.fox.com.au/listen)), and while it's working in Totem, the visualisations are taking 100% CPU usage (and besides, I really hate Totem, it doesn't work that well for me :P). Is there another player that will play this stream? (It seems that it won't play in VLC...)

Their site has a fox.asx file, with the following contents:
```

<ASX version="3.0">
   <Entry>
      <ref HREF="mms://66.70.119.243/FoxFM"/>
      <ref HREF="rtsp://66.70.119.243/FoxFM"/>
      <ref HREF="http://66.70.119.243:81/FoxFM"/>
   </Entry>
</ASX>

```

Thanks! :)

---

### Post by hodad on 2007-03-24
techstop-
Sorry, been out of town the past week...  

Thanks for the advice.  I installed streamtuner, and it worked right away with some of the url's they provided (the ones with .ogg and .mp3 suffixes). Some of the urls didn't work (the ones with locations and no mp3 or ogg suffixes).  I tried "cutting and pasting" some things I wanted to listen to, but it didn't work.  I'll have to figure out how to enter new "stations" to listen to.  

Tried Rhythmbox.  Tried "cutting and pasting" the url as mentioned before, but it didn't like it (can't recall the exact error message, but it couldn't recognize what I pasted).


Guess I'll go thru your earlier postings again, and try to figure out the "pointers" to other locations, and all of the various formats.

I may get back to you if I have any more Qs.

Once again, Thanks.

---

### Post by mgmiller on 2007-03-25
Look for a Firefox extension called MediaPlayerConnectivity.  It will give you a configure option in the tools menu of Firefox that lets you set any player for any kind of stream.

---

