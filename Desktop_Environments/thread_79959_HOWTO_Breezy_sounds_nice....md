---
title: "HOWTO: Breezy sounds nice..."
date: 2005-10-21
forum: Desktop Environments
---

### Post by Ranime on 2005-10-21
New Sound HOWTO

With all the fuzz going around, I felt compelled to write this new sound HOWTO.
First of all: I am NO Linux guru! I just want to use something else then the stuff from Redmond. I' ve tried lot's of diferent distro's and eventually I've stuck with Ubuntu :)

This howto is ment for any configuration, as long if ther is only **one soundcard** in your config! People with webcams that have built in microphones and stuff, or have more than one soundcard may run in some problems... The chipsets that drive the audio part for the cam or soundcard will be recognised as a(n extra) sounddevice! Check your alsamixer for certaincy!

Second: I'm Dutch, my English may not be all that well and my GUI is in Dutch too... That means I had to make some 1 on 1 translations that may not be all that acurate. Still I beleive you'll get the point while reading this howto ;) If not, I'll read it in your comments.

Well, having said all that. Let's get the sound up and running!

1. Make sure you have alle the universe, multiverse and restricted repositories in your repository list. If you're not sure if you do or if you don't, follow this guide: **[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)** and replace hoary with breezy. Do the replacement part **BEFORE** you do an apt-get update upgrade! Some error messages may concur. Saying stuff like "Could not conect to ftp://blablabla". That's because it isn't available yet for breezy. You can ignor those messages. It will be purged by apt-get.

In Synaptic make sure you've got the **smart pakage install** option enabled in te settings.

2. Go to your **ubuntu menu > system > preferences > sound** and disable the **start soundserver** option. Click close.

3. From a terminal:
```
sudo killall esd
sudo cp /etc/esound/esd.conf /etc/esound/esd.conf_backup
sudo gedit /etc/esound/esd.conf
```

4. Find this section:
```
...
auto_spawn=0
spawn_options=-terminate -nobeeps -as 5
...
```

5. Replace with the following lines:
```
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
```

6. Save the edited file.

7. From a terminal:
```
sudo apt-get install libesd-alsa0
sudo gedit /etc/asound.conf
```

8. Insert the following lines into the new file:
```
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000 *##use **41000** here, if you believe your sound is choppy...*
}
bindings {
0 0
1 1
}
}

```

9. Save the edited file.

10. From a terminal:
```
sudo ln -fs /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```

11. From a terminal:
```
sudo gedit /etc/libao.conf
```

12. Replace with the following lines:
```
default_driver=alsa
```

13. Save the edited file.

14. Open Synaptic and perform a **smart pakage install** on these pakages:
```
alsa-base
esound
esound-clients
esound-common
gstreamer0.8-plugin-apps
gstreamer0.8-plugins
gstreamer0.8-plugins-multiverse
libgstreamer0.8-0
libgstreamer-gconf0.8-0
libgstreamer-plugins0.8-0
linux-sound-base
```
Offcourse, if some of these pakages are already installed, you can skip them ;)

15. Close Synaptic.

16. Go to your **ubuntu menu > system > preferences > sound** and enable the **start soundserver** option. Click close.

17. Save and close all opened applications and reboot computer.

18. When back in gnome, test by playing a movie and a song (totem + rhythmbox)...

Your game-sounds problems should be over now. But I still haven' t managed to play Q3 and have Rhythmbox play mp3's... Still working on that one.

If for some reason your gamesounds dont play, try this. gedit and past this code:
```
esdctl off
sleep 2
your_game_here
esdctl on
```
save it with a **.sh** extension.

Execute the script from a terminal:
```
$ sh *script*.sh
```
And the sounds in the game should work (well, in Quake3 it should ;))
I have no idea for other games...

Again. In X you should ave duplex-sound now. In games you should have duplex sounds also (excluding midi's). But you can't use sound in X and in your game simultaniously (yet).

Enjoy!

---

### Post by derdewey on 2005-10-22
Thank you very much for that helpful howto!  My ESD wasn't working (dunno what happened...), it couldn't write to something.  Not quite sure what that meant.  Well, I did this howto and now I can play a video and listen to an mp3 at the same time.  Instead of before where I could do neither!

Thanks again!

---

### Post by aragorn905 on 2005-10-25
Perfect - Thanks for your sound HOWTO.  After dist-upgrading to Breezy, for some reason the sound stopped entirely.  Mixers worked, sample sounds "played" but you couldn't here them, etc.  The HOWTO fixed all this - beautiful sound back in Breezy again.  

-aragorn905

Insipron 6000 Laptop

---

### Post by Ranime on 2005-10-28
Tnx :)
But not all credits go to me. Ifound some out on my selve and found some stuff here and there and compiled it in to this howto ;)

---

### Post by poptones on 2005-10-30
I would like to add something (and maybe - hopefully - someone can offer another solution). I have an Nvidia motherboard with onboard realtek codec and the settings above have never worked properly for me. The sound under alsa has always been very poor with lots of "noise." Changing the setting "48000" to "44100" (ie making the codec output everything at 44100hz sample rate instead of 48000) is the only way I have found to get adequate sound output via alsa with this motherboard.

---

### Post by Ranime on 2005-11-03
[QUOTE=poptones]I would like to add something (and maybe - hopefully - someone can offer another solution). I have an Nvidia motherboard with onboard realtek codec and the settings above have never worked properly for me. The sound under alsa has always been very poor with lots of "noise." Changing the setting "48000" to "44100" (ie making the codec output everything at 44100hz sample rate instead of 48000) is the only way I have found to get adequate sound output via alsa with this motherboard.[/QUOTE]

I had the same problems with hoary. In breezy 48K seems to work (with me). But as always: If it works better for your config with 44k1, than use that setting.

I'll write the 441000 option in the conf file as an option for those with simular problems ;)

---

### Post by coaxx on 2005-11-06
I cannot find gstreamer0.8-plugins-multivers for breezy. Any hints?

---

### Post by linuxted on 2005-11-06
This worked great for mp3s.  I can't get midi files to play though.  Any ideas without resorting to manually installing programs?


Thanks

---

### Post by christooss on 2005-11-06
gstreamer0.8-plugins-multivers

The right one is

gstreamer0.8-plugins-multiverse

---

### Post by guoweiok on 2005-11-06
this one is very helpful!
thanks,man!

---

### Post by iNerdSure on 2005-11-07
Many thanks for the guide. I followed the steps, one-by-one. Twice. But I still can't get any sound. Been struggling in the sounds of silence since Breezy was released! Tried various solutions posted in Ubuntu and other Linux forums. SILENCE! NO SOUND! :(

Any other trouble shooting or diagnostics guide I should try? Thanks in advance.

---

### Post by Moebius on 2005-11-07
Put something with sound playing

Go to a console and type "alsamixer"

Check if your for muted items and un-mute them. 

Carefull when you do that, I had my sound to max and got blasted throught my headphones with Queen - Show must go on ;)

---

### Post by iNerdSure on 2005-11-07
Thanks, Moebius.

Run alsamixer in Terminal. Un-muted all channels and items. Still SILENCE - NO SOUND.

Tried music CDs, VCDs, DVDs. They all were recognized. Track numbers, song titles etc. Movies played ok, just SILENCE that's all.

In such situations, I wouldn't mind getting "blasted" in my ears. At least I would have achieved the success of breaking the (no)SOUND BARRIER. :)

What else should I try now? Thanks, again.

---

### Post by Copter on 2005-11-08
hi!

good howto. works without any problems on intel onboard soundcard :). although i still cant talk via skype and listen to b-m-p in the same time but i think its more like half duplex or skype issue.

copter :]

---

### Post by Spudgun on 2005-11-08
Worked great, thanks!

---

### Post by christooss on 2005-11-08
[QUOTE=Copter]hi!

good howto. works without any problems on intel onboard soundcard :). although i still cant talk via skype and listen to b-m-p in the same time but i think its more like half duplex or skype issue.

copter :][/QUOTE]

Change bmp's default output plugin(i think its OSS) to esound ESD or Alsa

---

### Post by Ranime on 2005-11-10
[QUOTE=linuxted]This worked great for mp3s.  I can't get midi files to play though.  Any ideas without resorting to manually installing programs?


Thanks[/QUOTE]
Sorry for my long absence :) (Been playing DOOM3 :D)

For the midi problem I don't have a solution yet. I believe you need another sound daemon for that, maybe something like SDL or so.

*@ iNerdSure*
Did you have sound in hoary? and if so, did you change your hardware in the meanwhile when you switched to breezy?

---

### Post by linuxted on 2005-11-10
[QUOTE=Ranime]Sorry for my long absence :) (Been playing DOOM3 :D)

For the midi problem I don't have a solution yet. I believe you need another sound daemon for that, maybe something like SDL or so.

*@ iNerdSure*
Did you have sound in hoary? and if so, did you change your hardware in the meanwhile when you switched to breezy?[/QUOTE]

Actually I switched from Fedora Core and didn't use breezy much.  The midi didn't work on Fedora Core either but things have been going so much better with Hoary that I wanted to give it a try.


Thanks

---

### Post by Copter on 2005-11-10
[QUOTE=christooss]Change bmp's default output plugin(i think its OSS) to esound ESD or Alsa[/QUOTE]thnx for a hint, but it is running on alsa already. on esd i got the same thing :/

---

### Post by Ranime on 2005-11-12
Intersting all... :)

---

### Post by madmusiq on 2005-11-25
Good posts.. it helped me.

---

### Post by RAV TUX on 2005-11-26
Awesome now the sound works for Solarwolf, and I can play my CD's....many thanks...:)

and answered my question in this thread:
[http://ubuntuforums.org/showthread.php?p=521341#post521341](http://ubuntuforums.org/showthread.php?p=521341#post521341)

...without getting all technical...thanks for the solution...thanks for the simplicity

---

### Post by Grae on 2005-11-26
does anyone know if this howto will work with hoary?

or of a howto that does work with hoary?

---

### Post by stalefries on 2005-11-26
Can someone move this?

---

### Post by Ranime on 2005-12-18
I'm glad it helped some people. I was struggeling for months befor all worked. With this thread I hope those who had the same problems could get their sound up and running much faster than I did! 

;)

---

### Post by ilbahr on 2006-01-09
hi,

I just want to add that virtual sound mixing works out of the box under breezy for my sound card: Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

All that is required is to change to alsa if you want to system>prefrences>multimedia system

change it to alsa. now virtual sound mixing work perfectly.

For any application that require oss just stick aoss command infront of it

aoss <application name>. This work perfect with realplay for example.
aoss realplay

For realplayer you can do that automatically by editing the realplay script shell find the line (this is near the end of the script)
$REALPLAYBIN "$@"

and replace it with

aoss $REALPLAYBIN "$@"

Now any application that require play (from sox package) replace play with aplay and it will work fine.

Now everything work fine you can play realplayer while opening totem and having gnubiff alert you of new emails no problems at all.

Those are my 2 cents of advise.

---

