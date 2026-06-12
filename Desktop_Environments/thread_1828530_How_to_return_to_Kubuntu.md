---
title: "How to return to Kubuntu?"
date: 2011-08-19
forum: Desktop Environments
---

### Post by tcarney57 on 2011-08-19
I've really done it this time! I've gotten Gnomed and I want to get back to KDE. Here's the details.

1. It all started when I was looking for a way to get rid of PulseAudio from my Kubuntu 10.10 installation. I wanted to use ALSA instead because I could not get PA to recognize any software sources for recording (such as audio from YouTube videos, etc.).

2. I spent several hours, surfed everywhere on the web, and tried many things that are now lost in a blur. The last thing I did was to follow what seemed to be a carefully documented procedure for doing what I wanted. The author went so far as to provide syntax to cut-and-paste, ready for sudo-ing. 

3. The multistep procedure seemed to delete PA, but the last step installed huge amounts of Debian stuff that flew by so fast I couldn't pay attention. After rebooting, I was left with the (no offense) damn Gnome desktop and only a few of the applications that were distributed with my Kubuntu. To add outrage to injury, fricken' PulseAudio was back in the driver's seat!!! I had some of my stuff appear on the desktop, so I don't think my user files have been affected. But wait, there's more:

4. After moving the main panel to the bottom on the desktop (where it belongs ;)), I poked around a bit, found my Firefox history and bookmarks were not showing, and just generally got more and more pissed off. When I went back to the panel, it was frozen solid. App icons on the desktop would work, and I could right-click on the desktop and get a menu. But the panel was frozen and I had no access to utilities, etc. This persisted even after two reboots.

5. I'm writing this using a live USB with Ubuntu and the Gnome desktop. It's my life raft, but I want to get back to shore. I want to reinstall the Kubuntu/KDE setup I had before and recreate all my settings, customizations, and :mad: . . . oh, you know.

6. Since I don't seem to be able to use what comes up now on rebooting, I'll need to work from this live version of Ubuntu. Any ideas? Am I hopelessly screwed?  

7. Here's one more thing: when rebooting as described above, the last thing on the screen was the _*Kubuntu*_ splash (with the little marque dots below moving from left to right). I don't know what this means except maybe some part of the system is still thinking Kubuntu even if the KDE desktop is not working.

That's a bunch of stuff to read, but I'm hoping someone might be willing to lead me out of perdition. ](*,)

Many thanks!,

Todd

---

### Post by realzippy on 2011-08-19
Boot in recovery mode,root shell,try:

```
sudo apt-get install --reinstall kubuntu-desktop
```


Btw,can't you get your needed data with your liveCD and make a fresh install?

---

### Post by ankspo71 on 2011-08-19
Hi,
For parts 1,2, and 3, there is an application missing in *ubuntu to record audio from your sound card. It is called 'pavucontrol' (Pulseaudio Volume Control). Install that application and then follow these generic instructions: 

[https://wiki.ubuntu.com/PulseAudio#Lucid_Lynx_10.04_and_Maverick_Meerkat_10.10](https://wiki.ubuntu.com/PulseAudio#Lucid_Lynx_10.04_and_Maverick_Meerkat_10.10)

The key part of the instructions is to change the recording stream to "monitor of <input device>" in the recording tab of Pulseaudio Volume Control. You need to repeat the instructions for every recording application you want to use.

I recommend realzippy's recovery mode advice too, especially helpful if the desktop is locking up on you. Hold down the shift key as your computer boots into Kubuntu to get into recovery menu.

Hope this helps.

---

### Post by XubuRoxMySox on 2011-08-19
Omygoodness, that must have been frustrating. But hopefully you learned a little bit...

The fun thing about all the 'buntus is that it's so easy to do a completely new installation (if you have a good internet connection) when I break it badly enough. And with a separate **/home** partition I can completely reinstall it without losing my settings, bookmarks, etc.

I use Xubuntu (awesomeness on my old hardware) which did not ship with PulseAudio 'til 10.04. And sure enough, PulseAudio messed stuff up on my 'puter too.

I wrote a quick-and-easy guide to replacing PA with ALSA [here]("http://robinsrantsandraves.wordpress.com/2011/07/27/replacing-pulseaudio-with-alsa-in-ubuntu/"), but it applies to Xubuntu 10.04 (I stick with the LTS versions). Maybe it'll help on your Kubuntu though.

-Robin

---

### Post by tcarney57 on 2011-08-20
> **realzippy said:**
> Boot in recovery mode,root shell,try:

```
sudo apt-get install --reinstall kubuntu-desktop
```


Btw,can't you get your needed data with your liveCD and make a fresh install?
Hey, thanks. The reinstall didn't work . . . It didn't seem to do anything. So . . . . . . Yes, I reinstalled from my "Ubuntu 10.10 Sixpack" cd. I got all my own stuff backup, but I forgot to backup my Firefox and Chrome histories and BMs. I really need to set up some kind of cron script or something to keep my backups more up to date. I'd just as soon backup system settings and preferences as well. I also wish I could somehow easily back up programs I've hand installed (either not available using apt-get or that don'e come with the standard distro. I'll look into this.  

Again, many thanks!

---

### Post by tcarney57 on 2011-08-20
> **ankspo71 said:**
> Hi,
For parts 1,2, and 3, there is an application missing in *ubuntu to record audio from your sound card. It is called 'pavucontrol' (Pulseaudio Volume Control). Install that application and then follow these generic instructions: 

[https://wiki.ubuntu.com/PulseAudio#Lucid_Lynx_10.04_and_Maverick_Meerkat_10.10](https://wiki.ubuntu.com/PulseAudio#Lucid_Lynx_10.04_and_Maverick_Meerkat_10.10)

The key part of the instructions is to change the recording stream to "monitor of <input device>" in the recording tab of Pulseaudio Volume Control. You need to repeat the instructions for every recording application you want to use.

I recommend realzippy's recovery mode advice too, especially helpful if the desktop is locking up on you. Hold down the shift key as your computer boots into Kubuntu to get into recovery menu.

Hope this helps.
Thanks for your reply. I spent another whole day struggling with this thing (I'm on vacation). See my reply to realzippy above. Now that I have a clean (re)install I will try your suggestion about using pauvcontrol. It was already installed and I did mess with it, but I was never able to do anything with the channels it displayed. Either the program was frozen or something else because I couldn't select, highlight, or do anything to any channel, even though they're displayed like vertical sliders. I'll follow the link to the wiki your provided and see if I can't get this resolved.

Many thanks!  -- Todd

---

### Post by tcarney57 on 2011-08-20
> **dixiedancer said:**
> Omygoodness, that must have been frustrating. But hopefully you learned a little bit...

The fun thing about all the 'buntus is that it's so easy to do a completely new installation (if you have a good internet connection) when I break it badly enough. And with a separate **/home** partition I can completely reinstall it without losing my settings, bookmarks, etc.

I use Xubuntu (awesomeness on my old hardware) which did not ship with PulseAudio 'til 10.04. And sure enough, PulseAudio messed stuff up on my 'puter too.

I wrote a quick-and-easy guide to replacing PA with ALSA [here]("http://robinsrantsandraves.wordpress.com/2011/07/27/replacing-pulseaudio-with-alsa-in-ubuntu/"), but it applies to Xubuntu 10.04 (I stick with the LTS versions). Maybe it'll help on your Kubuntu though.

-Robin
Many thanks! For an update, see my replies to the other kind souls who've also replied. Now that I have a clean install, I will try your guide to 86ing PA in favor of ALSA.

On a related note, I'm intrigued with the way you've set up a separate home partition. I take it that means that when you want/need to reinstall Ubuntu, it will leave the existing home partition alone (at least, if your select that install option). Am I understanding that correctly? Can I set up such a partition now that I have a whole-HD 10.10 partition now?

Thanks again!!!!  --- Todd

---

### Post by tcarney57 on 2011-08-20
I tried your suggestions on the wiki and I still can't get any recording done. I'm disgusted with PA, so I've removed it. It looks as though audio is one of the little corners of *buntu in which there are too many cooks. I've heard someone decided to go with PA because it provides a "cleaner" and "simpler" interface, one that's not confusing to the "casual" user. While I'm a bit more than a casual user, PA has only made my audio harder--nightmarish, in fact.

So, PA is gone so I presume ALSA is running the show. I've just moneyed with it a bit and I still can't get Audacity to recognize any input other than the built-in mic on my laptop. 

Do you have any ideas? 

Thanks. -- Todd

---

