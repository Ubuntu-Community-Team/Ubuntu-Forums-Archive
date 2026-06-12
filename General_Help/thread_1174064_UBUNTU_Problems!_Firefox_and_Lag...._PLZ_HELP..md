---
title: "UBUNTU Problems! Firefox and Lag.... PLZ HELP."
date: 2009-05-30
forum: General Help
---

### Post by justingwilson on 2009-05-30
[B]Okay everyone. I need some answers. First of all I have Ubuntu Linux version 9.04 and I can't watch youtube videos, OR ANY videos ONLINE. I have installed adobe flash player using firefox. So then, it started working. I could then on WATCH videos. Okay. But something happens a-lot. When I go to watch a video MOST THE TIME it gives me a GRAY player without ANY controls or anything. So, if I refresh the page USUALLY it helps. But got that out of the way. Next thing is WHEN I DO GET VIDEOS TO WORK, the SOUND it SKIPPING really bad. Meaning when someone says a word it will like kinda echo it. None of this happens in windows. Also I was watching youtube videos on my windows (which I am on right now.) and there was a guy said EVERYTHING that is happening to me is for him too. So, Therefore my ubuntu OS Is VERY FAST, But when I open firefox it GOES CRAZY. Meaning like the video and sound problem and everything. The OS Kinda lags a bit. Some1 PLEASE help me. I really like ubtunu. Please help. :sad:

Some system specs:

I have a compaq Presario C700

Which has a 100gb hard drive, 1gb of ram, 15in screen (laptop) its dual core processor. And thats all I know for now. Just ask for something and I'll try to find it. Thanks. Justin.[/B]

P.S. I have firefox 3 which is already installed. Also I forgot to say I installed ubuntu using wubi. And I also installed 8.10 then upgraded to 9.04!! Oh. :smile: and also I cant seem to connect using my wireless router too. I am using direct connection becuz of that! Justin.

---

### Post by Tipped OuT on 2009-05-30
Follow the directions from this website: [http://tombuntu.com/index.php/2008/10/16/install-adobe-flash-player-10-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/16/install-adobe-flash-player-10-in-ubuntu-804-and-810/)

This fixed it for me.

---

### Post by b@sh_n3rd on 2009-05-30
To install all restricted codecs and other needed programs/plugins including Java and Flash type this in a terminal. To start the GNOME terminal, goto, Applications > Accessories > Terminal. Type this at the prompt: ```
# sudo apt-get install ubuntu-restricted-extras
``` That's it. After that you have all you need :D. And welcome to the community! Have fun with Ubuntu :D

---

### Post by dunkar70 on 2009-05-30
I would also check your video chipset. Jaunty (9.04) is known to have problems with video playback in Jaunty on systems with Intel graphics chipsets. There are a couple of posts in these forums related to the problem. If you have an Intel graphics chipset, then you have a few options:
1. Reinstall Intrepid (8.10)
2. Attempt one of the work-arounds listed in these forums (search for Jaunty video with Intel)
3. Wait for the problem to be fixed

---

### Post by bacardiandwatermelon on 2009-05-30
Don't know if this applies to you. But when I was having flash issues I had both the "adobe-flashplugin" and "libswfdec-0.8-0" installed, removing the libswfdec package and restarting sped everything up for me.

---

