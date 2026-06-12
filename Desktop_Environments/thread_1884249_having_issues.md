---
title: "having issues"
date: 2011-11-20
forum: Desktop Environments
---

### Post by TheRacerX on 2011-11-20
im running Unity 2D on Maverick Meerkat and for some reason as you can see from the following screenshot the Clock and everything else has vanished, im still learning how to use Unity so if anyone can help me get those things back on the panel that would be appreciated

---

### Post by typhoon_tip on 2011-11-20
Try to run this and see if anything come back:
```
unity --reset
```

---

### Post by TheRacerX on 2011-11-20
would i run it in the terminal?

---

### Post by typhoon_tip on 2011-11-21
> **TheRacerX said:**
> would i run it in the terminal?

Yes, and do not close the terminal once done. Simply logoff and login again.

---

### Post by TheRacerX on 2011-11-21
tried running it in the terminal all i get is a command not found error

and on top of that theres no way for me to log off since the button thats USED to log off and shutdown is ALSO missing

---

### Post by andrea000 on 2011-11-21
I would upgrade to 11.10 it seems stable I've not had any problems out of it and I've been running it since it first came out.

I know 10.10 is stable but is there some reason you're not upgrading?

---

### Post by TheRacerX on 2011-11-21
my system cant run anything above 10.10 dont have enough power, ive tried 11.04 in the past and it nearly destroyed my computer

---

### Post by jimmydean886-2 on 2011-11-21
Another thing you could try is:
alt+f2
```
 unity --replace 
```I've never used that version of Unity, I only just heard of it in 11.04, so this may or may not work.

If ubuntu is running slow, try switching to lubuntu. Unity 2d can run on top of it, and it is quite probably the most viable light DE ever, for something that's just THAT lightweight. It's also almost instant for everything on the oldest of ubuntu 10.10 compatible machines.

Lubuntu also includes indicators in its own panel, which you can just set to autohide. The only problem I've had with it is that the default clock is stuck in 24-hr time.

---

### Post by grahammechanical on 2011-11-21
Something like this happened to me when I was using 11.04. I found that although the icons had disappeared the hot spots for clicking were still there.


The thing that messed up my desktop like that was trying to use Compiz Configuration Settings Manager to get a desktop effect working. If that is what you are trying to do then I would not recommend doing that with Unity on top of Gnome 2 which is what you have.

A reboot into a standard Maverick desktop might let reset you any changes you were trying to make.

I am now on 11.10 and I have wobbly windows effect set but others have found that there are still some Compiz desktop effects that mess things up.

Regards.

---

### Post by TheRacerX on 2011-11-22
> **typhoon_tip said:**
> Try to run this and see if anything come back:
```
unity --reset
```
i got the unity reset thing to work but how do i make things STAY that way the minute i close the terminal everything goes back to the way it was before im getting fed up and ready to just go back to Windows if this problem doesnt stop

---

