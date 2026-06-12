---
title: "Ubuntu sound **Literaly** just quit working?!"
date: 2009-01-22
forum: General Help
---

### Post by morbid_bean on 2009-01-22
I was jammin out to some tunes an after a bathroom break decided i would shut them off and go make something to eat...I just simply pressed the volume all the way down on my keyboard like i normally would, had my computer sit there idle. ...after getting on my pc few hours later sound just didn't  work??  
I have:


[LIST]
[*]Checked the volume on the speaker
[/LIST]
[LIST]
[*]Checked the volume on the volume control panel
[/LIST]
[LIST]
[*]Checked and seen if a test sound would work
[/LIST]
[LIST]
[*]Checked the speaker connections
[/LIST]

and still nothing

Whats going on??

---

### Post by travmon69 on 2009-01-22
strange?  I also have some problems sometimes after start up or reboot where all volume controls are turned down or muted for no reason. This confuses me.

---

### Post by Miles_Prower on 2009-01-22
hmm... open a terminal and execute this command

```
sudo /etc/init.d/alsa-utils restart
```

lemme know if that doesn't work.

---

### Post by morbid_bean on 2009-01-22
> **Miles_Prower said:**
> hmm... open a terminal and execute this command

```
sudo /etc/init.d/alsa-utils restart
```

lemme know if that doesn't work.

Did not work :(

---

### Post by Dr Small on 2009-01-22
Open alsamixer and check and make sure that none of the channels are muted or completely lowered:
```
alsamixer
```

---

### Post by morbid_bean on 2009-01-22
> **Dr Small said:**
> Open alsamixer and check and make sure that none of the channels are muted or completely lowered:
```
alsamixer
```

hmm now thats odd...I did and the only thing that shows up is the master volume...there should be more there?

---

### Post by Dr Small on 2009-01-22
> **morbid_bean said:**
> hmm now thats odd...I did and the only thing that shows up is the master volume...there should be more there?
There should be more if your sound card supports more.

---

### Post by Aralhach on 2009-01-22
Try putting "gnome-volume-control" that fixed my problem :)

---

### Post by morbid_bean on 2009-01-22
> **Dr Small said:**
> There should be more if your sound card supports more.

It should because it was working perfectly prior to its quitting.

---

### Post by svrkispm on 2009-01-22
have you tried to turn it off and on again? ;)

---

### Post by Agent ME on 2009-01-22
I've had pulseaudio stop working before, that might be the case here. Simply logging off and logging back on will fix that.

Or, if you don't want to have to log off, press Alt-F2, and run
```
killall -KILL pulseaudio ; sleep 0.5 ; pulseaudio
```
If the problem was pulseaudio, that should fix it.

---

### Post by morbid_bean on 2009-01-23
Well I had shut down the pc for about 2 hours started back up and everything was just fine...weird.

---

