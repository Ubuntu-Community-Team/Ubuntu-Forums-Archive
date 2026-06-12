---
title: "How to set refresh rate default?"
date: 2009-03-05
forum: General Help
---

### Post by jnewl on 2009-03-05
I have a widescreen LCD monitor that I run at 1680x1050x58Hz. In the screen resolution options, I can choose between 50Hz, 58Hz, or 59Hz but I have to choose 58Hz in order for the display to square up properly with the screen. The problem is, it defaults back to 59Hz every time when returning from a resolution change (after playing a game, for example).

So how can I make it default to 58Hz rather than 59Hz?

---

### Post by jnewl on 2009-03-06
Anyone?

---

### Post by hansdown on 2009-03-06
Hi jnewl.

What is the make and model of your display?

Also, what operating system are you using?

---

### Post by jnewl on 2009-03-08
Thanks for responding!

My monitor is an LG Flatron W2252TQ. My videocard is an nVidia GeForce 8800GT (w/latest driver). I am running Intrepid Ibex 8.10 w/all current updates. (It did the same thing under Hardy Heron.)

I lied a little when I said it always defaults to 59Hz. Sometimes it goes to 50Hz instead, which I guess means it's not "defaulting" to either of these at all. But I don't know what makes it choose either one of those frequencies, nor do I know why it never, ever chooses 58Hz, which is the one frequency I need it to choose!

---

### Post by hansdown on 2009-03-08
Are you using a VGA cable, or DVI-D cable?

---

### Post by jnewl on 2009-03-08
Looks like a regular old VGA cable.

---

### Post by hansdown on 2009-03-09
I hope this thread helps.

[http://ubuntuforums.org/showthread.php?t=779178](http://ubuntuforums.org/showthread.php?t=779178)

---

### Post by jnewl on 2009-03-09
Hehe. The only thing it helped me do is screw things up. I somehow made it so the nVidia driver isn't loading. Here's the error message I get now when I try to run System -> Administration -> NVIDIA X Server Settings:

[INDENT]You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. [/INDENT]

Can you tell me what to do to get things back where they were? I have the 177 or 1.77 or whatever it is driver on my system, but I don't know how to edit the file properly and "restart the X server."

EDIT: Ack! Never mind. I remembered how to reinstall the driver. Everything's peachy again.

Jesus, sometimes I can't see the forest OR the trees.

---

### Post by hansdown on 2009-03-09
Ummm..is it working jnewl?

---

### Post by jnewl on 2009-03-14
For whatever reason, after I reinstalled the driver, the problem cleared up. I'm somewhat shocked that it did, because I've had the problem since I started using Ubuntu nine months ago and I've done a couple of video driver installations in that time. It never made a difference. But anyway, yes, everything's working properly now. Thanks for following up.

---

### Post by hansdown on 2009-03-14
Thanks for answering back jnewl.

I was worried I steered you wrong.

---

