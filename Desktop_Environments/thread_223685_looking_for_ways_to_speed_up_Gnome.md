---
title: "looking for ways to speed up Gnome"
date: 2006-07-26
forum: Desktop Environments
---

### Post by bonefry on 2006-07-26
Hi people,

Although my system is pretty decent, the Gnome's drawing speed is very poor.

This redraw slowness is visible with every application that has enough widgets, or menu options.

I don't know if this is an issue with GDK/GTK+, or with Ubuntu, or with my system. I tried installing nvidia-glx, and although it installed ok, I couldn't see any speed improvments.

What can I do to speed things up ?
Isn't Gnome (XServer ?) using hardware acceleration ?


System:
AMD 3000+
Nvidia GForce 5500
1 GB DDRAM
Ubuntu Dapper


Thank you,

---

### Post by aysiu on 2006-07-26
Can you define "slow" in terms of seconds?
Can you give your computer's specifications, too?

---

### Post by bonefry on 2006-07-26
No, I can't define slow in terms of seconds, because it ussualy lasts less than a second (yes, it can take longer if I take a window and drag it on top of another really fast).

But I can define it in terms of ... I can notice how the windows/widgets are redrawn and it really, really bothers me.

I don't have such problems with KDE (except for Konqueror's KHTML, which is known to have slow rendering speed).

---

### Post by bonefry on 2006-07-26
nobody ?

After installing nvidia-glx, is there no way to activate some kind of hardware acceleration ?

---

### Post by Uncle Spellbinder on 2006-07-26
Please forgive me if this sounds rude, I sincerely do not mean this in a rude way. But how can *"it usually lasts less than a second"* be considered *slow*. Again, just curious. No rudeness intended.

---

### Post by Leigh on 2006-07-26
@Uncle Spellbinder: Usually when you can see the window redraw, that is considered slow, even if it is less than a second. It's more normal for the window to just "appear" instantly.

TO the original poster: Do you have the correct video driver for your graphics board?

---

### Post by John.Michael.Kane on 2006-07-26
To the OP you may need to install the drivers have a read here [**[COLOR="Red"]HOWTO: Latest Nvidia Drivers[/COLOR]**]("http://www.ubuntuforums.org/showthread.php?t=139264")

---

### Post by llamakc on 2006-07-26
Is hdparm enabled?

---

### Post by Uncle Spellbinder on 2006-07-26
> **Leigh said:**
> @Uncle Spellbinder: Usually when you can see the window redraw, that is considered slow, even if it is less than a second. It's more normal for the window to just "appear" instantly.

Thanks for the clarification. No offense intended. :cool:

---

### Post by -deadcats on 2006-07-26
> **bonefry said:**
> nobody ?

After installing nvidia-glx, is there no way to activate some kind of hardware acceleration ?

It's not enough to just install nvidia-glx. You must change your xorg.conf like thus:

Code: sudo gedit /etc/X11/xorg.conf

Then disable dri in the Modules section by placing a "#" in front of the line.

Then enable the nvidia driver, by changing "nv" to "nvidia" under Section "Device"

Save the file, reboot, and you should see the Nvidia logo at boot.

regards,
-dc

---

### Post by ardchoille on 2006-07-26
I noticed a speed increase after I switched the Metacity window manager with openbox in gnome. I wrote a tutorial about it: 

[https://help.ubuntu.com/community/ReplaceMetacityWithOpenbox](https://help.ubuntu.com/community/ReplaceMetacityWithOpenbox)

---

