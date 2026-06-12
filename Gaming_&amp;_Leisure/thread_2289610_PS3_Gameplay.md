---
title: "PS3 Gameplay"
date: 2015-08-05
forum: Gaming &amp; Leisure
---

### Post by lazarus_m on 2015-08-05
I just got my computer to the new 14.04 LTS and I have been wanting to record my gameplay.  I found a device that might work, [http://www.amazon.com/Diamond-Camcorders-supporting-composite-connection/dp/B000VM60I8/ref=sr_1_1?ie=UTF8&qid=1438786260&sr=8-1&keywords=diamond+vc500](http://www.amazon.com/Diamond-Camcorders-supporting-composite-connection/dp/B000VM60I8/ref=sr_1_1?ie=UTF8&qid=1438786260&sr=8-1&keywords=diamond+vc500).  On there they say that it can work for the 14.04.  My question is has anyone tried to use the device with Ps3 and on a Macbook with the 14.04 LTS?  Or are they any other devices that has worked with the 14.04, PS3 and the Macbook?  I really want to start recording and I need a device that will work.  Also, what other programs would I need to make everything work?  I'm very new to the whole video capturing thing.

---

### Post by TheFu on 2015-08-05
Don't know anything Mac specific with any of this stuff when running Ubuntu or any Linux.

If you are willing to use non-HiDef recording and stereo is fine, pretty much any of those cheap devices that works with Linux will work.  You will need an s-video output from the game console.  No HDMI, No component.  The yellow cable video is such poor quality, it just doesn't make sense.  Even s-video doesn't look very good compared to hidef stuff, however.

OTOH, if you want hidef video it becomes very difficult because most of the hardware doesn't have Linux drivers. Component video can be captured using the Hauppauge 1212 device.  There are development-versions of drivers for the Hauppauge 1512 (be certain to read the exact model versions support - not all sold as 1512 PVR2 from Hauppauge are supported. I have a 1512 and have to use Windows to record anything.

There is an easier way - this stand-alone device: [http://www.amazon.com/AGPtek-1080P-Click-Recorder-Capture/dp/B00MQQKDYE/](http://www.amazon.com/AGPtek-1080P-Click-Recorder-Capture/dp/B00MQQKDYE/)  It captures HDMI or Component video and stereo audio at 1080p, just connect some USB storage. No computer allowed when recording.  It isn't perfect - files are split at 2G (always) - which is about 20 min of 1080p hidef.  It supports fat32 and NTFS USB storage (nothing else).  These created files are not properly formed for other tools to do much with them as initial created (none of my editing tools work) and the h.264 encoder is more about real-time encoding at high bitrates than file size. Basically the files are HUGE.  I always transcode them down using handbrakeCLI to about 20% the original size without any visible loss in quality.  If I want to edit the file at all, it has to be transcoded using ffmpeg with  editor friendly settings.   $79 for the device - solved.  Storage is extra or use whatever you have laying around. USB flash drives make sense - just have 16G for 2 hrs of recording.  Make sense?

---

### Post by lazarus_m on 2015-08-05
That seems and looks perfect for now.  I just need something that will let me record then edit it slightly.  I have a 1 TB external HDD and a 250Gb external HDD so storage isn't an issue.  FAT32 is what the PS3 uses anyways so that is also no issue.  It can be edited to so degree connect?  HandbrakeCLI is that another program that I might need to get if so is it supported by Ubuntu?

---

### Post by TheFu on 2015-08-05
> **lazarus_m said:**
> That seems and looks perfect for now.  I just need something that will let me record then edit it slightly.  I have a 1 TB external HDD and a 250Gb external HDD so storage isn't an issue.  FAT32 is what the PS3 uses anyways so that is also no issue.  It can be edited to so degree connect?  HandbrakeCLI is that another program that I might need to get if so is it supported by Ubuntu?

It is a simple device for this purpose.  There are examples of the recordings on youtube. Check the amazon reviews. There are handbrake programs with and without a GUI for all the major platforms.

I can't figure out this: > It can be edited to so degree connect? Please explain.

---

### Post by lazarus_m on 2015-08-05
That's what I thought.  I'll definitely check YouTube and I already checked Amazon.  The last part my phone auto corrected it.  What I meant to ask can the video be edited after recording?   I know not directly with it but with some other program.

---

### Post by lazarus_m on 2015-08-08
So I took what you told me and I looked up the device.  I first looked at the AGPtek and done some youtubing and it I found out that I couldn't record in HDMI on the Ps3.  So I found a HDMI mini splitter that would bypass the HDCP.  After I found those I stared to look up different game recorders.  I found [SIZE=2]AVerMedia Game Recorder --C285.  I still need to re research but from what I found out so far is that it is the exact same thing as AGPtek in connection wise.  I would plug the 1st HDMI into the the Ps3 then to the splitter, then from the splitter to the 2nd one goes to the AVerMedeia.  Lastly, the 3rd cable goes from the Aver to the Tv.  Is there anything else that I am missing?  I know I need to AVerMedia, the HDMI splitter and 3 cables, I believe that is it.  What editing software are they for Ubuntu?[/SIZE]

---

### Post by TheFu on 2015-08-08
I don't know anything about the AVerMedia Game Recorder except that it is 2x more expensive. The output files may or may not be compatible with anything or nothing.  The output files from the AGPtek cannot be directly edited with any software I have. I have to transcode first into a compatible format. I use ffmpeg for that.

I don't edit on Ubuntu, except broad edits using mkvmerge (not a GUI).  VideoRedo is my tool of choice. It does NOT run under WINE.

---

### Post by MikeCyber on 2015-08-08
I edit Videos with Kdenlive, which is pretty good.

---

### Post by TheFu on 2015-08-08
> **MikeCyber said:**
> I edit Videos with Kdenlive, which is pretty good.

Does it support EDLs generated by other tools?
I need to batch my edit sessions with subtitle and caption edit/export support.  Need CC1 and CC3 support in these edits.

---

