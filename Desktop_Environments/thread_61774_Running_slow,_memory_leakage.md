---
title: "Running slow, memory leakage?"
date: 2005-09-02
forum: Desktop Environments
---

### Post by nomeat on 2005-09-02
I am new Linux.
I have installed Ubuntu 5.04 on two systems and have many problems on both that I have partly solved but I think it all seems to come to one point where I can't get any futher:
Linux's memory management!

A few examples of my problems are:

- after opening and closing several windows (usually Firefox - even after updating to 1.06) the system runs really slow and needs rebooting. This happens sometimes straight after booting but sometimes it works for hours with no problems. I am not using any other apps or adjusting anything.

- after a screen saver has been on a while the system gets slow and in some instances it totally freezes --> have to power off with 6sec power button. I have disabled sreen saver now of course.

-MP3's stutter after a few minutes playing. Strangley enough they don't seem to stutter with XINE but I hate this player and I would like Noatum to work smoothly. 
Some where I read I have to increase the audio buffers but I don't know how - I wish people would always post how to do it when they recommend it.

- Now the biggest hammer: while I made the mistake to use the automatic update feature it also attempted to replace the kernel (although the same version number -  some security update), and of course while installing the new kernel the system locked up :mad: 
I could not find a way to get the old kernel back (the machine wouldn't work with Grub) and I lost the work of days by having to reinstall everything from scratch. Is there any way to completely disable this update feature? I read that is uses memory resources as well.

Both systems are laptops and have 256MB memory. I cannot upgrade memory and I think it should be enough as 128M is required. I think it is ridiculous if I would need a gig of memory just for Firefox while listening to a bit of music.

Swappiness is 60 but the hard drive sometimes sounds like a chainsaw when things run slow.

Please don't start a discussion about how cool it is that Linux uses up all the memory to cache what it has done before, so it speeds things up. I don't think that is cool because it doesn't work for me. 
I would like to see some free memory available after apps are closed. Is there anyway to enable this?

Is there a trick or a little software application to clear the memory cache without rebooting ?
If I could just click on this app when things get sticky I would be already happier.

---

### Post by lol on 2005-09-02
I can't tell for sure, but AFAIK, your problem probably related to your 60Mb of swap... this is way to low!

Usually, Linux is not too bad when it comes to memory management, BUT this is true only as long as the swap isn't full. As soon as all the swap is used, few OS will behave as badly as Linux... My suggestion would be to create a swap partition of at least 512Mb in your case.

With only 256Mb of memory, I would also recommend not to use Gnome or KDE, as they both use way to much memory for nothing. Try XFCE instead...

Hope this can help.

---

### Post by nomeat on 2005-09-02
Can you tell me how I can get back to Gnome if things don't work out after installing XFCE? I really don't want to stuff more up.
I also need Java and all plugins and codecs to work. I don't want to start from scratch again if I install a new desktop. Even the touchpad was a real pain before I had it the way it should be.

My swap partition is 360Mb not 60Mb.
Swappines is a  factor that you can set when the system will start swapping to the disk. The higher the more it swaps as I understand it.
Adjusting it didn't really seem to improve things in my case though. I think it just got worse.

---

### Post by lol on 2005-09-02
oops sorry, my mistake, I misread your post...

You can install both XFCE and Gnome at the same time. When you log in with Gdm, you can then choose which one you want to use.

360Mb of swap should be enough, even with Gnome, so the problem probably comes from something else. I don't have a clue though... You should try to identify what wrong when things start to slow down, with 'top' for example. Check out how much of memory is still available, or if there is a process obviously using more CPU (or memory) than it should, etc.
You said that there seems to be a lot of HD activity when things start to run slow. Trying to figure out why is probably the first step to solve your issue.

---

### Post by nomeat on 2005-09-02
I edited my post above to clarify that it works OK with Gnome until "something?" goes wrong.
I will give XFCE a try just to see if I like it better, seeing the can co exist together.

I wish there was a Linux version of Memzip or something.

---

