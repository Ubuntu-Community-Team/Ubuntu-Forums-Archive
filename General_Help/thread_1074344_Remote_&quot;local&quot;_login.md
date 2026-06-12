---
title: "Remote &quot;local&quot; login"
date: 2009-02-19
forum: General Help
---

### Post by shadofall on 2009-02-19
The situation:

I've currently got 3 systems in one room. displaying to 3 different display's in another room

the problem is. if i need to reboot any of them i have to go to the other room hook up a keyboard. come back reboot the machine. from a vnc window. 

then go back to the other room and do what i call a "blind" login using the keyboard and no video display that i can see from my location

my question is. is there anyway i can setup vnc or something to be able to connect to these 3 machines from my laptop. and login as if i was starting a local X session so that what im seeing on my laptop display over the vnc is the same as on the displays in this room. this way i can reboot the systems and not half to walk to the other room to do the local login to get the display's working.

---

### Post by veloce on 2009-02-24
> **shadofall said:**
> The situation:

I've currently got 3 systems in one room. displaying to 3 different display's in another room

the problem is. if i need to reboot any of them i have to go to the other room hook up a keyboard. come back reboot the machine. from a vnc window. 

then go back to the other room and do what i call a "blind" login using the keyboard and no video display that i can see from my location

my question is. is there anyway i can setup vnc or something to be able to connect to these 3 machines from my laptop. and login as if i was starting a local X session so that what im seeing on my laptop display over the vnc is the same as on the displays in this room. this way i can reboot the systems and not half to walk to the other room to do the local login to get the display's working.

The easiest way to accomplish what I think you mean is just to ssh to the machine in question and issue a "sudo reboot" command. This assumes that they are all linux boxen - given that you mention X sessions this seems a reasonable assumption.

---

### Post by primus454 on 2009-02-24
What he said. 

```
sudo apt-get openssh
```

:cool:

---

