---
title: "&quot;The audio device is busy. Is another application using it?&quot;"
date: 2005-02-23
forum: Desktop Environments
---

### Post by Spif on 2005-02-23
When I pause music in Totem and pres the play button the continue listening to the song I get an error: "The audio device is busy. Is another application using it?"

I believe this program running in the background is what causes my sound to be muted in my games. When I shut down Ubuntu, I'm sure an application s being closed. I can see it in an instant before the shut down sequence starts.

How do I disable this program?

---

### Post by Spif on 2005-02-24
bump...

---

### Post by iomicifikko on 2005-03-22
that happens to me too.

anyone any idea?

byez

---

### Post by Lord C on 2005-03-25
[QUOTE=Spif]When I pause music in Totem and pres the play button the continue listening to the song I get an error: "The audio device is busy. Is another application using it?"

I believe this program running in the background is what causes my sound to be muted in my games. When I shut down Ubuntu, I'm sure an application s being closed. I can see it in an instant before the shut down sequence starts.

How do I disable this program?[/QUOTE]

Totem **always** gives me this message, with some videos.
But with others it works fine :s

It can't be the format either:
I have an AVI that always works, and an AVI that never works.

I don't understand it.

---

### Post by stoffe on 2005-04-03
I get this a lot too, although I haven't thought to look for special movies it happens in or so, I thought it was just something random. I'll have to start taking notes when I see it.

As for AVI, it is really not a file format as you mean it, it is just a container format that can contain video and sound, and those in turn can be of many different formats, as far as I know anything from MPEG to Real. So it sure can be specific formats that is causing the trouble and it would be nice to find such a connection.

Would love to get rid of this bug too, it is quite annoying. Especially since it chooses to open a popup in the middle of the screen, when you've put your feet up across the room and is watching something and trying to relax. :)

---

### Post by kassetra on 2005-04-03
Typically this kind of error happens when you're using the wrong audio sink... OSS for example doesn't let you play more than one sound at a time...

It also happens with Totem quite a bit by itself - so it might be something in the playback code that's not quite right.

Have you tried the same thing with xine or gxine?

---

### Post by Lord C on 2005-04-11
[QUOTE=kassetra]Typically this kind of error happens when you're using the wrong audio sink... OSS for example doesn't let you play more than one sound at a time...

It also happens with Totem quite a bit by itself - so it might be something in the playback code that's not quite right.

Have you tried the same thing with xine or gxine?[/QUOTE]
 My fix is - I just open the file in Xine and it works fine xD

---

### Post by jr06compmaster on 2006-12-18
I am having this exact problem every time I try to play a DVD.  It was working fine before I restarted my computer after a clean install.  Now it says "An error occurred The audio device is busy, is another application using it?".  Has anyone found a solution yet?

---

### Post by falsedust on 2006-12-21
I have the same problem if I switch from stereo to 5.1 surround within Totem. But that just means I can't listen to DVD's in 5.1. 
I have onboard sound NVidia CK8S (nForce 3 250gb AC97 controller), I am using 6.10 Edgy with the latest alsa drivers plus alsa-oss. Under volume control preferences I have my NVidia  CK8S device selected. In my multimedia system selection I have my audio output set to autoselect and my audio input set to ALSA.
I am unable to find where there is another program running that would be using my sound device at the same time as Totem. Or if there is simply a setting in Totems config that duplicates my sound device.
I can't seem to find a current thread that offers a solution, after reading through the fantastic sticky for audio problems I still haven't found anything to resolve this problem.

What is involved when you switch between stereo sound to 5.1 surround sound and how does this relate to having an onboard sound device (NVidia CK8S) ????

Any help would be good.

---

### Post by DarthTibault on 2006-12-21
Same problem here, totem keeps telling me the audio device is busy. Mplayer -> same thing. However Audacious plays my music just fine.
I don't know why it thinks something is using the audio device (or I don't know what's using the audio device). First I thought it was Gaim (nope), then I thought it was FF (nope), and well, those were all the apps running...

---

### Post by WorLord on 2007-10-04
This is flash related.

There are certain ads in flash that have audio in them.  Notably some that, every time they pop up, annoyingly proclaim in a friendly, female voice: "Congratulations!  You've been selected to win a free iPod/iPhone/Xbox 360!".

After I see one of these?  My audio device is busy until I log out and back into gnome again, at which point everything's ok.  The problem persists, as everyone else has said, even when Firefox is closed and there is no trace of it or flash still running.  

Is there an existing bug report I can put this new data into?

---

### Post by Taiebot65 on 2007-11-11
This is my first message... new ubuntu user. I ve got the same problem it seems that  there is a bug with Xine and our downloading programs. I'm using Azureus and when i put more than 2 torrent. the device is busy and i can't listen music...

I don't know how to report a bug.So i hope someone is going to do that.

Cheers

---

### Post by etotheipiplusone on 2008-03-22
I don't know if you had this problem for the same reason I did.  But what seems to happen to me is that some websites have Java ad banners that play a sound, and tie up your sound controller.  So, even when you close your web browser the Java applet is commandeering your sound card.  The simple fix is to kill the applet. 

1. Open a terminal window. 
2. Type 
```
ps -u *username* 
```
username is of course your username.  This basically lists all processes currently being run by your username. 
3. The output will look something like this. 
```
sjoshi@sjoshi-desktop:~$ ps -u sjoshi
  PID TTY          TIME CMD
 5490 ?        00:00:00 gnome-keyring-d
 5493 ?        00:00:00 x-session-manag
 5528 ?        00:00:00 ssh-agent
 5530 ?        00:00:00 gconfd-2
 5534 ?        00:00:00 dbus-daemon
 5536 ?        00:00:02 gnome-settings-
 5542 ?        00:00:00 compiz
 5544 ?        00:00:17 gnome-panel
 5546 ?        00:00:01 nautilus
 5550 ?        00:00:00 gnome-volume-ma
 5558 ?        00:00:00 bonobo-activati
 5584 ?        00:00:00 gnome-vfs-daemo
 5661 ?        00:00:11 gtk-window-deco
 5662 ?        00:00:20 compiz.real
 5667 ?        00:00:00 vino-session
 5668 ?        00:00:00 bluetooth-apple
 5673 ?        00:00:00 update-notifier
 5682 ?        00:00:00 evolution-alarm
 5685 ?        00:00:16 gnome-screensav
 5686 ?        00:00:00 trackerd
 5688 ?        00:00:00 python
 5694 ?        00:00:00 nm-applet
 5696 ?        00:00:00 gnome-power-man
 5711 ?        00:00:00 trashapplet
 5714 ?        00:00:00 evolution-data-
 5731 ?        00:00:00 evolution-excha
 5734 ?        00:00:00 mapping-daemon
 5766 ?        00:00:00 fast-user-switc
 5768 ?        00:00:01 mixer_applet2
 5781 ?        00:00:02 deskbar-applet
 5784 ?        00:00:01 notification-da
 5801 ?        00:05:21 opera
 5866 ?        00:00:00 operapluginclea
 6703 ?        00:01:05 amarokapp
 6706 ?        00:00:00 kdeinit
 6711 ?        00:00:00 dcopserver
 6714 ?        00:00:00 klauncher
 6716 ?        00:00:01 kded
 6733 ?        00:00:00 kio_file
 6735 ?        00:00:00 ruby
 7568 ?        00:00:19 pidgin
 8159 ?        00:00:01 operapluginwrap
 9159 ?        00:00:05 gnome-system-mo
 9453 ?        00:00:00 sh
 9454 ?        00:00:00 gnome-terminal
 9456 ?        00:00:00 gnome-pty-helpe
 9457 pts/0    00:00:00 bash
 9474 pts/0    00:00:00 ps
```

The numbers on the left are process ID numbers.  Find the process that says "Java" (I don't have one in my example above, sorry) or something that suggest a Java Runtime Environment.  Then find the process ID number of that process.  

Then, enter in the command line: 
```
kill *process_ID*
```

where of course process_ID is the ID of the Java process.  

This works for me every time, and hopefully helps you guys.

---

### Post by xen-uno on 2008-07-20
In my case, it was an process called *pulseaudio* causing the error. Killing it allowed Totem Xine to play (before that was the libdvdcss2 hurdle). Might be some interaction problem with the Alsa mixer according to [_this_](https://wiki.ubuntu.com/PulseAudio)

The process lister and killing of was a big help ... thanks.

---

