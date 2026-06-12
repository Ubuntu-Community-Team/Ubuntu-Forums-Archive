---
title: "which desktop environment for remote administartion?"
date: 2009-12-17
forum: Desktop Environments
---

### Post by midaskensai on 2009-12-17
Hello all,

Which desktop environment (kde or gnome) is the best to be used for remote administration via lan from a windows host?

And which remote administration app would be the most hassle free to configure?

I have used vnc in the past, but with rather meager success , Ii also tried freenx but could not get that to work on the windows side.

---

### Post by blackened on 2009-12-17
This a very subjective question. Personally I would use putty and ssh for commandline-only access. If you absolutely must have GUI control over the network then tightvnc would be my choice.

---

### Post by gdonwallace on 2009-12-17
I have not tried anything else, but Ubuntu comes with a desktop viewer installed by default.  It works for what I need, but I don't do more than check machines and make sure they are logged in and running.  If you need more then tightvnc is a good option.

But I also agree with the recommendation of ssh or putty.  If all you need is command line access, then both these programs are good for that.

---

### Post by midaskensai on 2009-12-17
i already use putty & ssh very successfully, but sometimes a full graphical client is required.
does the desktop viewer allow connection from a windows host? because, afaiu it does not.

---

### Post by gdonwallace on 2009-12-21
I connect from my Ubuntu box to Windows without any problems.  I have used it for everything from NT to XP and never had any problems with it.

---

### Post by lukeiamyourfather on 2009-12-21
> **midaskensai said:**
> Which desktop environment (kde or gnome) is the best to be used for remote administration via lan from a windows host?

Neither. If the system has no end user then there's no need for a desktop like GNOME or KDE. There are many reasons why a desktop is bad on a server but here's a few: hogs resources, opens more doors for security flaws, is slower for remote connections, many servers won't have a graphics chipset to even setup a desktop, the list goes on.

Traditionally ssh is used to administer remote systems that don't have an end user (e.g. file servers, web servers, etc.). PuTTY is the de facto ssh client for Windows. Can I ask why the system needs a desktop? If its because you're unfamiliar with the terminal then now is a great time to learn. Cheers!

---

### Post by midaskensai on 2009-12-29
> **lukeiamyourfather said:**
> Neither. If the system has no end user then there's no need for a desktop like GNOME or KDE. There are many reasons why a desktop is bad on a server but here's a few: hogs resources, opens more doors for security flaws, is slower for remote connections, many servers won't have a graphics chipset to even setup a desktop, the list goes on.

Traditionally ssh is used to administer remote systems that don't have an end user (e.g. file servers, web servers, etc.). PuTTY is the de facto ssh client for Windows. Can I ask why the system needs a desktop?
Convenience. It is my old reactivated desktop box with a (currently) 100Mbit connection to the client. It has a graphics card. As stated I have used VNC  in the past, but after the last distribution upgrade the default settings yield faulty colors using KDE, the distributions before had problems with the keyboard input using GNOME. I have not followed the development of either of these, hence the question to ppl with more experience.
Regarding the resource part: the vnc startup script I use, starts GDM/KDM before vncserver.
> **lukeiamyourfather said:**
> If its because you're unfamiliar with the terminal then now is a great time to learn. Cheers!
I am fairly familiar with the terminal, but for me, **currently **is nonetheless not a good time AT ALL to learn.

---

