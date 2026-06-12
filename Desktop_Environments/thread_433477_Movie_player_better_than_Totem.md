---
title: "Movie player better than Totem?"
date: 2007-05-05
forum: Desktop Environments
---

### Post by orange2k on 2007-05-05
I`ve been searching for a better movie player then the default Totem in the add/remove programs list, but I`ve been unable to find Xine. It was available in Dapper, so why is it not available anymore in Feisty? Or is there another alternative?

Totem plays movies kind of sluggish on my system: frame dropouts etc...

---

### Post by spin2cool on 2007-05-05
VLC is my media player of choice.  It'll handle pretty much anythign you throw at it.  One easy way to install it is with automatix ([www.getautomatix.com](www.getautomatix.com))

---

### Post by aidanr on 2007-05-05
also mplayer is great, but the default interface isn't, i just use it without a gui and use the keyboard shortcuts, i much prefer it that way

there's another frontend [here]("http://dekorte.homeip.net/download/gnome-mplayer/"), but i haven't bothered to try it

also there are two versions of totem, totem-xine and totem-gstreamer, and xine is the repos is under gxine (i really don't like it though)

---

### Post by orange2k on 2007-05-05
I`ve tried every player you suggested but I still get poor video performance...

But now I know why...beryl...when I switch to metacity videos play smoothly...

My machine is probably too slow, I`ll have to upgrade to be able to run beryl AND watch videos at the same time...

thanx anyway...

---

### Post by der_joachim on 2007-05-05
+1 for VLC. 

Another good media player is xine.

---

### Post by aidanr on 2007-05-05
> **orange2k said:**
> But now I know why...beryl...when I switch to metacity videos play smoothly...

try ```
mplayer -vo x11 movie.avi
```

---

### Post by katch22 on 2007-05-05
yeah, totem is definitely not the best player... After trying totem I tried mplayer which had serious problems, then I got vlc which is so far the best I have used on ubunu; which is funny because I didn't like vlc at all on windows because I use media player classic there which is truly the best movie player ever for any os, imho at least..

---

### Post by orange2k on 2007-05-05
> **aidanr said:**
> try ```
mplayer -vo x11 movie.avi
```

When I do that it plays back smoothly, but only in a small box without the option to resize, play fullscreen or any other option...you probably have to set all the options in the command-line...

but thanks

---

### Post by AMHA on 2007-05-05
hi orange 2k...
i am new with linux and ubuntu, but i had similar problem to yours.
but when i tried kaffiene ( the media player of kde) it worked fine with beryl working.

also when i installed my ATI driver, and used xgl session, all video programmes worked fine with me.

so i think you have these two options.
good luck.

---

### Post by ComplexNumber on 2007-05-05
> **orange2k said:**
> I`ve been searching for a better movie player then the default Totem in the add/remove programs list, but I`ve been unable to find Xine. It was available in Dapper, so why is it not available anymore in Feisty? Or is there another alternative?

Totem plays movies kind of sluggish on my system: frame dropouts etc...
totee isn't very good. i would go with vlc if i were you.  i would say that its the best video player on linux at this current time.

---

### Post by shoq on 2007-05-05
> **spin2cool said:**
> VLC is my media player of choice.  It'll handle pretty much anythign you throw at it.  One easy way to install it is with automatix ([www.getautomatix.com](www.getautomatix.com))

I installed it, but cannot figure out how to associate it in firefox. The firefox file associations (ff 2.0.3) won't let me add any, and I cannot figure out why.  When I look to preferences, manage file types, there is only an SPL extension for flash, and no button for adding a new association. 
Any tips here?

Never mind. Here's how you show the plugins in firefox. Now, to see if i can make VCL work.  
[http://ubuntuforums.org/showthread.php?p=2600941#post2600941](http://ubuntuforums.org/showthread.php?p=2600941#post2600941)

PSS
I have myplayer working, but when i go full screen, it does something very bizarre. I get TWO video images.  One in the center, running normally, but small, and a 2nd still image, running upper left corner.  What is up with that?

---

### Post by RTrev on 2007-05-06
> **orange2k said:**
> I`ve been searching for a better movie player then the default Totem in the add/remove programs list, but I`ve been unable to find Xine. It was available in Dapper, so why is it not available anymore in Feisty? Or is there another alternative?

Totem plays movies kind of sluggish on my system: frame dropouts etc...

I'm not sure precisely what it is you are looking for, but right now in Synaptic Package Manager I see:

amarok-xine

gxine

gxineplugin

kaffeine-xine

totem-xine

I personally like VLC the best, but the real question is why you can't find Xine?  Perhaps you're looking for something other than the above?

---

### Post by shoq on 2007-05-06
RTev

1) When I set firefox with About:config to show plugins, all the file extentions are set to "none" 
Are there no default extentions? Is this normal behavior?

2) When i browse for VCL to set it as the application to use for a given file type, how am I suppsoed to know where VCL is located?   Pardon my newbness, but I jsut still dont';; get this about linux.  Programs seem to be located all over the file system, or the home directory.   If there is no registry of where the executable is stored, how does the new user know where to find it?  Are we supposed to always drop to Terminal first, and use "locate?"    Am I missing something here?

---

### Post by RTrev on 2007-05-06
> **shoq said:**
> RTev

1) When I set firefox with About:config to show plugins, all the file extentions are set to "none" 
Are there no default extentions? Is this normal behavior?

2) When i browse for VCL to set it as the application to use for a given file type, how am I suppsoed to know where VCL is located?   Pardon my newbness, but I jsut still dont';; get this about linux.  Programs seem to be located all over the file system, or the home directory.   If there is no registry of where the executable is stored, how does the new user know where to find it?  Are we supposed to always drop to Terminal first, and use "locate?"    Am I missing something here?

I'm not sure, not having realized you were asking about Firefox plugins as opposed to just a stand-alone player.

Have you tried about:plugins as opposed to about:config?

This page might be of some use to you:

[http://plugindoc.mozdev.org/](http://plugindoc.mozdev.org/)

Are you running 64-bit?  I understand it isn't as easy to get plugins to work with 64-bit, and many people install a 32-bit browser on their 64-bit systems to handle the sites that need the plugins.  Automatix, for example, offers a 32-bit Swiftfox for those of us on Feisty AMD-64.

I had a lot of trouble with that arrangement, as I'd ask for my usual Firefox and it would run the Swiftfox instead -- and for some reason the Swiftfox wouldn't handle my favorite extension, Google Browser Sync.

Sorry I cqn't help more.  Please let us know if you find a way to get VLC to act as a plugin, that sounds like it would be a neat option.

I'm not sure if this is the default setup, but about:plugins shows a handful for mine.  The reason I'm not sure is that I had Automatix grab me the codecs and misc stuff, and it might have added something without my realizing it.

---

### Post by shoq on 2007-05-06
Argghh  This alone could send me screaming back to windows or mac. LOL.  
I will try plugins.  But now I cannot even get natutilus to recognize a simple  AVI or MPG.   The minute i quick some files, their type changes to ASF (which I've never seen before).  All of these files were copied over from a windows drive. Might this have been a problem?

HOw wouold you normally go about setting VCL to be the default application for MOST common video file types?  In mac or windws, the application would handle this itself.  I cannot find any such configuration in VCL.  This is all  pretty maddening. Thanks for any tips.

---

### Post by shoq on 2007-05-06
I found this threat to reset file associations hosed by gdesklets.  I suspect that could be part of the problem. I was warned they caused drama, and didn't listen

[http://ubuntuforums.org/showthread.php?t=432614&highlight=default+associations](http://ubuntuforums.org/showthread.php?t=432614&highlight=default+associations)

---

### Post by RTrev on 2007-05-06
> **shoq said:**
> Argghh  This alone could send me screaming back to windows or mac. LOL.  
I will try plugins.  But now I cannot even get natutilus to recognize a simple  AVI or MPG.   The minute i quick some files, their type changes to ASF (which I've never seen before).  All of these files were copied over from a windows drive. Might this have been a problem?

HOw wouold you normally go about setting VCL to be the default application for MOST common video file types?  In mac or windws, the application would handle this itself.  I cannot find any such configuration in VCL.  This is all  pretty maddening. Thanks for any tips.

Yeah, I know.. it takes some getting used to the differences, and I'm still in that phase myself.  I'm hoping somebody who knows what they're talking about will wander by.   :confused: 

First, ASF files are Windows Media Player files.. Advanced Streaming Format.  Totem will handle those for you, according to looking at my about plugins.

Maybe it would help to show you what about config shows on my Firefox 2.0.0.3:

```

Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
Totem Web Browser Plugin 2.18.1

    File name: libtotem-basic-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/ogg 	Ogg multimedia 	ogg 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	WMV video 	wmv 	Yes
video/x-wmv 	WMV video 	wmv 	Yes
video/x-ms-wvx 	Playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.1.3

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QT video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime

```

I hope that comes out being semi-legible.

As for how to make a given application the default for a given file type, I'm studying that myself at the moment.  I want VLC to pop up when I click on a file, and I haven't found it yet.  I'm sure it's something simple, somewhere in the Gnome or KDE settings.  I'll post back when I figure that out.

As for finding files, if you pull down the Places menu, there is a "Search for Files" option.  Tell it to search the file system, as it defaults to searching your own home directory.

Sorry, I'm a newb too!   :)

---

### Post by RTrev on 2007-05-06
> **shoq said:**
> 
HOw wouold you normally go about setting VCL to be the default application for MOST common video file types?  In mac or windws, the application would handle this itself.  I cannot find any such configuration in VCL.  This is all  pretty maddening. Thanks for any tips.

Okay, I just found this.  Find a file in Nautilus, and right click on it.  Pick properties, and then pick "Open With".

[COLOR="Red"]Note:[/COLOR] Don't just pick the first "Open With", make sure you go to Properties first.

It will give you the list of available applications, and when you select one it becomes the default for all files with the same extent.

Hey, we're getting somewhere!  :)

---

### Post by AndrewGene on 2007-05-20
I know this thread has been inactive for a week...

but if the op is still watching it...i use kaffeine even with the gnome desktop environment.  Can't beat it.  I'm running crapy intel integrated graphics card and i can run beryl and watch movies in kaffeine at the same time.  Though, I've heard Mplayer is awesome when configured correctly.

---

### Post by imon9 on 2007-05-20
my current choice:
mplayer-nogui + smplayer ([www.getdeb.net](www.getdeb.net)) + mediubuntu w32codec ([https://help.ubuntu.com/community/Medibuntu/](https://help.ubuntu.com/community/Medibuntu/))
- plays all video including RMVB, Quicktime, stage6 DIXV
- maybe trouble with some encryted stream.. no DVD menu support, but Smplyer Playlist handles the playlist nicely
- mozilla-mplayer plugin is good, but does support the powerful list of files that mplayer itself actually support. For exmaple: stage6 divx is not recognise by the plugin, but playable by smplayer. So for browser, need to use mediaconnectivity extension

choice 2:
libxine + kaffeine + w32codec
- play everything as mplayer.. reason i am not using it is that it give me a funny blue and green pixel distortion at times with flv files and the rendering is not too fast (so have drop-frame problem) and also that i dislike KDE interface

choice 3:
vlc
- plays everythign except RMVB and its browser plug-in doesnot works

choice 4:
gstreamer-totem + good, bad, ugly etc gstreamer package
- plays everything except Apple Quicktime (no sound), RMVB (not supported)
good thing is totem browser plug-in is good

---

### Post by moljac024 on 2007-06-01
> **orange2k said:**
> I`ve tried every player you suggested but I still get poor video performance...

But now I know why...beryl...when I switch to metacity videos play smoothly...

My machine is probably too slow, I`ll have to upgrade to be able to run beryl AND watch videos at the same time...

thanx anyway...

The problem is not in your system but in beryl, it's still in beta so is quite buggy...

---

### Post by DSAKA on 2007-06-02
> **spin2cool said:**
> VLC is my media player of choice.  It'll handle pretty much anythign you throw at it.  One easy way to install it is with automatix ([www.getautomatix.com](www.getautomatix.com))
Thank you thank you thank you for posting this about Automatix. I'll be humble and say that I have no idea what I'm doing (atleast yet) in terminal and trying to manually install programs (unsuccessfully) was killing me!

---

