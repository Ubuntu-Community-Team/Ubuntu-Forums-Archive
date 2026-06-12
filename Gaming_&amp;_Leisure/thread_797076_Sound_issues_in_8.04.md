---
title: "Sound issues in 8.04"
date: 2008-05-16
forum: Gaming &amp; Leisure
---

### Post by Rhemat on 2008-05-16
Heya All,

  I recently installed 8.04, and while some applications such as movie player provide sound, other applications do not.  The two I'm having trouble with are Quake 3 and Flash.
  One thing that could be causing this is that Ubuntu seems to think that I have 6 audio devices in my system:

<table style="width:194px;"><tr><td align="center" style="height:194px;background:url([http://picasaweb.google.com/f/img/transparent_album_background.gif](http://picasaweb.google.com/f/img/transparent_album_background.gif)) no-repeat left"><a href="http://picasaweb.google.com/fuzzyghost/Ubuntu"><img src="http://lh6.ggpht.com/fuzzyghost/SC5QIR7TxZE/AAAAAAAAADo/w8QKE4ETiOc/s160-c/Ubuntu.jpg" width="160" height="160" style="margin:1px 0 0 4px;"></a></td></tr><tr><td style="text-align:center;font-family:arial,sans-serif;font-size:11px"><a href="http://picasaweb.google.com/fuzzyghost/Ubuntu" style="color:#4D4D4D;font-weight:bold;text-decoration:none;">Ubuntu</a></td></tr></table>

  I believe the Ensoniq is the actual card in my system, and there is an onboard chip for sound (which fizzled out I believe), and I think the ATi card is actually my video card.  I've tried to find the program that gives the info on devices in my machine, but it does not seem to be in the menus.
  If any one has any suggestions, I welcome them.  I'm thinking that I may simply revert to 7.04, and hope for the best.

  Thanks in advance

---

### Post by cogadh on 2008-05-17
Uh, AFAIK, this forum has HTML disabled. Your table doesn't show up at all.

However, based on what you have said, it sounds like your first problem is you have an onboard and an off board sound card, both of which are enabled in BIOS. Go into your BIOS settings and disable whichever one you are not actually using and that may help clean things up a bit.

---

### Post by Rhemat on 2008-05-17
Thanks for the reply.  I had thought that the BIOS sound might be enabled, but just checked and it's off.
Also, sorry about the failed picture posting, I didn't realize it didn't work until much later.  Here is a link to it:

[http://picasaweb.google.com/fuzzyghost/Ubuntu](http://picasaweb.google.com/fuzzyghost/Ubuntu)

Thanks again for the help.

---

### Post by Rhemat on 2008-05-17
Well, I just logged into the machine, and just for the fun of it, I tested out the applications giving me trouble.  They work now.  The problem is, that I don't know how I did it.  I remember that I set the sound device to the Ensoniq (the actual card) last night before I shut it down.  That must be what did it.

Any way, thanks for the help.

---

### Post by Rhemat on 2008-05-17
Well, I hate to be a pain, but of course, sound is not working again, I didn't touch any configuration files.

I've seen other people having this issue, and was wondering if there is a common issue.  Have other people been having problems with PulseAudio, or some other sound library?

I might just go back to 7.04.

Thanks for the support.

---

### Post by cogadh on 2008-05-18
I had so many problems with PA, I ended up switching to Kubuntu, just because it still uses ALSA.

---

### Post by Rhemat on 2008-05-19
Thanks for the suggestion cogadh, I downloaded and installed Kubuntu 8.04, and sound just works.  MP3 and Ogg media drivers didn't take much fuss at all to install, and it found drivers for my ATi HD2400 card (haven't been able to test it, since I don't have installed a game that uses 3D acceleration yet, and I don't know the KDE equivalent of glxgears).

The one problem I have had with Kubuntu 8.04, though, is I was installing some media drivers (gstreamer (no bad or ugly set), I think libogg, flash, and a few that escape my memory), and apparently it conflicted with the KDE environment.  It decided to uninstall KDE, but it didn't notify me of such until after I hit Apply changes.  Is there a way to tell the system to notify me of such dependency conflicts?

Thanks in advance.

---

### Post by Rhemat on 2008-05-19
I spoke too soon.  Music volume works.  Flash still has no sound.  Haven't been able to test any games yet, but I fear I'll get the same result.  I'm wondering if the ATi card is to blame, because whenever I can get it's 3D acceleration drivers to work, the sound just goes away, but whenever sound works, Linux won't detect any drivers for the card.

It is the ATi card.  I got a solution from friend.  In terminal:

sudo asoundconf list
Find the device that is the actual card/processor that your speakers are using, and then:
sudo asoundconf set-default-card [card device listed in previous command]

Hope this helps other people with similar problems.

---

