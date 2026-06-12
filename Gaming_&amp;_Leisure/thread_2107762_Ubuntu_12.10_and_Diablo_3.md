---
title: "Ubuntu 12.10 and Diablo 3"
date: 2013-01-22
forum: Gaming &amp; Leisure
---

### Post by jayzon915 on 2013-01-22
I accidentally posted this in the Hardware forum first. I hope this is in the right place. I will try to be brief. 

I have a older gaming machine that was running Windows 7 and able to play Diablo 3 flawlessly on high settings. I really want to switch over to Ubuntu and learn more about Linux. However, the only thing that is holding me back is Diablo 3 performance.

I've been playing with it for a couple weeks now and am stumped. I was having some other issues with a wireless card Linksys AE1000 (RT3572) freezing the system. I read has trouble with sleep mode so I switched to a different card that seems to be working. Now I am trying, in vain I feel like, to get the video card performing close to it's Windows 7 performance. I have Diablo 3 installed using WINE and PlayonLinux separately but both installs lag significantly in game. 

SPECS:
AMD Phenom II x4 3.5Ghz
8GB DDR3 
2 500GB SATA 3 7200RPM HDs in RAID0
Asus M4A88t Motherboard
PNY GeForce GTS 250 1GB
- Running 'glxgears -fullscreen' I average ~3300 fps
- Running 'glxgears' I average ~23000fps
- nvidia driver version - 304.51
- Using NVIDIA Binary Xorg driver from nvidia-current

Things I have tried:
Installed Ubuntu 12.10
Switched from Unity to 'Gnome-Session-Fallback' because Unity has a negative impact on gaming performance. 
Using Nvidia binary Xorg drivers instead of the Nouveau display drivers because I have told that they have better performance. 
Upgraded the OS fully, 'apt-get upgrade' and believe that everything is updated and stable. 
Using PlayOnLinux v4.1.8 and Wine 1.5.5 patched for Diablo 3.
Tried setting the Affinity to both a single core and two cores within WINE with performance getting worse.

At the lowest possible resolution with all of the graphics set to low/off the game jumps 10-40fps constantly even when standing still. When I get in game the fps still drops and jumps like crazy and is unplayable at any resolution. I don't feel that it is a problem with PlayOnLinux or WINE as I have checked everything against other setups that work.

Any advice on things to check/fix within Ubuntu?

---

### Post by jayzon915 on 2013-01-24
Hm... No response. I guess there is not an easy answer for this one... ?

---

### Post by Thee on 2013-01-24
Probably not. I asked a similar question about WoW and got no response too. Only I have ATI card, and I was under the impression that Nvidia drivers are better on Linux and run the games under Wine much better then ATI. I didn't try to install Diablo 3 yet, but I bet I would get similar performance as you.

Sorry I'm no help, I'm just hoping someone answers you and maybe I learn something to fix my problem also :)

---

### Post by Lightning Dragon on 2013-01-25
Hello,

I'm sorry for the lack of replies/help, but I can only offer you directions to places you can read that might help you improve your gaming performance with Diablo 3.

[http://www.iheartubuntu.com/2012/05/install-diablo-3-on-ubuntu.html](http://www.iheartubuntu.com/2012/05/install-diablo-3-on-ubuntu.html)
[http://www.evilcodingmonkey.com/2012/05/15/playing-diablo-3-on-ubuntu-made-very-easy/](http://www.evilcodingmonkey.com/2012/05/15/playing-diablo-3-on-ubuntu-made-very-easy/)
[http://sixgun.org/gaming-diablo3/](http://sixgun.org/gaming-diablo3/)
[http://www.youtube.com/watch?v=InQNW6WFb3U](http://www.youtube.com/watch?v=InQNW6WFb3U)
[http://www.youtube.com/watch?v=FInth5Fdg2M](http://www.youtube.com/watch?v=FInth5Fdg2M)

I think your performance issue should be center towards the manufacturers of your GPU. If it is a problem of the driver/Linux not being able to recognize the GPU's full performance, you definitely need to file a bug report at the manufacturers or go to their forum to help you set it up properly. 

[https://devtalk.nvidia.com/default/board/98/linux/](https://devtalk.nvidia.com/default/board/98/linux/)

But you are right, it doesn't seem like a problem with PoL or WINE, as others play it pretty fine. However, if it isn't  your GPU or the driver/settings that is messing with you, it might be the configuration you have for PoL or WINE. You can try to downgrade WINE to 1.3 or 1.4. The 1.5 has been known to not work well with some people, and usually fixes issues.

I'm sorry I could not offer more personalized help. If I had the game I would definitely set the thing up and record it all down for you. 

As for you Thee, you should check out the WoW thread here for some answers or perhaps give them your question. Check out my sig for links, or check here; [http://ubuntuforums.org/showpost.php?p=12470858&postcount=2](http://ubuntuforums.org/showpost.php?p=12470858&postcount=2)

---

### Post by jayzon915 on 2013-01-27
Thank you very much for your reply... I will take a look into both of those tips. I think that Diablo has issues with WINE under 1.5... But that could be the issue. I am trying to find people that are interested in Linux to be able to learn from them. :-)Thank you very much for your help.

---

### Post by Lightning Dragon on 2013-01-27
Hello,

This forum is a great place to start, then. But if you want to learn more about Linux, consider getting a [Linux book]("http://www.amazon.com/s?ie=UTF8&field-keywords=Linux%20book&index=blended&link_code=qs&tag=linmin-20"), or read the [Ubuntu Pocket Guide]("http://www.ubuntupocketguide.com/index_main.html") or the [Manual]("http://ubuntu-manual.org/"). 

As for WINE, if downgrading fixes the problem for you, please come back and make a post telling us if it worked--or if you fix it with some other way, please share! :)

If you have any other problems, come back and ask!

---

### Post by jayzon915 on 2013-01-28
I actually do have a couple of books and will be sure to go back over them. And I have an AAS degree in Computer Networks and Security.... I am sort of fluent in Linux, I can get around at least. I just have trouble troubleshooting more than what I have already done. :-)

---

