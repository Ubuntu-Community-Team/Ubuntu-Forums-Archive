---
title: "Missing my beep (again)"
date: 2012-09-20
forum: Desktop Environments
---

### Post by silbar on 2012-09-20
Greetings,

A little over a year ago I posted
> In the upgrade to Ubuntu 10.04 LTS I seem to have lost my ability to beep within a script. Other sounds seems to work fine, as in videos on YouTube or with Rhythmbox. Re-installing the beep app in Synaptic did not bring it back. Any clues?
and got no responses to that posting.  So, I lived without beeps.

I have now upgraded to Ubuntu 12.04 LTS and I have the same problem: no beep.  Any enlightenment out there?  Does it have something to do with my sound card?  If I go into System Settings > Sound > Sound Effects, I get no audio response from any of the alerts.  I do get sound from radio stations and video or Flash clips.

---

### Post by papibe on 2012-09-20
Hi silbar.

Could you post the script code you are using to beep?

Regards.

---

### Post by stinkeye on 2012-09-21
The pc speaker is blacklisted.
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12035806&postcount=1").
Beep works here after editing **/etc/modprobe.d/blacklist.conf**

---

### Post by silbar on 2012-09-21
> **papibe said:**
> Hi silbar.

Could you post the script code you are using to beep?

Regards.

For what it's worth:

[INDENT]#!/bin/sh
# script for copying tar file to Jaz disk

ls -l /home

if [ -d /media/4B40-1A08/ ]; then 
  echo 'The disk is present'
else
  echo 'Disk not present, please insert'
  exit
fi

if [ -f /media/4B40-1A08/silbar.tar.gz ]; then 
  echo 'The tar file is there'
  rm -f /media/4B40-1A08/silbar.tar.gz
fi

cp /home/silbar.tar.gz /media/4B40-1A08
wait
ls -l /media/4B40-1A08
umount /media/4B40-1A08
beep[/INDENT]

---

### Post by silbar on 2012-09-21
> **stinkeye said:**
> The pc speaker is blacklisted.
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12035806&postcount=1").
Beep works here after editing **/etc/modprobe.d/blacklist.conf**

And that fixes it! I can beep again.  Thank you.

---

