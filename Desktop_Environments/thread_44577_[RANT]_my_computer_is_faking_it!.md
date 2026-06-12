---
title: "[RANT?] my computer is faking it!"
date: 2005-06-26
forum: Desktop Environments
---

### Post by virgule on 2005-06-26
'right
 Ok dont get me wrong but I am getting seriously itchy. From performance degradation to weird and unexpected behavior something is really fishy in here (be it Ubuntu or just my box).

(*) There is apt-get repositories posted in this forum that provides packages that can't be authenticated. I dont thrust this. --EDIT: I've been said its normal.
* hdparm tests say my disk is reading 160MB/second but there is no activity whatsoever with this drive when I order the test. I hear nothing, the led is not flashing and gkrellm line's stay dead flat. Whats THAT?! ](*,) 
* I 'activate' Firestarter firewall just to realize this blocked the internet. Using only the default settings and Google would not even load.
* Fonts keep changing aspect between different window managers/ desktop environment. If I adjust them from one, they are messed up in the others. This is a trinity?
* I mean, ~30 second to load 'kodo'?!?!? that hurt my feelings..
* How comes KDE 3.4, being such a bloatware, provide better responsiveness than the same app ran from Xfce4??
* Why does XMMS is running fine from XFce4 but can just crash in KDE and wont launch at all from GNOME?~?!

 It feel so wrong.. Linux is a cruel thing. :-x Of course it will be my configuration's fault.. heh? So, if it is my fault, please, show me what It can be when configured properly. I beg you dont send me to google once again. Lets start from scratch if need be! Lets make this thing scream glory! I begging you..

---

### Post by Kyral on 2005-06-26
Well, I can help you with the first one. The Backports (and maybe Universe and Multiverse) will always give you that "cannot be authenticated" error. Just ignore it as long as you use only Ubuntu Repos (Main, Security, Extras, Universe, Multiverse, Backports) you will be fine

---

### Post by hondje on 2005-06-27
> **virgule]
* hdparm tests say my disk is reading 160MB/second but there is no activity whatsoever with this drive when I order the test. I hear nothing, the led is not flashing and gkrellm line's stay dead flat. Whats THAT?! ](*,) 
[/quote]
The -T switch is basically testing your bus, the -t switch is basically testing how fast you can sustainably read from the disk.  It doesn't actually read, it just sees how fast you can get read through the buffer to the disk.  Confused me the first time I saw that, too   said:**
> 
* I 'activate' Firestarter firewall just to realize this blocked the internet. Using only the default settings and Google would not even load.


You'd have to explain how you have your network and internet access set up before someone could provide a reason and/or solution.

[QUOTE=virgule]
* How comes KDE 3.4, being such a bloatware, provide better responsiveness than the same app ran from Xfce4??
[/quote]

KDE isn't bloatware, it's feature rich.  Ignoring that, you should probably say what the exact application is.  If it's an application that depends on qt libraries and/or DCOP, then XFce needs to start those first, which are started during startup by KDE.

[QUOTE=virgule]
* Why does XMMS is running fine from XFce4 but can just crash in KDE and wont launch at all from GNOME?~?!
[/quote]

Good question. Open up a terminal and type 'xmms' and hit enter, and see if it gives you any error messages.

---

### Post by virgule on 2005-06-27
> **hondje]The -T switch is basically testing your bus, the -t switch is basically testing how fast you can sustainably read from the disk.  It doesn't actually read, it just sees how fast you can get read through the buffer to the disk.  Confused me the first time I saw that, too   said:**
> 
alright..

[QUOTE=hondje]
You'd have to explain how you have your network and internet access set up before someone could provide a reason and/or solution.

1- Install ubuntu
2- boot ubuntu

It is a cable modem. I think it work with DHCP. I never have been asked either changed any settings as far as I know only 'hostname' at install time.

Download speed is perfectly normal. Strange enough, again, is little things often take forever to perform. I.E.: a 'dict' lookup. Websites are almost always toooo slow to load especially those 'full of it' like forums with multiple little stuffs and buttons. It used to flow much better. I feel the 'reply' is having a hard time comming back in. Like that:
1- send a request to foo.com
2- waiting for a reply... 
3- ...still waiting...
4- ooh! page title is in... wait.. ok now it got the background color... lalalalala.. some widgets here and there...
5- Usually, a big block come in and I can see the general aspect of the page. Its still unusable tho..
6- Then it 'refresh' and is fully loaded.
7- Rince and repeat.

I happen too much to be normal internet latency. 

[QUOTE=hondje]
KDE isn't bloatware, it's feature rich.  Ignoring that, you should probably say what the exact application is.  If it's an application that depends on qt libraries and/or DCOP, then XFce needs to start those first, which are started during startup by KDE.
[/quote]
Im thinking of Opera 8.01 static. Lets say I want to select some texts for C&P in KDE its smooth and follow the pointer nicely but in Xfce4 it lags behind.. stuffs like that. Moving windows around is better in KDE too for the same reason. Xfce4 leave trails and I can see it redraw the window when I drop it while in KDE its smooth and redraw is quick enough. Same thing when using the scrollbars. Thats intriguing me because I always though Xfce is light (thats why Im on it most of the time) and easy on resources how can It run 'slower' than a full-fledged environment like KDE? :-?

[QUOTE=hondje]
Good question. Open up a terminal and type 'xmms' and hit enter, and see if it gives you any error messages.
[/QUOTE]
I made some progress here. It seam KDE and GNOME start ALSA upon login so XMMS complain it can't use it. It crash right there leaving no msg in terminals or lockup after clicking play button with  'could not open DSP device' or something.... I have shut down the Sound Server in both environments and now use OSS for XMMS audio. Its working 'fine' but consume almost 20% CPU. I recall my first Linux installation (YDL3) where it used only 3 to 8%. ALSA get choppy as soon as something else occur in the system. Never tried ESD.

I crossing my fingers and pray these manufacturers agree to provide Linux with the appropriate tools and informations to help the devs producing stuffs as 'good' as the mainstream OSs. O:)

---

