---
title: "Dell Latitude D620"
date: 2007-07-28
forum: Dell  Ubuntu Support
---

### Post by rebelxhardcore on 2007-07-28
Alright here is my story, I got windows on this dell latitude d620. I ran the live CD of ubuntu feisty and when it starts up it has a long pause. I slid in another SATA drive that was meant for this dell, and I get the same thing where it has that long pause.

Some people have witnessed this on their dell latitudes that are the same models also...

why is it doing this?

-john

also where can i get MP3 support? :)

---

### Post by lazyjedipenguin on 2007-07-30
I had this problem on my D620, this fixed it:

[http://ubuntuforums.org/showthread.php?t=93137](http://ubuntuforums.org/showthread.php?t=93137)

Ben

---

### Post by dmflad on 2007-07-30
I have D620. Went from Ubuntu 6 to Ubuntu 7 okay via upgrade and has been fine for few months. Something caused LT to fail yesterday and I did new install using 7.04 CD. Things seemed okay but now I find my term window not working correctly: keyboard not right, "insert" key not working in vi nor are arrow keys. Seeing same regardless of term window. Also system beep extremely loud.   Didn't have these problems before w previous Unbuntu install on same LT.

Any ideas which pkg I am missing? Hate to have to install 6x Ubuntu then upgrade from there, especially since I gave CD away to someone who wanted to try U on old PC.

---

### Post by wty on 2007-07-31
I installed 7.04 on my Dell Latitude D620, without any problems at all. All worked out well. But on my new Dell Latitude D630 were there more of a job installing it. After some tryes I finally got it to work, I used the alternate release, Maybe you should try it :)

wty

---

### Post by lithium06 on 2007-08-02
on the 620 does suspend work? when you resume does the usb and network interfaces (wired and wireless) work? i've been reading on the 630 forum and thinkpad T61 forums that when they resume they have no usb or networking. thanks

---

### Post by dmflad on 2007-08-04
Alternate release?  I remember reading in forums for v6 to "use alternate release". Then what good is getting CD/DVD from places like frozenTech? And why is there even an alternate?  Is there some way to get "alternate" via apt-get or synaptic?

---

### Post by kansei on 2007-09-06
> **lithium06 said:**
> on the 620 does suspend work? when you resume does the usb and network interfaces (wired and wireless) work? i've been reading on the 630 forum and thinkpad T61 forums that when they resume they have no usb or networking. thanks

The 620 and 630 barely even share casing, nevermind internal components. The screen, keyboard, and touchpad/fingerprint reader are the only physical parts of the computer that'll swap :P

The 630 is on the new-ish Intel chipset that the T61 is on (note: T60 has no issues, much like the 620).

Everything on my 620 works gloriously, aside from suspend (but I'm on Ubuntu Gutsy x64) --including bluetooth, smart card, fingerprint reader (using it for system sign in, including console), hardware 3d acceleration (nvidia), basic power management (dynamic core speed), automatic screen brightness (this is hardware though, totally independent of OS), volume control (not a hardware mixer like on thinkpads), docking/undocking, multiple monitors, wifi (with WPA2 ... intel 3945 card, not the dell one).. need I go on?

I gotta say, the D620 is a *great* laptop for linux, at least in the configuration mine is.

I have no clue if the other wireless cards, graphics cards, and WWAN options work well at all with Ubuntu.

---

### Post by Afishionado on 2007-09-06
dmflad: The "alternate" CD has a text-based installer instead of a graphical one. It needs less memory, and has been around longer, so it is slightly less buggy.

Basically, it isn't as easy to use, but works more reliably over different kinds of hardware.

---

