---
title: "my ubuntu went bananas!"
date: 2006-09-30
forum: Desktop Environments
---

### Post by Vlatko on 2006-09-30
yesterday was still normal and i had absolutelly no problems with it. but then i went to try out the games and opened aisleriot solitaire. i'm not sure if this has anything to do with the problem but that's when it started happening.

anyway it's really crazy. i log in, everything works for a few minutes than my mouse disappears and numerous nautilus windows start opening, other programs opening without me able to do anyhing. i start moving my mouse to try and see the pointer and when i do i start to close all the open windows. then if i put the cursor over any icons it opens it without me clicking on it. 

it's really crazy. right now it stopped so i'm writing this in hope someone can tell me where to look or what to do. i hope a re-install is not the solution.

---

### Post by Jussi Kukkonen on 2006-09-30
> 
anyway it's really crazy. i log in, everything works for a few minutes than my mouse disappears and numerous nautilus windows start opening, other programs opening without me able to do anyhing. 
So far it sounds like you opened a saved session (see System/Preferences/Sessions)

> i start moving my mouse to try and see the pointer and when i do i start to close all the open windows. then if i put the cursor over any icons it opens it without me clicking on it.
I can't imagine a hardware or software flaw that would do that...

---

### Post by aysiu on 2006-09-30
Can you try creating a new user and seeing if that test user has the same problem? If the "few minutes" before things go crazy isn't enough time to create a new user through the GUI, you can also do it from the terminal:

Press Control-Alt-F1
Log in
Type ```
sudo adduser testuser
exit
```
Press Control-Alt-F7
Control-Alt-Backspace
Log in as the test user

---

### Post by Vlatko on 2006-10-01
[QUOTE=Jussi Kukkonen ]So far it sounds like you opened a saved session (see System/Preferences/Sessions)[/QUOTE]
no, it wasn't a opened session. programs were opening wildly, not just a few, we're talking 20-30 opened windows!

aysiu, i created the test user and logged in with it and had no problems for about one hour. i logged in normallly and had no problems again for the rest of the day. btw how do i remove that test account? i see no reason for leaving it.

thnx for the ideas, guys. will report if it happens again.

---

### Post by aysiu on 2006-10-01
That's weird. Why don't you keep the test user around for a few more days until you're sure everything's okay?

You can delete the test user the same way you created it: System > Administration > Users and Groups

---

### Post by Vlatko on 2006-10-02
i agree it's weird, nothing i ever witnessed before. will try out some more using the test account.

ok, thnx, i created the user using the terminal.

---

### Post by az on 2006-10-02
> **Vlatko said:**
>  my mouse disappears and numerous nautilus windows start opening, other programs opening without me able to do anyhing. i start moving my mouse to try and see the pointer and when i do i start to close all the open windows. then if i put the cursor over any icons it opens it without me clicking on it. 


I have a mouse that does that when I plug it into a KVM switch.  There is something about the frequency it is polled (or something like that)  It's like I am pressing the mouse buttons a few hundred times per second.  I can pass some kernel parameters to make it better, but I guess I would have to spend an afternoon fine-tuning it.

It is not an intermittent problem such as your's, though.  Hmmmm...

---

### Post by Bloch on 2006-10-02
A (non-optical) mouse stuffed with dust can cause such problems.

Do all your problems occur when moving / uisng the mouse? Or do they keep happening even when the mouse is still?

---

