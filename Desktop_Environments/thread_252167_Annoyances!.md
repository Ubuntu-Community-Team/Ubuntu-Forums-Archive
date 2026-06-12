---
title: "Annoyances!"
date: 2006-09-06
forum: Desktop Environments
---

### Post by BlacKat_K on 2006-09-06
Hi guys.I've been looking around for solutions and since i havent found any i thought i'd ask for help myself.Here's the first problem: i sometimes get an annoying error saying sometimes like "Firefox is already running but not responding and if you wish to open Firefox you need to close the other session or restart your computer". This happens sometimes after using thunderbird or kopete and i think it has to do with the fact that i sometimes use preset buttons on my Microsoft Multimedia Keyboard to open either mail or the browser.Thing is i cannot find the other firefox session to close and simply logging on and off wont do.I have to restart completely.Does anybody else have this problem??
   Another "annoyance" is Flash,you see it works,i installed everything and videos do play as well as pages using Flash,though sometimes  get an error saying i'm not using the latest version.The problem comes with sound in those videos,it stayes farter and farter behind the image and it reminds me of having Windows 98 and 64 MB of RAM...So how do i fix that?On the other hand when ever i have VLC on,i get no sound from these videos.Oh and another thing (and i promise this is the last one) I'm using KdeTV and after closing it i can still hear a faint sound coming from it.I have to mute the TV before closing it or else is like somebody is wispering from my speakers all the time :-? 
   So what do you think?Can you help a little kitty love ubuntu more?:)

---

### Post by BlacKat_K on 2006-09-06
Hi guys.I've been looking around for solutions and since i havent found any i thought i'd ask for help myself.Here's the first problem: i sometimes get an annoying error saying sometimes like "Firefox is already running but not responding and if you wish to open Firefox you need to close the other session or restart your computer". This happens sometimes after using thunderbird or kopete and i think it has to do with the fact that i sometimes use preset buttons on my Microsoft Multimedia Keyboard to open either mail or the browser.Thing is i cannot find the other firefox session to close and simply logging on and off wont do.I have to restart completely.Does anybody else have this problem??
   Another "annoyance" is Flash,you see it works,i installed everything and videos do play as well as pages using Flash,though sometimes  get an error saying i'm not using the latest version.The problem comes with sound in those videos,it stayes farter and farter behind the image and it reminds me of having Windows 98 and 64 MB of RAM...So how do i fix that?On the other hand when ever i have VLC on,i get no sound from these videos.Oh and another thing (and i promise this is the last one) I'm using KdeTV and after closing it i can still hear a faint sound coming from it.I have to mute the TV before closing it or else is like somebody is wispering from my speakers all the time :-? 
   So what do you think?Can you help a little kitty love ubuntu more?:)

---

### Post by pyros on 2006-09-06
You get that firefox message when it didn't close properly. Usually it's extensions that are to blame. You can run gnome system monitor, for gnome or kde System Guard for kde and end/kill the firefox process to get rid of it.
As for the flash version, blame adobe. according to this page:
[https://addons.mozilla.org/plugins/](https://addons.mozilla.org/plugins/)
the most current version of flash they support on linux is flash 7. Windows and mac are up to flash 9.

---

### Post by pyros on 2006-09-06
!

---

### Post by marianom on 2006-09-06
See
[http://www.ubuntuforums.org/showthread.php?p=1467857](http://www.ubuntuforums.org/showthread.php?p=1467857)

---

### Post by hexion on 2006-09-06
Simply open a terminal and type:
> killall firefox-bin

Then it should start normally ;)

Do you have 2.6.15-23 kernel? I had that issue with that kernel.. If you do, upgrade to a newer version and maybe your problem will solve.

---

### Post by hexion on 2006-09-06
About the kdetv issue, why don't you install another tv client and give a try??

You can try mythtv, tvtime, xdtv (I use this because it's the only one which works with xgl)...


About the flash issue... find this forum for "flash 9 ubuntu". I read last week a trick someone discovered.. He edited one text file and made webs think he had flash 9.... that way he could watch all videos.

And ending.. the vlc stuff :)
> sudo aptitude install vlc-plugin-alsa should do the job.

Bye

---

### Post by matthew on 2006-09-06
The original was posted twice, but since there were replies to each I merged the threads. Sorry for any confusion.

---

### Post by BE(Hons)Computing on 2006-09-07
hi guys can anyone tell me why my browsers all of a sudden terminate without any notification. is it because i am using 128 MB RAM? i was using firefox and then i installed opera but problem remained even when i installed opera. can anyone suggest something?

---

