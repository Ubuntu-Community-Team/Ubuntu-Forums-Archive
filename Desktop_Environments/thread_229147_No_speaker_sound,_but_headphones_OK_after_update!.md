---
title: "No speaker sound, but headphones OK after update!"
date: 2006-08-04
forum: Desktop Environments
---

### Post by Robertjm on 2006-08-04
Hi all,

Tonight I upgraded by sources.list file to get some additional repositories. After doing that it came up with a whole bunch of updates, of which most were KDE-related.

So I ran the update and rebooted by computer. Now, I've got sound coming out of my headphone jack on the Soundblaster Live Drive unit. Also, the front panel's mic input (Line1) is working! It wasn't earlier so this is an improvement.

Unfortunately, my regular speakers are silent. Checked settings in the Alsa and main volume is full and unmuted, so that's not it.

I even went so far as to reinstall the alsa-base through synaptec and then reboot the computer.

Using Ubuntu Dapper Drake 6.06.

Anyone recently experienced something like this or have any suggestions on how to resolve this?

Tnx!!

Robert

---

### Post by edu65 on 2006-10-28
This is most strange. I had the same problem after going through the usual updates and switching to the 686 kernel in order to get SMP support.

I rebooted using the 386 kernel and got sound from the built-in speakers (just like after a fresh install).

Now the strange part... booting back to the 686 kernel has made the speakers work again!  

Sorry if this does not help anyone. I just wanted to share my experience...

Using Dapper with a 2.6.15-27 kernel (HDA Intel / alsa mixer) on a Dell Inspiron 6400.


> **Robertjm said:**
> Hi all,

Tonight I upgraded by sources.list file to get some additional repositories. After doing that it came up with a whole bunch of updates, of which most were KDE-related.

So I ran the update and rebooted by computer. Now, I've got sound coming out of my headphone jack on the Soundblaster Live Drive unit. Also, the front panel's mic input (Line1) is working! It wasn't earlier so this is an improvement.

Unfortunately, my regular speakers are silent. Checked settings in the Alsa and main volume is full and unmuted, so that's not it.

I even went so far as to reinstall the alsa-base through synaptec and then reboot the computer.

Using Ubuntu Dapper Drake 6.06.

Anyone recently experienced something like this or have any suggestions on how to resolve this?

Tnx!!

Robert

---

### Post by Robertjm on 2006-10-28
I had forgotten about this thread! Glad you posted as I've got a workaround for the issue.

If you log into KDE with the Alsa driver, you get a quick blast of sound, but  the speakers go silent. Open the GNOME sound mixer. YES!! I said Gnome mixer.  

You will see the PCM level full, even though its not working. Now, change from the Alsa mixer to the OSS mixer. Make sure that PCM-2 is accessible. When you check it, it will be set to zero. Set that slider to what you want and you have sound coming out of the speakers!!

At this point you can change back to the Alsa mixer if you'd like. However, when you restart KDE you're probably going to have to do the same song and dance again to get the volume up. I have the retain levels marked in Kmixer, but its not retaining the levels I set. Also, there is no slider for PCM-2 in KMix, which is why I'm using the Gnome mixer instead.

This problem doesn't occur in Gnome at all, which is why I've stayed with Gnome pretty much. After the last KDE update to 3.5.5 I tried it out KDE again, but still the same problem. 

Reported a bug in KDE, but haven't seen any progress on it at all. 

[https://bugs.kde.org/show_bug.cgi?id=135861]("https://bugs.kde.org/show_bug.cgi?id=135861")

Later,

Robert

---

