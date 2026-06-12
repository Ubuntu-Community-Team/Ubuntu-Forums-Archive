---
title: "beryl won't start"
date: 2007-06-10
forum: Desktop Effects &amp; Customization
---

### Post by banda on 2007-06-10
i installed nvidia drivers and enabled them , logged off and did ctrl+alt+backspace .. then i installed beryl
i i had no problems doing the above.. i started the beryl manager and still no  errors .. but the problem is nothing happened!!
no wobly windows .. no animations...:(
any ideas??

---

### Post by banda on 2007-06-10
i installed nvidia drivers and enabled them , logged off and did ctrl+alt+backspace .. then i installed beryl
i i had no problems doing the above.. i started the beryl manager and still no errors .. but the problem is nothing happened!!
no wobly windows .. no animations...
i don't know what i did wrong
any ideas??

---

### Post by banda on 2007-06-10
som1 please reply or i will need to reinstall..
 i am on ubuntu 7.04 and i installed beryl without trying system>preferences>desktop effects
now when i do that i get "the Composite extension is not available"


for my nvidia graphic card i installed drivers named nvidia-glx-new .. are they the wrong version??

---

### Post by Trueno22 on 2007-06-10
is emerald running?????

---

### Post by Trueno22 on 2007-06-10
did you remember to set beryl and emerald to automatically start at login

---

### Post by banda on 2007-06-10
changing emrald themes has no effect..

i don't know how to have it automatically start at login

i do start the manager each time i boot manually (nothing happens apart from the icon appearing)

---

### Post by BOBSONATOR on 2007-06-10
right click the icon, and select window manager, then beryl?

---

### Post by banda on 2007-06-10
no luck.. i tried that

---

### Post by banda on 2007-06-10
<bump>

---

### Post by calraith on 2007-06-10
```
glxinfo | grep direct
```
Does the output of that display "direct rendering: Yes?"  If not, X might be running a non-GLX driver.  You might need to reinstall your X driver.

---

### Post by banda on 2007-06-10
i get a yes

---

### Post by banda on 2007-06-10
only "yes" no direct rendering

---

### Post by calraith on 2007-06-10
> **banda said:**
> only "yes" no direct rendering
Huh?

Well, I take it that GLX is working on your system.  Try removing and reinstalling beryl.
```
sudo apt-get remove beryl
sudo apt-get autoremove -y
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install beryl beryl-settings emerald-themes
```

---

### Post by stryker719 on 2007-06-11
I'm having the same problem, only when I execute "glxinfo | grep direct" the following is posted.

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

I'm assuming that means that something hasn't been installed correctly.  Any thoughts?

BTW, I have an nVidia 8800gtx.

---

### Post by bapoumba on 2007-06-11
Duplicate threads merged.

---

### Post by banda on 2007-06-11
thanx

---

### Post by calraith on 2007-06-11
> **stryker719 said:**
> I'm having the same problem, only when I execute "glxinfo | grep direct" the following is posted.

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```I'm assuming that means that something hasn't been installed correctly.  Any thoughts?

BTW, I have an nVidia 8800gtx.
Yep, you're probably running driver "nv" rather than "nvidia" in /etc/X11/xorg.conf.  "nv" isn't GLX.

Niiiiiiice card, by the way.

---

