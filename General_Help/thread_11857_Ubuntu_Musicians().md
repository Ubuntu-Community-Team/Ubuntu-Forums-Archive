---
title: "Ubuntu Musicians(?)"
date: 2005-01-19
forum: General Help
---

### Post by bennyp on 2005-01-19
I just want to see if there are any dedicated Ubuntu musicians on the board.
My favorite software is JACK, Hydrogen, ZynAddSubFX, ecamegapedal, ardour, spiralsynthmodular.

---

### Post by EasyA on 2005-01-20
If I can get my Tascam US-428 to play back, it freezes promptly, I'll be using Ubuntu exclusivly...

---

### Post by wulf on 2005-01-20
Yes, although I haven't got particularly far with using Ubuntu to support my music. I've got as far as using Lilypond to notate a few tunes and Audacity to some some audio editing (I did manage to link up a Fostex MR-8 multitrack I've been borrowing via USB to get the audio source to work on). I'd be interested to hear what other people are using - particularly things that install from the Ubuntu Warty repositories without too much mucking around (I had a look at programs like Rosegarden4 and Brahms but haven't got them running smoothly).

Wulf

---

### Post by Ste on 2005-01-20
[QUOTE=wulf]Yes, although I haven't got particularly far with using Ubuntu to support my music. I've got as far as using Lilypond to notate a few tunes and Audacity to some some audio editing (I did manage to link up a Fostex MR-8 multitrack I've been borrowing via USB to get the audio source to work on). I'd be interested to hear what other people are using - particularly things that install from the Ubuntu Warty repositories without too much mucking around (I had a look at programs like Rosegarden4 and Brahms but haven't got them running smoothly).

Wulf[/QUOTE]
 [http://bloodshed.net/wired/?sid=5](http://bloodshed.net/wired/?sid=5)

I tried to get this to install last month but didn't have any luck.
Would love to use it.

---

### Post by Quest-Master on 2005-01-20
Rosegarden, Beast, and Swami are all excellent composition programs. :D

---

### Post by keyshawn on 2005-01-20
I've did some minor stuff in fruity loops before, on windows, I haven't had the chance to do on linux yet, though I'm excited to do so.

BTW, is there any program that is comperable to fruity loops, one that would help layer beats, come with some drum/bass loops as well [that would be a plus] ?

---

### Post by bennyp on 2005-01-20
[QUOTE=keyshawn]I've did some minor stuff in fruity loops before, on windows, I haven't had the chance to do on linux yet, though I'm excited to do so.

BTW, is there any program that is comperable to fruity loops, one that would help layer beats, come with some drum/bass loops as well [that would be a plus] ?[/QUOTE]
 [http://hydrogen.sf.net](http://hydrogen.sf.net)
So far it's only drums, but in the future there will be a piano roll to make melodies as well

I have a MOTU 828mk2, I'd love to get linux drivers, or even beter, specifications for it. If you think this is a good idea, head to MOTU's site at motu.com and let them know that you think linux (and darwin and hurd and BSD etc etc) musicians deserve a fair shake, too.

---

### Post by machiner on 2005-01-21
I couldn't get Hydrogen working in Ubuntu. Gave up after not being ableto set up Jack properly. It worked for me in FC3 without hassle, but that's sure no reason to switch back.

Nope, UH-UN!

I play bass and love playing with some cool drum tracks in Hydrogen.

Maybe I'll be able to set it up properly in the future, than I can help my guitarist buddies and maybe we can set up other software and record some schwEET!

rock on.

---

### Post by Ste on 2005-01-21
In this months Linux Format there's an article on "Audio and Music Production".
Have yet to read it.

Next month tho they'll be doing one on Rosegarden.
Going to be a feature for the next few months so keep an eye out for it.

---

### Post by Ste on 2005-01-21
Been reading up on this and reckon I'm going to get back into production.
Handy site I came across. [http://ccrma.stanford.edu/planetccrma/software/soundapps.html](http://ccrma.stanford.edu/planetccrma/software/soundapps.html)

---

### Post by Karlos on 2005-01-21
I've been muckin about with Ubuntu for a while now trying to work out a way to incorporate it into my studio.

So far Audacity works fine, as well as about 80% of the LADSPA effects. But I have had several crashes when I start to layer multitracks.

Sweep -- Brilliant little tool -- bit slow saving and opening stuff tho

Muse -- managed to get it to fire up, looks good, but garanteed to crash as soon as you do ANYTHING

Hydrogen -- AWESOME -- again, while its working

GNUSound -- very good -- not a very clear interface tho

ARDOUR -- supposed to work with hydrogen in a kinda of partnership so you get a logicy cubasey kinda thing going on -- But I cant get it to work..!

ROSEGARDEN -- ????????????? dont seem to do nothing ?????????? love to get it fired up tho

Anyway -- thats wot I reckon so far -- Most pleased that this thread has started tho.  

I'll be keepin my eye on this one

Cheers.......Karlos

---

### Post by bennyp on 2005-01-21
if you're having trouble with hydrogen, perhaps it is a JACK issue. is jack server runnig in RealTime mode? you will need the realtime security patch for this.

try the hydrogen-devel and hydrogen-user lists on sourceforge.

---

### Post by Ste on 2005-01-21
Been playing with Hydrogen the last few hours. Very impressed. Some things weren't working when I installed first but I installed an oldversion via apt-get/synaptic but just built the soucre and WOW even more impressive and a nicer GUI.

Thanks for letting me know of such a good program.

---

### Post by TravisNewman on 2005-01-21
You should check out DeMuDi (Debian Music Distribution).

I tried to get it to play well with Ubuntu, mostly with the customized low latency kernels, and I didn't have any luck. But you can install the applications with their apt sources and they work fine. However, you'll be much better off compiling from source. One of the great things about Linux. It runs smoother.

---

### Post by bennyp on 2005-01-21
it's possible to compile the realtime security patch as a module, which means you wont have to switch out your current kernel.

there are files here [http://sourceforge.net/projects/realtime-lsm/](http://sourceforge.net/projects/realtime-lsm/)
make sure you read the readmes (of course)
to get this to work, you will have to load it like so

modprobe realtime gid=18

substitute 18 for your audio group number (check /etc/group)

I'm going to try kernel 2.6.10 now as I'v read it's good for audio work... we shall see

If you are using the latest CVS snapshot of hydrogen, sighn up for the hydrogen-devel list!

---

### Post by Karlos on 2005-01-23
I have just found a program called Rezound - a sound editor 

It's in a beta sorta stage

Really good - well worth checking out 

I apt-getted it from somewhere - cant remember if it was ubuntu or sid

Nonetheless it worked for me straight out the box so to speak

---

### Post by Ste on 2005-01-23
[http://www.skale.org/](http://www.skale.org/)

Came across the other day, worked straight outa the zip.
Didn't play wih it yet but it's very fruityloops looking-esque.

---

### Post by bennyp on 2005-01-24
I went to the skale site... looks really cool, but it's non-free, that's not at all in the spirit of ubuntu.
I started a thread in the skale general discussion forum asking why it is non-free. Maybe some of us from here can go over to their board and politely suggest that the software be freed.

in regards to rezound, i love that program!! i used it for some sound design a little while back and some editing too!! audacity gets all the attention but rezound is great as well!
so is sweep!
try out spiralsynthmodular sometime, too!

---

### Post by TravisNewman on 2005-01-24
I gotta ask though, do you use flash, java, mp3, MS TT Core fonts, W32Codecs, etc...? Those are most definitely non-free.

---

### Post by jdodson on 2005-01-24
i use audacity, hydrogen and terminatorx.... 

never had any problems with hydrogen or audacity.

---

### Post by bennyp on 2005-01-24
[QUOTE=panickedthumb]I gotta ask though, do you use flash, java, mp3, MS TT Core fonts, W32Codecs, etc...? Those are most definitely non-free.[/QUOTE]
 I generally try to use fs over non free. I encode my songs with ogg.. yes, I listen to mp3s, but I also actively try to convert people (especially musicians) to ogg. i use javascript on my website, it was an experiment for digital photography class, perhaps next time I feel web-creative I will cut the JS. I also use non-free proprietary software to make music. Right now I'm running Mac OS X which has many non-free components. 

If you ask RMS, he will say that wherever a fs program is missing, it is alright to use non-free, so long as you intend to use the FS once it is available. That is my attitude as well.

---

### Post by Karlos on 2005-01-25
I just been looking at AGNULA (DeMhudi)

They say that you can install it over the top of a debian system (sarge)

Like this..........

 Q: Can I install A/DeMuDi over an existing Debian installation?

A: Yes, at least as long as you are running Sarge. Follow the following steps

    * become root
    * edit your /etc/apt/sources.list adding

deb [http://apt.agnula.org/demudi](http://apt.agnula.org/demudi) testing main local extra

    * from the command line issue:

# apt-get install demudi-install demudi-base

    * install the tasks you are interested in; to have a look at them run:

# apt-cache search demudi

      the task demudi installs them all
    * install the appropriate kernel for your processor:

# apt-get kernel-image-2.4.25-1-multimedia-<Type>

      where <Type> might be 386, 586tsc, 686, k6, k7, and the relevant ALSA modules too:

# apt-get install alsa-modules-2.4.25-1-multimedia-

    * finally you may want to run some customisation scripts which automatically tune your system:

# cfagent-demudi -D postbaseconfig -D upgrade


#################

Do you think this could work from a basic warty installation....?????????

Thing is I have to get some sort of distro on the go in order to connect this stupid speedtouch 330 modem i've got........!!!!!!!!!????????????...............

---

### Post by Karlos on 2005-01-30
[http://www.linuxmusician.com/](http://www.linuxmusician.com/)

Here's a handy site I came across the other day

Worth a look..!

---

### Post by Karlos on 2005-01-30
I've been trying to install WIRED from source

I need to install wxGTK-2.5 in order to get it to run

when attempting to ./configure I'm getting this message

configure: error:
Please check that gtk-config is in path, the directory
where GTK+ libraries are installed (returned by
'gtk-config --libs' command) is in LD_LIBRARY_PATH or
equivalent variable and GTK+ is version 1.2.3 or above.

?????????????????

I type gtk-config--libs    and get

-L/usr/lib -L/usr/X11R6/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm

?????????????????

I'm confused an I dunno what to do................

please help????????????????/

---

### Post by Quest-Master on 2005-01-30
Make sure you have the GTK development libraries installed.

---

### Post by Karlos on 2005-01-31
i'll look into it cheers...

one more thing....

looking on the agnula website (demudi) it mentions the 

kernel-image-2.4.25-1-multimedia-bla-bla

if I was to set about installing this on my ubuntu system would it mess everything up??

---

### Post by bennyp on 2005-02-01
[QUOTE=Karlos]i'll look into it cheers...

one more thing....

looking on the agnula website (demudi) it mentions the 

kernel-image-2.4.25-1-multimedia-bla-bla

if I was to set about installing this on my ubuntu system would it mess everything up??[/QUOTE]
 the question you should ask yourself is "If I were to do this, would I mess it up?"

---

### Post by Karlos on 2005-02-01
Absolutely.....wouldn't argue with that..!

I'm always breaking the system

---

### Post by bennyp on 2005-02-01
[QUOTE=Karlos]Absolutely.....wouldn't argue with that..!

I'm always breaking the system[/QUOTE]
 I've been playing with GNU/Linux systems for maybe 2 or 3 years now, I've destroyed my system so many times. The best way to learn is to break something and go crazy trying to fix it =)

---

### Post by ckm000 on 2005-02-07
Does anybody have any tips on upgrading to Hydrogen 0.9.1 for a newbie to Ubuntu/Linux?   Are there any packages I should get beforehand to make sure the install will go smoothly?

The Synaptic package manager only has Hydrogen 0.8.2.  I tried downloading 0.9.1, but unfortunately I am stuck after ./configure... 

 :oops:

---

### Post by bobmitch on 2005-02-08
[QUOTE=ckm000]Does anybody have any tips on upgrading to Hydrogen 0.9.1 for a newbie to Ubuntu/Linux?   Are there any packages I should get beforehand to make sure the install will go smoothly?

The Synaptic package manager only has Hydrogen 0.8.2.  I tried downloading 0.9.1, but unfortunately I am stuck after ./configure... 

 :oops:[/QUOTE]

Post the errors you are getting.  I got the latest hydrogen installed without too much bother.

---

### Post by Karlos on 2005-02-08
RE: hydrogen 9.1

download it from the demudi archive

you need to add the following to your /etc/apt/sources.list

######DEMUDI######

deb [http://apt.agnula.org/demudi/](http://apt.agnula.org/demudi/) testing local 
deb-src [http://apt.agnula.org/demudi/](http://apt.agnula.org/demudi/) testing local 

you can do this by opening a terminal and typing...

sudo gedit /etc/apt/sources.list

then copy an paste the above to the bottom of the page and save 

next you open a terminal and type...

sudo apt-get update
sudo apt-get install hydrogen (or 'hydrogen-cvs' if you fancy a go on the flashy new developement version)

that's it job done, have fun....

---

### Post by Karlos on 2005-02-08
oh.... an dont forget to open your litle "run application" box or a terminal an type "hydrogen" to get it to work

---

### Post by ckm000 on 2005-02-08
Thanks so much for the reply :)

I tried your suggestion, and here's what I got:

[I]requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  hydrogen-cvs: Depends: libasound2 (> 1.0.8) but 1.0.5-woody0.1 is to be installed
                Depends: libjack0.80.0-0 (>= 0.99.0) but 0.98.1-3ubuntu3 is to be installed
                Depends: libqt3c102-mt (>= 3:3.3.3) but 3:3.2.3-4ubuntu1 is to be installed
E: Broken packages[/I] 

I tried to apt-get those packages, but it says I already have the latest version.  Is there something else I'm missing?  Sorry to seem so clueless about this stuff - I really appreciate any suggestions you may have!

---

### Post by Karlos on 2005-02-14
Have you enabled universe???

If not then you need to..!

---

### Post by friendly_guy on 2005-02-14
I have a nice music set up under slackware with muse, hydrogen, audacity & all the ladspa plug-ins I can get my hands on.  

I am running ubuntu on my 'test machine'; I compiled all the above from source & the thought of being able to do it all from apt-get/synaptic is very tasty.  So far ubuntu is a little more 'cranky' than slack but I've an open mind & am looking forward to the next release.

---

### Post by Smurf on 2005-02-25
Check this out....

[http://www.ferventsoftware.com/index.php](http://www.ferventsoftware.com/index.php)

I am saving up as I type. I use Audacity with the Kristal Audio Engine under win2000 (ducks) And the 2 work well together. I dual boot with Xandros 2.5 biz, using Audacity on that for recording and the Hydrogen drum machine. I also have the Demudi distro, 1.2.0, and like it but it feels a little "clunky". since I like Rosegarden, and it has hit the 1.0 release, I think I will go the all-in-one Studio...to Go! route............unless someone can make a "music-tu" based distro that has just the basic, needed apps like Studio....to Go!

If I can get the modem working on this ubuntu distro I'll keep it around for a few. (ISA hadware modem and serial-port Rockwell, no joy dialing out yet on 4.10 ;-(

---

### Post by dolson on 2005-03-12
[QUOTE=Ste][http://bloodshed.net/wired/?sid=5](http://bloodshed.net/wired/?sid=5)

I tried to get this to install last month but didn't have any luck.
Would love to use it.[/QUOTE]


I *really* would do anything to get a package of Wired into Ubuntu main, or even universe or whatever. I just want it! :(

Audacity is what I use currently though (although I did use Hydrogen and SoundTracker on a couple tracks previously). My music is at [http://rivir.tk/](http://rivir.tk/) and it really sucks. Don't go there. Don't listen to it.

---

### Post by 23meg on 2005-04-07
i'm trying to get my m-audio quattro audio interface to work in 4-in 4-out with JACK under Hoary; no luck so far.

---

### Post by Karlos on 2005-04-11
> I *really* would do anything to get a package of Wired into Ubuntu main, or even universe or whatever. I just want it! 

i managed to install it from source about a month ago..the concept looked great but its very kinda early stages of development at the mo it crashed a lot so i gave up in the end .. definately is one to watch tho

---

### Post by pierlo on 2005-04-19
Hallo! i am quite new to Ubuntu and i was trying to set it up for making some chunes... :) I have tried Jack, Hydrogen and i *LOVE* them, while i'm having issues with ardour (crashes often, plus i dont feel really comfortable with it). After some research on the internet, i found out this pretty multitrack called ProTux [ [http://www.nongnu.org/protux/screenshots.html](http://www.nongnu.org/protux/screenshots.html) ] it seems really ok - unfortunately there is no such packege on the repos... can anybody submit this as a package request? THanks!!!!

---

### Post by Karlos on 2005-04-26
you could always install from source

it tried it a while back it was quite good ive rebooted into hoary since then.

I liked the way protux worked.. akinda keystroke/emacs style of going about things

in fact i might go and install it again right now..!

---

### Post by ggraham on 2005-04-30
[QUOTE=Karlos]I have just found a program called Rezound - a sound editor 
It's in a beta sorta stage
Really good - well worth checking out[/QUOTE]

I used rezound on warty for quick audio editing, but when I upgraded to hoary, I get the following error:

```
Error occurred while initializing audio output method 'oss'
 -- virtual void COSSSoundPlayer::initialize()
 -- error opening OSS device '/dev/dsp
 -- Device or resource busy
```

Anyone have any ideas what is wrong? By the way, when I couldn't get rezound to work, I tried audacity. It pops up an alert box saying "There was an error initializing the audio i/o layer. You will not be able to play or record audio."

By the way, this is a clean install of hoary, and I downloaded both applications from the Ubuntu universe. Other audio applications, such as XMMS, work fine. I also tried item #3 on [http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats) , which involves editing the esd configuration to release the sound card.

I'm going to do some more research into esd, OSS, ALSA, etc. I guess I will need to get to know what these things are if I'm going to do more audio on Ubuntu. It's not quite as straight-forward as Mac OS X, but that's life on the frontier!

Thanks,
Greg

---

### Post by ggraham on 2005-04-30
[QUOTE=ggraham]I used rezound on warty for quick audio editing, but when I upgraded to hoary, I get the following error...[/QUOTE]
I figured out an answer by looking at [this wiki page](http://www.ubuntulinux.org/wiki/SkypeHowto), which suggests the removal of ESD and replacing it with the polypaudio sound daemon/server. I followed the directions and then Rezound worked fine.

---

### Post by Karlos on 2005-05-03
i followed a few of the howto's in the hoary section of these forums.. 

and now everything works fine

read this

[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

i found it helpful....

---

### Post by motionsiren on 2005-05-11
I read, over and over again, the JACK web page / docs, Ardour, etc. and it's just confusing to me. I just want to know how to get Ardour and all these really amazingly good looking programs to work. 

Is JACK is so good, why aren't linux distros using that instead of ESD/ARTS/DMIX? Or am i still way off?

It's just frustrating and I would love to write a handbook on all this to help simplify it.

---

### Post by Michael Treadgold on 2005-05-11
I'm just moving to Ubuntu for sound production and recording. I am trying to get Jack  working so I can try Ardour.

Talk about frustrating!  I thought Windows was bad! Just kidding, it's the learning curve getting to me. If anyone knows a good site for Audio advice on Linux in general it would be a big help.

Current system:

AMD 2500+, 512MB SDRAM, 2 x 120GB WD, EMU 1820M(which is being sold if anyone wants it.) soon to add RME Hammerfall 9652. But I'd sure love to get my onboard sound working for now. Just to see if this software is any good at all.

---

### Post by EricS on 2005-05-15
motionsiren: Use qjackctl to run Jack before you run Ardour. It really can't be easier than with qjackctl. GUI all over. :)

---

### Post by whetherornot on 2005-05-20
[QUOTE=Michael Treadgold]I'm just moving to Ubuntu for sound production and recording. I am trying to get Jack  working so I can try Ardour.

Talk about frustrating!  I thought Windows was bad! Just kidding, it's the learning curve getting to me. If anyone knows a good site for Audio advice on Linux in general it would be a big help.

Current system:

AMD 2500+, 512MB SDRAM, 2 x 120GB WD, EMU 1820M(which is being sold if anyone wants it.) soon to add RME Hammerfall 9652. But I'd sure love to get my onboard sound working for now. Just to see if this software is any good at all.[/QUOTE]

I just got ardour working pretty quickly. I don't know what all of these things mean, but this is what I did.

Install jack and ardour with synaptic.
At a terminal: "killall esd". This kills the enlightened sound daemon.
Then: "jackd -d alsa" (If you want to understand this command go to "man jackd"). Keep this terminal going.
Then in a different terminal: "ardour". Ardour should start.

When I run audacity, I "killall esd" beforehand, and all goes well.

You can monitor when jackd is going and when esd is going by going into applications->system tools->system monitor.

This thread seems great, as well: [www.ubuntuforums.org/showthread.php?t=26567](www.ubuntuforums.org/showthread.php?t=26567)

hope it helped.
Oh, good website(s)-- linuxaudioblog.jawebada.de/ , alsa-project.org 
Using: delta 1010, AMD 2600+

---

### Post by Havoc on 2005-06-24
Hello,

Sorry for bumping this tread but I have a question and I didn't want to post a new topic.Also, I'm using Hoary, so, no relation to Warty whatsoever.Well, here goes:

I'm not a musician.But, I like music, and recently I used Fruity Loops on a friend's PC.I really liked this feature it has, playing (the guitar, bass, drums, whatever) with your keyboard.Your actuall keyboard.So, my question is, what program can do this for me in Linux? This sounds like a newbie question, but, I'm a newbie man.So far, and without any testing, Ardour, Rosegarden and mabye SpiralSynthModular seem likely.

So, anyone? The only Music Programs I've used are Ejay and Fruity Loops.I just want to kill time, and mabye make a couple of nice *pseudo* Rock tunes.So? Anyone?

Thanks!  :grin:

---

### Post by Karlos on 2005-07-05
Rosegarden4

Hydrogen

Audacity

Zynnaddsubfx

sweep

### that would give you loads to play with
you will need the jack sound server control program ###

qjackctl  (jack control)

install that lot and do a search for SOUND and MIDI in the hoary tips + tricks section of the forum .

do a bit of tweaking ie: follow the howtos and you should be fine

## I have found a decent < virtual keyboard > in the demudi repository
do a google search for demudi if your interested
I use the repository accassionally for things aren't in ubuntus (it's full of music stuff)

---

### Post by polo_step on 2005-07-07
It would be fun to try recording with Linux, but even if the software was up to the standards of Cubase, and even if there were Linux virtual instruments of the quantity and quality of the thousand or two VSTIs out there, there still wouldn't be a Linux driver for the Oberheim front end I use. :-( 

Dig: Between the time I left to go pick up the unit and the time I got back with it, Oberheim announced the company's bankruptcy, so they never even got their 2000/XP drivers issued, and the incomplete drivers were seized as assets.  So, believe it or not, I have to work in Win98SE.  On a 100% dedicated studio machine, it's stable enough.

---

### Post by Havoc on 2005-07-07
Hey, thanks Karlos!

I've been using ZynAddSubFx for a couple of days now and I like it!
Also, Hydrogen is great for Drums.If only they could add the Bass and I could make some nice tunes!

About Rosegarden, It needs half of the KDE files installed, so, I couldn't use it.I'm not connected to the net and I have to D/L all of my stuff from another PC.But, It sounds like a top program, so I might try...again...

Anyways, thanks for all the help.I'll try the DeMuDi Repo out.

Keep up the good work! Long Live Rock n' Roll (Rainbow) !  :grin:

---

### Post by hyspah on 2005-07-20
[QUOTE=jdodson]i use audacity, hydrogen and terminatorx.... 

never had any problems with hydrogen or audacity.[/QUOTE]

Hi

Good to know someone does not have problems with audacity, hydrogen and termnatorx.

I have installed the above softwares on ubuntu succesfully but any time i start audacity and hydrogen i get an error message saying can not start audio device and when i start terminatorx and click on power to enable my audio device it hands and crashes i suporse it can't start the my audio device as well.

I need you help...
i guess it's something relating to my audio device.

thanks.

hyspah ](*,)

---

### Post by Karlos on 2005-07-21
sounds like you need to configure your sound properly

check out the following threads

[http://www.ubuntuforums.org/showthread.php?t=26567&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=26567&highlight=sound)

[http://www.ubuntuforums.org/showthread.php?t=32063&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=sound)

hope you find a solution there

regards

Karlos

---

### Post by damu on 2005-08-04
Did any of you tried Studio to go! from fervent :

[http://www.ferventsoftware.com/index.php](http://www.ferventsoftware.com/index.php) 

...ok, it's not free (80 £ = 115 € = 140 $)...but it works!...and that mean something to anyone which tried to put together a DAW under linux...plus the price is not even 1/10 of a windows based system (one you bought the sequencer, synths, drum machine, good quality plug-ins, sampler...)

Rosengarden, Ardour, Hydrogen, many synths, more than 200 plug-ins!
Native support of most VST plug-ins

but mostly with the "free to think" open source feeling.

I I just switched from Cubase to Studio to go! and I am very happy with it

---

### Post by fragmental on 2005-08-06
Those of you thinking about trying out Wired, check this thread at the Wired Forums: [http://sourceforge.net/forum/forum.php?thread_id=1278998&forum_id=409329](http://sourceforge.net/forum/forum.php?thread_id=1278998&forum_id=409329) 

Ah yes, taste that sweet sweet binary package.  I have wired-cvs running on my system from that repository, but I haven't gotten sound to work(I'm having issues with that in some applications anyway).

---

### Post by alexidoia on 2005-09-12
Hi there,

Very Interesting discussion here,
I have tried long ago DEMUDI who was very good but I felt in love of ubuntu and its integration of gnome.
I will very shortly try to run ubuntu on a audio optimised kernel such as the one used by DEMUDI. I am a long time user of Cubase and want to switch to free software.
I have been introduced to Ardour which I think is capable of at least the same than cubase. My only problem is that there is no driver for the Motu 828.
I have been waiting and now wondered if
- I am going to sell for another card
- try to do a driver myself. hu !

I can see that most of you use composition software here. I essentially do recorginds and thus require a several IO sound card with a sequencer such as Ardour.
Can anyone recommend a professional card with enough IO (like the Motu) but one that is recognized on linux ?

Another question, is there any professional here that use linux solution in real recording conditions, can we have your views on the question ?

Thanks All
Alex

---

### Post by whetherornot on 2005-09-12
I have a maudio delta 1010, with 8 ins and outs, if that's what you're looking for. It's sturdy.
It works great.
It uses the envy24 driver, and works fine.

---

### Post by xyz on 2005-10-03
hi-i'm (very) new to ubuntu and absolutely very new to MusixGNU+Linux026 which I dowloaded...and that's it!:confused: ...
Any advice would be much appreciated...where could I start getting initiated to making music using Ubuntu?Very first steps type thing??
thank you 
PS:if any of you guys have any music of your own I could listen to, please do link to it in your answer!!:D

---

### Post by SFN on 2005-10-05
I've posted instructions for installing [lmms]("http://lmms.sourceforge.net/") in Breezy. You'd have to not mind installing packages from Debian but it does seem to work rather well.

Instructions are [here]("http://ubuntuforums.org/showthread.php?t=71984").

Hope this helps.

---

### Post by drucer on 2005-10-06
Hi, I'm a musician and I've been struggling to get my sound system working with Ubuntu. I've got ice1712 chipset based M-Audio Delta 66 sound card (professional soundcard). At the moment Ubuntu lacks envy24control application that is usually shipped with alsa-tools (/alsa-utils) package on some other distros. Ubuntu makes such a nice desktop OS that I think it's well worth the trouble to find a way to make my audio work on it. Once I have it working with Jack, Ardour, Rosegarden, Hydrogen and Qsynth I'll be really, really satisfied! Then I can honestly say that my Ubuntu has everything I need.

---

### Post by whetherornot on 2005-10-07
Hey, I use a Delta 1010, which also uses the envy24control app.

I've never used the envy24conrol app, because I had a lot of trouble getting it to run.

However, my card works fine, and I've no input/output issues yet. Perhaps I don't have perfect volume tweaks without the app, but it hasn't affected usability.

What exactly is the problem? Does it not work at all? Do you have alsa installed and configured. Are you running the proper sound servers when you need to, e.g. xine, esd, jack?

---

### Post by drucer on 2005-10-08
[QUOTE=whetherornot]However, my card works fine, and I've no input/output issues yet. [/QUOTE]

Hey, thanks for your reply! Actually this was entirely my mistake. I was running Breezy and I made a mistake and posted my message under this thread. I tried Warty and M-audio delta 66 seems to work great with it!

---

### Post by ramba on 2005-11-09
Has anyone got skaletracker working in 5.10? :confused:

Update: Ahha! It works perfectly!

---

### Post by sedition on 2005-12-17
I'd really like to get my eMagic EMI 2|6 working... but so far, I have to settle for my crap-bag internal card, but coming from the Window$ world, here's some equivalents of stuff I used to use:
ReCycle -> Freecycle (Loop editor/chopper)
Cubase -> Wired/Rosegarden/Ardour (Sequencing, multi-track editing)
WaveLab -> Audacity (Sound file editor)

---

### Post by sem on 2005-12-20
[QUOTE=drucer]Hi, I'm a musician and I've been struggling to get my sound system working with Ubuntu. I've got ice1712 chipset based M-Audio Delta 66 sound card (professional soundcard). At the moment Ubuntu lacks envy24control application that is usually shipped with alsa-tools (/alsa-utils) package on some other distros. Ubuntu makes such a nice desktop OS that I think it's well worth the trouble to find a way to make my audio work on it. Once I have it working with Jack, Ardour, Rosegarden, Hydrogen and Qsynth I'll be really, really satisfied! Then I can honestly say that my Ubuntu has everything I need.[/QUOTE]
Hi
I fetched this rpm file:
[ftp://fr.rpmfind.net/linux/Mandrake/2006.0/i586//media/main/envy24control-1.0.9-1mdk.i586.rpm](ftp://fr.rpmfind.net/linux/Mandrake/2006.0/i586//media/main/envy24control-1.0.9-1mdk.i586.rpm)

ran it through alien, which can be installed with apt.

and then installed it with dpkg -i <package name.deb>

And envy24control is now up and running on my Ubuntu 5.10

Delta 66 rules :)

/sem

---

### Post by starpause on 2005-12-28
[QUOTE=ramba]Has anyone got skaletracker working in 5.10? :confused:

Update: Ahha! It works perfectly![/QUOTE]

mmm, how did you get this to work :cool: :confused: 

i'm a tracker by nature did an ep in fasttracker a while back ... 

[http://www.floppyswop.co.uk/files/songs/STRPSE_K9D_THQ_TOPS-floppyswop--co--uk.zip](http://www.floppyswop.co.uk/files/songs/STRPSE_K9D_THQ_TOPS-floppyswop--co--uk.zip)

but anyway, yeah, i'm running an maudio audiophile 2496 under ubuntu 5.10. i nabbed the latest skale, no go "out of the box" aka clicking on Skale.x86 (yes, i know it's compiled for redhat, but it seemed like the best bet) ... and a peek at the cfg didn't open up anything ... clue me in :KS :p

---

### Post by StarFire on 2006-01-15
Hi Ubuntu Musicians!,

Give :KS  LMMS :KS  a try. Although I think it was designed originally for producing house music, I made some real nice hip-hop beatz with it. Quite an intuitive interface.

I'm still having trouble getting MIDI to work (installed freepats etc.), but beast keeps telling me that it's unable to find midi support. I remember having midi after using automatix, but I'm not fond of automated scripts messing up my beautiful system :???: 

Ardour keeps crashing. Not using it anymore.

Usefull lynx:
[COLOR="Green"]
[http://lmms.sourceforge.net/](http://lmms.sourceforge.net/)
[http://linuxsound.atnet.at/](http://linuxsound.atnet.at/)
[http://linux-sound.org/ddj.html](http://linux-sound.org/ddj.html)
[http://www.hitsquad.com/smm/linux/DJ_MIXING/](http://www.hitsquad.com/smm/linux/DJ_MIXING/)
[http://www.linuxdj.com/audio/lad/resources.php](http://www.linuxdj.com/audio/lad/resources.php)
[/COLOR]

Greetz, 
[COLOR="Red"]S[/COLOR][COLOR="Blue"]tar[/COLOR][COLOR="Red"]F[/COLOR][COLOR="Blue"]ire[/COLOR]

---

### Post by nalmeth on 2006-01-15
Can anybody share any success stories with a USB microphone? I have an old regular mic, but I think age has gotten the best of it. I had the windows version of audacity running my usb mic, until both wine and audacity were upgraded, and now am experiencing annoying graphical problems. I talked to a developer and administrator, and they said it had something to do with a 'port-audio' bug, and would be fixed later. Are there any apps that people know work on the go with a USB microphone?

---

### Post by alonso on 2006-01-23
Has anybody succeeded in making Rosegarden DSSI - aware? I compiled dssi and fluid-dssi from scratch, but at least the rosegarden, which is in breezy does not recognize fluid-dssi.

-A

---

### Post by Karlos on 2006-01-30
I've just set up a planet CCRMA system in my studio.  You have to do a full on Fedora Core 3 install first then put planet CCRMA on top. ..And it is brilliant, there is a choice of specialist kernels to try out, all the music apps work, and being fedora core hardware detection was excellent.  I thought another nice touch was that once you've installed the PlanetCCRMA-menus package you get extra menus installed (based on the music and video apps, similar to Demudi's menu's) and next to each application launcher is a link to the respective apps home page. I think this should become standard in all Linux distros it's a brilliant idea.  If your serious about computer music then I urge you to try it out.. that's the beauty of Linux the choice. I have a machine at work running the fed core 3+planetCCRMA install. My kids have Ubuntu machines. I have a Slackware machine which operates my printer. And the machine I'm using at the moment is Ubuntu with E17 window manager..I also carry a dyne:bolic cd about and a usb stick, great combination.......ah the choice!!!  By the way xsynth-DSSI the rosegarden plugin and the muse one all "just work" with planet CCRMA...I think that's why I mentioned it...I got carried away.........sorry?!!?!

---

### Post by christhemonkey on 2006-01-30
Very nice!

---

### Post by Karlos on 2006-01-30
I'm on a mission   a mission to make a music production studio using only linux apps  and I'm getting there...it can be done  takes a lot of fiddling about tho .. BEWARE

---

### Post by Karlos on 2006-02-01
I suppose what I'm trying to suggest is that someone creates one of these marvellous install scripts that install the realtime security modules, all necessary codecs and the modules and tweaks for midi etc. Then it could install the tons of music apps availiable. There is such a project for slackware called audioslack.  If something like this could be availiable for ubuntu it would be great, would it not??

---

### Post by sites on 2006-02-21
dedicated musician here, but i'm still struggling with Ub* in this area... so most of my work is still on a Mac.  but i'm also using the motu 828mkII, and share your pain.  i think that by the time low latency is a snap with Ub* i'll pick up an audiophile or something, & an nforce2 based mobo cuz my old one just gave me the finger.

---

### Post by motionsiren on 2006-04-05
I have a new mix up at [www.scavengerdnb.com](www.scavengerdnb.com) if you like dark Drum & Bass. Created, produced, mastered, yadda yadda with GPL tools. 

Graphic splash done in GIMP (and photoshop).

---

### Post by just1m on 2006-07-26
I am interested in giving Protux a try. Has anyone used it and if so can someone run me through installing it from the site in which it comes from. Thanks.

---

### Post by just1m on 2006-07-26
Here is the site: [http://protux.sourceforge.net/Download.php](http://protux.sourceforge.net/Download.php)

---

### Post by rcsarver on 2006-08-07
To the person asking for a program similar to fruity loops, try lmms. It's pretty good, and, well, makes using hydrogen pointless.

---

### Post by PipeManMusic on 2008-03-12
I have started a podcast for musicians about using Open Source. Check it out at [www.opensourcemusician.libsyn.com](www.opensourcemusician.libsyn.com)

---

