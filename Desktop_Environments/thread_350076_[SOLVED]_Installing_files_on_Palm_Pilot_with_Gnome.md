---
title: "[SOLVED] Installing files on Palm Pilot with Gnome on Edgy - how?"
date: 2007-01-31
forum: Desktop Environments
---

### Post by pinkunicorn on 2007-01-31
I just installed an old Palm V serial dock (via USB converter) to my Edgy system, and syncing of addresses and appointments and so on works fine.

Now, I'd like to install a .prc file onto my pilot, and I can't for the life of me figure out how to do it. I assume there is a simple drag-and-drop way to do this, but I can't find it.


The only thing I've found which is even remotely what I want to do it the gpilot-install-file program which I can run from a shell to mark files for installation. I could live with that, except that it doesn't work either...

```

$ gpilot-install-file CacheMate.prc 

(gpilotd-install-file:3415): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(gpilotd-install-file:3415): Gdk-WARNING **: locale not supported by C library
gpilotd-Message: Activating object OAFIID:GNOME_Pilot_Daemon

(gpilotd-install-file:3415): gpilotd-WARNING **: gnome-pilot-client.gob:780: Caught exception: IDL:GNOME/Pilot/UnknownPilot:1.0
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'Headset'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default

```

As far as I can tell, it doesn't find my pilot. But syncing the same pilot works fine. Help! ](*,)

---

### Post by wastrel on 2007-01-31
Try ```
pilot-xfer -p /dev/<whatever> -i file-to-install.prc
```

Note: you'll have to kill gpilotd before you can use pilot-xfer

---

### Post by pinkunicorn on 2007-02-01
Yeah, I guess something like that would work. It's not exactly elegant, though, and nowhere near a drag-and-drop solution. Is there a simple way to restart gpilotd afterwards, for that matter?

---

### Post by Pelon1 on 2007-02-13
You can drag the file to the gnome-pilot applet and it will transfer next time you sync.

---

### Post by User101 on 2007-04-11
> **Pelon1 said:**
> You can drag the file to the gnome-pilot applet and it will transfer next time you sync.

Thank you very much for this tip, which I could not find in the Help files for gnome-applet -- in general, your method works like a charm! :KS[INDENT]Note: As a n00b :) I've had to figure out how to implement this method, though. Here's what I learned, in case it's useful for others too: you have to place the gnome-pilot applet on the Gnome Panel. In other words, **right-click on an empty spot on the Gnome Panel** at the top of your screen > Select **Add to Panel** > scroll down to Utilities > Click on **Pilot Applet** > click **Add**. This will put the Pilot Applet icon (a circle with two black-and-white arrows) in the Gnome Panel at the top of your screen. 

Then, Click **Places** > **open the folder** where you have the file(s) that you want to transfer to the Palm device > **select** the file(s) > **drag the files to the Pilot Applet icon** on the Gnome Panel. Connect your Palm device to the Ubuntu PC and click the **Sync **button or icon on the Palm device.
[/INDENT]Thanks again for pointing me in the right direction to begin with.

---

### Post by User101 on 2007-04-11
I still have three questions:

[INDENT]1. Can you specify a default "file transfer to Palm" folder? Anything in that folder would then be transfered automatically to the Palm when you Sync. This would be useful if you have e.g. an off-line RSS reader or Podcast catcher that can place all their output files in one folder.

2. If there is no default transfer folder option, then can you preview the list of files after dragging it but before hitting Sync? This would allow you to delete files that had been dragged to the Palm Applet by mistake.

3. Can you stop Palm Applet from backing up the files that it had just transfered -- i.e. copying them from the Palm back to the Ubuntu PC? This is time-consuming and redundant, as by definition the files were already on the Ubuntu PC to begin with. :) [/INDENT]

Thanks in advance for your help.

---

