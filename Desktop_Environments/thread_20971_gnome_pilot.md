---
title: "gnome pilot"
date: 2005-03-19
forum: Desktop Environments
---

### Post by corefile on 2005-03-19
I can connect to my Treo 650 using pilot-xfer -l, is list everything I have on my treo 650. However I can't for the life of me get my treo setup with gnome pilotd. It just never connects, I've seen a couple other post about there possibly being a bug with gnome pilotd, do anyone have gnome-pilotd working with a palm device(using hoarty)?

---

### Post by fheinsen on 2005-04-05
I just purchased a new Treo 650 and have exactly the same problem.  Suggestions, anyone?

---

### Post by fheinsen on 2005-04-06
I forgot to mention that gnome pilot was working perfectly with my previous PalmOS device (a Treo 600 that unfortunately fell and broke) -- perhaps this tidbit of information will help someone figure out what the problem might be.  Anyone?

---

### Post by fheinsen on 2005-04-07
UPDATE: gnome pilot sees my device if I run it as superuser.  For example, if I click on Applications -> Run Application, and run 'gksudo gpilotd-control-applet', this allows gnome pilot to see the Palm device.  Suggestions, anyone?

---

### Post by fheinsen on 2005-04-11
Hotsync had stopped working for me when I upgraded from a Treo 600 to a Treo 650.  The problem, it turns out, was that the Treo 650, being a new device, had not yet been included in the device identification file used by gnome-pilot.  Here's how I solved the problem:

1. Open gnome-pilot's device identification file:
```

# sudo gedit /usr/share/gnome-pilot/devices.xml

``` 

2. Add the following lines to the devices.xml file:
```


<!-- PalmOne -->

<!-- Treo 650 -->
<device vendor_id="0830" product_id="0061" />


``` 

3. Kill all gpilotd and/or pilot-applet processes that may be running on your system:
```

 # sudo killall gpilotd gpilot-applet
 
``` 
  
4. Configure gnome-pilot as you normally would -- i.e., on the Gnome menu, click on System -> Preferences -> Palm Preferences, and then follow the instructions on-screen.

---

### Post by fheinsen on 2005-04-11
The "backup" conduit wasn't working with the Treo 650, but this fixed it:

1. Open your backup-conduit configuration file:
 ```
# gedit ~/.gnome2/gnome-pilot.d/backup-conduit:
``` 

2. Set gnome-pilot to exclude "Shim Logs" files.
 ```
exclude_files=Shim\ Logs
``` 

For further info, see
[http://mail.gnome.org/archives/gnome-pilot-list/2004-December/msg00009.html](http://mail.gnome.org/archives/gnome-pilot-list/2004-December/msg00009.html)

I hope this is helpful to others -- it's my tiny "thank you" to the Ubuntu team.

---

### Post by Blackneto on 2005-04-14
I had everything working under Hoary:

[http://ubuntuforums.org/showthread.php?t=21466](http://ubuntuforums.org/showthread.php?t=21466)

Now I cannot get the calendar to sync at all.


under hoary, calendar sync locked up the first time but now it wont work at all.
All other conduits that i use work fine:
Eaddress
Etodo
File

---

### Post by Psquared on 2005-04-15
Funny thing happened. I had been reading about all these problems with syncing Evolution to PDAs and I decided to try it myself. I have an older Sony Clie. The first time it didn't work. I was using a USB connection so I tried editing the connection to ttyUSB0. That didn't work so I changed it to ttyUSB1. Bingo - worked like a charm. I did a one time copy from pilot to evolution and everything was there. The only conduits I use are calendar, task, time and contacts.

Then, I set it up to synchronize between the two and I experimented by adding entries first in Evolution and then on my Sony and ran it again. Bingo - worked again.

In fact, I would have to say that this is a heckofaloteasier than doing a sync in w$. I didn't have to install any third-party software.

Cudos to Ubuntu again.    :grin:

---

### Post by jfdill_2 on 2005-05-18
[QUOTE=fheinsen]I forgot to mention that gnome pilot was working perfectly with my previous PalmOS device (a Treo 600 that unfortunately fell and broke) -- perhaps this tidbit of information will help someone figure out what the problem might be.  Anyone?[/QUOTE]
Somewhat OT but, How does the Treo 650 compare to the Treo 600 in your experience?  I have lots of dropped calls on my Treo 600 with Verizon, slightly improved since I upgraded the firmware, but now I hear the Treo 650 is available and I am debating to upgrade or say to heck with it and switch to a Blackberry (yeah, I know the Blackberry does not sync directly with Linux, but I do not rely much on that feature anyway).

---

### Post by fheinsen on 2005-06-22
[QUOTE=jfdill_2]Somewhat OT but, How does the Treo 650 compare to the Treo 600 in your experience? I have lots of dropped calls on my Treo 600 with Verizon, slightly improved since I upgraded the firmware, but now I hear the Treo 650 is available and I am debating to upgrade or say to heck with it and switch to a Blackberry (yeah, I know the Blackberry does not sync directly with Linux, but I do not rely much on that feature anyway).[/QUOTE]

I use Sprint PCS in New York City, and the service has been reasonably good so far.  Voice quality is comparable or perhaps a bit better than with the Treo 600 in the PCS network.  No idea about voice quality on Verizon's network.  Hope this is helpful.

---

### Post by bpilgrim1979 on 2005-07-26
Hello, to what apps do the Palm address book, todo, etc sync?  The gnome-pilot docs mention several default conduits but don't mention any apps.

I am aware of Ximian and Jpilot.  But does Gnome have default apps?  Or do you guys use the KDE pilot apps?  Thanks!

---

