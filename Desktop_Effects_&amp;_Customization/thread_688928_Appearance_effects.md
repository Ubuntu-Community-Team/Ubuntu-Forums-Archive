---
title: "Appearance effects"
date: 2008-02-05
forum: Desktop Effects &amp; Customization
---

### Post by HanaD on 2008-02-05
Hola Amigos!

I am using Ubuntu7.1 on my X61 tablet.
Though i have been able to tweak almost everything else with help of forums,but i am encountering this strange trouble - when i try to enable normal or Extra in visual effects at Appearance Preferences, i get the message that desktop effects could not be enabled.

can anyone suggest what th eproblem might be and a posible solution to it.

Regards,
Hana

---

### Post by zmjjmz on 2008-02-05
Chances are it's a problem with your Graphics Card.
Do you know what Graphics Card you have?

---

### Post by kool_kat_os on 2008-02-05
do you have an ATI graphics card?

---

### Post by venator260 on 2008-02-05
I just attributed that error to my computer not being fast enough to handle the settings. That's the message my laptop gives me, but being that it's 5-6 years old, I take the lack of Compiz as the only problem to be acceptable.

---

### Post by HanaD on 2008-02-05
i have integrated graphics Intel 3100

---

### Post by zmjjmz on 2008-02-05
Maybe your chip can't handle OpenGL...
Did you try any other applications that require OpenGL, such as GL-117? (It's a flight sim, and I believe it's in the repos...)
Also, did you ever get anything in the way of 3D effects on your previous OS?

---

### Post by sowelie on 2008-02-05
You need to install the proper video driver to get this to work.  I would first take a look at the restricted driver manager (system -> administration -> restricted drivers) and see if there is a video driver listed there.  If so, try enabling it.  Otherwise you need to install the driver manually.

Check out this thread, it may be of some help:

[http://ubuntuforums.org/showthread.php?t=582873&highlight=intel+3100]("http://ubuntuforums.org/showthread.php?t=582873&highlight=intel+3100")

---

### Post by HanaD on 2008-02-05
restricted driver manager says that my hardware does not need any restricted drivers.

also this is the copy of Xorg.conf file:

Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

i think its something with the drivers, but not sure what or how to get it working.

---

### Post by FuturePilot on 2008-02-05
I think your card has been blacklisted
[http://ubuntuforums.org/showthread.php?t=582112]("http://ubuntuforums.org/showthread.php?t=582112")

---

### Post by HanaD on 2008-02-05
that does not sound good,
what exactly does that mean?

---

### Post by smartboyathome on 2008-02-05
It doesn't run Compiz very well, so they made it so you can't use compiz with it unless you take your card off the blacklist.

---

### Post by K.Mandla on 2008-02-06
Moved to Desktop Effects and Customization.

---

### Post by sowelie on 2008-02-06
From what I gathered, there's an issue with the desktop effects that will break video playback.  There is a workaround (described in the post I linked to I believe), but if you watch any video at all it's  obviously not worth sacrificing video playback for eye candy.  At this point, you're always better of with an nvidia adapter unfortunately.

---

