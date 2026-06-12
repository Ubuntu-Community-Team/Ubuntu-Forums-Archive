---
title: "switching sound device"
date: 2011-10-23
forum: Desktop Environments
---

### Post by ginjabunny on 2011-10-23
I have just upgraded from 10.10 server with a light Gnome desktop to 11.10 server with full Lubuntu-desktop, everything seems to be working with a couple of annoyances but one thing I can't figure out is how to switch sound devices, by default it uses the built-in sound card but I have a usb dongle for a wireless speaker which I was using under gnome where I could switch using gnome-volume-control but there doesn't seem to be an equivilent on Lubuntu, I've tried using alsamixer and I can see the "SYNIC Wireless Audio" but can't figure out how to switch.

Any ideas?

GB

---

### Post by ginjabunny on 2011-11-14
I spent quite a while on this, I even set up a test server so I didn't break mine, the ALSA stuff seemed pretty complicated and I couldn't figure it out. 

I read some stuff about Pulse but was reluctant to install it but had to in the end as I couldn't find any other way of switching. So this is what I did 

sudo apt-get install pulseaudio

To get the device names use

pactl list cards (and use the following lines)

Card #0
  Name: alsa_card.pci-0000_00_11.5
  Active Profile: output:analog-stereo+input:analog-stereo
Card #1
  Name: alsa_card.usb-SYNIC_SYNIC_Wireless_Audio-00-Audio 
  Active Profile: off

so I switched off the PCI card, using

pactl set-card-profile alsa_card.pci-0000_00_11.5 off

it seems pulse automatically switched to the USB when I turned off the PCI card, and it remembers in the user profile and uses the USB when I plug it in. (I don't have speakers so not bothered that the PCI card is always off)

If anyone knows how to do it in ALSA please post how.

GB

---

### Post by Rodney9 on 2011-11-14
I'm  afraid I don't have an answer however these sites maybe of help 

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

and this one, more up todate, but still a work in progress, however very good - 

[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit)


Rodney

---

### Post by stinkeye on 2011-11-15
On Ubuntu 11.10 I use this script (uses pulseaudio) to toggle between usb and internal soundcard.
Don't know if it will work in lubuntu but you could glean some info from it.
```
#!/bin/bash

declare -i sinks=(`pacmd list-sinks | sed -n -e 's/\**[[:space:]]index:[[:space:]]\([[:digit:]]\)/\1/p'`)
declare -i sinks_count=${#sinks[*]}
declare -i active_sink_index=`pacmd list-sinks | sed -n -e 's/\*[[:space:]]index:[[:space:]]\([[:digit:]]\)/\1/p'`
declare -i next_sink_index=${sinks[0]}

#find the next sink (not always the next index number)
declare -i ord=0
while [ $ord -lt $sinks_count ];
do
    echo ${sinks[$ord]}
    if [ ${sinks[$ord]} -gt $active_sink_index ] ; then
        next_sink_index=${sinks[$ord]}
        break
    fi
    let ord++
done

#change the default sink
pacmd "set-default-sink ${next_sink_index}"


#move all inputs to the new sink
for app in $(pacmd list-sink-inputs | sed -n -e 's/index:[[:space:]]\([[:digit:]]\)/\1/p');
do
    pacmd "move-sink-input $app $next_sink_index"
    
done

#display notification
declare -i ndx=0
pacmd list-sinks | sed -n -e 's/device.description[[:space:]]=[[:space:]]"\(.*\)"/\1/p' | while read line;
do
    if [ $(( $ord % $sinks_count )) -eq $ndx ] ; then
        notify-send -i notification-audio-volume-high --hint=string:x-canonical-private-synchronous: "Sound output switched to" "$line"
        exit
    fi
    let ndx++
done;
```

---

### Post by ginjabunny on 2011-11-15
thanks for the suggestions, I will have a play at the weekend,

---

