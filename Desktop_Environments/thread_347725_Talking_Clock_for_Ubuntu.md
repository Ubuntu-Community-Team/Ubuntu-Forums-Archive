---
title: "Talking Clock for Ubuntu"
date: 2007-01-27
forum: Desktop Environments
---

### Post by asnd16 on 2007-01-27
Is there a Talking Clock feature Available for Ubuntu.  I really would like my computer to announce the time at every hour.  A friend of mine has a program for windows and thought I would see if anyone know of a program compatible for Linux?

---

### Post by Aleksandersen on 2007-01-29
Mac OS X series have a feature that can announce the time on any given interval. :-k

I think the number one reason why you have not and will not see a feature like this in a Linux distribution any time soon is pretty simple: There are no voice libraries developed for Linux. The cost a fortune to make (just ask IBM or Apple, they have made a few!)

---

### Post by dare2dreamer on 2007-01-29
Well, that and there's about a dozen different ways to script up something to do the job.

Try reading "man festival" for a starting point.

---

### Post by asnd16 on 2007-01-30
> **dare2dreamer said:**
> Well, that and there's about a dozen different ways to script up something to do the job.

Try reading "man festival" for a starting point.

what? as in the festival festival? It looked quite nice!

---

### Post by ka9qlq on 2007-11-07
I made a talking clock called Al-clock because it uses my voice recordings :guitar: for my own use but am willing to email it to anyone

---

### Post by Rhubarb on 2007-11-07
This will speak out the current time:
```
date +%I:%M%p | espeak
```
Then all you have to do is to set up a cron job to execute this command (in a bash script or something) every hour.

Or you can grab saytime (saydate is in there too) from the repositories.
```
sudo aptitude install saytime
saytime
```

---

### Post by ka9qlq on 2007-11-08
Any clue on tweeking the outputs?

```
ka9qlq@dittohead:~/$ date +%I:%M%p | espeak
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000

```

and 
```

ka9qlq@dittohead:~/$ saytime
sox raw: '/usr/share/saytime/the_time_is.au': sample rate not specified; trying 8kHz
sox stio: Can't open output file '/dev/audio': Device or resource busy
child process returned a non-zero status 2

```

---

### Post by 5h4rk on 2007-11-09
Same here:

> chad@laptop:~$ espeak "Hello"
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000


---

### Post by Rhubarb on 2007-11-09
I don't know how to change the audio device that espeak uses.
You could try out festival (you'll need to get it from the repositories), festival has the same syntax as espeak does for this simple use.

Otherwise you could try this not-very-elegant solution:
```
#!/bin/bash
date +%I:%M%p | espeak -w time.wav
play time.wav
rm time.wav
```
Save this as time.sh, make it executable (chmod +x time.sh), then run it.
it uses "play" to output the wav file to your sound card, it might work better for you.

---

### Post by guyx666 on 2008-02-06
#my talking clock
# i use aoss in it ,

#!/bin/bash
#talking clock
echo "it is now," ; aoss espeak "it is now"
echo ; date +%I:%M%p ; date +%I:%M%p | aoss espeak

#i hope i have post this messeage in the good forum
#

---

### Post by nidelius on 2008-02-18
I had the same problem

```

PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
```


I realized that it was GizmoProject that locked down the sound device. So when I shutdown gizmo it worked fine.

Probably some program locked or are locking down your audio device
__________________

---

