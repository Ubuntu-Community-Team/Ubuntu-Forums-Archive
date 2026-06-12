---
title: "PS3/XBOX - Live Streaming"
date: 2013-09-02
forum: Gaming &amp; Leisure
---

### Post by stew3 on 2013-09-02
Hi all, 

Just wondering if anyone has had any experience of doing this on Ubuntu.

Basically, what I'd like to be able to do is stream my gaming from my PS3 and/or XBOX 360 via an Ubuntu box to Twitch.tv or uStream.

I'd guess that I'm going to need some hardware in order to pass through the HDMI signal into the Ubuntu Box - then back out to my TV, does anyone have any recommendations of video capture cards (USB or PCI - no preference)

I'm obviously going to need some software too so any recommendations for this would be great also!



Thanks in advance

Stew

---

### Post by TheFu on 2013-09-02
Depending on where you are in the world, this may be difficult, expensive, and/or illegal.

I see you want HDMI - that makes it harder and more expensive.
I don't think you can do this without using the analog HDCP hole, at least not with my research.  There is lots of hardware and software needed - most of it only works on Windows.  The Haupauge 1512 is probably what you want, but HDFury and BlackMagic also make HiDef video Capture stuff. The 1512 is the only box that captures audio - also look into the 1212 and the Collosus.  Using the component out cables, the video resolution will probably be down sampled to 480p - required by the HDMI standards.

Ok, so there might be a way to do it with MythTV and hardware compatible with it - again - through the analog output hole.  Without HiDef resolutions, capture is relatively easy and any $50 capture device compatible with Linux works. Again, look for MythTV compatibility.

Perhaps someone smarter than I will reply. I hope so.

---

### Post by stew3 on 2013-09-03
Thanks for the reply

I'm from the UK and have streamed PC gaming from my Windows machine with no problems (xSplit + Twitch.tv = win)

If I'm honest I've done a small amount of research - but I think I'll need to be doing a bit more in order to do it for the time frame I'm looking at - I'd like to be able to get my GTA V playthrough streamed

Money isn't really a huge deal, I've got £150 left over from another project and this was the next thing I wanted to get done. 

I'll post my findings here if and when I find out what to do!

---

### Post by TheFu on 2013-09-03
PC gaming is different than PS3 gaming, as you know.

I think xbox360 doesn't add HDCP to the HDMI output, but for the PS3, it is reported as doing that. Only the component out will skip the HDCP protections on a PS3 and stay hidef.  

I spent about a month looking into splitting HDMI (I needed audio to be split) and learned about HDCP.  I have a projector that doesn't do audio return and have a new HDMI-only output device. I'm not interested in replacing a perfectly great receiver that doesn't support HDMI at all, so splitting the audio and video out were my needs. Along those lines, it seems that many people try to record their gameplay from xb360 and PS3 devices ... 

I'm a huge Linux guy ... the only Linux-based solution that I know is to use 
* hauppauge 1212 HDPVR device (most others don't have Linux drivers)
* Component out
* toslink or digital RCA audio out
* Whatever drivers that MythTV uses to capture the play.

I own a newer Hauppauge 1512 - no Linux drivers. I'm not holding my breath.  Video processing is the only thing I do on Windows.

There are sub-US$100 devices that claim to "strip HDCP" - they are illegal in the USA and EU.  The hauppauge Collosus is the only device that I'm aware which ignores HDCP - alas [http://www.mythtv.org/wiki/Hauppauge_Colossus](http://www.mythtv.org/wiki/Hauppauge_Colossus) says that there are no Linux drivers. The BlackMagic cards, other Hauppauge and any ATI cards **will** honor HDCP. There are higher-cost devices that bend the HDCP rules - in the US$500-US$5000+ range. Those devices are not dependent on Linux - they are stand-alone.

The best thing to do is skip HDMI completely - use the component analog hole for as long as it exists. The next gen game consoles probably will not have any analog hole over 480i resolution.  Low resolution output will probably be going away too. My Roku3 only has HDMI out - nothing analog at all for video or audio. No other audio outputs either.  I've ordered 2 devices. 1 to split the HDMI into different signals and 1 to strip off the 5.1 audio into an RCA digital output.  It will be another month before they arrive.  All of this to listen to movies on an older high-end receiver and to be able to watch on a projector. I'm stupid. Reading 50 books would be cheaper and last longer.

I don't think any of this research is incorrect, but someone with more experience might post. We can hope.

Have you already picked out the recording hardware you will use?

---

### Post by dannyboy79 on 2013-09-05
i don't live stream BUT i do capture my xbox 360 gameplay using a HD-PVR model 1212 using the command line, audacity to capture my commentary, and then use kdenlive to edit it all together. It's 720p over component cables from my xbox 360. There are many guides on the net showing how to stream to twitch or justin.tv using a script (which actually just uses ffmpeg) so it is possible but with HDCP I seriously doubt it's going to be worth the hassle to try it over HDMI, not to mention streaming 1080p would require like a massive upload speed from your ISP. Just streaming 720p content requires around 5Mbps which is why I dont' stream, i only have .5Mbps

Good luck

---

