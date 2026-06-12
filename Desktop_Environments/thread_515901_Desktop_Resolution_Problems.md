---
title: "Desktop Resolution Problems"
date: 2007-08-02
forum: Desktop Environments
---

### Post by broddr on 2007-08-02
Hello,

I will start by saying that I am completely new to the whole Linux world having been a windows user for many years.

As such I know very little about Linux and Ubuntu (so far)

Here's my problem.

I am trying to install Xubuntu on a low spec laptop and I cannot get the screen resolution to a respectable level.

I am using an IBM thinkpad 600 with a neomagic neograph graphics chip.

I have successfully installed Xubuntu on the machine but the maximum resolution I can get is 800x600 and it looks terrible.

There must be a way to get the resolution to its native size of 1024x768

I have previously installed Windows 98 and 2000 on this machine and the resolution is great, 1024x768. Only in 16 bit colour but that is fine by me.

In 800x600 the text is brokenup and the whole thing looks horrible.

I have also installed puppy linux on this machine and again it works in 1024x768 and looks great.

I want to start using a flavour of linux but I don't want to use it on my main pc until I know a bit more about it and know what I am doing but it seems impossible to get it to work properly without knowing the tricks.

I suppose you guys always hear this form new users who are used to windows all the time.

I have also installed Ubuntu on the machine and get the same result.

Help anyone please?

---

### Post by benerivo on 2007-08-02
You could try editing your /etc/X11/xorg.conf file. To do this, type

sudo gedit /etc/X11/xorg.conf

in a terminal. Then scroll to the bottom where there will be a section listing various resolutions under the title 'Section "Screen"'. Here you can add "1024x768" to each line so that it the system tries to go with that resolution first, and if it fails it will try the second option, which will now be the "800x600".

---

### Post by broddr on 2007-08-02
Thanks for that.

I was messing around for ages with no success until I realised I had to install gedit from the package manager first!

Anyway, it already says 1024x768 in the screen section. Still makes no difference.

My own opinion is it is something to do with the graphics driver.

The bit I can't figure out is why puppy linux and windows work okay but xubuntu doesn't.
Is there any way I can install the driver puppy linux uses into xubuntu?

Then again, looking at the xorg.conf file it states the right piece of hardware under graphics device but has the LCD screen listed as generic monitor.
Could that be the problem?

Can I just change the conf file to LCD screen?

---

### Post by Jhongy on 2007-08-03
What does it have listed under "Graphics device", and, which driver does it show?

(ignore the monitor section for now).

---

### Post by broddr on 2007-08-03
I have sorted it!

Did a bit of investigation and found this in a forum

"Ctrl-Alt-F1
Killall gdm
sudo dpkg-reconfigure xserver-xorg
This gets a bunch of screens where you can choose driver, video memory, keyboard, ... In my case, Ubuntu didn't realize the video memory was 65536KB. I'm not sure what you have. This is the big limiter on resolution."

I mucked about with the graphics and monitor settings and rebooted. Hey presto, lovely clear 1024x768 screen.

I think the problem was that xubuntu was trying to give me the best available resolution with 24bit colour.

When I changed the colour depth to 16bit it gave me 1024x768 no problem.

I am happy with that. I have never got this laptop to run over 800x600 in 24bit colour with any OS.

I would rather have 16bit and nice smooth graphics than the lower res.

Thanks for all your help though guys.

I am beginning to believe.

Sick of Bill Gates taking my money and supplying crap.
Looking forward to going all linux very soon.

Just need to figure out how to run windows apps on linux but I have read that it is possible and pretty simple if you have a decent spec PC.

bRODDR

---

### Post by Jhongy on 2007-08-03
Glad you got it sorted.


WINE can be a bit of an exercise in frustration, IME, as you can get "odd crashes". If the PC is powerful enough (enough memory), look into VirtualBox and set up a Virtual Machine to wean yourself off windows :-)

---

