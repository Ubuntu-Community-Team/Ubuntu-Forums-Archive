---
title: "apt-get a secondlife"
date: 2008-02-29
forum: Gaming &amp; Leisure
---

### Post by ibanez on 2008-02-29
Somebody is building and maintaining debs for secondlife now... 
& have to say they work alot better than the linden tarballs :)

The website is here 
[http://www.byteme.org.uk/secondlife/apt-get-a-secondlife.html](http://www.byteme.org.uk/secondlife/apt-get-a-secondlife.html)

along with repo addresses 
they seem to keep on top of official linden releases too , If you play SL and have trouble with videos or voice these may help you.

---

### Post by exneo002 on 2008-03-01
nice!

---

### Post by robincornelius on 2008-03-10
Hey, thats me!

Glad the debs work for you.

Is there any *official* ubuntu effort to get secondlife or associated missing libraries into ubuntu at all? My primary effort is Debian but it makes a lot of sense for us to work together where common effort can be shared.

Currently as well as secondlife on debian we are missing xmlrpc-epi, openjpeg and libllmozlib. openjpeg is well on its way to being included. xmlrpc is a bit of a problem as upstream is dead BUT php5 use a (patched) version of the code. Trying to find out what other distros are doing about xmlrpc-epi and if its worth doing an upstream fork to maintain a sane build for both PHP5 and secondlife (and anyone else who is using it?. libllmozlib again i am working on, but other input is welcome.

The long and short of it is, if there is a ubuntu developer/packager who wants to work on these packages I will be glad to work together with them.

Regards

Robin

---

### Post by Wobedraggled on 2008-03-10
What's the benefit of grabbing these vs. the client from the Linden site?

and is it the standard client, or windlight?

---

### Post by robincornelius on 2008-03-11
The benefits are :-

A number of stability and bug fix patches, is the biggest. 

ONLY free/open source components, there are no non free dependencies. This means openal for sound, gstreamer for streaming audio and video.

There are i386/amd64 and powerpc builds available.

The packages can auto update with apt-get upgrade or your favorite package manager.

Hopefully, it will pull in all required dependencies on your system automatically as it seems many have trouble with the linden tarballs due to missing packages etc.

And both current release AND release candidate (in this case windlight) are now available.

Disadvantages are :-

No voice out of the box, voice is a non free component, but as it connects to the viewer via TCP/IP it an be added by the end user.

Robin

---

### Post by Wobedraggled on 2008-03-11
I gave it a go, I must say stability is great.

I love the look of the fonts and everything, good work.

---

### Post by Vadi on 2008-03-11
I just get them from getdeb.net...

---

### Post by robincornelius on 2008-03-19
Getdeb seem to be distributing a "downloader" that just pulls the tarball from secondlife.com and extracts it somewhere for you (and probably gives you a menu/icon etc).

Thats fair enough and gives you a true "linden" viewer with no modifications. It would seem reasonable you could install mine and getdeb's at the same time which would be nice to spot little difference and compare stability and performance.

Robin

---

### Post by chewearn on 2008-03-19
I wish I could: apt-get install a-second-life

with a patch for more $$$
:lolflag:

sorry, can't resist...

---

### Post by Crinos512 on 2008-03-19
I refuse to get a Second life until after I get a First one!

:P

---

### Post by reyfer on 2008-03-21
I like this, a lot, but there's one thing I don't like: every 12 to 15 seconds, everything freezes for a second or two, and then back to normal. And I have noticed that even though the voice thing is not active in this, if I run this client, exit and then run the Linden client, voice is activated, if I turn voice off on the linden client, run this client and then open the linden client again, voice has been activated again. It did not happen before installing this client (from repos), so I guess it is something inside the client that triggers the voice activation (even though the client itself says voice is not activated).

Could it be possible that whatever is activating voice is responsible for the freezings? I am using Kubuntu 7.10, 1.5 Gigs memory, Nvidia GeForce 5500 video card, latest Nvidia drivers.

---

### Post by HunterK on 2008-03-21
***"sudo apt-get a life!"***

Someone should totally design a T-shirt with that line on it!  Then have an Ubuntu logo on the back or something.  HAhahahah:)

---

### Post by reyfer on 2008-03-22
Well, I do have a life. I have my own Eco-adventure travel company, I am consultant with several organizations in the field of eco-tourism, etc... But secondlife helps me relax and forget a little about the insanities of the real world. The ones that should get a life are those patronizing individuals that think that just because THEY think something is not useful, EVERYBODY must think like them.

---

### Post by kougaru on 2008-03-25
> Disadvantages are :-

No voice out of the box, voice is a non free component, but as it connects to the viewer via TCP/IP it an be added by the end user.

Robin

Is there any particular way to add voice to the apt-get client? I'm having issues with the linden client getting voice to work :\

---

### Post by zFire on 2008-06-13
Why does mine say "window creation error"?  I cant get secondlife to run deb file or from linden!!
Its all installed!  Why wont it open?

---

### Post by Vadi on 2008-06-13
It looks like a bug in the game. Can you tell us the whole error that it says?

---

### Post by keith11 on 2008-11-29
I downloaded and installed the latest version of SL client, on Kubuntu 8.10, from the suggested Web site, added whatever was required to add in the sources' list, updated, installed, and then again installed the openviewer; everything suggested in the post. But once I sign in, the screen goes black, and leaves only a small crosshair on the screen - my systems hangs(?!) and the Keyboard stops responding. I can't even switch to another console. I have to shutdown the system using the power button, as everything else doesn't respond. 

Does someone know about this issue and how to fix it? Also, if I choose the same file to log the chat, in Vista and Kubuntu, will one overwrite the other? Thanks...

Keith

---

### Post by Naiki Muliaina on 2008-11-30
Works fine on my Ubuntu and Xubuntu intrepid 64 bit installs. Playdebs never seemed to work on my 64bit installs. Thankyou very much for the link!

---

### Post by OrangeCrate on 2008-11-30
> **chewearn said:**
> I wish I could: apt-get install a-second-life

with a patch for more $$$
:lolflag:

sorry, can't resist...

:)

---

### Post by tkdEvan4 on 2008-12-09
Hey, I tried running it recently on Intrepid 32 bit. The game loads and I can log in/run around. The rendering, however, seems to be messed up. Object faces, avatars, even buttons are fast-changing random textures/pixelated/non-exsistant/blacked out...

I've scoured Google and I can't find a solution. I was able to run it just fine on 8.04, so the hardware is OK. Anyone have a suggestion?

thanks in advance,
    new guy

here's a pic of what I'm experiencing...

---

### Post by oldHat on 2009-01-15
I second that.

I've been using "omvviewer" to connect to SecondLife for the last few weeks.  It seems to work fine.

[http://www.byteme.org.uk/secondlife/apt-get-a-secondlife.html](http://www.byteme.org.uk/secondlife/apt-get-a-secondlife.html)

---

### Post by cardinals_fan on 2009-01-15
Apt-get a real-life

Sorry, couldn't resist :D

---

### Post by ac7ss on 2009-03-31
The thread title says it all. 
I love the t-shirt Idea. But add the penguin.

---

### Post by Nick_Nack on 2009-09-17
ok now that I followed all the directions from the site and got the "ok"  How do i get the program?

---

### Post by Perfect Storm on 2009-09-17
Open Synaptic Package Manager and search for it. When found, right click on it and choose installation.

---

### Post by Nick_Nack on 2009-09-17
what am i searching for?  I tried omvviewer, openmetaverse, metaverse...etc

---

### Post by sbalteau on 2012-12-03
I have been playing SecondLife on Ubuntu 12.10 for a couple of months with no problem. You all should have fun as I have, so here's how I do to get all of viewers running. I installed _3D scene graph_ from *Ubuntu Software Center*. Yes, I was not sure which one to install and chose all 3D scene graph related files. Let me know if it helps you. Yes, I installed debian and fonts etc etc as others suggested in the forums. To answer your question how I figured this out, I typed "Virtual Reality" in the Ubuntu Software Center search. Be sure to reboot after install.
-Wild Newbie :guitar:

---

