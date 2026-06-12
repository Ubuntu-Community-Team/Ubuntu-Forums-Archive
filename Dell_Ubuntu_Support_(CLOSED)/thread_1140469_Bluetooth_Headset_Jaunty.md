---
title: "Bluetooth Headset Jaunty"
date: 2009-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gaurab on 2009-04-27
Hi,

I have an Inspiron 1420 and a Dell Bluetooth headset (BH200). But they wont talk. 
I can find it with *hcitool scan*. 
I tried several tutorials (for hardy actually).
This one [http://www.sharpee.com/wordpress/?p=36]("http://www.sharpee.com/wordpress/?p=36") worked with hardy. But then I couldn't use the as the default systemwide audio device. I tried pulseaudio, without any success. Then I installed Jaunty from scratch and now I can't even have my headset work with mplayer.
Would really appreciate some help. 

Thanks,
Gaurab

---

### Post by rpineger on 2009-04-29
Hi Gaurab, I'm not a noob but might as well be when it comes to the mysterious workings of ALSA and hcitool. I seem to have my Nokia headset working on Jaunty on a Dell 9300 though. All I can tell you is what worked for me.

I was following the instructions here:
[https://help.ubuntu.com/community/BluetoothHeadset/](https://help.ubuntu.com/community/BluetoothHeadset/)
But when I came to the modprobe snd_bt_sco it gave a FATAL not found.

I then found an old thread from 2007 that recommended I look here:
[http://www.stgraber.org/category/gbtsco](http://www.stgraber.org/category/gbtsco)

So it seems that snd_bt_sco was part of bluez-btsco package and that it is deprecated as uneeded. 

All one needs to do is create/edit .asoundrc as follows:

```
sudo gedit ~/.asoundrc
```

..and add the following lines..

```
pcm.bluetooth {
type bluetooth
device XX:XX:XX:XX:XX:XX
profile "headset"
}
```

(Where XX:XX:XX:XX:XX:XX is the mac address of your headset found using 'hcitool scan')

To make it work, stop and start bluetooth.

```
sudo /etc/init.d/bluetooth stop
sudo /etc/init.d/bluetooth start
```

Hope that helps , Rich

---

### Post by pauna on 2009-05-01
I can confirm that the instructions given in the help.ubuntu.com link given and augmented by rpineger basically work. I got my Nokia stereo bluetooth headset working just now based on those instructions.

Although I did not have to do all the steps in there (for example editing /etc/bluetooth/ files) and BT pairing has a nice GUI in Jaunty, you do need pulseaudio if you want to dynamically select which output device you want to use (speakers or headset).

BTW, I did not have a bluetooth device present in /proc/asound/cards, but nonetheless I still get sound in my BT headset.

---

### Post by emerix on 2009-05-09
Hi!
I'm running Jaunty 64bit and I tried to connect my Nokia BH-102 bluetooth headset using the infos on this thread.
It seems that the bluetooth connection is OK for my setup : the handset appears on the list of "Known devices" in the bluetooth preferences. However, I have no success trying to configure PulseAudio. 
The command ```
pactl load-module module-alsa-sink device=bluetooth
``` fails : ```
Failure: Timeout
```
During this command my headset made a bip so I guess the connection was ok...
Do you know what I could do next to troubleshot this ?

---

### Post by gaurab on 2009-05-14
Thanks a lot Rich and pauna. After starting the thread I got real busy and forgot about it (I didn't get any notification about your replies!)

I followed your instruction and did OK till step 18 from [https://help.ubuntu.com/community/BluetoothHeadset/](https://help.ubuntu.com/community/BluetoothHeadset/)

But then as I was running kubuntu I couldn't find the PulseAudio controls, and logged out of kde and logged into ubuntu. And the nothing worked. I couldn't reproduce the success I had on KDE.

Then I found the post (mentioned at the top of [https://help.ubuntu.com/community/BluetoothHeadset/](https://help.ubuntu.com/community/BluetoothHeadset/))
[http://forums.overclockers.com.au/showthread.php?t=694010](http://forums.overclockers.com.au/showthread.php?t=694010)

And the author of the thread referred to a newer thread for JAUNTY
[http://forums.overclockers.com.au/showthread.php?t=780054](http://forums.overclockers.com.au/showthread.php?t=780054)

And it works like a charm.

emerix you may try to to visit the post. Its for JAUNTY (not sure about 64-bit though)

---

### Post by Dante_101 on 2009-06-13
Works great on jaunty 64 bit :D.

but someone knows how to enable the controls that are present on the bluetooth headset.
(play, pause , track change, etc).
I have dell XPS M1530, and the dell BH200 headset.

---

### Post by Boondoklife on 2009-09-11
I think someone already mentioned that but try adding uinput to /etc/modules.

On a side note all I had to do to get my headset working was

[LIST=1]
[*] install  padevchooser
[*]create the .asounrc
```
pcm.headset {
   type bluetooth
   device 00:0E:16:04:53:4B
   profile "hifi"
}

```
[*]then slapped together a script to enable and disable the headset
```

#!/bin/bash

#Lets check to see if the headset is connected
HEADSET_NAME_ASOUNDRC="headset"
HEADSET_QUERY=`pactl list | grep "device.string = \"$HEADSET_NAME_ASOUNDRC\""`
if [ -n "${HEADSET_QUERY}" ]; then
        echo Device is connected already.
        HEADSET_ID=`cat /tmp/asoundrc_id`
        pactl unload-module $HEADSET_ID
        killall padevchooser

else
        echo Device not connected.
        pactl load-module module-alsa-sink device="headset" > /tmp/asoundrc_id
        HEADSET_QUERY=`pactl list | grep "device.string = \"$HEADSET_NAME_ASOUNDRC\""`
        if [ -n "${HEADSET_QUERY}" ]; then
                padevchooser
        else
                zenity --info --text="Connection not established, try disconnecting and reconnecting\nthe headset from the bluetooth applet and try again."
        fi
fi

```
[/LIST]
All I do is start up my headset and click the button I have mapped to my connect command. This starts the padevcontrol applet and from there I just route the audio. When your done disconnect the headset with the script and turn it off.

Also not the pcm.headset and the variable HEADSET_NAME_ASOUNDRC need to match, in my case I named them headset.

Hope this helps streamline things for others.

---

