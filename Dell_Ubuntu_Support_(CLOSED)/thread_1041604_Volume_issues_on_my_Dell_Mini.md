---
title: "Volume issues on my Dell Mini"
date: 2009-01-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by msuplee on 2009-01-16
The function buttons that control my laptop's speaker volume (ie., FN+4:mute, FN+5:volume down) seem not to be working properly. When I have my HDA Volume Control panel open and I press the mute key, for example, it mutes and unmutes the headphone column not the master. Also, I can't seem to find any way to use a headphone jack sense. When I plug in my headphones sound still comes out of the internal speakers. Please help. I'm new to Ubuntu. Please give it to me like I'm daft.

---

### Post by sirebral on 2009-01-16
Are you using 8.10?

---

### Post by msuplee on 2009-01-23
No, I'm using 8.04. But some of this started after running an Ubuntu update.

---

### Post by ugm6hr on 2009-01-24
Try right-clicking on the volume icon in the panel top-right, and selecting preferences.

Ensure HDA Intel ALSA Mixer and Master are selected.

---

### Post by wenfei on 2009-02-02
I have the same problem on my 8.04 platform. I think it worked prior to the large 182 item update that has caused so many problems with firefox and such. The function keys for volume do not work even after confirming the preferences that ugm6hr suggested.


thx in advance

---

### Post by Ryback on 2009-02-11
I'm having the same problems with my function keys no longer working to adjust the volume control (on 8.04).  Everything was still working for me after I installed the 180 odd updates from dell, I think this problem started after I adjusted my mic sound settings for skype (internal mic boost).  I also checked the settings which ugm6hr mentioned in his post.  Anyone got any further suggestions on this, or know if there is a bug reported anywhere?  Thanks.

---

### Post by iseeclouds on 2009-02-13
> **msuplee said:**
> When I plug in my headphones sound still comes out of the internal speakers.
anyone who knows how to fix this?

---

### Post by Ryback on 2009-02-17
> **iseeclouds said:**
> anyone who knows how to fix this?

I normally just work around it by right clicking on my volume icon, selecting Open Volume Control and muting the Speaker volume output.  If it isn't there you can add it by going to edit -> preferences.  

Although it would be nice to have a regular fix whereby sound stops coming out of speakers automatically when the mic is plugged in...

---

### Post by iseeclouds on 2009-02-17
> **Ryback said:**
> I normally just work around it by right clicking on my volume icon, selecting Open Volume Control and muting the Speaker volume output.  If it isn't there you can add it by going to edit -> preferences.  

Although it would be nice to have a regular fix whereby sound stops coming out of speakers automatically when the mic is plugged in...
thanks for the help. but there's no headphone option under "preferences". so i'm kinda stuck and don't know what to do.

---

### Post by Ryback on 2009-02-18
> **iseeclouds said:**
> thanks for the help. but there's no headphone option under "preferences". so i'm kinda stuck and don't know what to do.

Ahh I see, so you get no sound through the headphones either.  Sorry I'm not sure how you'd reconfigure your sound setup to get that back :?  Are you using the HDA(Intel) Alsa Mixer? (see ugm6hr's post).

---

### Post by iseeclouds on 2009-02-18
no, when i plug in my headphones i hear sound from both the headphones and through the internal laptop speakers. i want that when i plug in the headphones, the internal speakers mute. the option presented in this topic didn't offer me a solution. i tried this topic as well [http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620) but i got stuck with the codes. my computer can't seem to find them.

---

### Post by Ryback on 2009-02-19
> **Ryback said:**
> I normally just work around it by right clicking on my volume icon, selecting Open Volume Control and muting the Speaker volume output.  If it isn't there you can add it by going to edit -> preferences.  

Although it would be nice to have a regular fix whereby sound stops coming out of speakers automatically when the mic is plugged in...

> **iseeclouds said:**
> thanks for the help. but there's no headphone option under "preferences". so i'm kinda stuck and don't know what to do.

In that case the workaround I mentioned above should at least help.  You need to look for and mute the "Speaker" output when you go to volume preferences, not "Headphone" - all I was suggesting is that you manually mute the speaker after plugging your headphones in (it's not much of a workaround, but still :)).  Sorry to say I can't help with the problems you had from the other post though.

---

### Post by iseeclouds on 2009-02-23
well, i only have "master" and "pcm" in the volume control. nothing like "speaker" or "headphone" or anything.

---

### Post by dustigroove on 2009-02-25
> **iseeclouds said:**
> well, i only have "master" and "pcm" in the volume control. nothing like "speaker" or "headphone" or anything.

Right click on the Volume icon and select "Open Volume Control" then click on the "Preferences" button. Do you see "Speaker" listed as one of the options?

If yes, make sure the box for it is checked.

If no, you'll need to edit the alsa-base file.

```
sudo gedit /etc/modprobe.d/alsa-base
```At the end of file add "[COLOR=Navy]*options snd-hda-intel model=dell*[/COLOR]" (minus the quotes of course) and save.

Now restart ALSA sound system by entering the following:

```
sudo alsa force-reload
```You should now see the "Speaker" entry in Volume Control. (Note - it may need to be unmuted first.)

Hope this helps...

Cheers.

---

### Post by Ryback on 2009-02-28
> **msuplee said:**
> The function buttons that control my laptop's speaker volume (ie., FN+4:mute, FN+5:volume down) seem not to be working properly. When I have my HDA Volume Control panel open and I press the mute key, for example, it mutes and unmutes the headphone column not the master....Please give it to me like I'm daft.

I managed to fix this problem on my mini today.  Go to System -> Preferences -> Sound and check on the right hand side that ALSA is selected and "Master" is the source highlighted.  This seems to be a different setting to the one ugm6hr mentioned in post #4 in this thread.  

Are the highlighted entries in "System -> Preferences -> Sound" and "right-click volume icon -> Preferences" supposed to be the same setting?  If so there is a bug, if not then I guess this is the solution.

It seems to me there are too many ways to access too many different configuration screens for sound in ubuntu.  Maybe we could just do with one main preferences window once and for all!

---

