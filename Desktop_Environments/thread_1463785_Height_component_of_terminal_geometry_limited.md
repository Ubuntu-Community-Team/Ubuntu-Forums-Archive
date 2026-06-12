---
title: "Height component of terminal geometry limited"
date: 2010-04-27
forum: Desktop Environments
---

### Post by gumbeto on 2010-04-27
Hi,

I like to have my terminal opened with a specific geometry already, but I am not being able to do this in the release candidate for ubuntu 10.04, which I just installed.

Using the command 
```
gnome-terminal --geometry=80x38-80
```
everything works fine, but increasing the height over this value (or doing so plus changing the Y displacement) has no effect.

For instance, the following commands have the same effect as the previous command:
```
gnome-terminal --geometry=80x39-80
gnome-terminal --geometry=80x200-80+500
```

Still, if I do
```
gnome-terminal --geometry=80x38-80+100
```
the result is the expected again, because the didn't exceed the 38 character limit for the height

It seems like something is limiting the height of the window. This used to work fine on my previous versions of ubuntu. Anyone has a clue what is going or and how to fix it?

---

### Post by PhilLord on 2010-04-27
I think that I am getting the same thing. The behaviour has definately changed from 9.10. Reading the command line documentation is says "sets the geometry, if this comes before the --window, sets the default". The practical upshot of this is that my script which opens three terminals, setting their profiles and locations runs fine but the X+Y locations are totally ignored. 

Confusing eh?

Phil

---

