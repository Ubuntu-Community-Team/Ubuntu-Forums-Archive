---
title: "RealPlayer launches, freezes when buffering and more"
date: 2005-10-27
forum: Desktop Environments
---

### Post by seatea on 2005-10-27
Thanks to a lot of help from these  forums, I finally got RealPlayer 10 installed and to launch. Unfortunately, my excitement over getting that  done was short lived when I tried to use it on a website that  I want to access that requires RealPlayer. The file loads, starts buffering and then freezes and won't respond. I then have to force quit the program. I tried going to real.com and trying to open one  of their clips which did start to play, except there was no video or sound, The play controller just moved across the bottom of the  window silently and without picture. It then froze again and had  to be forced quit. I searched on the web and in these forums hoping to resolve this, but I could not. Once again, I am asking for assistance  in getting this troublesome application to work. I would gladly try an alternative, but HelixPlayer won't work and I am guessing  none of the other  players as these are real files. Can someone give me  some guidance on this problem?

---

### Post by Emerzen on 2005-10-27
For most of my streamed video, I've used MPlayer w/ a Plugin for Firefox.  I followed The Guide to install Mplayer [www.ubuntuguide.org](www.ubuntuguide.org) .  To get the streaming web-video cooking, I followed this thread [http://www.ubuntuforums.org/showthread.php?t=60505](http://www.ubuntuforums.org/showthread.php?t=60505).

Finally, if you need some of the more difficult to get packages, there are Ubuntu packages at this website...just add the lines they tell you to your sources.list file.

[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

---

### Post by seatea on 2005-10-27
The website I need to access requires RealPlayer. Will MPlayer be able to translate  files meant  specifically  for RealPlayer?

---

### Post by Emerzen on 2005-10-27
Yes, I view RealPlayer clips all the time w/ Mplayer plug-in.  I have kids who spend a lot of time on the PBS site for kids...much of which requires realplayer.  I just tested it again and it works great.

---

### Post by seatea on 2005-10-28
I looked at the ubuntuguide.org link. That might  be  doable for mplayer.I looked at the thread link and itis way over my head at this time or that is my perception anyway. Part of the problem is that I am using  a PM G4 400, ppc based computer. Those repository  add-ons often link to only the i386 version, which won't go on my computer. That's why I think it  was so complicated for me to install RealPlayer. I thought once it was installed, the troubleshooting would be more straightforward in getting RealPlayer to function, but maybe I was wrong. Additionally, I have the  complication of being very new to using Linux of any variety. While I have gotten a lot better with the concepts, it is still a rather daunting process.

---

### Post by seatea on 2005-10-28
I installed mplayer. It opens, but looks  strange. A window with no menu options opens  with  a picture of  a play button  and the  word mplayer on  a blue background and, separately, a  very small controller that looks  fuzzy on my screen opens. When I right  click on the controller, the menu opens but  does not respond. I went to the website and  tried to use it. The  player opened  in Firefox, buffered and stopped. There was no freeze of my program. One  other thing that has  occurred is  that  Firefox has  been unexpectedly quitting since I installed the mplayer plugins. I may have to uninstall it.

---

### Post by jworr on 2005-10-28
Personally I think Realplayer for linux is a joke and I don't like mplayer very much, so I use gXine.  It will work for sites the need quicktime, windows media player, or realplayer and it is easy to use. Here is how to install it:

go into synaptic and enable the universe repository under settings => repositories
search for gxine and check the box to install it

now you need to install the firefox plugins, to do this run the following commands

sudo ln /usr/lib/gxine/gxineplugin.so /usr/lib/mozilla-firefox/plugins/
sudo ln /usr/lib/gxine/gxineplugin.la /usr/lib/mozilla-firefox/plugins/
sudo rm /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.xpt
sudo rm /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.so

this should do it for you hope this helps you

---

### Post by seatea on 2005-10-28
I installed it  from synaptic and followed your instructions to install plugins. Everything seemed to go ok. I tried to open a BBC broadcast from gxine's menu, but it wouldn't play. I got two error messages. 1) missing drv4.so.6.0 and 2) could not find sipr.so.6.0. I tried to sudo apt-get those two files, but each came back, "file not found". I tried to open a RealPlayer file on my desktop and nothing  happened. What next?

---

