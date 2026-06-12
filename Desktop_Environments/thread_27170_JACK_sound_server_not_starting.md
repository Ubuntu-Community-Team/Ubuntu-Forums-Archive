---
title: "JACK sound server not starting"
date: 2005-04-15
forum: Desktop Environments
---

### Post by Tarrasque on 2005-04-15
Hello everybody.

I'm new to Ubuntu but really seems great. I tried it on my Laptop (HP Pavilion dv1000) where no other distro I tried could recognize all the hardware. Ubuntu does.

Now I wanted to use JACK as a sound server. I installed the packages throug Synaptic seemlessly.

Problem is, when I start qjackctl it reports:

"Could not open ALSA sequencer as a client. MIDI patchbay will not be available
ALSA lib seq_hw.c446:(snd_seq_hw_open) open /dev/snd/seaq failed: No such file or directory
JACK compiled with System V support"

Then if I try to start the server anyway it stops and says:

"cannot load driver module alsa
Could not connect to JACK server as a client"

Can anybody help me, please?

Thx very much in advance.

---

### Post by bobmitch on 2005-04-15
I use Jack myself without any problems on Hoary, so I can`t help you personally.

You will get the best help in the world from the guys on #ardour at irc.freenode.net though - the author of jack (and ardour) himself is usually there as well - so if he can`t help you, nobody can. :)

---

### Post by Tarrasque on 2005-04-15
Edit to the above post> this is the full output of jackctl when starting the server. I hope it helps pinpointing the problem.


10:34:23.491 Startup script...
10:34:23.492 artsshell -q terminate
sound server terminated
10:34:23.777 Startup script terminated successfully.
10:34:23.778 JACK is starting...
10:34:23.778 /usr/bin/jackd -R -dalsa -dhw:0 -r48000 -p1024 -n2
10:34:23.791 JACK was started with PID=7577 (0x1d99).
jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
Couldn't open hw:0 for 32bit samples trying 24bit instead
Couldn't open hw:0 for 24bit samples trying 16bit instead
jack_create_thread: error 1 setting scheduler parameters after thread creation: Operation not permitted
cannot start watchdog thread
cannot load driver module alsa
10:34:23.887 JACK was stopped successfully.
10:34:25.890 Could not connect to JACK server as client.




Thx

---

### Post by bobmitch on 2005-04-15
It may be that you are trying to start the jack deamon in real-time mode without having the linux real-time kernel module installed.

In your qjackctl settings, make sure the 'realtime' option is unticked, and try again.

---

### Post by segrewb on 2005-04-15
I found these two suggestions (quick google search)

> Try running qjackctl as root (open a console, log in as root and type qjackctl &)  

and

> ran alsaconf from the terminal, then used a mixer (eg. alsamixer) to set volume levels. 

at this [website](http://mandrakeusers.org/lofiversion/index.php/t21046.html) .

Goodluck!

---

### Post by sto6ma9ch on 2005-05-09
Although not exactly, I did run into a similar scenario when starting up jackd with the alsa driver. 

**Hardware:**
Sony VAIO PCG-F560 notebook
256MB RAM
Intel PIII
Yamaha YMF-744B sound card

**Software/OS:**
Ubuntu Linux "Hoary" (5.04 patched with universe repositories added)
Installed ```
qjackctl
```

I ran ```
sudo modprobe snd-seq
``` to fix Rosegarden4's sequencer from endlessly looping at program startup. After that, the program would start, but there was no sound. I then focused my attention on Jack.

Here's the output of starting jackd the first time around with the alsa driver:

```
jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|1024|2|48000|1|1|nomon|swmeter|-|16bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: cannot set number of periods to 2 for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
19:56:06.506 JACK was stopped successfully.
19:56:08.435 Could not connect to JACK server as client.
19:56:27.674 Startup script...
19:56:27.675 artsshell -q terminate
19:56:28.066 Startup script terminated with exit status=256.
19:56:28.068 JACK is starting...
19:56:28.069 /usr/bin/jackd -dalsa -dhw:0 -r48000 -p1024 -n1 -S -i1 -o1
19:56:28.092 JACK was started with PID=8164 (0x1fe4).
jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|1024|1|48000|1|1|nomon|swmeter|-|16bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 1 periods
ALSA: cannot set number of periods to 1 for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
19:56:28.186 JACK was stopped successfully.
19:56:30.112 Could not connect to JACK server as client.
```

Starting jackd with the oss driver was fine ... except I couldn't use Rosegarden4 (or anything else with cool alsa stuff). Here's what I did to start jackd successfully:

I ran ```
sudo qjackctl
```
I clicked the Setup button
In the Setup window -> Settings tab,
[list]
[*]Driver = alsa
[*]Realtime = unchecked
[*]Force 16bit = checked
[*]Periods/Buffer = 5
[*]Input Channels = 1
[*]Output Channels = 1
[/list] 
I have no freakin' idea what all that stuff means, but I clicked OK to save the setup info., clicked the Start button to start the server, and Ta DA! Jack started w/alsa.

My $0.02; share yours.

sto6ma9ch

---

### Post by Karlos on 2005-06-15
What you have to do is type..

[SIZE=3]$ sudo jackstart -d alsa[/SIZE]

qjackctl should then be active

once you get rosegarden up and running there is an option in the settings to start the jack server when the program fires up . thats how i do it . I now open R-garden before anything else and hey presto!

---

### Post by fragmental on 2005-08-05
All I had to do was run qjackctl and then uncheck realtime and click start.

I had the same error before I noticed the post about turning real time off.  If I'd seen the setting I would have done it myself because I know that the Ubuntu kernel doesn't have a real time patch.

In order to get zynaddsubfx to work, i then had to use qjacktl to connect the pcm out to zynaddsubfx and that was it.

---

