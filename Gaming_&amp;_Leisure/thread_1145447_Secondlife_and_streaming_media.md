---
title: "Secondlife and streaming media"
date: 2009-05-01
forum: Gaming &amp; Leisure
---

### Post by arilds on 2009-05-01
In the latest Ubuntu release (9.04), Secondlife crashes instantly when I enable any kind of streaming media in the Audio & Video tab in Secondlife Preferences.

Has anyone seen this problem before, and is there a solution to it?

It happens if I use the regular release or the test viewer.

---

### Post by Naiki Muliaina on 2009-05-02
What bits are in your PC, what viewer are you using to play Second Life, and what version of flash are you using? Also 64 bit or 32 bit?

---

### Post by arilds on 2009-05-02
Many good questions.  I have a 64 bit CPU and use the test viewer to play SecondLife.

Not sure about Flash; just upgraded Ubuntu from the Hardy release to 9.04 so I did not do anything with Flash, I just let the upgrade complete.

Would I need to download and install new Flash software?

---

### Post by Naiki Muliaina on 2009-05-02
Have you tried the repo for the OMVviewer? (change intrepid to jaunty in the repo lines of course ^^) 

[http://naiux.wordpress.com/2008/11/30/cracking-news-on-second-life-front/](http://naiux.wordpress.com/2008/11/30/cracking-news-on-second-life-front/)

Setting up my Jaunty Xubuntu properly today (havent migrated yet) so can have a test later on to see whats working and what isnt.

---

### Post by Naiki Muliaina on 2009-05-03
I have Jaunty Xubuntu with OMVviewer working fine on a 64 bit PC. Test viewer crashed a few times.

---

### Post by arilds on 2009-05-03
Thank you for your help.

---

### Post by Naiki Muliaina on 2009-05-03
Did you get it working?

---

### Post by arilds on 2009-05-03
Unfortunately it crashes.  I tried to start it from the shell, but I can't figure out which of the messages that is causing it to crash.

I created and attached a log file.  If you can help me understand why the software crashes even before I get a chance to log in, that would be very much appreciated.

---

### Post by JDRagsdale on 2009-05-06
I'm also using Jaunty 64bit, with the standard game interface (on wine) and having the exact same problem. If I even tick the enable streaming media box on the login screen, it immediately crashes to the desktop.
 
Will try to install the Flash 10 64bit beta tonight, maybe that will help/fix.
 
Any ideas would be appreciated.

---

### Post by arilds on 2009-05-06
That is exactly the same issue. I would be very interested to know if your Flash installation will fix the problem.

---

### Post by JDRagsdale on 2009-05-07
Well, didn't have time to update flash last night, will try again tonight. :P

---

### Post by arilds on 2009-05-07
I installed the latest secondlife test release, and the software does not crash anymore, but there are still no streaming music or video working at all.

---

### Post by kasper.s on 2009-05-10
This worked for me for streaming audio at 64-bit intrepid and jaunty. Video streaming still not working but does not crash.

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
Open the secondlife file into a text editor. Look for this block near the top:
     Code:
     ## - Avoids using any OpenAL audio driver.
#export LL_BAD_OPENAL_DRIVER=x
## - Avoids using any FMOD audio driver.
#export LL_BAD_FMOD_DRIVER=x 
Uncomment (remove the # from the front of) the "export LL_BAD_OPENAL_DRIVER=x" line. This will force the viewer to use the older but more compatible fmod audio engine instead of OpenAL. Be sure the line "#export LL_BAD_FMOD_DRIVER=x" line remains commented (has the # in front of it).
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

[http://vboards.stratics.com/showthread.php?p=836114](http://vboards.stratics.com/showthread.php?p=836114)

---

### Post by JDRagsdale on 2009-05-10
> **kasper.s said:**
> This worked for me for streaming audio at 64-bit intrepid and jaunty. Video streaming still not working but does not crash.

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
Open the secondlife file into a text editor. Look for this block near the top:
     Code:
     ## - Avoids using any OpenAL audio driver.
#export LL_BAD_OPENAL_DRIVER=x
## - Avoids using any FMOD audio driver.
#export LL_BAD_FMOD_DRIVER=x 
Uncomment (remove the # from the front of) the "export LL_BAD_OPENAL_DRIVER=x" line. This will force the viewer to use the older but more compatible fmod audio engine instead of OpenAL. Be sure the line "#export LL_BAD_FMOD_DRIVER=x" line remains commented (has the # in front of it).
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

[http://vboards.stratics.com/showthread.php?p=836114](http://vboards.stratics.com/showthread.php?p=836114)

Well... good news good news....  I installed the flash 64 beta and youtube works like a champ... AND ... I followed these extremely simple instructions.. AND..... I HAVE STREAMING AUDIO IN SECONDLIFE NOW!!!

Thanks Kasper!!

---

### Post by arilds on 2009-05-11
Worked for me too :))  Thanks.

The only mystery left to figure out then is the streaming video issue.

---

### Post by kasper.s on 2009-05-14
Yes indeed!! It would be so nice to get video streaming finally working on ubuntu/secondlife:)

---

### Post by HDave on 2009-05-23
@kasper.s -- thanks much, worked like a charm

---

### Post by zoe-scutterbug on 2009-05-25
sorry i decided my post not relevant to this discussion.

---

### Post by arilds on 2009-06-15
I assume there are no solution to this problem at the moment, so I guess I have to live without streaming video in secondlife.

---

### Post by Calendula on 2009-12-24
Ok, I have a question regarding Second Life, streaming audio, and whether or not there is any Linux software compatible with the Second Life viewer for streaming my own music in, especially with regards to live performance.

My husband is the Linux guru, but this is something he won't touch. So any help ANYONE can provide will be gratefully received.

I'm running Ubuntu, Karmic Koala. 32-bit.

---

### Post by adimac on 2010-03-25
> **kasper.s said:**
> This worked for me for streaming audio at 64-bit intrepid and jaunty. Video streaming still not working but does not crash.

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
Open the secondlife file into a text editor. Look for this block near the top:
     Code:
     ## - Avoids using any OpenAL audio driver.
#export LL_BAD_OPENAL_DRIVER=x
## - Avoids using any FMOD audio driver.
#export LL_BAD_FMOD_DRIVER=x 
Uncomment (remove the # from the front of) the "export LL_BAD_OPENAL_DRIVER=x" line. This will force the viewer to use the older but more compatible fmod audio engine instead of OpenAL. Be sure the line "#export LL_BAD_FMOD_DRIVER=x" line remains commented (has the # in front of it).
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

[http://vboards.stratics.com/showthread.php?p=836114](http://vboards.stratics.com/showthread.php?p=836114)

Well, I did that but... I lost all sound in SL

---

### Post by LewRockwellFAN on 2010-04-26
I can run Second Life pretty well under the  32 bit Sabayon, but under the 32 bit Ubuntu (current versions of both) I get an error message at start up:

"[I]Just so you know, your computer dows not meet Second Life's minimum system rfequirements. You may experience poor performance. Unfortunately the Second Life Support Portal can't provide technickal support for unsupported system configurations.

Visit [http://www.secondlife.com/corporate/sysreqs.php](http://www.secondlife.com/corporate/sysreqs.php) for more information?[/I]"

This message, and the page referred to, seem to imply an insufficiency of hardware but the hardware is the same when I boot in Sabayon. If I go ahead and log in everything is very slooooooooooooooooooooooooooooooooooooooooooooow, so much so it might as well be called a crash.

I've tried the OM Viewer (which is a fork of Snowglobe) with the same result.

Ideas?

---

### Post by LewRockwellFAN on 2011-01-02
Guess I should mention Hippo seems to work fine for me under Ubuntu now while the LL official client and several alternative clients don't work at all for me now. Been through a lot of updates of Ubuntu and the SL clients and the server software since my previous post and I haven't a clue about the why of what works and what doesn't. I'd suggest anyone having trouble getting an SL client to work keep trying different alternative viewers. By the time you've tried them all if you haven't got one to work, probably LL will have changed the server code, half of the viewers will have been updated, and Ubuntu will be on Zaftig Zebra. So you can start over. :)

---

### Post by socialcharlotte on 2011-01-02
> **arilds said:**
> I assume there are no solution to this problem at the moment, so I guess I have to live without streaming video in secondlife.
 
Arilds, Did you (or anyone else for that matter) get the video streaming working at 64?

---

### Post by LewRockwellFAN on 2011-01-07
Not I. I haven't been able to get an SL client to run under 64 bit Ubuntu 11.04. Hippo works for me under the 32 bit but it often (maybe one session out of 2) suddenly spikes the cpu usage to 100% or almost on both cores of my Pentium D. Then my it starts missing maybe half my keystrokes and then either it gets better or it logs me out. If I relog everything is fine. My attitude toward SL now is that it isn't worth working too hard to fix a problem because as soon as you do the server code, or the client code, or something in linux will change and it's broke again. So I just try clients under different linuxes until one works, cross my fingers and hope it will work longer this time until it breaks again. :(

---

