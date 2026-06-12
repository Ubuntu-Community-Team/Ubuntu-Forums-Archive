---
title: "Sound disappears randomly"
date: 2008-12-07
forum: General Help
---

### Post by fizikz on 2008-12-07
I upgraded to 8.10 from 8.04 about a month ago, and everything seems great except that the sound vanishes randomly after some time (maybe a few hours or maybe a day or more). This didn't used to happen before with 8.04. I try restarting alsa but that doesn't fix anything. If I try to start any program that needs sound, it usually says it couldn't connect to the sound device or that it doesn't exist, etc. I've searched around but haven't found a solution yet, and I'm running out of ideas. Rebooting the system always fixes the problem but it's very annoying to have to reboot every time this happens.

---

### Post by stefangr1 on 2008-12-08
You're not the only one experiencing this problem, and there's (to my knowledge) no clearcut solution. However, you don't have to reboot, restarting X is should be sufficient, if you just press ctrl-backspace you'll be up again in 5 secs.

---

### Post by fizikz on 2008-12-08
I realize I'm not the only one with this problem, and that further surprises me that it hasn't been addressed. If you know of any solutions, even if not clearcut, please let me know. Also, I don't think that restarting X solved it for me, but I'm just going from memory. Next time the sound goes out, I'll try it again and see if it works. But in any case, I find little difference, practically speaking, between rebooting the system and restarting X. I still lose whatever I was doing. 

Now in terms of trying to find a solution, I noticed that once the sound disappears, doing 'alsa-utils restart' goes through the motions but doesn't bring the sound back. However, trying 'alsa-utils reset' fails. I think it does not find a sound device to reset. Also, any program requiring sound also does not find the sound device or gives a similar error. If any specific error message would be helpful, please ask. I thought that perhaps some faulty program is grabbing the sound device and not letting it go, but I couldn't isolate it or even determine if that's the case. Usually, the programs I have running at any given time include: aMSN, cGmail, firefox, and sometimes VLC and/or Rhythmbox. I hope a solution can be found soon.

---

### Post by orrorin on 2008-12-08
I'm running Hardy and sound devices are not available if I'm running skype. So, there are times when I need to quit skype to be able to use audio thru other devices.

---

### Post by fizikz on 2008-12-08
Thanks for the input. I'll keep that in mind, but I haven't even installed skype on this system. Please keep the ideas coming!

---

### Post by fizikz on 2008-12-10
I had an opportunity to test the effect of restarting X, as opposed to rebooting the system, when the sound disappeared again recently. Unfortunately, restarting X didn't solve it. I had to reboot. 

As a note, this time when the sound vanished or crashed, it kept repeating the last segment of the sound it was playing just before freezing. Another perhaps unrelated note is that I often notice a zombie process 'aplay' whose parent process is wish8.5 which I believe is aMSN.

---

### Post by Ganael on 2008-12-20
try to disable the login sounds in System>Administration>Login Window
under Accessibility
that helped for me :)

---

### Post by fizikz on 2009-01-10
I'll give it a try, but how would login sounds be related to the sound disappearing problem?

---

### Post by fizikz on 2009-01-16
Even after disabling login sounds, the sound froze once again today. This time it is continuously repeating a very small segment of an audio file that was playing at the time. 

This has happened to me with both Rhythmbox and now Amarok. Closing the program doesn't release the sound. I've also tried ```
sudo /etc/inid.d/alsa-utils restart
``` but that doesn't change anything.

First, is there a way to free the sound without having to restart? And secondly, how can this be avoided? This is seriously irritating, and it happens about every couple of days, or less.

---

### Post by Tarvok on 2009-01-16
I just want to let you know you're not the only one having this problem. At this very moment, the last sound it played before stopping is repeating continually. Restart just spat out a whole bunch of "Invalid card number" errors... and then made the noise louder. Reset gave me a fraction of a second of hope, because the noise quit for a moment... then started right back up again.

I'm hoping a solution can be found. It's happening a lot, so I'm having to restart a lot. I'm associating it with xmms2 (I recently started using Esperanza), but I think it was also happening before. I'll have to go back to using Rhythmbox exclusively to test that theory.

---

### Post by Tarvok on 2009-01-23
Since I've gone back to using Rhythmbox, as opposed to xmms2 (via Esperanza), my sound crashes have stopped.

---

### Post by fizikz on 2009-01-24
That's interesting, and I'm glad it worked out for you. In my case, the sound freezes have happened with Rhythmbox and with Amarok. Also, I don't necessarily need to be playing anything for the sound to simply disappear. This problem has been around for quite some time; I think I may eventually try a clean install of the latest Ubuntu. My current install has been upgraded to 8.10 from 8.04, and although it seemed to work great, it's the only idea I've got at the moment.

---

### Post by diJenerate on 2009-02-25
> **fizikz said:**
> That's interesting, and I'm glad it worked out for you. In my case, the sound freezes have happened with Rhythmbox and with Amarok. Also, I don't necessarily need to be playing anything for the sound to simply disappear. This problem has been around for quite some time; I think I may eventually try a clean install of the latest Ubuntu. My current install has been upgraded to 8.10 from 8.04, and although it seemed to work great, it's the only idea I've got at the moment.

My experience is almost identical to yours and I have concluded it isn't alsa that is crashed but pulseaudio. Alsa may be related to the problem but restarting it has no effect because it's not crashed afaik.

I have a Realtek ALC890 chip on my board with a Geforce8200 motherboard chipset and an Geforce 9400GT card in the PCi-e slot. I suspect that my problem is due to combination of hardware and their drivers and the fact that, as have you, I upgraded from Hardy to Intrepid.

It may also be related to the fact that my audio card was very very poorly supported under Hardy so if you have similar hardware to what I have described, we can start to narrow down the potential causes and finally solve this problem.

diJenerate

---

### Post by sunbear on 2009-03-25
Just wanted to add that this is also happening to me. When sound stops working I also notice that if I open up the sound controls (by double clicking on the sound icon on the top right hand corner of the screen),all of the choices in the "Device" menu have disappeared except for one called "Analog Devices AD1989B (OSS Mixer)".

i.e. The other 4 ALSA options have completely disappeared.

This seems to indicate to me that ALSA has encountered some kind of fatal problem. Does anyone have any idea where I could find any logs that might help to diagnose what might be wrong?

I have also noticed that even when sound is working, a really strange thing happens to sound under VMWare (Ubuntu 8.10 host, Windows XP Pro guest). Sound suddenly gets really choppy to the point that it's unusable. If I move the mouse around really quickly though (within the guest OS), then sound actually improves. I guess the mouse movement must be causing some interrupts or something.. who knows ...

---

### Post by yurtsev on 2009-03-27
I am also experiencing the same problem. It seems to usually happen after my computer goes into sleep mode and has been on for at least several hours. I'm on Ubuntu 8.04. Dell Inspiron 6000.

---

### Post by z_diver on 2009-03-30
I'm seeing the same thing on a fresh install so I wouldn't recommend anybody to reinstall as a means of fixing the problem.  I have a dell 400sc which has an Intel sound card on board.  It's so random it's hard to track down.  As with the OP, restarting alsa has not solved it, restarting x has not either.  Only a reboot works for me.  

Note: When sound goes out for me it's usually after I have been watching video on the web AND have used rhythmbox once or twice.  I've never gotten the looping that the OP mentioned, instead it'll just be quite when the next web video plays or something.

I do see Intel ICH5 and Analog Devices AD1980 listed under Devices when I open up volume control.  Neither are greyed out.

z

---

### Post by fcuk112 on 2009-03-30
i'm having the same issue, here's hoping that the problem will be fixed in jaunty.  as an aside, i did find that the following command brings the sound back (without rebooting):

press ctrl-alt-f2 to go into terminal:
```

pkill -9 -u username

```

it's almost the same as rebooting but at least it might save some time...

---

### Post by z_diver on 2009-03-30
> **fcuk112 said:**
> i'm having the same issue, here's hoping that the problem will be fixed in jaunty
Ouch!  That's a wait.  I've started troubleshooting PulseAudio through the highly informative thread below.  I'll probably write back to let everyone know how it goes.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

z

---

### Post by ianhaycox on 2009-03-30
I had almost the same problems after upgrading from 8.04 to 8.10. Playing a movie would stop sound working in Firefox, or conversely using youtube would prevent Amarok from playing, along with various other 'random' combinations.

My fix was to run

```

$ pulseaudio -k

```
 
straight after logging in and it fixed the problem.

---

