---
title: "Gnome Volume Control crashes"
date: 2008-11-30
forum: Desktop Environments
---

### Post by paul.sild@hotmail.com on 2008-11-30
Hello!

Before I explain this problem, I should mention that I am a fairly new user of this operating system [Ubuntu 8.10 Intrepid Ibex], so if more detail is needed, just say!

I'm having pretty bad problems with sound at the moment, I've never got it working yet with my laptop speakers - that's another problem though!

O.K. - the actual problem!

When I right click on the volume icon in the top right panel, and select Open Volume Control, the window comes up after a few seconds, and there is nothing in it apart from grey - it has effectively stalled. Another rather annoying problem twinned with this one is the volume slider - it doesn't work smoothly when I drag it with the mouse, or click on the slider - it's a bit, well, "jumpy" (not that I can hear anything anyway!).

When I use the Gnome system monitor to see what's happening, I look under the Processes tab and find that the status of the process "gnome-volume-control" is "Uninterruptible".

I don't know what this means, but I do know that Volume Control worked perfectly before I changed the Sound playback device to HDA NVidia STAC92xx Analog (ALSA), where, when I pressed the "test" button, I got an error message saying:

audiotestsrc wave-sine freq=512 !
audioconvert ! audioresample ! gconfaudiosink:
Could not open audio device for playback.

Is there any way I can get volume control working again?

---

### Post by paul.sild@hotmail.com on 2008-11-30
Also, I should mention that when I try to close the Volume Control window, it goes dark blue/grey, and a window comes up with an option to force quit/exit.

EDIT:

I've looked through the forums, and there's a user with a similar problem, thread title:
volume control not working

The message about Gstreamer plugins was also a problem I had, before I removed the volume control icon from panel, and added it again - then I got no error message, but volume control doesn't work now.

---

### Post by paul.sild@hotmail.com on 2008-11-30
New info!

I tried opening gnome-volume-control as root from terminal, so

root@<my_laptop>:/# gnome-volume-control

and it works perfectly!

However, when i open gnome-volume-control from terminal as myself it just stalls!

I've read somewhere else on these forums about permissions being the problem - sometimes one randomly loses permissions for certain audio modules (I think it's modules, not sure), and that might be what's causing the conflict - I have permission to open gnome-volume-control, but the ALSA or OSS or whatever that one can normally view Gnome Volume Control are not permitted?!?

---

### Post by paul.sild@hotmail.com on 2008-12-01
I found a great solution for this:

REINSTALL.

---

