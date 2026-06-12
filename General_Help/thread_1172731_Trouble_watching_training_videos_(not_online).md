---
title: "Trouble watching training videos (not online)"
date: 2009-05-28
forum: General Help
---

### Post by akakingess on 2009-05-28
Ok, this may be such a simple question that I will be slapping my head when ya'll answer this one.  I am going through some Cisco training and am watching the CBT Nuggets (basically just a series of video training modules). So you are supposed to launch a browser and open the "home" page which has the links to the videos/training modules and for some reason I can't get them to load under Ubuntu/Firefox. I know they use ActiveX, so maybe that is the problem? Again, I am new to linux so any help is appreciated and if you need more details please let me know what info I can provide. Thanks in advance for any assistance you may be able to provide.

Earl

BTW, I am dual-booting Jauny and Vista Home Premium on the same laptop which is where I watch all of these nuggets, I would just prefer to be able to keep Ubuntu up all of the time rather than switch over to Vista just to watch the training vids. Thanks again.

---

### Post by QIII on 2009-05-28
If they use Active X, you're not going to be able to view them without some work.

Active X is probably the single most egregious offender in Microshaft's arsenal of security holes -- and I'm not sure I'd want it on any of my Linux boxes even if I could do it easily.

If you Google "Active X Linux", you'll get a million hits from everyone hawking a "linux version" of Active X.  I think MS is still working on DCOM, or may have fielded it.  But what's the point of having Windows and Gates in your world without walls or fences?

I'd be suspicious, but who knows?

I've heard CORBA might be a solution, but I've never experimented with it.

Personally, I'd just take the 90 seconds it takes to reboot and let your Windows partition take the risk of the security breaches...

---

### Post by akakingess on 2009-05-28
> **QIII said:**
> If they use Active X, you're not going to be able to view them without some work.

Active X is probably the single most egregious offender in Microshaft's arsenal of security holes -- and I'm not sure I'd want it on any of my Linux boxes even if I could do it easily.

If you Google "Active X Linux", you'll get a million hits from everyone hawking a "linux version" of Active X.  I think MS is still working on DCOM, or may have fielded it.  But what's the point of having Windows and Gates in your world without walls or fences?

I'd be suspicious, but who knows?

I've heard CORBA might be a solution, but I've never experimented with it.

Personally, I'd just take the 90 seconds it takes to reboot and let your Windows partition take the risk of the security breaches...
I appreciate the quick response, and I had feared that ActiveX was going to be the culprit. I also agree with you, I do not want to compromise my precious Ubuntu with anything that is suspect. I won't even install WINE for those reasons. I am trying to migrate to working solely on Linux, hence my trying to find some way to do this training under Ubuntu, but I will live with Vista long enough to finish this Cisco certification.  Thanks again for confirming my fear, no decent way to work around ActiveX (which I agree, is just agregious).

Earl

---

### Post by akakingess on 2009-05-28
I have one more silly question, I figured why go through all of the "fancy" opening in a browser and linking to the particular lesson, and just go straight to the source vids which are wmv unfortunately, but can't play those for some reason, I thought I was able to view wmv files within ubuntu (I forgot the name of the media player), but it is trying to open and then saying I need some sort of download and I allowed it to do the search to find whatever it needed just to play it and it was unable to find anything (open or 3rd party - which really baffled me) and it gave me a message that claimed it needed some windows speech decoder. Now, I am thoroughly confused and wanted to know if anyone could shed some light on just watching WMVs within Ubuntu's media player, or if there is another media player that I would have luck with.  Thanks again in advance for your time, attention, and willingness to share some knowledge with a noob.

Earl

---

### Post by QIII on 2009-05-29
I installed the codecs for wmvs somewhere along the line, but I was following a tutorial.

If you use the search bar at the top right, do a search on

medibuntu and wmv.

Found it:  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by dmizer on 2009-05-29
Hint: Try medibuntu.

---

### Post by akakingess on 2009-05-29
> **dmizer said:**
> Hint: Try medibuntu.
Thank you for the tip, I have installed Mplayer and will now use that as my default media player, but I am still getting the "audio codec" message that is not allowing the WMVs to playback, I have checked out the documentation and can't seem to find anything that relates to that issue, do you perhaps have any tips on audio codecs and how to find/install them for Medibuntu?  Thanks again for all of your help and I think I am on the right track if I can get around this silly audio codec issue (and no it is not telling what codec the files are using).

Earl

BTW, if it is easier for you to IM me via AIM, ICQ, or MSN I am online all night and available that way, but I will try not to take up too much of your time (as if I haven't already, right?)

---

### Post by ActiveFrost on 2009-05-29
ffmpeg is your friend ( convert or at least get some information about audio streams being used in your videos ) :p

---

### Post by akakingess on 2009-05-29
> **ActiveFrost said:**
> ffmpeg is your friend ( convert or at least get some information about audio streams being used in your videos ) :p
I did find out that the vids are using "Windows Media Audio Speech" codec. I don't know if that helps ya'll any, and I am currently googling, etc. to see if I can find some more info on that particular codec. Thanks again.

Earl

BTW, you may need to help me understand ffmpeg, is that a tool I can use to convert audio files or a way to get more info on the vids? That question is just a "if you have the time" I would like to learn as much as I can.

---

### Post by ActiveFrost on 2009-05-29
> **akakingess said:**
> I did find out that the vids are using "Windows Media Audio Speech" codec. I don't know if that helps ya'll any, and I am currently googling, etc. to see if I can find some more info on that particular codec. Thanks again.

Earl

BTW, you may need to help me understand ffmpeg, is that a tool I can use to convert audio files or a way to get more info on the vids? That question is just a "if you have the time" I would like to learn as much as I can.

Try this :  
```
sudo apt-get install faac faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs
```

Additionally, ffmpeg documentation : [http://www.ffmpeg.org/documentation.html](http://www.ffmpeg.org/documentation.html) ;)

---

### Post by andrew.46 on 2009-05-29
Hi akakimgess,

> **akakingess said:**
> I did find out that the vids are using "Windows Media Audio Speech" codec. I don't know if that helps ya'll any, and I am currently googling, etc. to see if I can find some more info on that particular codec. Thanks again.

If you have installed the Medibuntu MPLayer you also need to install the w32codec package from the same source as MPlayer uses one of these codecs for this type of file:

```

andrew@skamandros~$ mplayer -ac help | grep 'Windows Media Audio'
wma9dmo     dmo       working   Windows Media Audio 9 DMO  [wma9dmod.dll]
wmadmo      dmo       working   Windows Media Audio DMO  [wmadmod.dll]
[B][COLOR="Purple"]wma9spdmo   dmo       working   Windows Media Audio 9 Speech DMO  [wmspdmod.dll]
wma9spdshow dshow     working   Windows Media Audio 9 Speech DShow  [wmavds32.ax][/COLOR][/B]

```

> BTW, you may need to help me understand ffmpeg, is that a tool I can use to convert audio files or a way to get more info on the vids? 

A little bit of both :-). An excellent start is here:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

All the best,

Andrew

---

