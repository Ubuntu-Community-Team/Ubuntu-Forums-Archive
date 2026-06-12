---
title: "newb with problems..."
date: 2005-12-22
forum: Desktop Environments
---

### Post by emm on 2005-12-22
Hey ya'll, 

First post tonight. I am brand new to linux (and I do mean "new"). I installed ubuntu in a dual-boot set-up with XP. Things seemed to go ok with the major portion of the install, but now I have noticed three issues. 

First and foremost my wireless doesn't work. I still have the NIC for wired acess, but nothing on the wifi front. Being brand new, I read awhile, and then ran 'lshw' and found my Broadcom card listed as "unclaimed." Tried installing ndiswrapper and linuxant, but haven't had much success. Linuxant actually said the card couldn't be found. I am sure it's something obvious, but I know nothing about Linux yet. 

Second - my speakers do not work. Unlike the wifi, the sound card is listed, but no sound. Tried everything I read. 

Last - the customization I'm doing in Firefox, mainly extension settings, are not "saved" when I next load Firefox. It's not just Forecastfox or the gmail notifier. It's all of them. They load, but without any changes I've made in the options. 

Any help on these issues would be appreciated. I have read the forums as a lurker for quite a while, and you have been very helpful to others. I wish I had the kind of knowledge going into linux already, but I don't. If it's ok, I would ask that any suggestion be written so an absolute moron can understand them. 

Thanks in advance. I appreciate all the assistance. By the way, should I post the 'lshw' results here, too?

-Emm

---

### Post by hoodwink on 2005-12-22
> 
First and foremost my wireless doesn't work. 

Do some digging in the forums. There is lots of dta about wireless. I can't help with that, since I'm a desktop junky.

> Second - my speakers do not work. Unlike the wifi, the sound card is listed, but no sound. Tried everything I read. 
The most likely reason for this is that your sound card is muted. That's the (IMO very dumb) default with ALSA. Check in your Gnome menu to find a MIXER option, and unmute the sound. I can't give you specifics, because I'm using KDE.

> Last - the customization I'm doing in Firefox, mainly extension settings, are not "saved" when I next load Firefox. It's not just Forecastfox or the gmail notifier. It's all of them. They load, but without any changes I've made in the options. 
Hmmm! I've never encountered that problem. Are you sure you're clicking OK after changing the settings? Sometimes a settings panel will position too low on the page, and you don't notice the OK button hidden off page.

HTH,

---

### Post by Michael Steinberg on 2005-12-22
As for the wireless card: make sure you've got the correct driver--the one the ndiswrapper site shows, not the one the manufacturer may have on the web site. I've also found that I had better luck with ndisgtk, the GUI tool, than I did with the command-line tools--it found and configured the card right away once I had the correct driver. (That may just be my Mac background showing....)

Of the control tooks, so far I like NetworkManager best. (run nm-applet). Have fun when it gets working!

Michael Steinberg

---

### Post by ltmon on 2005-12-22
[QUOTE=Michael Steinberg]Of the control tooks, so far I like NetworkManager best. (run nm-applet). Have fun when it gets working![/QUOTE]

I think you have to install NetworkManager first: [https://wiki.ubuntu.com/NetworkManager](https://wiki.ubuntu.com/NetworkManager)

L.

---

### Post by Michael Steinberg on 2005-12-22
well, yes. I tossed that bit in since it took me a bit of searching to find out how to run the *%&! thing once I installed it....

---

### Post by blair on 2005-12-22
First a suggestion: Do not mix multiple problems in the same post. It makes it harder for others to follow/assist. Not a flame, just a recommendation. 


I can't help you on some of the items, but re: sound, are you running 5.04 or 5.10. There are several problems in 5.04 that were magically solved in 5.10. Also, you did not mention your sound card. Integrated chipsets on the motherboard have different common problems than add-on cards. It is always helpful to specify your specific model device when seeking hardware troubleshooting assistance. It also makes the answer easier for the next person with the same problem and same hardware to search and find this thread and your ultimate solution. Again, not a flame but a recommendation. 

So, re: sound, I have integrated sound on my Intel i845 motherboard. Here's how I resolved my sound problem:

1.	Applications > Sound & Video > CD Player > Open Preferences > Enable Start playback when CD Player starts.
2.	Open [http://wiki.ubuntu.com/SoundProblemsHoary](http://wiki.ubuntu.com/SoundProblemsHoary) and follow instructions there:
a.	General Fix (edit esd.conf file, restart machine, change default Sink and Source to Alsa
b.	Install Flash plugin and make Firefox.flash fix described
3.	Applications > Sound & Video > Volume Control > File > Change Device > Select correct audio device
4.	Applications > Sound & Video > Volume Control > Edit > Preferences> Enable all audio controls to be viewable
5.	Applications > Sound & Video > Volume Control > Playback tab > Ensure all sliders are up and all controls are unmuted.
6.	Applications > Sound & Video > Volume Control > Capture tab > Ensure CD is not muted anywhere.


Hopefully this will provide you with some troubleshooting clues. Good luck.

---

