---
title: "Skype. Ubuntu. Microphone does not work."
date: 2009-01-09
forum: General Help
---

### Post by Roasted on 2009-01-09
So after success with Skype in Vista I decided I wanted to get Skype to work in Ubuntu so I can at least utilize it with contacting friends and whatnot.

Thing is, I can't get it to work. Half the time I can't even get my microphone to work. I have tried everything I know of. Using SoundRecorder, I tried to verify that my microphone works. One time I got it to work. Literally minutes later I tried to recoord myself again and it didn't work. The results are completely inconsistent.

I'm using Ubuntu Intrepid 8.10 64 bit. I have a Turtle Beach Montego DDL 7.1 PCI Sound Card that I plug my headphones/microphone into in order to use Skype and whatnot. If anybody can tell me the EXACT things I have to make sure that are enabled to get this to work, that'd be great. This is something I'd really like to have but, sadly, Skype in Ubuntu is giving me a headache where Vista worked since day 1. Can anybody help?

---

### Post by jamin_melville on 2009-01-09
Hi there, I had the problem of my mic not working in skype also. How I got it to work was open skype, then go to options, then sound devices, and from there change the "sound in" and "sound out" devices to something else other than default, for me it was HDA Nvidia, but I think that depends on your sound card. If you have a few things to choose from then it might be a bit of trial and error. good luck!

---

### Post by upapilot on 2009-01-09
Try using the microphone with kopete.

---

### Post by Roasted on 2009-01-09
> **upapilot said:**
> Try using the microphone with kopete.

What is kopete??



> **jamin_melville said:**
> Hi there, I had the problem of my mic not working in skype also. How I got it to work was open skype, then go to options, then sound devices, and from there change the "sound in" and "sound out" devices to something else other than default, for me it was HDA Nvidia, but I think that depends on your sound card. If you have a few things to choose from then it might be a bit of trial and error. good luck!


I know. I set the top line to my sound card and the other two to pulse.

C-Media CMI8768 (hw:CMI8768,0)
Pulse
Pulse

But my microphone still doesn't work.

I'm beginning to think it's a problem with my microphone in Ubuntu rather than a problem with my microphone in Skype. Other threads have confirmed that soundcard + pulse + pulse work fine, while I still get no microphone. Plus, like I said, sound recorder doesn't pick up my voice when I talk.

---

### Post by Roasted on 2009-01-19
Okay, problem here. I right clicked on my volume level in the upper right and went to open volume control. I went to preferences and I enabled "Microphone Capture." The recording tab appeared. 

This is what I see.

[http://s2.photobucket.com/albums/y36/Roasted/?action=view&current=volume.jpg](http://s2.photobucket.com/albums/y36/Roasted/?action=view&current=volume.jpg)

If I check the icon on the right to unmute it, and without closing that window, go into sound recorder, I hear my microphone working.

If I exit the volume preferences and go back into it, it magically mutes itself again.

What can I do to keep this thing unmuted??

EDIT

Okay, figure this one out. So I guess that muted feature I was talking about doesn't matter. I think, anyway. I put the rocker up 100% and recorded myself in sound recorder and audacity, proof that my microphone works in ubuntu intrepid. I then rebooted to test this theory. When I booted up, my microphone worked instantly without changing anything... however that mute icon was still there. 

Can someone shed some light on this?

---

### Post by zero777zero on 2009-01-19
sounds like a buggy driver, plenty of em in linux.

---

### Post by Roasted on 2009-01-19
Would this be something that is sound card related?

It's a PCI sound card. Maybe I should hook up my onboard card and see what happens.

Thoughts?

And does anybody else have any ideas as to what I can do to get this thing working? If it isn't already, that is. Like I said I don't know what I did different that caused it to work upon starting up, but if I had to guess, I guess it'd be that I was too focused on the muted icon on the right side and not as much on the rocker level of the mic.

Can somebody who has Skype working in Ubuntu 8.10 64 bit verify if this setting on their volume preferences is muted or not?

Right click volume icon, open volume control, recording tab. There's two icons under the level bar. Is one muted? If so, which one?


EDIT - I took out my PCI sound card and enabled my onboard card. My onboard card acts the exact same way my PCI card does. That icon is still muted. I guess it just matters that the volume rocker is turned up. I guess that's where my problem was initially and maybe I didn't even realize it. I was just really focused on the mute icon, I thought that was it. *shrug* If anybody could offer any insight on what exactly that does, I'd like to know. Because while I was troubleshooting, it seemed to work intermittently. Maybe a restart was the final push to get it working? *shrug* 

My only question now is, sound recorder and audacity work with my microphone and I can hear myself when I play it back. Only thing now is I can't seem to get it to work with the skype test call. I don't get the skype test call though, cause it'll say "you should hear your voice play back" but the woman IMMEDIATELY starts talking, so I'm like, uh, when would I hear myself talk back if she's yacking? *shrug*

---

### Post by Roasted on 2009-01-20
I looked on the Skype site and they said the following is required.

   ```
 * Software requirements
    * Qt 4.2.1+
    * D-Bus 1.0.0
    * libasound2 1.0.12

Technical details
Version 2.0.0.72
```

I searched synaptic and found that I had d-bus 1.2.4 installed and libasound2 1.0.17 installed. Seeing as though these are newer versions I figured that was okay. Qt on the other hand I'm not sure about, I don't find "Qt" in Synaptic. At first I thought Qt was regarding QuickTime, which confused me. Any input on that, anybody?

I got my microphone to work in Ubuntu. Turns out I had to enable the setting for my microphone to even be visible so I can unmute it. 

```
Right click your volume control. Go to open volume control. Click preferences. Check the box for microphone capture. A recording tab appears. Change the setting accordingly.
```

I did that and my microphone level was 0%, so I jacked it up to 100% and now sound recorder works fine. It's just I still don't hear anything in Skype. :(

---

### Post by SyberKowboy on 2009-01-21
I was having the same issue. I just basically did all the same things you have and got cranked the mic boost up. That did it for me but the quality is still terrible. I have an intel chipset. It might be a buggy driver or skype/driver compatability issue.

---

### Post by Roasted on 2009-01-21
> **SyberKowboy said:**
> I was having the same issue. I just basically did all the same things you have and got cranked the mic boost up. That did it for me but the quality is still terrible. I have an intel chipset. It might be a buggy driver or skype/driver compatability issue.

Quite honestly, I'm beginning to blame Skype. All this time I was convinced Ubuntu had something wrong on my end... only to find out that I had to click that little checkbox for Microphone Capture and drag the bar to the top to enable the sound.

My sound quality with recording in the program "sound recorder" is just fine. I just can't get it to work period in Skype.

A side note about microphones while you said your quality was bad... The other day on this computer in Vista I was on a mic chat in Left 4 Dead (online game) and my buddy said my voice was awful and he was hearing awful static. He kept blaming me. I called him an idiot. He said unplug your mic and plug it back in. I called him an idiot again. Afterwards, I did just that. He said wow, everything is clear now... simply by unplugging-replugging in that mic it fixed some static problem that other people were hearing from me in Vista. Maybe you're as lucky as I was to have a simple solution like that?

---

### Post by Neural oD on 2009-01-21
Quickly just to add to that - I too had problems with my mic - which I sorted out :) 
I then found that my recorded voice was very distorted - so make sure that your mic gain is not turned on - or else you will get very distorted sound!

---

### Post by Roasted on 2009-01-21
> **Neural oD said:**
> Quickly just to add to that - I too had problems with my mic - which I sorted out :) 
I then found that my recorded voice was very distorted - so make sure that your mic gain is not turned on - or else you will get very distorted sound!

Do you have Skype working?

If so, what are your sound settings within Skype? I can't get any combination to work. :(

---

### Post by paprikk on 2009-01-24
> **jamin_melville said:**
> Hi there, I had the problem of my mic not working in skype also. How I got it to work was open skype, then go to options, then sound devices, and from there change the "sound in" and "sound out" devices to something else other than default, for me it was HDA Nvidia, but I think that depends on your sound card. If you have a few things to choose from then it might be a bit of trial and error. good luck!

THX!! It's working now

I just changed the "sound in", have to test with every single choice, but it works for me.:D

---

### Post by diablo75 on 2009-01-24
All I do to get my mic working in skype is open up Skype's preference/control panel, go to where the Sound settings are, and change it from "default" to something else.  I actually have to go through each device listed in there one at a time, hit the "Test call" button to see if it works or not.  It's a little tedious, but easy.

---

### Post by polkadotteapot on 2009-04-04
What's the 'mic gain'?

My mic quality is awful and I want to be able to talk to my family tomorrow!

---

### Post by _Purple_ on 2009-04-04
I had similar issues while trying to run skype in intrepid and finally managed to solve it by following the sound setup mentioned in this [link.](http://ubuntuforums.org/showthread.php?t=843012) btw mine is 32 bits.

---

### Post by giancast on 2009-05-04
I just built a new computer, just because my old machine was very slow (10yrs old). Ubuntu ran fine in it, everything but skype. Now with the new machine I had the same issue Skype is dead microphone wise. This machine is brand new, I built it last week. I started with 8.04 immediately went to 8,10 and still Skype would not work, I could not even record myself with sound recorder. I could hear the test voice but not mine. I tried everything and nothing worked. Yesterday I upgraded to 9.04 and still the same issue, but this time voice recorder worked fine. Skype still nothing my voice was just very faint, today I decided to try something that I had never tried:
skype-options-sound devices there is a box that says Allow Skype to automatically adjust my mixer levels, by default it is checked and for the fun of it I unchecked a lo and behold now I can hear my voice loud and clear and Skype works fine, just as it does in windows.
I hope that this helps somebody.

---

### Post by waldherrvonbirnbaum on 2009-08-01
For getting skype working on a G40, G41, R40, R50, R50e, R50p, R51, T40, T40p, T41, T41p, T42, T42p, X31, X32 or X40 thinkpad with jaunty you need to set all volume controls to loud, just mute (with the little red X) microfone in alsa for preventing dis peeeep feedback. now go to skype-> options-> sound devices:

and set it there like this:
{{{sound in-  pulse
sound out- Intel 82801DB-ICH4(hw:I82801DB-ICH4,0)
ringing-   Intel 82801DB-ICH4(hw:I82801DB-ICH4,0)}}}

et voila: enjoy talking to your parents!

[[http://www.thinkwiki.org/wiki/AD1981B]](http://www.thinkwiki.org/wiki/AD1981B])

---

