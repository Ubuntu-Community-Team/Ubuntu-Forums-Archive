---
title: "Sound in VMWare server, how?"
date: 2006-07-13
forum: Desktop Environments
---

### Post by Dearhell on 2006-07-13
I have sound in Ubuntu and works pretty well, but has anyone achieve to get sound in VMWare Server? (I have a Windows XP Pro installed through VMWare in Ubuntu)

---

### Post by zhoux on 2006-07-13
yeah, i've gotten sound b4, you need to add the sound driver by editing the host settings

---

### Post by Billquinn1 on 2006-07-13
I think all you need to do is shut down the running XP and add a sound device in the virtual machine settings.

---

### Post by fakie_flip on 2006-08-23
Doing a `killall esd` before powering on the virtual machine is the only way to get sound working that I found. Has anyone found a better way to get sound working in VMware Server? How can this software be commercial and sold for money if the sound doesn't work. There must be a way to get it working besides killing all sound in Linux.

---

### Post by OrganicPanda on 2006-08-23
I would also very much like a work around for this, I have the sound adaptor enabled in vmware server but in the client (xp) device manager it says there is no audio device installed, even with vmware tools installed. Sound used to work with vmware-player but not now, what's going on?

---

### Post by h0mer on 2006-08-23
I've installed a couple of vmware's and sound usually works for me out-of-the-box, except in one case. I got a '/dev/dsp: no such device'. A quick look at the device manager showed me that in fact my sound device was actually /dev/dsp0, for whatever reason. One symlink later, I was listening my mp3's through windows media player!

If any of you are in a similar situation, try this:

situation: 'cannot initialize /dev/dsp: no such device' message while booting a virtual windows. It could also be '/dev/audio' or something like this. Note: if you don't get this message but no audio either, try setting an audio device in vmware to '/dev/dsp'; if that's not it, you'll at least get this message and go on from here hehe:p 

What worked for me: (disclaimer: surely seasoned ubunteros will have better workarounds, Im quite a noob!)

1. goto system-> device manager
2. Find your sound device:

This is kinda tricky because there usually are many. Im sure experienced folks know of some cli command that displays the device's name, so feel free to contribute. I don't, so I had to look through list.

Find an entry for your Audio controller, it usually carries the name of your hardware (Audigy, AC97, etc). Expand it.

There will be ALSA and OSS playback devices. Click on them to show the properties. Open the 'advanced' tab on the right.

Look for a key called 'linux.device_file'. If should have a value like '/dev/dsp' or '/dev/audio' or '/dev/dsp0' etc. Thats the string we're looking for.

3. Create a device with the found device; either enter it manually in vmware config or create a symlink from /dev/dsp to the one you found. Try

```
sudo ln -fs /dev/dsp /YOUR/DEV 
```

4. Trial and error. I found many audio devices on this machine, so I had to make a few attempts in order to find the proper device.

Hope it helps!

---

### Post by fakie_flip on 2006-08-25
good. why didn't i think of that? thanks.

---

