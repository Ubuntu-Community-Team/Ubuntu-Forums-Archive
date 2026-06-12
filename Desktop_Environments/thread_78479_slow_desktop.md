---
title: "slow desktop"
date: 2005-10-18
forum: Desktop Environments
---

### Post by brechtvb on 2005-10-18
Well now, at first, i've been a gentoo user for about a year, litlle experience, not to much.  Now i'd like to use ubuntu-linux.

Now, i'm running rhythmbox, gaim and firefox, and when i'm browsing a ntfs-hd or gaim plays a notification, my mp3 from rhythmbox is playing little pieces, it start-stops-start-stops-start-stops in a fast frequency for a second or 2.  Can i fix this, i've know there is ubuntu guide, but i can't find it.  Are there more sites like that ?

And gtk-apps are also not realy fast

--brechtvb

---

### Post by Stormy Eyes on 2005-10-18
The Ubuntu Guide is [here.](http://ubuntuguide.org/). As for sound issues, what sort of sound card have you got? I need to know before I offer specific advice so that I don't steer you wrong.

---

### Post by brechtvb on 2005-10-18
i've got an nForce2 motherboardh, but onboard sound is disabled in bios.  Now i use a Creative Sound Blaster Live! 24-bit, with the ca0106-alsa driver.  But now i was changing some settings.  And now ESD doesn't start anymore, and i can't find it in /etc/init.d/...

---

### Post by Stormy Eyes on 2005-10-18
[QUOTE=brechtvb]And now ESD doesn't start anymore, and i can't find it in /etc/init.d/...[/QUOTE]

Be glad for that. ESD is utter garbage. I'd use harsher words to describe it, but I promised I'd behave myself. For now, open **System -> Preferences -> Multimedia System Selector** and set your audio input and output to ALSA. Then open a terminal and do **sudo killall -9 esd**. That usually solves my sound problems, and I use a SB Audigy2.

---

### Post by brechtvb on 2005-10-18
i have done as you have said, but my mixer can't find any sound-devices.  now i have been doing things described in:

[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

should i reverse things ? :s

---

### Post by Stormy Eyes on 2005-10-18
[QUOTE=brechtvb]should i reverse things ? :s[/QUOTE]

Follow the guide's instructions to the letter.

---

### Post by brechtvb on 2005-10-18
i have done that, and it doesn't solve my problem.  My mixer still can't find any sound-device.  I really did the guide word by word.  I used gentoo for 1,5 year aproximatly, and i do know how to do such things right. (not to blame u).

---

### Post by Stormy Eyes on 2005-10-18
[QUOTE=brechtvb]i have done that, and it doesn't solve my problem.  My mixer still can't find any sound-device.  I really did the guide word by word.  I used gentoo for 1,5 year aproximatly, and i do know how to do such things right. (not to blame u).[/QUOTE]

I don't have any other ideas at the moment. I'm sorry I couldn't help you.

---

### Post by brechtvb on 2005-10-18
thanks anyway, with gentoo i had huge problems but it was a very fast system when fully operational. Maybe i'll go back to gentoo if i can't set ubuntu fully to my needs.

---

