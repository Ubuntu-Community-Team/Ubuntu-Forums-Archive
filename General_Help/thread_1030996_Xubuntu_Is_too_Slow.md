---
title: "Xubuntu Is too Slow"
date: 2009-01-04
forum: General Help
---

### Post by Drewmanfuu on 2009-01-04
After about of year on and off working on this laptop I haven't quite the linux distro. Currently I have Xubuntu installed on an Fujiitsu Lifebook P1120 with 240MB of RAM and a 792 MHz processor. Windows was originally installed on it and it was slow so I decided to try ubuntu but then quickly switched to Xubuntu. However both were very slow almost slower than windows. I've tried other distros of linux but none of them worked right with my wifi becuase of its WPA encryption. Right now I'm looking if someone can help me install Fluxbuntu, which seems like my best choice. It doesn't have a CD-ROM drive but I have an external one that I can't seem to boot from. I'd really appreciate anyones help. Thanks

---

### Post by spcwingo on 2009-01-04
Why not give Puppy a shot.  I think you will be much happier with the speed especially after a HD install.

---

### Post by lykwydchykyn on 2009-01-04
I've tried a lot of distros, and I've found that switching distros doesn't do nearly as much as switching desktop environments.  Instead of wiping out your install, just install icewm or jwm and give that a shot.  You can set up nm-applet to run on startup and still have your wpa capabilities.

24Mb is going to be a stretch for running X windows in any case, but XFCE is not as "light" as people hype it to be (especially in Xubuntu, which brings in a lot of GNOME stuff).  It's lighter than GNOME or KDE, but not a whole lot.

---

### Post by Greyed on 2009-01-04
Let's be realistic...

```

root      5355  3.8  6.3  43784 24220 tty7     Ss+  19:04   2:12 /usr/bin/X 

```

When X itself is taking up 24Mb there's nothing you're going to be able to do to prevent swapping.  24Mb spacious back in the 486 days.  Back then, however, I didn't run X on my Linux boxes because it was too hefty.  What you have would make a great console box or utility box like a router in the corner but without more RAM that is about all it will ever be.

---

### Post by Drewmanfuu on 2009-01-04
Sorry guys, my error 240MB of RAM, kind of a big difference ;). And  I really like puppy its just that I couldn't get WPA to work on it no matter how much I tried but thanks for all the suggestions otherwise, Ill try em out.

---

### Post by abn91c on 2009-01-04
try dreamlinux, go here to download: [http://www.dreamlinux.com.br/download.html](http://www.dreamlinux.com.br/download.html)

---

### Post by Greyed on 2009-01-04
> **Drewmanfuu said:**
> Sorry guys, my error 240MB of RAM, kind of a big difference ;). And  I really like puppy its just that I couldn't get WPA to work on it no matter how much I tried but thanks for all the suggestions otherwise, Ill try em out.

Oh, 240Mb, that's different.  Yeah, Puppy should work.  However so should Xubuntu.  I think it depends on the applications you're running.

This VM only has 386Mb allocated for it and here's my output for free:
```

{grey@igbuntu:~} free -m
             total       used       free     shared    buffers     cached
Mem:           375        366          8          0         10        116
-/+ buffers/cache:        240        135
Swap:          391        135        256

```

That is with KDE 4.2b1(?), TBird and Firefox running.  Sure, 135Mb swapped but 135Mb free.  386 - 135 = 253.  In your box you'd be swapping a bit but this is a beefy install I'm cramming into this VM.  I could pare it down a bit and the first step on that would be to go to XFCE.  So you shouldn't be hurting too bad unless you're trying to run some really large applications.  Basic functionality should be fine, though.

---

### Post by Drewmanfuu on 2009-01-04
I agree, I thought Xubuntu would run smooth but boot up times were slow and it took firefox like 30-40 seconds to boot. So I thought Id give ya an exact boot time and what not so I turned my computer on and Xubuntu brought me to something that says:


BusyBox v1.10.2 (ubuntu 1:1.10.2-lubuntu6) built in shell (ash)
Enter help for a list of commands.

(initramfs) _

What now??

---

### Post by nemilar on 2009-01-05
Might want to take a look at [http://fluxbuntu.org/](http://fluxbuntu.org/)

---

### Post by jrusso2 on 2009-01-05
Everything will be slow with 24 mb of memory thats really low.

Ok I read now its 240, I would give sam linux, anti x and Puppy Linux a try along with Deli Linux.

---

### Post by Kato4059 on 2009-01-05
> **Drewmanfuu said:**
> After about of year on and off working on this laptop I haven't quite the linux distro. Currently I have Xubuntu installed on an Fujiitsu Lifebook P1120 with 240MB of RAM and a 792 MHz processor. Windows was originally installed on it and it was slow so I decided to try ubuntu but then quickly switched to Xubuntu. However both were very slow almost slower than windows. I've tried other distros of linux but none of them worked right with my wifi becuase of its WPA encryption. Right now I'm looking if someone can help me install Fluxbuntu, which seems like my best choice. It doesn't have a CD-ROM drive but I have an external one that I can't seem to boot from. I'd really appreciate anyones help. Thanks

You will be very surprised with Puppy Linux.
Kato4059:P

---

### Post by Drewmanfuu on 2009-01-05
I really did like puppy linux, it worked the best out of all the linux distros I've tried its just I couldn't get WPA encryption to work on it.

---

### Post by redilyn on 2009-01-05
Have you tried installing ubuntu with a minimal install and then adding just the stuff you need?

You would need the alternative install cd I think.

---

### Post by compgeek83 on 2009-01-05
> **redilyn said:**
> Have you tried installing ubuntu with a minimal install and then adding just the stuff you need?

You would need the alternative install cd I think.

that would be my suggestion, I've tried xubuntu but really dont like the xfce interface, call me crazy...

---

### Post by snowpine on 2009-01-06
Puppy WPA worked just fine on my computer. I think it could just be an issue with your particular wireless card or router. Have you tried looking for support over on the Puppy forums? I had to download and install the correct driver to get wireless working on my eee; it took about 5 minutes.

I don't think any Ubuntu/Debian version is going to compete with Puppy in the speed department on very old hardware.

---

