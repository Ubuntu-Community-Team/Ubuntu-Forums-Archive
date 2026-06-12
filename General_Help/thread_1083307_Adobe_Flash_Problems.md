---
title: "Adobe Flash Problems"
date: 2009-02-28
forum: General Help
---

### Post by DocEsq on 2009-02-28
Running Ubuntu 8.04 LTS with the latest version of Firefox.  I have always had a problem with web pages that require Flash (NYtimes, Historychannel, Youtube, Hulu, etc...)  Searching with Google it seems that a lot of people have the same problem that I do in that nothing shows up, or you get the arrow.

Any way I have tried reinstalling Flash from Add/Remove, Synaptic Package Manager and directly from Adobe (FYI Synaptic Package Manager installs a later version then what is is on the Adobe site).  I even went Root and made sure that I had all of the plugins in "/usr/lib/firefox" "/usr/lib/mozilla" and "/usr/lib/mozilla-firefox" as I had all folders in my system.

Still no luck so I then uninstalled completely from Synaptic Package Manager the Adobe Flash Plug in and also the flashplugin-nonfree.  I then reinstalled the Adobe Flash Plugin and I what is different now is that I will also get a message on the web pages to "Upgrade Flash Player".

At this point I am not sure what else I need to do since the only way for me to see websites that have Flash is to boot into Windows, which I would rather not do.

Any help would be greatly appreciated.

Thanks in advance

---

### Post by DocEsq on 2009-03-04
^Bump^

---

### Post by Therion on 2009-03-04
Try this first:```
sudo apt-get install ubuntu-restricted-extras
```
Restart Firefox.

If still no joy, open Synaptic, search on **gnash** and remove any gnash-related packages you find.
Restart Firefox again.

---

### Post by DocEsq on 2009-03-05
Most if not all from the "ubuntu-restricted-extras" is already on my system and my problems occur whether gnash is installed or not.

Any other suggestions?

---

### Post by DocEsq on 2009-03-12
After long periods of research, installing and uninstalling packages, even installing IE6 I have found a workaround.  I installed Opera and am able to visit sites that use Flash without having to install anything else.

As I can use Opera I believe that my problem is with Firefox since I have not had to change any pathways.  Trying to correct this (even if possible) is beyond my skills at this time.

The good news is that I am able to use Ubuntu more and more and do not need to boot into Windows as much now.

---

### Post by killabee44 on 2009-03-14
Doc,

I am having the same problem. I use 8.10 Intrepid and only get a black tv screen where the video should be. I have this problem with Firefox and also with Konqueror. 

If anyone has found a solution please post. Opera worked as a temporary solution. Thanks for that one.

---

### Post by DocEsq on 2009-03-14
From what I have found in reading all of the "solutions" there is a problem with how Flash integrates with Firefox.  Most instructions are to remove the flash and then then download from adobe the .deb file and install.  I have found that this does not work.

Since I have Opera now I will use that whenever there is a site with flash that I need to acesss.  For the rest it will be Firefox.

I hope that this bug will be fixed in the future.

I am curious if those running Mint are having the same problems.

---

### Post by avtolle on 2009-03-14
I'm running Mint (along with 8.10); no problems with Flash either side under Firefox, FWIW.

---

### Post by killabee44 on 2009-03-14
Well, after much reading and tweaking I've been able to get konqueror to work but still not firefox. At least now I have options. 

I will continue to try to get firefox to work.

---

### Post by Twitch6000 on 2009-03-14
> **avtolle said:**
> I'm running Mint (along with 8.10); no problems with Flash either side under Firefox, FWIW.

Same here I am running the .deb from adobe themself though.

I am using Mint 6 and Ubuntu Jaunty right now.

---

### Post by DocEsq on 2009-05-21
I some how have flash working now.  I bought a new hard drive and did a fresh install and flash is working great.

go figure.

DocEsq

---

