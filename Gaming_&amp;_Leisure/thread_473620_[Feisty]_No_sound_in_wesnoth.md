---
title: "[Feisty] No sound in wesnoth"
date: 2007-06-14
forum: Gaming &amp; Leisure
---

### Post by daniel311 on 2007-06-14
I just installed wesnoth on my fresh Feisty installation but I don't get sound nor music in Battle of Wesnoth:

Sound and Music checkboxes in options stay empty when being leftclicked.

I do have sound in Totem, and several LGP games. The GDM start sound (very short one) is played. But no furhter sounds in Gnome are played. In System->Preferences->Audio Tests are functional but Systemsounds on the second Tab don't play. I can play these files trough totem.

alsamixer only works, if i sudo su -, it does not work as a user or directly with sudo. Can this be a problem?

Some via82xx modules and the whole snd_...-stuff is loaded properly

How can I fix that? I'll do some investigation about what actual sound chip is on my motherboard. I am using onboard sound. What information can be usefull for hunting this bug? (aplay -l, ls -l /dev, /etc/esd/esound.conf?)

---

### Post by Cappy on 2007-06-14
I think the problem of not being able to control alsamixer from a user happens when you either turn off that user's ability to do that, remove them from the audio group, or remove the audio group. Unfortunately, I can't remembe/find how to do the last two.
In (System-->Administration-->Users and Groups), Click on your username, click Properties, click "User Privileges" and make sure "Use audio devices" is checked.

---

### Post by daniel311 on 2007-06-14
Thank you, i'll try that today. Problem may be, that I didn't do a fresh install as I previously stated. It was a upgrade from edgy eft.

---

### Post by daniel311 on 2007-06-15
Problem resolved. strace alsamixer helped here. Solution was to rm ~/asound.rc and rm ~/asound.rc.* 

So for anyone upgrading from edgy and some applications don't play sound properly, try that solution.

---

### Post by Bokonon on 2007-06-20
Thanks for the help.  I had the same trouble, no sound, no option to 'x' the sound and turn it on it the game.  

Using your help, I commented out the line in .asoundrc and I was able to get sound.

[HTML]# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
#</home/<username>/.asoundrc.asoundconf>
[/HTML]

---

