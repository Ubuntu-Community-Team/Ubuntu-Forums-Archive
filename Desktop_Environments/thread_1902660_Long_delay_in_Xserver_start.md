---
title: "Long delay in Xserver start"
date: 2011-12-31
forum: Desktop Environments
---

### Post by dasan on 2011-12-31
My Kubuntu 11.04 is booting in 60 seconds but taking about 200 sec to show the login screen..  
What might be the reason.. 
i am attaching boot chart...
Thanks in advance...

The image size was too small to view 
[http://imageshack.us/photo/my-images/835/aumsysnatty201112315.png/](http://imageshack.us/photo/my-images/835/aumsysnatty201112315.png/)

---

### Post by 2F4U on 2011-12-31
Are there any errors in .xsession-errors in your home folder? What applications are automatically started on login?

---

### Post by inobe on 2011-12-31
[http://img835.imageshack.us/img835/3997/aumsysnatty201112315.png](http://img835.imageshack.us/img835/3997/aumsysnatty201112315.png)

@dasan high res link.

---

### Post by dasan on 2012-01-01
I solved it by giving kdm on etc/rc.local file..
but now my soud system is not working till i log off and login after some time...

So i hope that the sound device might be the one who was making it slow 

how can i load sound also with kdm
aplay -l output

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


There are no application started by Default..

---

### Post by dasan on 2012-01-01
Fixed this tooo

by adding a new file "asound.conf" in etc with following options

pcm.!default {
type plug
slave.pcm "elemix"
}

pcm.elemix {
type dmix
ipc_key 1024
ipc_perm 0660
slave.pcm "hw:0,3"
}

I really don't know what it stands for or what that means but it fixes :popcorn:

Thanks for All of your help.....:lolflag:

---

