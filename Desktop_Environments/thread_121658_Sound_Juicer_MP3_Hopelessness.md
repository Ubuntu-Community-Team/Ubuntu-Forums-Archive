---
title: "Sound Juicer MP3 Hopelessness"
date: 2006-01-25
forum: Desktop Environments
---

### Post by Farthing-or-less on 2006-01-25
I have been trying to get Sound Juicer to encode MP3s on Breezy. Hopeless. I tried out the how-to at [http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html](http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html) but with no success. 

To clarify, I first installed the necessary files via Synaptic, then added the line, audio/x-raw-int,rate=44100,channels=2 ! lame name=enc , to the gnome-audio-profiles-properties as user. I had to change the name of the Profile from what the author instructed because I wasn't permitted by the properties to do so. I just called it MP3.  Then I selected MP3 as the encoding choice, ran Sound Juicer, and when I clicked the extract button, I got the message, "Sound juicer could not extract the CD. Reason: Could not create GStreamer encoders for MP3."  

I then decided to try the whole thing using sudo. I first sudo'd the properties window, added the new profile, and then ran sudo sound-juicer. This time when i clicked the Extract button, things seemed to go fine, and when the process was complete, I had new artist and album folders in my home directory. Unfortunately, they were empty.

Any suggestions? I have no problems encoding MP3s with RipperX or Goobox, but I can't get Sound Juicer to cooperate (or Totem for that matter, but that is a different topic)....

---

### Post by Farthing-or-less on 2006-01-25
Well, I will reply to myself in case anyone else out there wants to know how things went. 

I kept trying things but no success. I saw somewhere that after installing the various gstreamer plugins, I shoudl open a terminal and type gst-register-0.8 (as user), so I did that, but to no avail. Finally I went to the Sound Juicer help file to see what I could see. I double checked the gstreamer pipline line I had typed in to see if there were any problem, but there were none. 

Finally, I just copied the pipeline line from the help files, and pasted it into the editor where I had my original, and, though I don't know why.... things just worked. So there was something wrong there, but I could not catch with the naked eye, I guess. Case closed. Problem solved.:D

---

### Post by ysse on 2006-02-19
In case anyone else reads this, here's a beginning of a howto for getting Sound Juicer to rip MP3s. There may be other, better ways.

Install the packages **gstreamer0.8-lame** and **lame**.

In Sound Juicer's Preferences dialog, select Edit Profiles. Add a new profile using New. Set the profile name to MP3. Select the new profile in the list and click Edit. In the text box **GStreamer Pipeline** add the following:
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc
```
Set the **File Extension** to **mp3**, and be sure to put a check mark in **Active?**.

After all this, you need to restart Sound Juicer for the MP3 option to show up in the Preferences.

---

### Post by aysiu on 2006-02-19
This probably isn't the answer you're looking for, but with Goobox you don't have to do all that jumping through hoops to encode to MP3, as long as you have the proper packages installed via Synaptic.

---

### Post by Nolgthorn on 2006-02-22
[QUOTE=ysse]In case anyone else reads this, here's a beginning of a howto for getting Sound Juicer to rip MP3s. There may be other, better ways.

Install the packages **gstreamer0.8-lame** and **lame**.

In Sound Juicer's Preferences dialog, select Edit Profiles. Add a new profile using New. Set the profile name to MP3. Select the new profile in the list and click Edit. In the text box **GStreamer Pipeline** add the following:
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc
```
Set the **File Extension** to **mp3**, and be sure to put a check mark in **Active?**.

After all this, you need to restart Sound Juicer for the MP3 option to show up in the Preferences.[/QUOTE]

Thanks ysse, that worked PERFECTLY.

Edit: goobox looks good too, thanks.

---

### Post by Sidha on 2006-02-26
that works cool... it only encodes at 128kb/s
using the switch -b 320 doesn't seem to work from within Sound Juicer??

---

### Post by doclivingston on 2006-02-26
[QUOTE=Sidha]that works cool... it only encodes at 128kb/s
using the switch -b 320 doesn't seem to work from within Sound Juicer??[/QUOTE]

You need to change the pipeline in the audio profile editor, add "bitrate=320" after "lame". You can run "gst-inspect lame" from a terminal to see all the options the lame supports (there are a *lot* of them).

---

### Post by twowheeler on 2006-03-07
[QUOTE=ysse]In case anyone else reads this, here's a beginning of a howto for getting Sound Juicer to rip MP3s. There may be other, better ways.

Install the packages **gstreamer0.8-lame** and **lame**.

In Sound Juicer's Preferences dialog, select Edit Profiles. Add a new profile using New. Set the profile name to MP3. Select the new profile in the list and click Edit. In the text box **GStreamer Pipeline** add the following:
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc
```
Set the **File Extension** to **mp3**, and be sure to put a check mark in **Active?**.

After all this, you need to restart Sound Juicer for the MP3 option to show up in the Preferences.[/QUOTE]

Hey, it ***does*** work perfectly.  Thanks!

---

### Post by jamaas on 2006-03-08
I can encode a couple of cd's to mp3's just find but try another and get an error message ...

Sound Juicer could not extract this CD.
Reason: Invalid parameters

is the CD protected or have I got another problem?

Thanks

Jim

---

### Post by spd106 on 2006-07-08
> Sound Juicer could not extract this CD.
Reason: Invalid parameters
I had a similar message, and was able to proceed by removing a colon from the cd title obtained through cddb.

---

### Post by shilliard on 2006-07-08
> **spd106 said:**
> I had a similar message, and was able to proceed by removing a colon from the cd title obtained through cddb.

Thanks for pointing that out I had a similar problem and took out a question mark and it now works fine.

---

