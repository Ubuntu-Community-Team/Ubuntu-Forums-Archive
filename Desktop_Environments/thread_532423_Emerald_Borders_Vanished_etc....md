---
title: "Emerald Borders Vanished etc..."
date: 2007-08-22
forum: Desktop Environments
---

### Post by Uber Nooblett on 2007-08-22
I had beryl and Emerald working great, until the other day when I played about a bit installing new bits etc and rebooted, at which point, emerald themes stopped loading (windows are not decorated when it is selected and there are no borders at all). I can run Aquamarine as the decorator, however it crashes when I use certain effects such as shading the window.

I've tried to backtrack my changes but now I am completely lost and dont know what to do :(

Please please help me get it shiny again! :)

Thanks!

[[IMG]http://img250.imageshack.us/img250/5751/desktop6gu5.th.jpg[/IMG]](http://img250.imageshack.us/my.php?image=desktop6gu5.jpg)

[[size=3]**Video of the problem**[/size]](http://uk.youtube.com/watch?v=-OPFul1dsVY)

[[size=2]**vid of setup working without emerald working**[/size]](http://uk.youtube.com/watch?v=AJTtzTvjbXE)

---

### Post by Chymera on 2007-08-22
[SIZE="7"]OH MY GOD THE BORDERS DISAPPEARED, I HAVE TO MAKE A BIIIIIIIIIIG CAPTURE AND PUT IT DIRECTLY ON THE FORUM!!!![/SIZE]

no really, its making the layout go bananas, i'm sure no one would mind clicking a link if you would provide one instead o the giant image.

now about your problem. I believe its something that has been discussed a lot on the forums, but rather in connection with compiz than with beryl... no matter, the solution is probably the same, type this in a terminal:
```
emerald --replace &
```

---

### Post by por100pre1 on 2007-08-22
An enormous screenshot, videos too. :shock: This thread should become a classic...

---

### Post by Uber Nooblett on 2007-08-23
> **Chymera said:**
> [SIZE="7"]OH MY GOD THE BORDERS DISAPPEARED, I HAVE TO MAKE A BIIIIIIIIIIG CAPTURE AND PUT IT DIRECTLY ON THE FORUM!!!![/SIZE]

no really, its making the layout go bananas, i'm sure no one would mind clicking a link if you would provide one instead o the giant image.

now about your problem. I believe its something that has been discussed a lot on the forums, but rather in connection with compiz than with beryl... no matter, the solution is probably the same, type this in a terminal:
```
emerald --replace &
```

Oups :) will replace with a smaller link there

that was one of the first things I tried by the way. All that does is attempt to load up emerald... and of course it does not work as Emerald isnt working for whatever reason...

p.s. I assumed that the image would be automatically resized as is usually the case with other forums :)

---

### Post by Chymera on 2007-08-23
hmmmm... 
the fact that emerald themes don't load would rather point out that emerald is not activated...
remember, there is a big difference between emerald --replace and emerald --replace & , if the first yielded no results (which is mostly the case) it does not mean the 2nd won't.
But if it really does not work for you try 
```
beryl --replace &
```
and ```
emerald --replace & 
```afterwards 
... if that still doesnt work i would reinstall emerald altogether

---

### Post by Uber Nooblett on 2007-08-23
> **Chymera said:**
> hmmmm... 
the fact that windows dont load would rather point out that emerald is not activated...
remember, there is a big difference between emerald --replace and emerald --replace & , if the first yielded no results (which is mostly the case) it does not mean the 2nd won't.
But if it really does not work for you try 
```
beryl --replace &
```
and ```
emerald --replace & 
```afterwards 
... if that still doesnt work i would reinstall emerald altogether

when I did the beryl I got this: 
```
jj@jj-desktop:~$ beryl --replace &
[1] 6321
jj@jj-desktop:~$ **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (8192x8192)

Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (8192x8192)

XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 141 requests (140 known processed) with 0 events remaining.
       
```

and then when I did the same with emerald I got this:

```
jj@jj-desktop:~$ emerald --replace &
[1] 6365

```

and the prob persists

---

### Post by Uber Nooblett on 2007-08-23
I also re-installed emerald altogether and beryl and still no joy

Would it be worth purging it completely and starting from scratch? Is there any way to save the settings file so I dont have to figure out what I like all over again should it work?

---

### Post by Uber Nooblett on 2007-08-23
I have purged Emerald and Beryl, rebooted, re-installed and then run through console:

```
jj@jj-desktop:~$ sux
Password:
root@jj-desktop:/home/jj# beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (8192x8192)

Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (8192x8192)

Reloading options
beryl: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
beryl: Plugin 'dbus':initDisplay failed
beryl: Couldn't activate plugin 'dbus'
Couldn't initialise dbus. This should not happen!
```

then I ran it from the manager and Beryl works fine, but once again, Emerald does not and the same shading crash occurs

---

### Post by Chymera on 2007-08-23
uhm.... I'm out of ideas...

---

### Post by Uber Nooblett on 2007-08-23
> **Chymera said:**
> uhm.... I'm out of ideas...

thanks for giving it a go anyways :)

---

### Post by Chymera on 2007-08-23
ah well... i was pretty sure you were getting the same-old emerald border problem everyone seems to come across once in a while...

---

### Post by Uber Nooblett on 2007-08-26
Anyone else have any ideas? prob is still unsolved :(

---

### Post by missiledave on 2008-03-05
fixed. thanks.

except when i close out of the terminal the problem starts again.?

---

