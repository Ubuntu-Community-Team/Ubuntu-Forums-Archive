---
title: "Flight Gear Error"
date: 2006-06-29
forum: Gaming &amp; Leisure
---

### Post by CameronCalver on 2006-06-29
Hello i downloaded fligh gear from synaptic and when i run it this is what happens

cameron@ubuntu:~$ fgfs
opening file: /usr/share/games/FlightGear/Navaids/carrier_nav.dat
/usr/share/games/FlightGear/Navaids/TACAN_freq.dat
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
open /dev/[sound/]dsp: Device or resource busy
Audio initialization failed!
   There was an error opening the ALC device
terminate called after throwing an instance of 'sg_exception'
Aborted
cameron@ubuntu:~$

and i have been having sound problems with games for a while

---

### Post by Rayston on 2006-07-16
Did you ever get this fixed?&#12288;I am having the same exact error

---

### Post by vem0m on 2006-07-16
hmmmmmm

---

### Post by jISh on 2006-07-16
Try typing 
```
killall esd
```
into the terminal before playing.

Can type 
```
esd
```
after playing.

---

### Post by CameronCalver on 2006-07-16
that would work but i dont think you should have to do that ubuntu should really fix that

---

### Post by jISh on 2006-07-16
Meh it's not a big deal, you can just make a shell script to do it for you.

---

### Post by CameronCalver on 2006-07-16
can you give me instructions of how to do that plz

---

### Post by slimdog360 on 2006-07-17
install it using synaptic

---

### Post by b0rkman on 2007-11-21
The solution to this problem is to create a files called .openalrc - that is DOT+openalrc (which becomes a hidden file as are all configuration files in your home directory). Then enter the following text into the file:
	define devices '(pulse))

NOTE: there is no closing ' character - do not put one in. 
This will direct FlightGear's sound system to use the esd sound server as it's output device.

This file can be created in one shell command:

	$echo "define devices '(esd))" > ~/.openalrc

NOTE: The tilde character ~ in the above command is shorthand for your home directory. 

If you have the pulseaudio sound server installed then it gets complicated, unfortunately. I have found that only by killing the pulseaudio sound server will FlightGear sound work.

Happy flying!
tonymac

---

