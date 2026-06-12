---
title: "DVD Defaults and Firewall Config"
date: 2005-06-28
forum: Desktop Environments
---

### Post by monkeywork on 2005-06-28
First off Ubuntu is amazing - great job everyone :)   

My questions are as follows:

1.  How can I make xine be my default DVD player rather than the default package (it's name eludes me right now).

2.  Is there a tutorial on configuring the firewall via command prompt (incase i'm SSH'd to the box and need to make a change).   Firestarter is currently installed.


Thanks!

---

### Post by monkeywork on 2005-06-28
bumping 

---------

Also adding question #3

My machine has multiple soundcards and ubuntu detects all of them and they all work, however the problem is different applications use different soundcards (DVD playback through one and system sounds via another).  How can I force all sound to be directed to one card?

---

### Post by doclivingston on 2005-06-28
1) Under system->preferences->removable storage you can change the program that gets launched when DVDs (and other media) get inserted.

2) I'm not sure if there is a tutorial for editing firestarter's configuration from the command line, but the files are in /etc/firestarter/

3) It's probably that the are set to using different audio devices. You'll probably have to change them in quite a few places. You can change GStreamer's audio configuration by using `gstreamer-properties`, but I can't remember exactly how you set which device to use off the top of my head. Sorry.

---

### Post by monkeywork on 2005-06-28
Thank you for the reply :)  If anyone else has anything to add to the soundcard issue let me know

---

### Post by cwaldbieser on 2005-06-28
I know the SDL library likes to read the AUDIODEV environment variable to determine which sound device to use.

---

