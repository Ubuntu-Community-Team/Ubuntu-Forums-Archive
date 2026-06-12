---
title: "Sound!!!"
date: 2005-04-21
forum: Desktop Environments
---

### Post by lee_connell on 2005-04-21
Hey all sound does work but when i try something like frozen-bubble sound doesnt work.  now i used the unofficial ubuntu 5.04 guide and it fixed the sound until i rebooted, then no sound at all and saying it couldn't write to the device.  Is there a step missing in the tip?

anyways i switched back and it's back to ubuntu normal.  how can this be fixed?

---

### Post by Mel45 on 2005-04-21
I feel for you.
I've been in sound hell myself for a while.
The only thing that works for me is reloading the sound drivers.

# sudo /etc/init.d/alsa force-reload

Then I have to unmute the output and adjust levels, etc
The bad news is that I lose the sound every time I reboot the box so I have to repeat
all of the above.
Good luck
Mel

---

### Post by spencer on 2005-04-22
[QUOTE=lee_connell]Hey all sound does work but when i try something like frozen-bubble sound doesnt work.  now i used the unofficial ubuntu 5.04 guide and it fixed the sound until i rebooted, then no sound at all and saying it couldn't write to the device.  Is there a step missing in the tip?

anyways i switched back and it's back to ubuntu normal.  how can this be fixed?[/QUOTE]



Hello,

I have had  no sound in frozen-bubble too. I unticked "enable sound server startup" in the sound preferences and that gave frozen-bubble sound. 

If you have no sound after reboot, maybe your sound module isn't loading at startup. Is your soundcard written to the "/etc/modules" file? You can try this command in the terminal, "sudo gedit /etc/modules" and write whatever your sound card is to the bottom of the file if it isn't. Save the file before you close it. That should load the sound module and give you sound after reboot. I had sound trouble myself and finally sorted it out with the following post [here](http://ubuntuforums.org/showthread.php?t=23369&page=2&highlight=spencer) 

I hope this is a fix for your sound troubles.

-spencer

---

### Post by lee_connell on 2005-04-23
hey guys,


my sound drivers do load properly, that wasn't the problem.  force-reload does work to make sound work for everything "excluding desktop event sounds".  So I think just disabling start sound server on startup is the same thing with less steps to take to get it to work.  this time you don't have to keep running force-reload.  Bummer this wasn't something that was looked at more carefully during this release. 

I also notice that totem-gstreamer has out of sync speech on dvd's.  gxine works perfect, i'm sure totem-xine would problably work just as well.  anyone else notice this?

---

### Post by Nob on 2005-04-23
how do i set default levels to sound server? on every reboot i have to set manualy Master and PCM..
how do i make curent values as default? [master - 100%, PCM - 50%]

---

