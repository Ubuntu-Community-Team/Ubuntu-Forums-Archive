---
title: "Looking for Gnome-bluetooth"
date: 2006-06-03
forum: Desktop Environments
---

### Post by MrGreen on 2006-06-03
Hi,

Just got Dapper installed ... ran automatix 

but I cannot seem to find gnome-bluetooth ?

Has it been changed or should I be looking for something else?

TIA

---

### Post by angkor on 2006-06-03
The package gnome-bluetooth is in universe.

If you installed gnome-bluetooth, can start the bluetooth manager with the command: gnome-bluetooth-manager. 

Maybe this is what your looking for?

---

### Post by toorima on 2006-06-03
Is the gnome bluetooth manager any better then it was in breezy? used kbluetoothd before which is great but don't want to use kde stuff if possible

---

### Post by adam.tropics on 2006-06-03
I have found bluetooth in gnome a bit of a mess and not at all unified in approach. The gnome-bluetooth for recieving is the best bit though. My biggest problem has been sending information via obex server. I have found it slow, and with an incredibly long start delay. It does all work, it's just not great. I am hoping bluetooth might be properly addressed with Edgy, as it surely deserves some TLC !!

---

### Post by JoWilly on 2006-06-03
Yea you can search a long time for gnome bluetooth. Its a big mess.

Fortunately there is a google summer of code project that is taking care of this (by Mattew Garett I think). Hope it'll be in egdy.

---

### Post by adam.tropics on 2006-06-03
> Fortunately there is a google summer of code project that is taking care of this (by Mattew Garett I think). Hope it'll be in egdy.

Excellent news! Look forward to seeing how things develop.

---

### Post by angkor on 2006-06-04
[QUOTE=JoWilly]Yea you can search a long time for gnome bluetooth. Its a big mess.

Fortunately there is a google summer of code project that is taking care of this (by Mattew Garett I think). Hope it'll be in egdy.[/QUOTE]

That's great news. For now I'll stick to using kde's bluetooth in gnome. :(

---

### Post by MrGreen on 2006-06-04
I'm sorry but whats universe .... will have to go looking I guess ....

OT .... was looking for smart too 

& a link to using apt-get would be nice ... just to get me started ;-)

---

### Post by angkor on 2006-06-04
[QUOTE=MrGreen]I'm sorry but whats universe .... will have to go looking I guess ....
[/QUOTE]

The universe repository. If you enable this repository you enable extra software.


[https://wiki.ubuntu.com/AddingRepositoriesHowto?](https://wiki.ubuntu.com/AddingRepositoriesHowto?)

---

### Post by MrGreen on 2006-06-04
Thanks got Smart Openbox & gnome bluetooth now .....

---

### Post by dirtvoyles on 2006-07-11
I don't think my question is worthy of it's own thread, so I'll ask here:

Can anyone tell me how to start kdebluetooth from CLI or how to setup a Belkin PCMCIA card to work with a headset in Skype?

Links to how to's are greatly appreciated.

---

### Post by MrGreen on 2006-07-12
Got this from an Article

```
modprobe -v snd_bt_sco
esdctl stop
hcitool scan
btsco [address]
ls -l /proc/asound
aplay -D plughw:Headset <soundfile>.wav
```

HTH

---

### Post by dirtvoyles on 2006-07-12
esdctl gets me: bash: command not found

Any other suggestions?

I'm not trying to be smart, just asking.

---

### Post by MrGreen on 2006-07-12
no its cool I'm just quotin' from the article figure most use alsa anyway 

jsut tryin' to help

---

### Post by angkor on 2006-07-12
> **dirtvoyles said:**
> Can anyone tell me how to start kdebluetooth from CLI 

You don't mean 'kbluetoothd' don't you?

---

