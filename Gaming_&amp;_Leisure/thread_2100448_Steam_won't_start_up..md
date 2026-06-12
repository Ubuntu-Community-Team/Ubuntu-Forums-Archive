---
title: "Steam won't start up."
date: 2013-01-01
forum: Gaming &amp; Leisure
---

### Post by sonicjms on 2013-01-01
Whenever I click on Steam on ubuntu 12.04 LST nothing happens, at all, not even in the system manager. When I run it through terminal I gets the following.

root@james-XPS-L501X:~# steam
Installing breakpad exception handler for appid(steam)/version(1355957371_client)
Xlib:  extension "GLX" missing on display ":0".
Looks like steam didn't shutdown cleanly, scheduling immediate update check
Installing breakpad exception handler for appid(steam)/version(1355957371_client)
Installing breakpad exception handler for appid(steam)/version(1355957371_client)
unlinked 0 orphaned pipes
removing stale semaphore last operated on by process 7612 with name 0eBlobRegistryMutex_5311AA5171E26917583685E205E3D491
removing stale semaphore last operated on by process 7612 with name 0eBlobRegistrySignal_5311AA5171E26917583685E205E3D491
removing stale semaphore last operated on by process 7612 with name 0emSteamEngineInstance
removing stale semaphore last operated on by process 7612 with name 0eSteamEngineLock
Xlib:  extension "GLX" missing on display ":0".
OpenGL GLX extension not supported by display


I have no idea what to do, I've tried reinstalling it, removing it then installing again, nothing is working please help.

---

### Post by Hedgehog1 on 2013-01-01
Don't lose heart - Steam on Linux is great once you get it running. I am loving it.

The issue is that you don't have you video card driver setup correctly for open GL extensions hence the:'OpenGL GLX extension not supported by display' error.

Try running 'jockey' (also called 'additional drivers' in the hardware setup area) and see if there are special drivers for your video card. Simply installing them may get you where you need to be.

If that doesn't work, please post answers to the following questions:

What brand of video card are you running?

Also, as your running the 32 bit or 64 bit version of 12.04LTS?

***The Hedge***

:KS

p.s. I am running 64 bit 12.04LTS and I had to load the 32bit libraries to get some steam games to run.

---

### Post by ubudog on 2013-01-01
*Thread moved to Gaming & Leisure.*

---

### Post by sonicjms on 2013-01-01
Im running 32-bit dual booting with Windows 7 64-bit
I have an Nvidea 420m graphics card, I installed the experimental drivers as one of the first things I did when I installed ubuntu

---

### Post by Hedgehog1 on 2013-01-01
Hmm... So far it sounds like you are doing the right things...

If you have not done so already, please type 'nv' in the dashboard and then run the 'nvidia  X server settings' app and check the settings; running this may update the config file.

If steam still won't start after that, you may need to use the nvidia-xconfig command in a terminal window: 

[http://manpages.ubuntu.com/manpages/lucid/man1/alt-nvidia-96-xconfig.1.html]("http://manpages.ubuntu.com/manpages/lucid/man1/alt-nvidia-96-xconfig.1.html")

***The Hedge***

:KS

---

### Post by normva on 2013-01-02
You have to install Bumblebee and then run steam with optirun command. for example: optirun steam

---

### Post by sonicjms on 2013-01-03
What's Bumblebee?

---

### Post by Lila7714 on 2013-01-03
I haven't used steam for ubuntu yet. Why the need to run as root just curious?

---

### Post by mentorious on 2013-01-04
> **sonicjms said:**
> What's Bumblebee?

It's a "Add-on" with support for NVIDIA's Optimus Technology: **[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)**

---

### Post by sonicjms on 2013-01-07
Bumblebee worked Thanks so much everyone that commented on this thread. The ubuntu community is really great!

---

