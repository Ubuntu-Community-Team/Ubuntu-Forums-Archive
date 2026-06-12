---
title: "Doom 3, Quake 4, Enemy Territory: Quake Wars sound delay fix"
date: 2011-03-12
forum: Gaming &amp; Leisure
---

### Post by Virus666 on 2011-03-12
Hi all,

I finally found the accurate sound solution for **Doom 3**, **Quake 4** and **Enemy Territory: Quake Wars**. As all we know that these **ID Software** games mainly use **OSS** and **ALSA**. However, for an unknown reason new **PulseAudio** releases have lack of compability with those old drivers/components. Thus, generally we hear up to 30 seconds boring sound delay... Here is the solution:

**alsa-oss**: ALSA wrapper for OSS applications

All we need to do is install alsa-oss package and start the game with **aoss** command.

Install the alsa-oss package with **Synaptic Package Manager** or via **Terminal**:

```
sudo apt-get install alsa-oss
```Then make OSS default for the game. I am typing for Quake 4; you may edit it for the other games.

```
quake4 +set s_driver oss +set s_numberOfSpeakers 2
```As you see there is no voice; do not worry; we have just made OSS default for your game and there is no OSS package is installed on your system. Exit the game.

Start the game with **aoss** command:

```
aoss quake4
```Ta taaa!... As you can hear, there is no sound delay and the voice synchronization is like a charm... :D

If you do not desire to enter aoss command eveytime, you may made a starter to the desktop which seems like at the attachment.

Have fun... :guitar:

---

### Post by figure002 on 2011-04-10
I got it working, thanks for the post!

There's one thing I don't quite understand. Do you run the command "quake4 +set s_driver oss +set s_numberOfSpeakers 2" from the terminal? And why is it needed?

---

### Post by Virus666 on 2011-04-21
> **figure002 said:**
> I got it working, thanks for the post!

There's one thing I don't quite understand. Do you run the command "quake4 +set s_driver oss +set s_numberOfSpeakers 2" from the terminal? And why is it needed?

Because, the out of box game works with ALSA and that driver has compability issues with PulseAudio. That is why those games have huge sound delays with new GNU/Linux distros. The code makes games's default sound driver as OSS. Then after we start the game with "ALSA wrapper for OSS applications" the sound comes after wrapping process, so the delay dissappears... :)

You may run the command via terminal or **Alt+F2** function.

---

### Post by figure002 on 2011-04-22
> **Virus666 said:**
> Because, the out of box game works with ALSA and that driver has compability issues with PulseAudio. That is why those games have huge sound delays with new GNU/Linux distos. The code makes games's default sound driver as OSS. Then after we start the game with "ALSA wrapper for OSS applications" the sound comes after wrapping process, so the delay dissappears... :)

You may run the command via terminal or **Alt+F2** function.

The funny thing is that I skipped that "+set" command, and used just the wrapper with the command "aoss <game>" which worked as well. It looks like the "+set" command isn't even necessary to get rid of the delay.

---

### Post by JuliaS on 2011-04-23
Thanks a lot for this post! It worked with me :)

Julia

---

### Post by Virus666 on 2011-04-23
> **figure002 said:**
> The funny thing is that I skipped that "+set" command, and used just the wrapper with the command "aoss <game>" which worked as well. It looks like the "+set" command isn't even necessary to get rid of the delay.

Well, since I changed the game's sound driver many times in order to get rid of the sound delay, my game's sound settings may be broken.

So, try to start the game with aoss command;

```
aoss <game>
```**IF** the sound delay still exists or there is no sound, change the sound driver of the game as OSS;

```
<game> +set s_driver oss +set s_numberOfSpeakers 2
```Then, start the game with aoss command;

```
aoss <game>
```You may make a game launcher for the last code:

[http://ubuntuforums.org/showpost.php?p=10553620&postcount=1](http://ubuntuforums.org/showpost.php?p=10553620&postcount=1)

---

### Post by Chislucas on 2011-04-23
I got it working, thanks for the post!

Lucas

---

### Post by emmar on 2011-05-07
It doesn't work for me. No sound at all. I have Ubuntu 11.04.

---

### Post by Shazzner on 2011-05-08
pasuspender always worked for me for ID games.

---

### Post by emmar on 2011-05-11
I tried:
pasuspender ./etqw +set s_alsa_pcm plughw:0
aoss ./etqw +set s_driver oss +set s_numberOfSpeakers 2

None of them works.

---

### Post by Virus666 on 2011-05-19
> **emmar said:**
> I tried:
pasuspender ./etqw +set s_alsa_pcm plughw:0
aoss ./etqw +set s_driver oss +set s_numberOfSpeakers 2

None of them works.


**pasuspender** never worked for me with **Qauke 4**. You need to install **alsa-oss** package first. Then start the game with **aoss** command; if there is no improvement, make the game's sound drive as OSS: **<game> +set s_driver oss +set s_numberOfSpeakers 2** . Now you can start the game with aoss command: **aoss <game>**

---

### Post by azurehoney on 2011-06-17
Nonono, you don't need aoss nor pasuspend.

Simply set "s_alsa_pcm" to "plug:hw".

```
seta s_alsa_pcm "plug:hw"
```

---

### Post by Rodney9 on 2011-07-23
> **emmar said:**
> It doesn't work for me. No sound at all. I have Ubuntu 11.04.

Same here, I did have some sound, now after running these commands Quake 4 is totally silent.

<snip>

---

### Post by Rodney9 on 2011-08-02
How can this be marked solved ? when some of us still have no sound ???

---

### Post by azurehoney on 2011-08-04
I guess because it was solved for original thread creator. You and him/her are not guaranteed to have exactly same sound issues.

---

### Post by Soulcage on 2011-08-04
```
quake4-smp +set s_alsa_pcm plughw:0 +set s_driver alsa +set r_alphaToCoverage "0"
```
```
quake4 +set s_alsa_pcm plughw:0 +set s_driver alsa +set r_alphaToCoverage "0"
```
```
doom3 +set s_alsa_pcm plughw:0 +set s_driver alsa
```
```
etqw +set s_alsa_pcm plughw:0 +set s_driver alsa
```
```
etqw-rthread +set s_alsa_pcm plughw:0 +set s_driver alsa
```
etqw-rthread and quake4-smp are the 64bit versions
also r_alphaToCoverage fixes some surfaces like windows and... you can change it in the console too.

---

### Post by Rodney9 on 2011-08-05
> quake4 +set s_alsa_pcm plughw:0 +set s_driver alsa +set r_alphaToCoverage "0"

Did the trick, Well Done, Thank You

---

### Post by tkmn on 2011-08-05
This finally solved my sound problems.
Except my output device was different: **front:0**

You can list outputs with **aplay -L**

```
~$ aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Live,DEV=0
    SB Live! 5.1 Dell OEM [SB0228], ADC Capture/Standard PCM Playback
    Front speakers
```

---

### Post by kaldor on 2011-08-06
Sound *was* working before after trying these fixes. The OP's solution did not work for me. This, however, did:

```
quake4 +set s_alsa_pcm plughw:0 +set s_driver alsa +set r_alphaToCoverage "0" 
```

But after taking a break for a few hours, there's no sound at all. Nothing I can do to make it work again. Any ideas?

---

### Post by Soulcage on 2011-08-07
kaldor make sure no other program is playing sound before you launch, pausing should be enough.
Also if you have been using something like mumble make sure you close it then: ```
killall speech-dispatcher
```

---

### Post by figure002 on 2012-06-04
In Ubuntu 12.04, the trick with aoss no longer works properly (I get distorted sound). But the following does work:

```
quake4 +set s_alsa_pcm plughw:0 +set s_driver alsa +set r_alphaToCoverage "0"
```

---

### Post by Bromden on 2012-06-04
Ok everything works fine!

You have to install _**ia32-libs**_ libraries on 12.04 beacuse they contain:
 lib32asound2-plugins - ALSA library additional plugins (32 bit)  lib64asound2-plugins - ALSA library additional plugins (64 bit)  libasound2-plugins - ALSA library additional plugins

Probably this way will be solved a lot of Wine's problems too.

To launch the game use the string suggested above:
> quake4 +set s_alsa_pcm plughw:0 +set s_driver alsa +set r_alphaToCoverage "0"

---

### Post by ant2ne on 2012-07-31
> **Soulcage said:**
> ```

[CODE]doom3 +set s_alsa_pcm plughw:0 +set s_driver alsa
```

:guitar:

Is there a fix for wide screen monitors and full screen play? The image looks a little distorted.

---

