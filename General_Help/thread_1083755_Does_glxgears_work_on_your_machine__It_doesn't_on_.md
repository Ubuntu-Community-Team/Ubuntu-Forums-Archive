---
title: "Does glxgears work on your machine?  It doesn't on either of mine!"
date: 2009-03-01
forum: General Help
---

### Post by MattPhillips on 2009-03-01
Hello everybody,

I've been having some pretty brutal problems getting opengl to work properly on Ubuntu 8.04, discussed at length here--

[http://ubuntuforums.org/showthread.php?t=1067979](http://ubuntuforums.org/showthread.php?t=1067979)

but what amazes me is that I have the same problem on a Dell Inspiron, 945gm, AND on a Mac using an ATI Radeon X1900 card.  So this makes me wonder:  (With direct rendering enabled.)  Who out there is actually able to get glxgears to work properly?  And what's your secret? :)

What happens when I run it is that the client area of the window--the gears+black background--isn't getting repainted properly.  If I drag another window (e.g. a terminal) on top of the glxgears window, the spinning gears float on top, while the frame lies beneath the new window as it should.  If I click on the frame and move it to a new location, something (either a black square or the spinning gears themselves) stays behind until I release the mouse, or longer.  This is probably related to other serious opengl problems I am having so I'm not just being picky.

So, dear reader: When you run glxgears--i.e.,

$ glxgears

do you get the above problems, too?  Or does it run perfectly smoothly, resize smoothly, repaint properly, etc.?  Please let me know!  Thanks--

Best,
Matt

---

### Post by MattPhillips on 2009-03-02
Hello,

Could someone please get back to me on this?  No expertise required, just

$ glxgears

and post what happens, i.e. whether you have the problems described above.

I'm worried that this is a genuine issue with Ubuntu, since I get it on two very different platforms, both of which appear to have no OpenGL issues under their native OSs.  Thanks--

Best,
Matt

---

### Post by emarkay on 2009-03-02
9107 frames in 5.0 seconds = 1821.369 FPS
9800 frames in 5.0 seconds = 1959.920 FPS
10336 frames in 5.0 seconds = 2067.176 FPS
12331 frames in 5.0 seconds = 2466.039 FPS
9496 frames in 5.0 seconds = 1899.172 FPS
9603 frames in 5.0 seconds = 1920.505 FPS
10199 frames in 5.0 seconds = 2039.678 FPS
10163 frames in 5.0 seconds = 2032.574 FPS
10125 frames in 5.0 seconds = 2024.915 FPS

Works OK for me with the NVIDIA PC - moving the frames and overlaying them does not affect the "gears".

But I didn't use the "$" symbol FWIW

---

### Post by MattPhillips on 2009-03-02
Thanks emarkay,

Hmmm, neither of my graphics cards are NVidia so I wonder if that has something to do with it.  Wouldn't expect a problem with an ATI Radeon X1900 but at this point I don't know what to think.

Could you please post your xorg.conf file?  And I assume you have direct rendering enabled, i.e.

$ glxinfo | grep direct

returns "yes"?  (btw '$' just means command line prompt, for easier reading)

Could you also post the output of 

$ X -version

I'm wondering whether my somewhat older version of xorg and xserver is part of the problem.

Anyway, great to hear that not everyone has this problem, thank you!

Best,
Matt

---

### Post by Matsukaze on 2009-03-02
Glxgears works fine on my desktop with an Nvidia card, but I have the same problem you described on my Inspiron 1525 laptop running Ubuntu 8.10. However, the laptop also works fine if I change the Visual Effects setting (System-Preferences-Appearance-Visual Settings tab) to None.

There is a lengthy [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094") about various problems with Intel graphics.

---

### Post by MattPhillips on 2009-03-02
Thanks a lot Matsukaze, that bug report described exactly my problem, and removing desktop effects as you suggested made my glxgears problem go away.  What I don't understand though is why I would have the same problems with an ATI card--does ATI come closer to intel architecture, or something like that?

Unfortunately, I was just using glxgears as a simple barometer of other, disastrous opengl problems I am having while trying to do some software development, which remain unsolved.  Also as in the bug report rendering remains slower in Ubuntu than on the native OS.  But thank you for a very helpful post.  

Best,
Matt

---

### Post by fragos on 2009-03-03
glxgears fps results vary if you change it's window size of run other aps simultaniously. It's not a scientific measurement and to any meaning at all it should be the only ap running with the terminal window open to report the fps.

Note: glxgears works on my desktop which has an Nividia card and my laptop which has the Intel video chipset.

---

### Post by kelvin spratt on 2009-03-03
The truth is not many ATI cards work in linux, Nvidia has always given good support 
this is my Nvidia with compiz effects tuned on all bells a whistles
19247 frames in 5.0 seconds = 3849.235 FPS
19306 frames in 5.0 seconds = 3861.199 FPS
19312 frames in 5.0 seconds = 3862.309 FPS
19334 frames in 5.0 seconds = 3866.761 FPS
19371 frames in 5.0 seconds = 3874.102 FPS
19295 frames in 5.0 seconds = 3858.865 FPS
18556 frames in 5.0 seconds = 3711.187 FPS
18303 frames in 5.0 seconds = 3660.550 FPS
19103 frames in 5.0 seconds = 3820.585 FPS
19273 frames in 5.0 seconds = 3854.427 FPS

and this without compiz
24719 frames in 5.0 seconds = 4943.708 FPS
24026 frames in 5.0 seconds = 4805.071 FPS
24216 frames in 5.0 seconds = 4843.112 FPS
24220 frames in 5.0 seconds = 4843.808 FPS
24115 frames in 5.0 seconds = 4822.856 FPS
24038 frames in 5.0 seconds = 4807.578 FPS
24116 frames in 5.0 seconds = 4823.161 FPS

---

### Post by MattPhillips on 2009-03-03
fragos and kelvin,

Thanks to both of your for your responses.  Actually I'm not using fps as a measure for anything (though fwiw I'm getting ~10800fps consistently with or without desktop 'special effects', with default window size).  I was probably unclear when I said 'post what happens', I didn't mean standard output, I meant whether or not this bad repainting I've described occurs.  I presume not, for either of you--in which case could I get the xorg.conf and X -version?  Maybe there's something in there that could help things.

> 
The truth is not many ATI cards work in linux

Really??  Has that been written up anywhere?  OUCH!  So then I'll have to go back to the MacOS, so sad...

Best,
Matt

---

### Post by MattPhillips on 2009-03-03
kelvin,

On second thought, the Mac OS is Unix-based--and several ATI cards (though not my particular one I don't think) are options on the Mac Pro website.  I don't suppose you know what the relevant Mac/Linux difference would be, which accounts for ATI cars being good under one OS but not the other?

Best,
Matt

---

