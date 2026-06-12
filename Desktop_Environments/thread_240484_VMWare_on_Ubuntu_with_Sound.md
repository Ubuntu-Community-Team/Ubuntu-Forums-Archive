---
title: "VMWare on Ubuntu with Sound?"
date: 2006-08-20
forum: Desktop Environments
---

### Post by Rayston on 2006-08-20
Has anyone ever got sound working? I am running ubuntu, and VMware, I got VMware working, but I cant get the sound working at all. Are there any special tricks? I am running an onboard sound card.

---

### Post by torf on 2006-08-20
If you mean getting sound working within a VM, make sure you added a sound device in the VM settings. (Where you can edit the VM's hardware, such as CD ROM and Floppy drives, USB controller, sound device, etc.) You should see a little icon for the sound device in the VMware window along with any other virtual hardware, such as an ethernet card.

Feel free to contact me if I'm way off on this one.

---

### Post by Rayston on 2006-08-21
Yah, I did that and it it says 

Failed to open sound device /dev/dsp: Device or resource busy
Virtual device sound will start disconnected.

---

### Post by x64Jimbo on 2006-08-21
This often happens when there's another process that's using the sound on your system. Make sure you have all other sound processes turned off before you start vmware.

---

### Post by Gannin on 2006-08-21
As an experiment, in a terminal type "sudo killall esd" and then try to run VMware and see how that works for you.

---

### Post by RikoW on 2006-08-21
I need esd when using sound on a virtual machine. In particular, when I have esd turned of and there is or was a kde application, which uses the sound device, running I get the "sound device busy" message. With esd turned on, it all works.

- Riko

---

### Post by Lunar_Lamp on 2006-08-31
So, it's impossible to have amarok playing music and any sound at all from VM?

---

### Post by x64Jimbo on 2006-08-31
you could try switching to another sound driver in amarok

---

### Post by Lunar_Lamp on 2006-08-31
Well, my main problem with that is that I don't know that Amarok is the only one using the sound engine, and the xine engine is the only one amarok gives me to choose from.  It works just fine also, so I'd rather not fiddle around with it.

---

### Post by Gannin on 2006-09-01
What about changing the sound driver that Xine uses?

---

### Post by rejser on 2006-09-01
Have no problem with sound, have turned it of though. Don't feel the need for i through wmware. You can't game, running multimedia I can do through linux much better so.... And I don't really miss the login sound

---

