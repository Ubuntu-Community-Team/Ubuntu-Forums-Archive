---
title: "How to kill pulseaudio to play pSX in 9.10?"
date: 2009-10-30
forum: Gaming &amp; Leisure
---

### Post by kirbyboy on 2009-10-30
Hi, i'm trying to kill pulseaudio to play pSX emulator, but every time i kill pulseaudio, pulseaudio restarts by itself.
I even use a script, but it doesn't work.  This is what i use:

#!/bin/bash
# A script to disable pulseaudio, run pSX, then renable pulseaudio

gksu /etc/init.d/pulseaudio stop
sleep 1
gksu killall pulseaudio         # Forcefully ends pulseaudio if still running
sleep 1
exec ./pSX
sleep 1
gksu /etc/init.d/pulseaudio start

---

### Post by bruno9779 on 2009-10-30
```
gksu /etc/init.d/pulseaudio start
```

doesn't this mean that at the end of your script you restart pulseaudio?

wouldn't it be easier if you just:

ALT+F2

```
killall pulseaudio
```

before starting PSX manually?

---

### Post by kirbyboy on 2009-10-30
Before trying that script, i tried to kill it manually, but it has the power of the resurrection.

---

### Post by Warpnow on 2009-10-31
gconftool-2 -s -t bool /apps/gnome_settings_daemon/plugins/sound/active false

pkill pulseaudio

---

### Post by trendzetter on 2009-11-02
I had to add this line:

autospawn = no

in ~/.pulse/client.conf
and then 
killall pulseaudio
to stop pulse-audio from restarting automatically. I can now play warzone2100 and glest with sound. :D

---

### Post by kirbyboy on 2009-11-02
Adding autospawn = no in ~/.pulse/client.conf(i had to create the file) has worked perfectly, thanks.

---

### Post by Yeti can't ski on 2009-11-02
Thanks! Fantastic!

Creating the file and adding the line + doing ```
killall pulseaudio
``` allowed me to use an OSS only application without stuttering. 

Does anyone know if there is a way to restart bloody pulseaudio again without having to reboot?

---

### Post by ekilfoil on 2009-11-02
Does pasuspender not work?

pasuspender ./pSX

---

### Post by Yeti can't ski on 2009-11-03
> **ekilfoil said:**
> Does pasuspender not work?

pasuspender ./pSX

Hum, very interesting. Thank you. I will give it a try (not on a Linux system now, unfortunately).

But shouldn't we add "--" before the name of the executable file? 

Like this:

```
pasuspender -- ./<executable file>
```


At least, it is what this page says:

[http://linux.die.net/man/1/pasuspender]("http://linux.die.net/man/1/pasuspender")

---

### Post by ekilfoil on 2009-11-03
> **Yeti can't ski said:**
> ```
pasuspender -- ./<executable file>
```

That should work as well. "--" means it's the end of getopt style options like the "-al" in "ls -al".  On a completely unrelated note, that's how you would delete a file named "-rf":

```
rm -- -rf
```

Without that, rm treats -rf like options.

---

### Post by Yeti can't ski on 2009-11-04
No success with "paususpender". Instead of making audio work directly through ALSA I had no sound and the system became more instable. 

I guess that the blocking of autospawn in ".pulse/client.conf" + "killall pulseaudio" will be my official workaround for the time being. 

Thanks anyway!

---

### Post by kirbyboy on 2009-11-04
With the "autospawn = no", if you make a script with the next code:

killall pulseaudio
./pSX #(or the aplication you want to run)
pulseaudio -D

you can kill pulseaudio, play whenever you want without sound problems, and pulseaudio runs after without problems, at least it works for me.

---

### Post by Yeti can't ski on 2009-11-05
> **kirbyboy said:**
> With the "autospawn = no", if you make a script with the next code:

killall pulseaudio
./pSX #(or the aplication you want to run)
pulseaudio -D

you can kill pulseaudio, play whenever you want without sound problems, and pulseaudio runs after without problems, at least it works for me.

Thank you! "pulseaudio -D" was the missing part to reactivate PA after using the OSS-only application.

---

### Post by KIAaze on 2009-11-16
This might work too and is easier:
```
padsp GAMECOMMAND
```
From the man page:
```
NAME
       padsp - PulseAudio OSS Wrapper

SYNOPSIS
       padsp [options] PROGRAM [ARGUMENTS ...]

       padsp -h

DESCRIPTION
       padsp starts the specified program and redirects its access to OSS compatible audio devices (/dev/dsp and auxiliary devices) to a PulseAudio sound server.

       padsp uses the $LD_PRELOAD environment variable that is interpreted by ld.so(8) and thus does not work for SUID binaries and statically built executables.

       Equivalent to using padsp is starting an application with $LD_PRELOAD set to libpulsedsp.so

```

---

### Post by hikaricore on 2009-11-16
pSX just needs pulseaudio support (or better audio handling) and that's all there is to it.
I've never been able to run it even once no matter what i tried. >.<

---

### Post by cdctm on 2010-02-10
Hello everyone,

It's really depressing that to play with warzone or emulators I cannot use Karmic. I hate this. Using pulseaudio with the extigy usb that I've got, pcsx sounds like a drunk frying pan ^_^" 

Following these advices finally I'n now able to kill it. Just one minor problem, I don't have any kind of audio output in pcsx now. That's the error that come out from the terminal while runnig the .sh script:

ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
Audio open error: No such file or directory

:(

Thats the content of the script that I'm using:

killall pulseaudio
pcsx
pulseaudio -D

I need help, please...

---

### Post by Yeti can't ski on 2010-02-11
> **cdctm said:**
> 
Thats the content of the script that I'm using:

killall pulseaudio
pcsx
pulseaudio -D

I need help, please...

Is pcsx your executable? If yes, shouldn't you add "./" before it to run it like an executable? 

You said you are able to run the program (without sound) so is probably only a typing error in the message, but one never knows...

---

### Post by cdctm on 2010-02-11
If I add the ' ./ '
./pcsx: No such file or directory

Could you let me know what I should install to have audio working?
Thanks in advance

---

### Post by Yeti can't ski on 2010-02-11
Ok, so it is a systemwide command, and not a locally executable file. 

Sorry, but for the rest I am a real numb. 

Have you tried reinstalling/updating ALSA packages?

---

