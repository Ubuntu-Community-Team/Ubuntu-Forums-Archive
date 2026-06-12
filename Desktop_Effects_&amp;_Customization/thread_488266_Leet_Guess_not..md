---
title: "Leet? Guess not."
date: 2007-06-30
forum: Desktop Effects &amp; Customization
---

### Post by mitchell486 on 2007-06-30
Ok. I am totally for Ubuntu. Don't get me wrong. Greatest thing since sliced bread that I've seen so far. But I am having troubles. I have the drivers and such for my video card installed. And I have pretty decent system specs I'd say.

AMD Athlon(tm) 64 Processor 3500+
2.00 Gigs of RAM, PC3200
160 GB SATA Hard Drive
ASUS A8N-SLI Mobo, Socket 939
ATI 512 MB Radeon 1600x


No reason really as to why Ubuntu shouldn't run TIP top shape on my computer. I can't get Beryl to work, I looked into Compiz but couldn't get the site working that day. At least if you guys could help with Beryl that would be super. Or not. Anything to help my system run primo really I guess. I had Vista before this, and I know I know, I don't want to compare but, It handled my Video card and such well. I want that with Ubuntu. I have Feisty BTW. So. If anyone can help me with:

A-Find out all the info on my video drivers and make sure they are up to date. (A command to check them or anything)
B-Mobo or any other devices listed that might be affecting this problem. (Same as A in that respect)
C-Anything to help speed up some websites whilst loading (eg. I go to [www.digg.com](www.digg.com) and it slows down the rest of Firefox)

I know enough about computers to tell me that this system is like *blow your socks off into next months' last week* but, its not any little child's toy. There should be no reason that this system won't do what I want. So. If anyone knows anything or has anything that could help I would greatly appreciate it. Thank you all very much for your help in advance. :)

---

### Post by Scheater5 on 2007-06-30
Well, one issue could be your video driver.  Ubuntu probably came with an open source driver.  And while there are philosophical advantages to staying with that, if you want to use beryl etc the truth is that the closed source drivers still get more milage.  

```
sudo aptitude install restricted-manager
```
and after install 
```
restricted-manager
```

and that will bring up a GUI to install the closed source driver if there is one for your graphics card

And after that try checking out the [unofficial wiki]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") for the instructions on installing beryl.  And while you're at it, check out Compiz Fusion.  Beryl was a fork of Compiz, and they have since remerged to create Compiz Fusion.  I would assume all the "newest and coolest" would be on Fusion.

---

### Post by mitchell486 on 2007-06-30
Hey thank you very much. Is there any way to see what I am using for my video card tho? Cuz I want to see if everythings working before I take the time to install Beryl or Fusion and it not work. :( :S Anyone know?

---

### Post by mitchell486 on 2007-06-30
Ok. I am SO close. I got it all installed and working almost! I now have to find someway to not use my fglrx driver. I read in another thread that to get it to NOT be all fuzzy and crap whilst I start it using a XGL session, I need to disable my fglrx driver. If that is correct, how do I do that?

---

### Post by Mr Greencastle on 2007-06-30
For Beryl, follow every step on this page:
[http://ubuntuforums.org/showthread.php?t=399643](http://ubuntuforums.org/showthread.php?t=399643)

Hope that helps!

Mr Green

---

### Post by mitchell486 on 2007-06-30
It does not help actually. I still have the jumbled screen. I can try taking a screenshot I guess to explain what i mean but.. It's annoying and its SO close to working. Just not yet. I know this card has troubles but I have beryl installed. I have XGL installed. I then reboot. Log in to the session Gnome with XGL. It says do you want to make this default. No. I type in name and pass. Then the screen is ALL grey-ish with an X in the middle where my mouse is. Then it logs in the rest of the way with my background and stuff being vaguely what it used to me. It's all skewed and full of lines that don't work. I can't click anything. And so. I reboot and go back to using just Gnome and everything is fine but no beryl. Any suggestions? Help? I'm close but just not quite there.

---

### Post by dwebb86 on 2007-06-30
Hey, you said you're using FIrefox? This doesn't really belong in this forum, but I have a little hack to speed your browser up (what you asked for in number 3).

Open a new tab and type **about:config** in the URL entry line, hit enter.
Right click somewhere in the window and go to **New > Integer**
Type **nglayout.initialpaint.delay** for the first box, and 0 for the second.

This tells your browser to wait 0 milliseconds before painting the page in your browser window.
Instead of waiting until all the information is downloaded and displaying it, it displays it as it downloads. Have fun.

---

### Post by mitchell486 on 2007-06-30
Thank you! <3 That helped quite a bit. :D Still nothing on the XGL thing. I'm trying different things and none are working so much so far. :(

---

### Post by pardesi on 2007-06-30
u may also want to disable ipv6

---

### Post by mitchell486 on 2007-07-02
How do I disable that? And sorry but this isnt working on my computer. It's making me mad.

---

### Post by pardesi on 2007-07-02
go to firefox and type
```
about:config
``` in the place u type addresses.

then u will be lead to a screen.then go to
```
network.dns.disable.IPv6
``` double click on it to change the value to true

---

### Post by mitchell486 on 2007-07-02
That's fine and dandy and all but how does that affect what my XGL driver does? I don't understand? Its the XGL driver that is messing up when I log into that session. SO. Thank you but. I need help with that right now. OOOOOOOH! I see. Your thing is for firefox. Got it. Sorry. Just getting frustrated about the drivers issues. :(

---

