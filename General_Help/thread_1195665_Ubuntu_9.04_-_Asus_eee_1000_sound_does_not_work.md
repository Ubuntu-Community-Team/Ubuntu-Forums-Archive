---
title: "Ubuntu 9.04 - Asus eee 1000 sound does not work"
date: 2009-06-24
forum: General Help
---

### Post by Mad_Duke on 2009-06-24
Hi! 

Can anyone help me. I am moving around and around trying everything, but the sound simply does not work. What do I need to do? It has ALC269 sound chip.

---

### Post by gettinoriginal on 2009-06-24
Reading reviews of the Asus 1000, some seem to be having sound problems related to Pulse Audio.
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

---

### Post by hibliss on 2009-06-24
What version of Ubuntu are you using? Do you have the array repository in your sources list? [http://array.org/ubuntu/]("http://array.org/ubuntu/")


There are a lot of additions that come from the array repository.

I assume you are using Jaunty, add this repository -- [http://array.org/ubuntu/setup-jaunty.html]("http://array.org/ubuntu/setup-jaunty.html"). If you are using a different version of Ubuntu, they have other repos for previous versions here -- [http://array.org/ubuntu/setup.html]("http://array.org/ubuntu/setup.html")

If your exact EeePC model is just the Eee 1000 with no letters after it, there are known issues that array can help with.

This applies directly to the sound on your machine -- [http://array.org/ubuntu/snd-hda-intel.html]("http://array.org/ubuntu/snd-hda-intel.html")

I have the Eee 1000he and everything worked out of the box, including the FN keys because I installed Eeebuntu with all of these drivers and custom repos already in the kernel when you install.

You can accomplish the same thing by adding the repos and installing some of the kernel enhancements on this page -- [http://array.org/ubuntu/enhancements.html]("http://array.org/ubuntu/enhancements.html")

---

### Post by Mad_Duke on 2009-06-24
Thanks. I am a bit of a noob. I only used linux for a few months back in 1999.  

My exact model is Asus Eee 1000HG (It is AFAIK just an 1000H with a 3G broadband inside which is working out of the box and a larger HDD)

So I will add these and try to update everything. Hope it works!

---

### Post by hibliss on 2009-06-24
Well if it has the same hardware components as the 1000h it will be fully supported by the array kernel. Make sure you get eeepc-acpi which will make all of your FN keys work properly.

eee-control is also an important one, which lets you set the power saving modes and whatnot.

---

### Post by Mad_Duke on 2009-06-24
Hi people!

I tried and installed the eee kernel and it still does not work. I go to sound options to test it and there the only options that want to start are :

"Autodetect" 
"ALSA Linux Sound Architecture" 
"PulseAudio Sound Server".

But there is no sound coming out (I tried also playing a mp3 and a movie with VLC)
The rest:

"HDA Intel ALC269 Analog (ALSA)"
"HDA Intel ALC269 Analog (OSS)"
"HDA Intel ALC269 Analog (OSS)"
"OSS Open Sound System"

Just throw out some weird error
"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback".

Could someone who has the same card please tell me exactly what options are in which config and what version of a driver does he have. Or simply, just a solution. I will be going on a vacation soon, and I would hate to have to put Windows XP back on it. Especially because everything works absolutely great except the sound.

---

### Post by hibliss on 2009-06-24
You don't just add the kernel, you have to add the necessary packages to your system, more info on Array.org.

---

### Post by Mad_Duke on 2009-06-25
Hi!  

I "fixed" the problem. How?  Really strange. 

I started the ubuntu live CD and heard there was a sound. I reinstalled Ubuntu on my laptop and I had my sound working. After that I used apt-get dist-upgrade and the sound still worked

After that I routinely wrote this command

```
$sudo update-rc.d -f gdm remove
```Because I like it more when it boots into console. And after reboot and after I entered startx I had no more sound in Ubuntu. I would go into Sound options and pressed "test" and it would just go on without a sound coming out.  

So I wrote this:

```
$sudo update-rc.d gdm defaults
```Now it works. LOL
--

Can someone tell my why would the above command influence my sound?   And also. Is there a way for me not to boot into Gnome. I could live with it, but that is not a solution.

Thanks in advance ;)

---

### Post by Mad_Duke on 2009-06-25
SOLVED

Now that I found what was the problem. It was easier to find a solution. This helped me
[http://ubuntuforums.org/showthread.php?t=1002780&page=2](http://ubuntuforums.org/showthread.php?t=1002780&page=2)

Thanks you for your effort guys ;)

---

