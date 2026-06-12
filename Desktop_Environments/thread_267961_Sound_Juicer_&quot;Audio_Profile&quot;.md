---
title: "Sound Juicer &quot;Audio Profile&quot;"
date: 2006-09-29
forum: Desktop Environments
---

### Post by dschaller on 2006-09-29
I know I've seen a similar thread in here, but I still haven't found any answers to this: On 6.06 when Sound Juicer starts I get the message "The Currently Selected Audio Profile is not Available on your installation." When I click "change profile" things seem to proceed normally, but I get this message every time. Does anyone know what's going on? I don't even know what my "Audio Profile" is!

I just upgraded from Breezy to Dapper this week and I'm working my way through the audio bugs.

---

### Post by mitch.c on 2006-09-29
> **dschaller said:**
> I know I've seen a similar thread in here, but I still haven't found any answers to this: On 6.06 when Sound Juicer starts I get the message "The Currently Selected Audio Profile is not Available on your installation." When I click "change profile" things seem to proceed normally, but I get this message every time. Does anyone know what's going on? I don't even know what my "Audio Profile" is!

I just upgraded from Breezy to Dapper this week and I'm working my way through the audio bugs.
I haven't personally seen that message, but it would seem you have an invalid profile.
[LIST=1]
[*]Open Sound Juicer
[*]On the **Edit** menu, click **Preferences**
[*]Click **Edit Profile**
[/LIST]
You can also access those profiles by typing this at <ALT>+F2 or a prompt:
```
gnome-audio-profiles-properties
```
Try switching to each profile and see if you can determine which causes the error, then correct the problem, or install the needed codecs, or delete that profile.

---

### Post by mulvila on 2007-05-05
> **dschaller said:**
> I know I've seen a similar thread in here, but I still haven't found any answers to this: On 6.06 when Sound Juicer starts I get the message "The Currently Selected Audio Profile is not Available on your installation." When I click "change profile" things seem to proceed normally, but I get this message every time. Does anyone know what's going on? I don't even know what my "Audio Profile" is!

I have a similar problem since upgrading to Edgy. 

Currently there are no audioprofiles at all in my system. How could I get back the original set of audio profiles?  Where are the profiles located?

Have done some searching but nothing has come up so far.

Marko

---

