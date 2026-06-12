---
title: "Ubuntu wont shut the computer down (FS LB E8020)"
date: 2009-01-15
forum: General Help
---

### Post by KristofferAndreas on 2009-01-15
Hi

I have some problems with my Fujitsu Siemens Lifebook E8020...

when i shut it down, ubuntu, and the screen shuts down, but not harddrive and other parts... 

This is kinda a problem since it wont suspend or hibernate either...

This is my school computer so i really need the battery and im forgetting to hold the power button every time...

Ive read about the same problem with some of the netbooks, and i added rmmod snd-hda-intel
into the halt file... but it didnt help
The hardware is very alike the netbooks....
Intel pentium m 2ghz
iw2200bg wireless
915 graphics

Can someone help me with the shutdown problem, and if some one can help me with suspend and hibernate, that would be nice to :)

thanks for all help

Kristoffer

---

### Post by redilyn on 2009-01-15
Just curious, What happens if you try to shutdown from a console?

Press alt+F2, login, then type the following

```

sudo shutdown -P 0

```

If it hangs on a message please post the message here.

---

### Post by KristofferAndreas on 2009-01-15
Well it dosent hang... ubuntu shuts down normaly... 
ANd it didnt display a error...
but when the shutdown prosess is finished, the computer light is still on, and the hardrive is spinning... so if i forget to turn off manually it wont have any power left...

i will be greatefull for help

---

### Post by redilyn on 2009-01-15
Can you try logging out and then shutting down from the GDM login screen and see if you still have the problem.

This was a temp solution in gutsy I believe.

Which version of ubuntu are you using?

---

### Post by boof1988 on 2009-01-15
> **redilyn said:**
> Just curious, What happens if you try to shutdown from a console?

Press alt+F2, login, then type the following

```

sudo shutdown -P 0

```

If it hangs on a message please post the message here.

Thanks for posting this command... I haven't seen it yet.

> **KristofferAndreas said:**
> Well it dosent hang... ubuntu shuts down normaly... 
ANd it didnt display a error...
but when the shutdown prosess is finished, the computer light is still on, and the hardrive is spinning... so if i forget to turn off manually it wont have any power left...

i will be greatefull for help

If you haven't done it yet... Have a look at the man pages for shutdown etc:

```
man shutdown
man poweroff
```

I just looked at them and there is some interesting info (it's the first time I've looked at them).

If you're not able to get it to shutdown properly using shutdown, you may try:

```
sudo poweroff
```

This is a little more agressive (I think) and is probably not a good way to *routinely* shutdown your machine.

Hope this helps some...

---

### Post by KristofferAndreas on 2009-01-15
I use Ubuntu 8.10 installed thru wubi...

I will try poweroff command after my class..

---

