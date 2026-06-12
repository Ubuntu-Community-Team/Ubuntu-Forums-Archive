---
title: "Ubuntu 606 myspace im problem"
date: 2006-07-19
forum: Desktop Environments
---

### Post by joker535 on 2006-07-19
I am new to ubuntu (getting tired of xp problems), new to linux/unix, and trying to find a decent alternative to XP. I really like ubuntu but so far I have found a problem that I haven't been able to figure out on my own. Hopefully someone here has had the same problem and can help me. 

I installed ubuntu 606 desktop from the live CD and it works great. I built the machine it is on out of old parts I had laying around so my girl will have a pc to use while I am at work. She is addicted to myspace and loves to im her friends there. Since switching to ubuntu I have found what I believe are flash problems with the site. When using the IM client in myspace, the person you are messaging sees all the text you type and thier side is fine but on your side of the IM window no text is displayed either in the box where you type or where the text the other person is sending you is supposed to appear. I have flash 7 installed successfully and it plays videos and such so I think it's ok. I also notice on myspace sites that have music, the player box is blank and it appears to not be working. I don't have any speakers yet to know if there is audio or not. This may be related but i'm not sure. Is this a flash problem or is it something like java?

Any help is appreciated. If I get this working, we are going to stick with ubuntu and leave windows in the dust forever.

Thanks

Bob

---

### Post by monergist on 2006-07-19
Hey Bob,

Well you have two options. The first is simply this: break her addiction to myspace! Well alright, since I have a myspace I guess I can't try and get you to do that in good conscious, so the second thing you can do is:

Make sure you have the universe and multiverse repositories, and type in your terminal:
```

sudo apt-get install flashplugin-nonfree
sudo update-flashplugin

```

That should work for you. Notice of course that flash support for Linux stopped at 7 I believe. Anything above that still will not work. 

For more info check out: [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by mrbaz on 2006-07-19
Download Automatix and use it to install all the necessary firefox plugins if you haven't already done so.

---

### Post by avtolle on 2006-07-19
IIRC, Myspace upgraded the version of Flash it is using to 8.

---

### Post by joker535 on 2006-07-19
Ok I will do these things when I get home tonight. Thanks for the help hope this works.

I personally don't care for the myspace. Everytime she wants to do something, she goes and finds code on the net, installs it and it doesn't work like it's supposed to. I end up spending an hour pasting the code into dreamweaver and finding a typo that shouldn't have been there. It's a waste of time to me but she enjoys it and other than mp3's and e-mail, it's the only thing she does on the computer. I really built the other PC for her to enjoy. Hopefully I can get it all ironed out so she can have fun.

Thanks

Bob

---

### Post by -Phi- on 2006-07-19
Myspace now uses Flash 9 so it won't work even with the linux Flash plugin. There's a thread about it here [http://ubuntuforums.org/showthread.php?t=218008&highlight=myspace](http://ubuntuforums.org/showthread.php?t=218008&highlight=myspace)

They switched to stem a flash worm. Article: [http://blog.washingtonpost.com/securityfix/2006/07/myspace_pages_defaced_using_fl.html](http://blog.washingtonpost.com/securityfix/2006/07/myspace_pages_defaced_using_fl.html)

A workaround is to download and run the Windows versions of Firefox and Flash 9 with Wine. Good luck!

- Phi

---

