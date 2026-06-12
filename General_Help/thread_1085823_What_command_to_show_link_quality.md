---
title: "What command to show link quality"
date: 2009-03-03
forum: General Help
---

### Post by 5BallJuggler on 2009-03-03
if i type "iwconfig wlan0" i get this

```
wlan0     IEEE 802.11bg  ESSID:"Livebox-9930"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:7E:00:5A:F6   
          Bit Rate=18 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=67/100  Signal level:-57 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

but i only want to display the Link Quality

Is it possible, if so what command do i need? i've tried using cut and line commands, but it does not display correctly

"iwconfig wlan0 | cut -c24-25"     gives this

```
 F
/s
it
en
67
id
re
```

and the line command only gives me the top line.

---

### Post by heindsight on 2009-03-03
try:
```
iwconfig wlan0 | awk '/Link Quality/{ print$1" "$2 }'
```
That will print something like:
```
Link Quality=80/100
```

You could also use:
```
iwconfig wlan0 | awk -F'[=/]' '/Link Quality/{ print$2 }'
```
which will just print:
```
80
```

---

### Post by 5BallJuggler on 2009-03-03
> **heindsight said:**
> try:
```
iwconfig wlan0 | awk '/Link Quality/{ print$1" "$2 }'
```
That will print something like:
```
Link Quality=80/100
```

You could also use:
```
iwconfig wlan0 | awk -F'[=/]' '/Link Quality/{ print$2 }'
```
which will just print:
```
80
```

That's great, thanks for your help, I had to use the cut command due to the app that i'm using it for doesn't like 2 sets of brackets

```
iwconfig wlan0 | awk -F'[=/]' '/Link Quality/' | cut -c24-25
```

---

### Post by heindsight on 2009-03-03
> **5BallJuggler said:**
> 
```
iwconfig wlan0 | awk -F'[=/]' '/Link Quality/' | cut -c24-25
```

Just keep in mind that if you ever get 100% link quality (although that's probably unlikely to happen in practice), that will report the quality as 10... 

Also, if you're doing it that way, you don't need the -F option to awk, you could just do:
```
iwconfig wlan0 | awk '/Link Quality/' | cut -c24-25
```

---

### Post by ibuclaw on 2009-03-03
Erm....
Why not just go for the obvious.
```
cat /sys/class/net/wlan0/wireless/link 
```
Much quicker that using pipes in bash (well... considering it is all done in < 0.08 seconds) :)

And besides, you have one flaw in your one-liner... you are assuming that the "Link Quality" will never be 100.

Regards
Iain

---

### Post by 5BallJuggler on 2009-03-03
> **tinivole said:**
> Erm....
Why not just go for the obvious.
```
cat /sys/class/net/wlan0/wireless/link 
```
Much quicker that using pipes in bash (well... considering it is all done in < 0.08 seconds) :)

And besides, you have one flaw in your one-liner... you are assuming that the "Link Quality" will never be 100.

Regards
Iain

thanks Tinivole, that makes things alot tidier.

---

