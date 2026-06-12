---
title: "Webcam app that works on mini 10v (Not cheese)"
date: 2009-09-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Greyed on 2009-09-18
Does anyone know of a webcam app that will work with the Mini 10v, other than cheese, and using the base 8.04 install from Dell?  Backports are ok.

Cheese records to ogv and has taken to the habit of having a bad header or something.  So when I try to convert from ogv to mp4 using devede I get a 4k, 1 frame(?) mp4 video.  Not good.

I have installed most of the other applications listed with the command "apt-cache search webcam".  Most do not work at all.

I've pulled vlc 0.9.9a from PPA.  It records the video nicely enough.  However it won't recognize audio when recording.  Playback works fine; love the feedback.

Any other suggestions?

---

### Post by Gooler on 2009-09-18
You can try Kamoso [http://www.kde-apps.org/content/show.php/Kamoso?content=111750](http://www.kde-apps.org/content/show.php/Kamoso?content=111750) , also kdenlive is able to record from the webcam.

---

### Post by Greyed on 2009-09-18
Kamoso is not available in the base 8.04 repositories for the Mini and the only version in PPA failed to build.

KDEnlive is in the repositories.  I'll give it a whirl.

---

### Post by Greyed on 2009-09-20
Just an update on my search.  kdenlive on 8.04 didn't recognize the webcam so it was a no-go.  I decided to try 9.04 UNR to see if newer versions might help.

Cheese - unusable, it is slower in 9.04 than it was in 8.04.  1/2 second delay when monitoring the web cam, recording doesn't get sound and is something like 5 seconds delayed?  Not sure.

Camorama - doesn't see webcam.

Camstream - doesn't see webcam.

vlc 0.9.9a - Sees video, I don't think audio works, 1/2 second delay when monitoring the web cam.

Haven't tried kdenlive yet but given that there's been no change in the other apps over their 8.04 counterparts I don't think there will be any there as well.

---

### Post by mikewhatever on 2009-09-20
Hi Greyed, I just tried Cheese on a similar hardware, Dell mini 10. In fact, I think we have different CPUs, but everything else should be identical. Cheese worked, but as you described, was slow displaying and recording video. Try changing the default resolution 1024x768 under Edit->Preferences to something lower, 320x240. That fixed video lagging for me, and rationalizing, I think the default resolution is simply not a match for an Atom cpu. As for the sound recording, does you mic work?

---

### Post by no2498 on 2009-09-20
see if you can find ( wxcam )

---

### Post by Greyed on 2009-09-21
> **mikewhatever said:**
> Hi Greyed, I just tried Cheese on a similar hardware, Dell mini 10. In fact, I think we have different CPUs, but everything else should be identical. Cheese worked, but as you described, was slow displaying and recording video.

True, however I am concerned that Cheese in 9.04 will still have the issue which made it unusable in Dell's 8.04, namely it records a video but somewhere in the first x frames is something that Decede cannot use.  IE, the purpose to which I want to employ the cam is moot.

> As for the sound recording, does you mic work?

Worked under Dell's 8.04.  Not sure about 9.04.

---

### Post by swallisa on 2009-09-23
Does anyone know of a way to install the Dell Web Chat application supplied with 8.04lts from Dell to an upgraded Ubuntu supplied 9.04unr?

---

### Post by Greyed on 2009-09-27
> **mikewhatever said:**
> I just tried Cheese on a similar hardware, Dell mini 10. In fact, I think we have different CPUs, but everything else should be identical. Cheese worked, but as you described, was slow displaying and recording video.

I have determined that at least on my 9.04 install the problem isn't Cheese, it's the display drivers.  I was in Yohoho! Puzzle Pirates' Bilge puzzle and 9.04 was laggy.  Popped over to my 8.04 install and it was perfectly smooth.  So far my instincts have been correct in keeping Dell's 8.04 for the superior hardware support.  9.04 UNR has been just on minor annoyance after another on that front.  :(

---

