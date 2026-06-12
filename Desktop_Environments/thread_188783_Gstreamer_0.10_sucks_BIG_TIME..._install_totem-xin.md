---
title: "Gstreamer 0.10 sucks BIG TIME... install totem-xine instead"
date: 2006-06-04
forum: Desktop Environments
---

### Post by ThirdWorld on 2006-06-04
I upgrade Dapper from brezy few days ago, the new gstreamer 0.10 is the same thing as gstreamer 0.08, it wont play .wma and other restricted formats correctly even if you have all the codecs. When it does play some files you cant resize them, or what is more odd it pick and choose wich .wma file to play. ](*,) 

I had to install totem-xine in synaptic so totem can play media again. I guess this new version of gstreamer is an improvement, but that does not mean that is useful. if you are having this problem install the totem-xine engine in synaptic.

then, go to system -> administration -> software properties 

in software properties click on the "add" tab -> custom ->

add this in URI:

[ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

close it go to synaptic and search for w2codecs, install them and you will be able to play all the formats that you want. 

It works for me.  :mrgreen:

---

### Post by shamrock_uk on 2006-06-04
It's funny you say that, and I'd traditionally be the first to put the boot into Gstreamer, but I'm exceptionally pleased with the later versions of 0.10. 

I actually find that I'm getting *better* performance (in terms of smooth playback) with totem and gstreamer than I do with xine and w32codecs - it's come a heck of a long way since Breezy IMO. I never really need to switch to xine/Mplayer these days - it even handles .wmv files fine for me. The only thing that still annoys me with Totem is when the fullscreen menu bar doesn't fade out.

Ah well, just goes to show how different computers are!

---

### Post by ThirdWorld on 2006-06-04
did you did a clean istall or an upgrade? maybe that was my problem

---

### Post by jamesford on 2006-06-04
totem gstreamer doesent play wmv for me either, but otherwise it works way better than in breezy. gxine for wmvs and totem for the rest works for me, oh an vlc/mplayer for those really obscure things

---

### Post by shrift on 2006-06-04
My totem won't play DVDs with the gstreamer version.... Switch to the xine version and it's all good. Sad. I do have libdvdcss2 installed, before anyone even asks.

---

### Post by Lord Illidan on 2006-06-04
I prefer **Xine.  **It works. Nuff said.

---

### Post by Kmantis on 2006-06-04
I agree with shamrock_uk in that GStreamer has been great since the 0.10 release. It plays just about everything now, except for the more exotic formats like Realvideo. 

That said, I still use VLC player for all my divx/xvid needs. Altough totem & gstreamer can open and play avi's using those codecs, the playback is a bit choppy when compared to VLC. When using totem, it seems that every 2-5 seconds, a few frames are dropped. VLC doesn't do that.. plays movies a lot smoother.

---

### Post by hanzomon4 on 2006-06-04
gst10 plays most video files fine 

but it freezes on wm8 files when I try to scroll or fast foward

I read some where that gst can't play DVD

---

### Post by disturbed1 on 2006-06-04
Gstreamer works just fine for me. Ogg music files, Xvid/ogg video files, Theora video, quicktime video, mpeg1/2 video.

But I do think Totem sucks :mrgreen: So I use VLC to playback all videos.

---

### Post by speedsix on 2006-06-21
I had to bump this because I think gstreamer is lousy. It failed to play lots of files that xine/mplayer can and it won't play dvd's either. Rubbish.

Yes I have all the gstreamer plugins installed.


How the hell do you tell it to use a different codec? It won't play files that I KNOW ffmpeg handles even though it is installed. Totem-gstreamer has absolutely zero options to control gstreamer.

](*,)

---

### Post by H.E. Pennypacker on 2006-07-08
I am glad I dumped Gstreamer.  I was having so many problems with it, it was unbelievable.  I can now play videos (finally!) without any hassles!

---

### Post by jimbo2150 on 2006-07-13
I will agree with some points and dissagree with others.

For one thing, compared to .8 version, .10 is a huge leap forward.

The only major problems I see still with GStreamer is:
1. Lack of exotic codec support. Many WMVs will play... without video.
2. Lack of speed: While faster than .8, the video playback is still choppy (especially when playing higher-resolution videos) as compared to xine.

It isn't a total loss, but I would still reccomment running on xine, mplayer and or vlc untill either one or all can play more formats.

---

### Post by Sweezel on 2006-07-13
Am I reading right? That the default player in Ubuntu doesn't work correctly?

**Is anyone asking for something that is not advertised as available in Ubuntu?**

---

### Post by RAOF on 2006-07-13
> **Sweezel said:**
> Am I reading right? That the default player in Ubuntu doesn't work correctly?
...
Not quite: some people are having trouble playing WMV video (patented, no open-source decoder available **at all**).  And some other video formats in the same boat (realvideo).

Totem-gstreamer works **just fine** when you're using codecs that Ubuntu can support out of the box.  Sadly, that essentially means: ogg vorbis and theora :|.  Everything else is pretty much either patent encumbered, or of questionable legality (I'm looking at **you**, win32codecs).

On the plus side, as a part of the Google summer of code FFmpeg is getting an LGPL VC-1 decoder (sort of a superset of WMV3).  That means that gst-ffmpeg should be getting the capability to (reliably) play WMV.

---

### Post by Sweezel on 2006-07-13
Excellent reply.

Are there any questions as far as base support is concerned?

---

### Post by Buffalo Soldier on 2006-07-13
since i found out about gstreamer pitfdll plugin, my experience with gstreamer has vastly improved. But then again maybe my needs are not that high. It's usually Apple trailers, youtube and google video. pitfdll + w32codec = near perfect multmedia capabilities.

I'll be sticking with gstreamer, giving what ever help/feedback I can. I believe in the long run the gstreamer frame work will give end user far better benefit than the conventional media player.

---

### Post by justinjstark on 2006-10-25
There are a few things that need to be fixed in gstreamer:

1) WMV videos don't play reliably.  They freeze on seek if they play at all.
2) DVDs do not play.  This is due to gstreamer0.8-dvd not being ported to gstreamer0.10 yet, if I read correctly.
3) Some MP3s sound like crap.  Some of the mp3 files on my system tend to echo in the left channel.  It's only really noticeable while wearing headphones and listening to voice audio such as podcasts but it's annoying as hell.

It's too bad we will have to wait ANOTHER 6 months for a gnome release that may or may not fix these issues.

---

### Post by finite9 on 2006-11-23
I have used Gstreamer instead of totem-xine since moving to Dapper and lately, it seems a lot better!  I will stick with it despite its failings because it is by all accounts, the way to go forward with Linux media, and it has been developed so rapidly over the last year that in all probability, the remaining issues will fade in the next year.  For the time being, it does what I want.

Now to draw out Satans sword of flame and slice down Totem for being the crappest media player I have ever had the misfortune to use:  I can play DVDs in totem-gstreamer with libdvdcss2 installed, but as of writing, using Dapper with latest updates, Totem can ONLY *play* a DVD.  It cannot reliably fastforward, rewind, or skip chapters.  I cannot believe that such basic functions do not work!?!?  amd64 btw.  It sucks!  Then there is the issue of completely non-sensical error messages when it comes across a format it cannot play.  Then there is the interface behaviour...stability is not the name of the game here is it?

Flame over.

---

### Post by temcat on 2006-11-23
The fact that the Default Video Player cannot play DVD is ridiculous. Why not make the Xine backend default until gstreamer quirks are worked out?

---

### Post by justinjstark on 2006-11-25
> **finite9 said:**
> I have used Gstreamer instead of totem-xine since moving to Dapper and lately, it seems a lot better! ... For the time being, it does what I want.

Now to draw out Satans sword of flame and slice down Totem for being the crappest media player I have ever had the misfortune to use.


It's not totem's fault that it cannot play dvds.  Totem-xine plays dvds just fine including menus and seeking.  The reason that the default totem cannot play dvds (yet) is because of gstreamer.

Totem as a media player is very well integrated IMO, very easy to use, and just works.

---

### Post by EagleDM on 2007-11-22
Some examples why gstreamer SUCKS more BIG time than the original poster said.


* Gstreamer does not play AC3 files, nor AC3/DTS files inside .avi or .mkv.

Totem has NO WAY to configure the gstreamer plugin, and I'm talking about the latest Ubuntu release, Gutsy.

+ Xine plays AC3 files just fine, all channels are correclty identified.


* Gstreamer plays DTS-Audio CD's in STEREO NO MATTER WHAT... even after configuring Surround51.

+ Xine plays DTS Audio just fine, all channels accounted for, no problems.


* Gstreamer does not have any kind of equalizer, nor any programs that use it and some music sounds just plain flat.

+ Xine can be used in conjuntion with Kaffeine and it's build in equalizer, sound is much much more pronounced on my Home Cinema with these.

* Gstreamer lags A LOT on the Video deparment, even with all codecs installed, when doing Compiz Fusion and moving windows, you can actually see the whole rendering going down because of video, still got stuttering all over the place with BIG HD files in 1920x1080.

+ Xine plays even the highest HD files just fine, no stuttering, oh, by the way, gstreamer does not seem to be using more than 1 core (I have a Quad Core CPU) Xine seems to be using a little of all four all the time, playback perfectly smoth, no openGL slowdowns..


Should I go on?

So.. the question is... why in Hell did they create gstreamer?


Daniel
[www.maximopc.org](www.maximopc.org)

---

### Post by loell on 2007-11-22
> **EagleDM said:**
> 

So.. the question is... why in Hell did they create gstreamer?




you can google what is gstremer and its purpose.

and no one is stopping you from using xine component,

---

### Post by genesis2seven on 2007-12-26
Had similar problems playing DVD's with gstreamer. Tried a ton of different solutions unsuccessfully. Installed xine and DVD's work great and all video formats that I've tried except .avi. Those worked great in gstreamer but don't work for me in xine. Audio is garbled and video color pretty scrambled.

---

### Post by daengbo on 2007-12-27
GStreamer used to be immature and buggy. It used to support few formats. These days, there's very little it won't play. It can even use w32 codecs now. I use Totem as the default player and keep MPlayer for stuff like .bin and .iso files.

---

### Post by thefirstM on 2007-12-27
I agree... Even though gstreamer provides acceptable performance on my system, it has zero customizability (like changing the video output device), so I could not make it use XvMC with my expensive nVidia card that I bought for that purpose.  I use xine and the w32codecs.  It works great in XXMC mode.

---

### Post by disturbed1 on 2007-12-27
> **thefirstM said:**
> I agree... Even though gstreamer provides acceptable performance on my system, it has zero customizability (like changing the video output device), so I could not make it use XvMC with my expensive nVidia card that I bought for that purpose.  I use xine and the w32codecs.  It works great in XXMC mode.

Are you sure your *expensive* Nvidia card even supports XvMC? It was removed for all 8xxx + series cards, IMO the 7xxx series cards are rather cheap.

You can control the video output that GStreamer uses. You can set it to XV, X11, GL, or provide a custom sink.

Playing back a DVD (MPEG2) with default XV uses ~4% CPU, using XvMC it uses ........ ~4% CPU. If you have anything above a 1gig processor, XvMC is just about useless. Even with an AMD 950 DVD (MPEG2) playback using XV (no XvMC) only uses ~30% CPU.

reference links -
[http://www.phoronix.com/scan.php?page=news_item&px=NTc0OQ](http://www.phoronix.com/scan.php?page=news_item&px=NTc0OQ)
[http://www.mythtv.org/wiki/index.php/XvMC](http://www.mythtv.org/wiki/index.php/XvMC)
^^ As seen by the above link, unless you are using a VIA video card, there is little to absolutley no benefit using XvMC to playback SD content. I question some of the results for HD playback. The numbers just don't match my own results plus they conflict with one another. Such as an Athlon 3000+ being slower than a 1600+ and a 2500+. Along with that same 2500+ performing better than a 3200+, but a 2800+ just kills them all. The results for HD don't add up.



The only gripe I have with Totem/GStreamer is the lack of DVD Menu support. Even MPlayer can not do this properly, at least VLC does.

---

### Post by thefirstM on 2007-12-27
Yes, I am sure my card supports XvMC.  It was expensive when I bought it several years ago.  It is a 6600gt, and it works great when using XvMC with xine.  Additionally, it reduces the CPU load by about half.

---

### Post by vek on 2007-12-27
I really, really like the gsteamer "concept"  The way things plug into each other and its easy to transfer and show and clip and alter content with it.  A true stream based filter-like method.  Its really nice to code with.  

However.

It doesn't seem to actually be able to smoothly play my media.  It skips.  It pauses.  It drops frames.  Especially on high end MKV's (HD).  Using players like plain old mplayer, that same content uses under 10% of CPU on this machine and plays smoothly.  On Gstreamer it spikes 100% and stutters and fails.

I mean, all elegance and ease-of-coding aside, if it can't actually play the media, I can't use it :(

So for now, I'm dropping back to mplayer or non-gstreamer versions of my playing apps.

Oddly enough, even Miro (under windows) has this problem playing the same media content (But it plays fine under media player classic or windows media player).  I'm not sure if this is a clue as to why its not working correctly.  But I figured I'd throw it in there.

---

