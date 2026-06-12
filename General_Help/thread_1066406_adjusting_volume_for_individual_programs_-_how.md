---
title: "adjusting volume for individual programs - how?"
date: 2009-02-10
forum: General Help
---

### Post by not a pipe on 2009-02-10
Quick question, how do you adjust the volume for individual programs (make one louder/quieter than another)? I've tried searching some, but that inevitably leads to stuff about alsamixer. =/

---

### Post by aktiwers on 2009-02-10
I think you need a newer version of PulseAudio, but I could be wrong. I know the next version of Ubuntu (9.04) will have this feature natively, but you could have a look at this in the meantime:
[http://lifehacker.com/378670/pulseaudio-volume-control-handles-individual-app-levels](http://lifehacker.com/378670/pulseaudio-volume-control-handles-individual-app-levels)


EDIT:

I was wrong!!

You can control it like this:

Install pavucontrol...
```
sudo apt-get install pavucontrol
```And open pavucontrol:
```
pavucontrol
```

---

### Post by not a pipe on 2009-02-10
Thanks, that works well. :)

---

