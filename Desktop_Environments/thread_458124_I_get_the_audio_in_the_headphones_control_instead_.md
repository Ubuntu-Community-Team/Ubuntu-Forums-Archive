---
title: "I get the audio in the headphones control instead on master"
date: 2007-05-29
forum: Desktop Environments
---

### Post by madelman on 2007-05-29
I have my speakers plugged to the speakers port and I can hear the sound in them but when I try to use the sound control to control the volume the one handling the sound is the headphone control not the master. If I plug the speakers to the headphone port in my computer I do not hear anything.

Where can I configure this in ubuntu 7.04?

---

### Post by Pragmatist on 2007-05-29
I've attached a script callled "sound_info.sh"  Please download this to your home directory and then type these commands:

```
chmod a+x sound_info.sh
```
```
./sound_info.sh mysound.zip
```

Attach the file "mysound.zip" on your next post.

---

### Post by madelman on 2007-05-29
Here is the output.

Thank you.

---

### Post by madelman on 2007-05-30
The file is attached. 

....

---

### Post by Pragmatist on 2007-05-30
So everything sounds fine, but the controls are mislabeled?
  Is that correct?  What volume controls are you using?  Have you tried this:
```
alsamixer
```

So far I haven't seen anything too strange in the output you attached.  The master volume is a little low at 39%.  What happens if you play around with the controls in alsamixer?

---

### Post by madelman on 2007-05-31
"So everything sounds fine, but the controls are mislabeled?
Is that correct?"
>> No I think they are correctly labeled. 

" What volume controls are you using? "
>> Gnome Volume Control which is shown in icon in the Top Panel. It is Volume Control 2.18.0 GNOME/GStreamer

"So far I haven't seen anything too strange in the output you attached. The master volume is a little low at 39%. What happens if you play around with the controls in alsamixer?"
>> I have tried with alsamixer and it has the same problem. 

I am not sure if this could be the issue, but I have 2 speakers plugged to the subwoofer then the subwoofer goes to the speakers port in the computer. I noticed that the buffer is not actually sounding. I can hear sound out the speakers though. The sound is controlled by the headphone control in both volume control tools. When I try to increase the sound for the master, it does not do anything, but when I try to increase the volume with the hedphones control It does increase the volume, which is not the highest and I can hear that the subwoofer is not playing anything.

Also I connected other speakers directly without any suwoofer and the same thing happened, headphones control is the one increasing the sound.  I am attaching a screenshot of alsamixer. If you see the master volume is totally low. 

thank you.

---

### Post by madelman on 2007-05-31
here is the file.

---

### Post by Pragmatist on 2007-05-31
FYI, "MM" means that it is muted.  To toggle mute on and off in alsamixer, you press "m" on the keyboard.  You might want to try muting and unmuting different combinations to see what is going on.

I don't have any columns called "headphone".  To control the volume of the headphone jack, you use the "Phone" control (which you also have).  So, I tend to agree with you that it has something to do with how you are connecting the speakers.

What brand and model of speakers are you using?

What brand and model of sound card are you using?

---

### Post by madelman on 2007-05-31
What brand and model of speakers are you using?
>> Harman/Kardon  HK-395

What brand and model of sound card are you using?
>> It says is an Integrated ADI 1885 (Audio Devices Inc) 
SoundMAX Integrated Digital Audio 

Computer is a Dell  Dimension 2300

---

### Post by Pragmatist on 2007-05-31
Are you using the onboard sound, or did you get a seperate sound card?

Have you tried these instructions?:
[http://support.dell.com/support/edocs/acc/hk395/en/setup.htm](http://support.dell.com/support/edocs/acc/hk395/en/setup.htm)

---

### Post by madelman on 2007-05-31
Are you using the onboard sound, or did you get a seperate sound card?
>> onboard sound

Have you tried these instructions?:
>> Yes, That's how I have the speakers connected.

---

### Post by Pragmatist on 2007-05-31
> **madelman said:**
> I have my speakers plugged to the speakers port and I can hear the sound in them but when I try to use the sound control to control the volume the one handling the sound is the headphone control not the master. If I plug the speakers to the headphone port in my computer I do not hear anything.
Where can I configure this in ubuntu 7.04?

This was your original post.  So, you CAN control the volume.  You just have to use the "headphone" controls to do it.  If you want to hear something when you plug the speakers into the headphone port, you need to increase the volume on the "Phone" setting in alsamixer.  Can you increase/decrease the sound with the physical knob on the speaker?

I should have asked for a clearer definition at the beginning.  What exactly do you want to accomplish?

---

### Post by madelman on 2007-06-01
I think the problem is not the way the speakers are connected. 

The problem is that the speakers are connected to the right port and I have a subwoofer, which is not working. The volume control is handled by the headphones control and that is not right, since it recognizes the speakers as a headphones instead using the master volume control. I can use it like that but that is not the point. I can increase the volume with the GNome Volume control and alsamixer volume control using the headphones controls only. 

I was searching about this issue and it looks more like the problem is about channels handled by ubuntu and the drivers used for this sound card.  Most of the problems I have found are similar but on laptops. The master volume does not work. It looks like ALSA drivers have to be installed in certain order during the ubuntu installation, but I am trying to understand more about how the channels are configured.

---

### Post by herroy on 2007-06-02
I have a similar issue.

THe volume control knob on my keyboard increases the "treble" option instead of "master volume". I can increase the master volume manually using the mouse and dragging it up/down abd it works fine. My mouse scroll wheel also increases the master volume too in alsamixer,

Tried using gnomes keyboard shortcut app and it still dosnt work.

Any suggestions?

---

### Post by vruzeda on 2008-02-27
I get the same problem...

I'm using Ubuntu 7.04 and I'm using my onboard sound card:
```

$> cat /proc/asound/cards
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1885 at 0xe8181000, irq 22

```

I'm using a generic speaker with subwoofer from Clone manufacturer. In Windows, the speaker gives me good quality sound, but in Linux, it appears to be a big piece of crap.

Both alsamixer and Gnome Volume Control (2.18.0 using GStreamer 0.10) associates the speakers volume with the headphone channel, and the Master handle doesn't changes a bit of it.

I can't stand listening to music in Linux since the sound is terrible. Has anyone found a solution to this problem?

---

### Post by pantomax on 2008-03-09
I found this answer in another post and it worked for me:

System->Preferences->Sound->Default mixer tracks - This is where you can select what setting(s) the volume keys should control in Gnome.

---

### Post by vruzeda on 2008-03-10
Thanks, pantomax, that were another question I was trying to solve.

But the problem isn't it: I'm not trying to adjust wich volume I'm controlling by keyboard, but to adjust wich channel is associated with my speakers.

It's not a style question; I don't mind having my speakers in the Headphone channel, but I do mind having the low quality sound of a headphone in my speakers + subwoofer (wich could give me a lot better sound then it's actually giving).

---

