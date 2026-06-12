---
title: "Multiple GUI clients on a single host"
date: 2009-04-18
forum: Desktop Environments
---

### Post by freakalad on 2009-04-18
I've bought a fairly serious machine to do some VM/dev work, so I'm not lacking for hardware resources. Along with the machine, I bought a 3D card with multiple outputs: VGA, DVI & HDMI (all of witch work great).

I'm considering setting the machine up in a "hydra"/multi-headed configuration: mapping a TTY (<ctrl><alt><F1>-<F3>) to a video-out+keyboard+mouse configuration, and running a X on each, so that a single machine/host's resources could be shared by multiple clients.

This would be extremely useful & cost-effective in environments such as an office, net-cafe or even a home. Instead of buying & configuring additional systems, just add another video, monitor, USB keyboard & mouse.
This would save on resources such as power, storage, and somewhat simplify networking & security overhead.

Since Linux/Unix/Posix stems from the old mainframe days, the OS should already be capable of catering to this concurrent multi-user environment, and USB allows you to add as many controlling peripherals as you wish.

So there should be nothing (or very little) lacking in terms of hardware or OS/kernel in order to get this going.

Has anyone attempted anything like this? (like a DIY mainframe)

---

### Post by savagenator on 2009-04-18
The multiple usb keyboards and mouses problem(mice?) How do you assign a usb keyboard for each X session? 

possible solution: xorg.conf? But i don't think it has that feature

Also you can try out multiple pointers (don't remember what it is named.)

My 2 cents

---

### Post by freakalad on 2009-04-18
Hey, savagenator,

Thanks for the suggestion.

I haven't figures any of this out yet.

All I'm able to do at present is get all the video-outputs to work on a single GUI, and I'm able to make use of any of the USB keyboards & mice attached to my system.

Binding & pairing them up is a mystery.

Also, trying to get multiple GUI's/X's functioning via separate TTY's is beyond my skills at present, though I do recall being able to initiate a remote-X session from the Ubuntu login dialogue (though you have to make use of a separate username, if I recall).

Like I mentioned before, the hardware is capable (on paper at least), and the OS has been truly multi-user since day-1, so AFAIKS, there should be very little that would not permit such functionality. 
As you've mentioned, it may be as simple as a very creative X config file.

I see that there have been a [few]("http://ubuntuforums.org/showthread.php?t=992843&highlight=multi-head+multi-user") [prior]("http://ubuntuforums.org/showthread.php?t=937271&highlight=multi-head+multi-user") [posts]("http://ubuntuforums.org/showthread.php?t=425396&highlight=multi-head+multi-user") dealing with the matter, but little seems to have come of it.

Once I get this stage going, I'm [hoping to take it a step further]("http://ubuntuforums.org/showthread.php?t=1112467"), and bind the TTY's/heads to VM's via a remote-X session

---

### Post by savagenator on 2009-04-18
multiple GUI's/X's functioning via separate TTY's:

> startx -- :1

that command will start a new X session in a different tty

and i actually found a guide for you:

[http://linuxgazette.net/124/smith.html](http://linuxgazette.net/124/smith.html)

> Problems:  Did you catch the phrase "between resets" above? While the system worked very well, it was extremely unstable. In particular, we got a kernel oops fairly often when we logged out. A syslog trace of one such oops is available here. 

The guide is pretty advanced, but good luck!

---

### Post by freakalad on 2009-04-18
UPDATE: located the following articles, demonstrating possible solutions: 

[http://vignatti.wordpress.com/2008/09/23/multiseat-roadmap/](http://vignatti.wordpress.com/2008/09/23/multiseat-roadmap/)
[http://wiki.c3sl.ufpr.br/multiseat/index.php/Main_Page](http://wiki.c3sl.ufpr.br/multiseat/index.php/Main_Page)
[http://cgit.freedesktop.org/xorg/app/mdm/](http://cgit.freedesktop.org/xorg/app/mdm/)
[http://wiki.x.org/wiki/Development/Documentation/Multiseat](http://wiki.x.org/wiki/Development/Documentation/Multiseat)
[https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)
[http://wiki.debian.org/Multi_Seat_Debian_HOWTO](http://wiki.debian.org/Multi_Seat_Debian_HOWTO)
[http://www.linuxtoys.org/multiubuntu/multiubuntu.html](http://www.linuxtoys.org/multiubuntu/multiubuntu.html)
[http://linuxgazette.net/124/smith.html](http://linuxgazette.net/124/smith.html)


UPDATE/possible SOLUTION:

The following 2 guides seem to offer a pretty straight-forward solutions:
[http://wpkg.org/Configuring_multiseat_X_workstation](http://wpkg.org/Configuring_multiseat_X_workstation)
[https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)
[http://www.linuxtoys.org/multiubuntu/multiubuntu.html](http://www.linuxtoys.org/multiubuntu/multiubuntu.html)

---

### Post by freakalad on 2009-04-19
Thanks for the info.

I'll have to create a how-to guide once I'm done...

---

