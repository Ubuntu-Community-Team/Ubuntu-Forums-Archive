---
title: "Multiple X Sessions with multiple keyboards mice &amp; Monitors"
date: 2007-07-21
forum: Desktop Effects &amp; Customization
---

### Post by Percius on 2007-07-21
I know its possible to run multipe X display sessions, and linux is inherantly terminal based, but I was wondering if anyone has ever taken it one step farther.

I have a Nvidia video card capable of doing duel monitor display, 2 keyboards (ps2 and usb) and 2 mice (ps2 and usb). What I would like to do is make it so that 1 screen and keyboard mouse combo is assigned 1 xsession and 1 screen assigned the other. 

Has anyone ever done this or have ideas on where to start. I think it would be possible with 2 xorg.conf files where each one has a different input set specified, but I am in  a conundrum on how to get them both to launch simotaneously and how to specify the screens seperately so that the other X session leavse it alone without useing a second video card.

Thanks in advance.

---

### Post by JonathanRRogers on 2008-02-20
I am trying to set up exactly the same thing. I know multiple simultaneous X sessions, each with display, keyboard and mouse is possible, since I read about [someone doing it ]("http://www.linuxplanet.com/linuxplanet/tutorials/3100/1/")several years ago. That HOWTO uses two video cards, but I'm hoping to figure how to do it with just my one PCIe Nvidia card with two ports. I am not that hopeful that I can, however, since two different X server processes would have to simultaneously access the one PCIe device, something which is quite unlikely to work.

One possibility is running a single X process configured with two screens, then running an Xnest connected to each screen. However, I don't know yet if the input devices can be properly associated in that scenario.

---

### Post by JonathanRRogers on 2008-02-20
After searching a bit more, I've discovered that, as I'd hoped, multi-seat X is much easier to configure these days, requiring no patches to either Linux or Xorg. [Chris Tyler's Blog]("http://blog.chris.tylers.info/index.php?/archives/14-Multiseat-X-Under-X11R6.97.0.html") seems to be the best resource currently for multi-card setups.

I'd almost given up on a two-seat configuration using my single dual-output card until I found [this]("http://netpatia.blogspot.com/2008/02/multiseat-computer-with-ubuntu-804.html"). That appears to be exactly what we're looking for, so I'm trying it as soon as possible.

---

### Post by himikeb on 2008-04-10
Just out of curiousity, has anyone tried the "multiseat" package in Ubuntu??  Seems it's been in there for a few releases now, I'll be trying it and posting my results eventually.

---

### Post by theDaveTheRave on 2008-04-20
hi Guys.

Sounds interesting, I use my laptop with an external trackball. Both the scratchpad and the ball work beatifully, but what would be really cool is if I could have 2 separate pointers?

I'm going to have a look JR's links and see if there is a setup for this and get back to you.

Soon I am going to be emigrating, and will buy an external Keyboard, and will obviously need to have both functioning simultaneously, and have 2 sets of dictionaries for the system. Which is going to be my main requirement!

I'll get back to this post later on.

Dave

---

### Post by LCC on 2008-05-01
I was thinking about this possibility, even suggested a GUI for which would make a multi-seat really easy and popular above all,
I suggested that GUI on Ubuntu Brainstorm project, perhaps you guys could vote for it.

        [COLOR="Red"]http://brainstorm.ubuntu.com/idea/7861/[/COLOR]


[http://linuxgazette.net/124/smith.html](http://linuxgazette.net/124/smith.html)

---

### Post by andersja on 2008-05-07
Check out and vote for these: (also read the comments for more info):

[http://brainstorm.ubuntu.com/idea/3442/]("http://brainstorm.ubuntu.com/idea/3442/")
and
[http://brainstorm.ubuntu.com/idea/3153/]("http://brainstorm.ubuntu.com/idea/3153/")

---

### Post by andersja on 2008-05-13
[[IMG]http://brainstorm.ubuntu.com/idea/3442/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/3442/)

---

### Post by altonbr on 2008-05-15
I hope this goes through.

The school board I work for badly needs this and their quite interesting in running Ubuntu!

---

