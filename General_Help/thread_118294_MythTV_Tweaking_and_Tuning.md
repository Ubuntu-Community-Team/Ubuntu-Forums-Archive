---
title: "MythTV Tweaking and Tuning"
date: 2006-01-16
forum: General Help
---

### Post by greyhound4334 on 2006-01-16
I'm starting this thread as a placeholder to collect up questions (and hopefully some answers) about tweaking and tuning MythTV on Ubuntu.  I think most of this is probably Window Manager agnostic, but since Ubuntu gets alot more traffic than Kubuntu, I figured I'd place it here.

I inadvertently semi-hijacked this excellent thread [http://www.ubuntuforums.org/showthread.php?t=106713&page=2](http://www.ubuntuforums.org/showthread.php?t=106713&page=2) so I thought it might be better to create a new place to keep this info.

Personally, I've just completed building my MythTV box, and have it running (mostly) in the family room, complete with IR Remote Control.  Far and away the most current, complete, and well-written HowTo (especially if you're running (k)ubuntu and using a Hauppaugge PVR-150 card) is the one published in the aforementioned thread by Daniel Hyams.  If you're just starting out, that's the place to go.

Below is the original post I made on that thread, seeking information about tuning picture quality with MythTV.  Let me summarize, since that original post is a little long-winded and meandering.

1. I've got (what I think is) a powerful enough box (AMD64 3200+ with 512MB RAM), so I'm not really looking for ways to run "more efficiently".  Instead, I'm looking for ways to get the best possible quality picture.  

2. In addition, I'm not really looking to collect debugging help (though heaven knows I've got a few bugs that, despite ample googling, I am having a hard time finding any helpful info).  Nor am I looking to collect any more general "HowTo" information.  Both of these topics seem pretty well covered elsewhere.  What does NOT seem to be well covered is techniques for TUNING your picture to get the best possible quality.

3. The biggest picture quality problem I have right now is with "fast motion" programs, most easily seen with U.S. Football.  Motion can be "blurry" or "jerky" or "grainy" or "lacking detail" -- hard to put your finger on it, but definitely noticeable.  You can see these effects on some other broadcasts, but they're far less noticeable than live, fast-action sports with lots of panning.

4. While I'd like to focus on practical techniques for tuning, it seems important, at least in some cases, to delve a little bit into understanding some of the underlying technologies (e.g., XvMC, V4L, IVTV, etc.).  Again, there are plenty of general purpose resources on these topics, but not too many that focus on how to best tune them for a high quality MythTV recording or live picture.

5. Personally, I have a SD CRT television set, so this is my particular focus.  I'm sure that lots of MythTV folks have High Def TVs, but that's a whole 'nother set of technologies that I don't know anything about.

6. I am starting with very little knowledge, but eager interest to learn how to get the most out of my MythTV.  I'm hoping to learn and share information and techniques, but I don't think this will be a success unless other folks are willing to share as well.  

So... if you have questions (great) or answers (even better :D ) please jump in.

If we get any momentum going here, I'll take on editorial duties and get any useful stuff gathered up and posted somewhere appropriate (like an Ubuntu HOWTO doc and/or the MythTV wiki).

Cheers,
john

[Here's the original post from the HOWTO thread.  Nothing terribly useful here, but it does mention a few more specific technical questions, so I thought I'd include it for completeness]

> 
Thanks very much for this awesome guide.

Apologies in advance for what turned out to be a longish post. And for any "hijacking", but this seems like a great gathering place for Ubuntu MythTVers. If there's any signficant interest in this topic, I'll start a new thread and continue discussion there.

Thanks largely to this HOWTO, and a few other good ones, I've got things functioning at 90+% -- certainly enough to "deploy to the living room" and turn it over to the users (who will have to be convinced that this is better than the Tivo they've been asking for!)

I'm in the process of trying to fine tune things, especially the quality of the picture. I'm fairly new to TV, video, etc. (but not so much to Linux/Ubuntu), but very interested, and willing to spend some time learning and documenting the nuances of tuning a MythTV box. Seems like the general HowTo space is pretty well covered at this point, but there's very little gathered wisdom on tuning.

As a tiny bit of background: I'm mostly motivated to try to get the best possible picture on a Standard Definition old-fashioned CRT type television. And I'm mostly motivated to try to make watching sports on LiveTV under MythTV as close to "broadcast quality" as possible. And I'm using a fairly powerful processor (AMD64 3200+), so I'm not too worried about trading computing power for picture quality.

So I'm starting with a bunch of questions. Anybody that's got insight into these (or wants to add more, or disagrees with the question), I'd sure appreciate hearing about it, including pointers to other reference material. As I said, if I gather anything more useful than "tweak it until it breaks or looks better" I'll gladly gather it up and post it here.

Here are some of my starting questions:

1. What's up with XvMC? As far as I can tell, it's a feature supported by modern nVidia cards that, to be used by MythTV, needs to be compiled into the MythTV software. As far as I can tell, the current breezy badger 32-bit repository versions of Myth do NOT include XvMC support. I don't know this for sure, and would appreciate an expert opinion.

At this point, my opinion is based on running ldd on several myth binaries and not seeing any reference to the nVidia XvMC libraries (e.g.,
Code:

ldd /usr/lib/libmythtv-0.18.1.so.0 ldd /usr/lib/libmythavcodec-0.18.1.so.0 ldd /usr/bin/mythfrontend

1.a. How beneficial is XvMC to picture quality? Opinions seem to be mixed. What kinds of benefits is it supposed to provide?
1.b. If you DO use XvMC, are you not able to also use the "De-interlace Playback" feature?
1.c. If you DO use XvMC, are you not able to also use the "Custom Filters" feature?
1.d. If you DO use XvMC, are you not able to also use the "Use libmpeg2 for decoding" feature?

2. How do the various xorg.conf settings affect picture quality? What are appropriate values for Display "modes" and how do they affect quality? Do specific "modelines" provide enhanced quality? Are there other settings (besides the ones covered in the HOWTOs, like
Code:

Option "TVStandard" "NTSC-M" Option "TVOutFormat" "SVIDEO" Option "TVOverScan" "0.6" Option "ConnectedMonitor" "TV"

that one should be tweaking?

3. Does mythfrontend's Setup->TV Settings->Recording Profiles->MPEG-2 Encoders->LiveTV->Video Compression affect quality? For LiveTV, why not set these values as high as possible? What is the maximum effective bit rate? On this page, what is the "Stream Type" parameter?

4. What are the tradeoffs between using libmpeg2, ffmpeg, and XvMC (are these, in fact, 3 mutually exclusive options for mpeg-2 decoding?)

5. How do the various features that deal with picture size/scale/overscan interact? For example,
- you can set DisplaySize in your xorg.conf file
- you can use nvidia-settings to change the picture scale
- you can set TvOverScan in your xorg.conf file
- you can set values in mythfrontend's Setup->TV Settings->Playback->Overscan,
- you can set values in mythfrontend's Setup->TV Settings->Recording Profiles->MPEG-2 Encoders->LiveTV->Image Size (Height/Width)

Do they have any interaction? Any precedence? Is there a methodology for tuning them?

6. What does the General Playback->"Use Xv Picture Controls" feature do? Is Xv the same as XvMC?

7. How do you use the various nvidia-settings features to optimize playback? How do these features interact with other similar settings?

Sorry for the long post. Hopefully a few other people are interested in this topic.

Cheers,
john


---

### Post by greyhound4334 on 2006-01-16
On the original thread, Deon wrote:

> Hey greyhound4334

I'd be very keen on a "Myth Tweak" kind of thread.
Did you come right with your motion blur? I've solved this before by editing the recording profiles to be the same frame size as your capture card. i.e if you are capturing (in my case PAL) 720x576 then change the recording profiles from the default 480x480 to 720x576. I can't remember what the thinking was here - maybe some kind of resize for each frame drawn? I worked on this problem about 8 months ago so I can't remember the specifics.

Cheers
Deon


Hi Deon,

Thanks for the suggestion.  I tried setting recording profiles (both default and livetv) to 720x480 (I'm in NTSC land).  That didn't make a noticeable difference, though I haven't done a really strict A/B comparison.  

(Aside: part of the problem is that it's very hard to do an A/B comparison on livetv; especially since some of the "blur" problems are really hard to pin down.  I'm wondering if there's some technique -- analogous to a test pattern or a test tone -- that might be useful for judging the effectiveness of a particular adjustment?)

By the way, are you running de-interlace (if so, with what algorithm?) and/or filters (if so, which?)

Thanks,
john

---

### Post by greyhound4334 on 2006-01-16
Just for completeness, I wanted to mention the only other tidbit of info that I posted on the original thread:

> I did get confirmation from Matt Zimmerman - former Ubuntu MythTV maintainer - that indeed the Ubuntu MythTV packages were built *without* XvMC support.

Many threads I've googled on MythTV quality mention XvMC, though my sense is that people come down on both sides of the quality issue: some seem to report an improvement, some a degradation.  As far as I can tell, XvMC is *most* relevant if you are running a marginally configured machine and need to offload some of the MPEG decoding from your processor to your (nVidia only?) video card.  This is mostly speculation on my part, so I'd be glad to hear more about people's real-world experience with XvMC.

---

### Post by evil-boweevil on 2006-01-16
This is a good thread.  I've had the same problem watching basketball games.  The motion blur is really bad with all the panning and motion going on.  I've found that setting mythtv to 2x framerate for the deinterlacing helps a little bit.  But then that doesn't look great when watching other channels.

Also I think setting to 720x480 helps because I think it's the native resolution for recording with hauppauge cards.

I don't know if there is really going to be a good solution to this.

---

### Post by greyhound4334 on 2006-01-17
evil,

Thanks for the tip.  I'll try the 2xframerate and see if it helps.

I, too, worry that there may just be a limit to the quality that is not really acceptable for fast-motion sports.  I'm surprised that this isn't discussed more on the mailing lists.

One of my motivations is to figure out whether the Hauppauge cards have such a limit, and whether other cards offer better quality.  I'm willing to go buy a capture second card, which would be a nice feature anyway, if I can identify the issues and find a card that performs better.

Cheers,
john

---

### Post by deontaljard on 2006-01-18
Hi John

I setup a machine using the PVR150 how to yesterday and was expecting the motion blur that I usually have to contend with.  My test is to switch to one of our soccer channels and usually when the ball is kicked I experience this.  It was, however, as near to perfect as one can expect.  I switched from normal tv to the myth rendered one and could see no noticeable difference.

I think with the right settings it is possible to get the picture right.  I did make some changes that were different to the "how to".

1) all the ivtv "char-major" stuff was put into one file in /etc/modutils/ivtv as per instructions at [http://ivtv.writeme.ch/tiki-index.php?page=TvOutPal](http://ivtv.writeme.ch/tiki-index.php?page=TvOutPal) (they have an NTSC how to as well that needs to be followed to a point and then the PAL "how to" ) - instead of in aliases

2) another setting I recall under Settings => Appearance is something like "use gui size for TV playback" this is used when you are resizing your display to fit your TV.  Maybe yours is enabled and the machine is resizing the TVout and not keeping up on the fast motion ?

By the way I'm using a PVR350 and pushing the X display out through this card.
I've got a PVR 150 as well which I will use an Nvidia card to do the TVout - will keep you posted on the results with this (tonight maybe)

This problem isn't limited to Linux though - I run an XP box with MediaPortal and without tweaking the graphics card I get the same problem - so could be graphics card related.

Cheers
Deon

---

### Post by greyhound4334 on 2006-01-18
Hey Deon,

Interesting bit about ivtv.  I may give that a try.

Right now I'm planning to rebuild my kernel and try the 18.2 version of Myth (yes, venturing into the wild and compiling it from source).  While this topic remains near and dear, I have to appease the natives who are now quite nervous about a problem I'm having: if you pause LiveTV for too long (undefined period as yet), the frontend gets pretty confused.  Especially if you rewind.  As a result, video tapes are being mentioned as a "failsafe" around here: obviously I'm in danger of losing my audience!  This, plus a few other nuisances, are prompting me to try an upgrade.  I may be distracted on that for a bit.

I've made a ton of notes on alot of this stuff over the last 2  days though, so I'll definitely be back on this thread soon with more updates.

Cheers,
john

---

### Post by meastp on 2006-01-21
Hi!

Have managed to install mythweb, and noticed the fine-tune fields...
When I change a value in one of them, is it necessary to reboot the computer for the changes to take effect?

---

### Post by greyhound4334 on 2006-01-23
Sorry, don't know for sure about that.  If I was guessing, I'd say shutting down the frontend and backend would be sufficient to reload any parameters.  

cheers,
john

---

### Post by meastp on 2006-01-26
Ok... Could someone help me with a script that tunes to channel-frequencies i specify in a textfile, and then records like 10 seconds .mpg-file, adds 62500Hz to the frequency, records 10 seconds, adds 62500Hz etc.? 

Then tunes back to the channel frequency and subtracts 62500Hz, then records 10 seconds, subtract 62500Hz etc. Then next frequency in the text-file.

I don't know how to make the script, but i guess there would be a couple of loops. 
1. how many entries in textfile?
-loop-
2.entry in textfile
  3. remove 20 * 62500 Hz
  4. record 10 secs
  5. add 62500 Hz
  6. record 10 secs
  7. do this 40 times (20 before textfile-frequency and 20 after)
-endloop
8. go to next frequency-entry and repeat the process.

Then I could watch the frequencies and decide which to use.

relevant command-suff:
```

mythtv@tvboks:~/fine-tune$ ivtv-tune --frequency=196.250
/dev/video0: 196.250 MHz
mythtv@tvboks:~/fine-tune$ cat /dev/video0 > 196250.mpg

```

Note: the freqency is in MHz

Also I no longer have sound... any suggestions?

---

### Post by crane on 2006-02-02
This may be a silly question, but how are you guys connecting to the TV? Are you using a card with video out and a sound card?

---

### Post by crane on 2006-02-04
i also have a second question. When I go towebsite in the Mythweb my keyboard in not correct. Certain letters do not work, such as the "d" key. Is ther a setting I possibly missed that changes Keyboard layout? If I exit Mythtv and use Ubuntu all is fine. Any help or just a point in the right direction would be wonderful.

---

### Post by minirx7 on 2006-02-06
[QUOTE=deontaljard]Hi John

By the way I'm using a PVR350 and pushing the X display out through this card.
I've got a PVR 150 as well which I will use an Nvidia card to do the TVout - will keep you posted on the results with this (tonight maybe)

Cheers
Deon[/QUOTE]

Are you using the PVR350 to push the X display out of the PVR350 ?  How do you do this?  I went from Knoppmyth to Breezy, but i am unable to get the TV out to work on the PVR350.

How did you deal with the ivtvdev?

---

### Post by greyhound4334 on 2006-02-07
[QUOTE=crane]This may be a silly question, but how are you guys connecting to the TV? Are you using a card with video out and a sound card?[/QUOTE]
Crane, sorry for the delay.

Yes, I use an nVidia 5200 based video card that has svideo out.  They're commonly available (at someplace like newegg.com) for less than $80.  Another common choice is the Hauppauge PVR-350, which combines the video capture and the video out on one card.

For sound, I use an on-board processor with a S/PDIF (fiber optic) output to my AV Receiver.  Any normal sound card will do.

cheers,
john

---

### Post by greyhound4334 on 2006-02-07
[QUOTE=crane]i also have a second question. When I go towebsite in the Mythweb my keyboard in not correct. Certain letters do not work, such as the "d" key. Is ther a setting I possibly missed that changes Keyboard layout? If I exit Mythtv and use Ubuntu all is fine. Any help or just a point in the right direction would be wonderful.[/QUOTE]

Do you mean Mythbrowser?  I don't use that, so I can't help there.  Mythweb is the web-based frontend to Myth.

---

### Post by crane on 2006-02-08
Thanks for the help Greyhound. This lets me know I have all the hardware I need. Now I'll just find some How-Tos on enabling and setting Svideo out.

 I guess I do mean the Mythbrowser. I don't really use it but, it's not working right. Sometimes things just bug me if they aren't working right on my system whether I use them or not.;)

---

### Post by xinix on 2006-02-19
How exactly do you install mythweb (mythtv 0.19)

I had mythweb working under 0.18  but after updating to 0.19 it fails.
 I get this error when I try to load mythweb:
"Please install the MySQL libraries for PHP.
The package is usually called something like php-mysql."

I have php4-mysql installed and phpmyadmin works well.  So, I don't
think it's a lack of the php-mysql files.  Prior to updating to 0.19 I
completely removed 0.18 as a 'just in case'.
I've followed the readme and the instructions at:
[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html) . But I still get that
error.  Any sugestions?  I may try downgrading to 0.18 just to see if it still works.

---

### Post by oblib on 2006-02-20
crane,

Yes, MythBrowser has a bunch of keys reserved as shortcuts or something -- it's not meant to be used with typing. I had to copy/paste my name/password to get to some places. If you want to browse with a keyboard, you're better off bringing up Firefox. MythBrowser is intended to be couch-browsable with a remote control I think.

xinix, keep us posted on 0.19 progress (or more likely there should be a thread made for it) I'm interested in doing to upgrade myself, but don't want to hose things.

---

### Post by Titus A Duxass on 2006-04-02
Hi,
I hope this is right place for this.

I have followed the Hyams HowTo which is damn good.

I did experience the firmware problems with ivtv installation (Section 5.2) but these were cured with a cold restart after a 30 second delay.

Working:
Tv
Weather
News feed
DVD playback - though I think I will change mplayer to xine.

Outstanding issues:

1. MythBrowser does not have any plugins and therefore I cannot listen to BBC Radio which needs RealPlayer.  I can change the browser to firefox, but I want to use MythBrowser.

2. I cannot import DVDs - clicking on the button does nothing.

3. I cannot import CDs - again clicking on the button does nothing.

I have disabled auto-running of CDs, DVDs and plug-in media.
I have disabled screensavers and power management.

I get errors about opening tracks and having 0 files which is related to CD playback.

Any pointers would be most welcome.

Thanks

---

### Post by Titus A Duxass on 2006-04-12
I found out the importing (ripping) failure was due to missing directories.
I had to create in /mnt the follow directory store then a sub-directory of that named music.
Then I changed the permissions and all is well now.

The browser problem is also fixed, mythbrowser does not support plugins. So I changed the entry for mythbrowser to firefox in the mythtv setup area

---

