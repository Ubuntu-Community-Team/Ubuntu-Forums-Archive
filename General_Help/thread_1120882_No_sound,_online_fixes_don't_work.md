---
title: "No sound, online fixes don't work"
date: 2009-04-09
forum: General Help
---

### Post by d42 on 2009-04-09
Hi all,

I have a little bit of experience with Ubuntu/Linux, but this is my first time installing Ubuntu on a laptop.

The laptop in question is a Panasonic T2. It doesn't have a cd drive so I had to barrow a usb cd drive from a friend to boot off of. In the mean time I put wubi on it to test how well it worked out of the box. Everything was ok, except I couldn't change the sound level. The sound was set to whatever I had  last set it to in windows xp. 

So I got the cd drive, and decided to install ubuntu 8.10 and figure the sound problem out later. Absentmindedly though, I still had the sound on mute when I installed ubuntu on the entire system. 

So now I have no sound, and I've tried every fix I could find ([like this one]("http://onlyubuntu.blogspot.com/2008/11/fix-for-no-sound-issue-in-ubuntu-810.html")), with no results. I also booted up a puppy linux 4.2 live cd a had leying areound, and had similar sound problems.

Thanks in advance.

---

### Post by maheshasolkar on 2009-04-09
Could you run the following in terminal:

```
  alsamixer -Dhw
```

It will show all the playback and capture items in your sound hardware. Do you see any item muted? If you do, try to un-mute it by pressing 'M' key. Also, if there is an 'External' item that is not already muted, try to mute it, again by pressing the 'M' key. You can navigate through the items with arrow keys. When done, hit 'ESC' key to exit alsamixer.

This always works for me, may be it will help you too

---

### Post by d42 on 2009-04-09
I had actually already tried that, but hadn't realized that it continued off the right of the terminal. All sound unmuted on max, external muted. App on panel on max, youtube on max, no sound. (Though youtube may not be the best indicator- I don't have any sound at all)

I curently have ALSA set for all my drivers.

---

### Post by maheshasolkar on 2009-04-09
I agree, youtube may not be the best indicator. You might want to try playing a CD or one of the media files that come with Ubuntu - I believe they are in /usr/share/example-content/Experience or linked somewhere in the home directory.

---

### Post by d42 on 2009-04-09
Oh, I'm sorry, that's what I meant. I had youtube running in the background, but I also tried sounds from system>sounds>sounds. Example sounds aren't making a peep either.

---

### Post by fooman on 2009-04-09
i am not sure what sliders are available in alsamixer (i am on a windows machine atm)....but you might want to install the gnome-alsamixer from synaptic (system > administration > synaptic...search for gnome-alsa-mixer),or just open a terminal and type or copy/paste the following:
 
```
 
sudo apt-get install gnome-alsamixer

```
 
then find it in applications > sound & video
 
make sure all of the sliders are maxed.
 
hope that helps.

---

### Post by d42 on 2009-04-09
[http://odie.sork.nu/cf-t2/](http://odie.sork.nu/cf-t2/)

"Also, if you mute the sound using Fn-F4 in Windows, the Linux ALSA driver is unable to unmute it, and your Linux will remain silent until you unmute in Windows."

This is Slackware 10.2 on a panasonic t2, but it seems to agree with my conclusion.

You don't happen to know a way to know a way to access windows from the cd without partitioning or wiping out Ubuntu, do you?  

Ah well, I'll do this tomorrow or something...

---

### Post by d42 on 2009-04-09
@ fooman:
I got the mixer. Everything is at full, nothing is checked. I got this error message on start up:
"An error occurred while loading or saving configuration information for GNOME ALSA Mixer. Some of your configuration settings may not work properly."

Edit: Misc. has rec. checked in the mixer

---

