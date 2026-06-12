---
title: "Problem with BT nokia hs-26W and skype"
date: 2009-02-11
forum: General Help
---

### Post by luquino on 2009-02-11
Hi to all!
I downloaded Blueman 06-r121-0ubuntu3-ppa1i, my OS is ubuntu Intrepid 8.10 on eeePc, same issue on desktop pc with Ubuntu 8.10 AMD64.
I usually use skype and I tried to connect my BT headset nokia HS-26W.
Blueman can recognize and connect the headset and activate the audo service on it.
To use it with alsa I added the .asoundrc file to my home dir like this

pcm.Headset
{
   type bluetooth
}

no other lines in the file.

After a fresh boot the connection is ok, skype can make the test call, the sound quality is perfect, no noise at all, but after that there is no way to obtain further connections between skype and the headset. I have to reboot the system.
Blueman can connect and disconnect the headset as many times as I want, it shows always the status icons in ok state, and connect it to audio services.
XMMS as well connects and use the headset without problems.
But skype can' t use it, after the first connection always says "audio connection problems".

Does anybody knows a trick to fix this?

---

