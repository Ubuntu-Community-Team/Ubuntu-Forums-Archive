---
title: "How do I configure sound input?"
date: 2005-12-11
forum: General Help
---

### Post by Eleaf on 2005-12-11
Hello everybody!  
I am loving Ubuntu but I need to get sound input working.  I have all other sound working fine.

I have jack configured fine, and I can edit files in ardour and other audio applications fine, but I do not know how to configure sound input.  I have a sound card built into my motherboard wich has a sound out, microphone in, and sound in.  I'm wanting to get the sound in working so I can record some of my music.  I however do not know how to configure this, all I know is that sound input isn't showing up on the recording level monitor and it isn't working with any of the applications to record.

I'm just wanting to know how to configure my sound input to work.
Thank you anybody who helps!!! =-)

---

### Post by Zelut on 2005-12-11
This may sound pretty elementary but have you checked the Volume Control to make sure your "Capture" Devices are UN-muted?  I was trying to deal with a line-in as well (mic)--took me an hour before I thought to check that.

Give that a try.. let me know.

---

### Post by Eleaf on 2005-12-11
Alright, well I didn't have to mess with the mixer settings, I already had those set fine from a long time ago when I was trying this.  But I was able to get it working, SOMEWHAT.  At first, it was only coming in one channel, but I found out it was just old wires and connectors.  So now I have it coming in stereo using Audacity, but I'm not sure how to set this up for ardour.  So far this is great but I just need a little help getting ardour and jack set up and configured to accept sound in.  I'll tell you if I get any new progress.

Thanks! =-)

---

### Post by Eleaf on 2005-12-11
Also, I have another question.  Whenever I record with Audacity, the final recording is really, really bad quality.  During recording, the quality is great, but on playback, the quality is really bad.  But I have my recording settings in Audacity to the highest quality... = S

---

### Post by Eleaf on 2005-12-11
Ok, I have it working in ardour fine now.  But the quality is horrible.  It sounds fine before I record it.  But after I record it and play it back, it just sounds awful, nothing like the way it sound when I was recording it.  I don't understand what is wrong!! = S

---

### Post by Eleaf on 2005-12-13
I really need help with this.  This quality is awful!  :mad:

---

### Post by anil_robo on 2005-12-17
Good news!
 I have successfully recorded sound in Ubuntu few times just half an hour back! Read my post [here]("http://www.ubuntuforums.org/showthread.php?t=102377#6")

---

### Post by Eleaf on 2005-12-17
Yes I know, I have sound recording working.  But the quality of the recorded material is horrible, but it sounds fine when I am just monitering the input.

Again, I need help. :mad:

---

### Post by Eleaf on 2005-12-20
I am still stumped.  I am in dire need of assistance.  Does anybody know of something you must configure or change for the quality of the input?  Again, it sounds great while just monitering the sound, but once you listen to the recorded piece, it sounds way different.

Help!!!

---

### Post by bazzer on 2006-12-29
Hi there. I might not exactly be able to help straight off the bat - but have you identified if the levels of the recording are correct? What I'm getting at is that you can set a **recording level**, separate from a **monitoring level**, separate from a **playback level**. For example, you may be listening to the monitor as you're recording and it seems fine, but the **recording level** may be too high producing clipping distortion?

What is bad about the playback? Can you try to describe the sound?
I'm interested because I'm just beginning to try my linux box as a recording device (when I can figure JACK out!!). I've some knowledge of sound engineering principles but no practical experience so this may be all waffle!!

[edit: just noticed the post date a year ago!!]

---

