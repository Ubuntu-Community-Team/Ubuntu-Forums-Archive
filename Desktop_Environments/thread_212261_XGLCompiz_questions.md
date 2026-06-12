---
title: "XGL/Compiz questions"
date: 2006-07-09
forum: Desktop Environments
---

### Post by lungdart on 2006-07-09
I have XGL/Compiz installed on ubuntu (6.06). I ahve an XGL startup script as a session to choose from as login (Theres a tut out there for how to set it up that way)

My question is: WHy dont my keyboard shortcuts work anymore? I'm not talking about the default gnome ones, im talking about application ones. pressing alt+left or f11 in firefox does nothing, although they should go back/fullscreen. Same with other applications like the superkey+z-b combos with amarok. They just dont function. Its as if I pressed the keys alone.

A friend of mine is using ubuntu 6.06 as well on his dell laptop with aiglx instead of xgl and compiz, and he can still use his keyboard shortcuts.

Anyone ran into this problem aswell? :confused:

---

### Post by falcon15500 on 2006-07-09
I think it might be because different key combinations are in use by XGL/Compiz...  F11 for example, is used by Compiz.  You might have to configure things differently for them to work?

falc

---

### Post by lungdart on 2006-07-10
Well, the f11 was in use with compiz, but im still having trouble with alt and super keyboard shortcuts. The super/alt key doesnt even work with compiz shortcuts with XGL. I had to reconfigure to use with ctrl. 

I have installed gset-compiz and the compiz-start.py and when I switch back to metacity it still has the same problem so I beleive that it resides in XGL and not compiz. IS there anything specific I could look for in the XGL configs, or does it just use the xorg.conf?

Any help would be appreciated

---

### Post by lungdart on 2006-07-13
Bump:

It turns out the right alt key doesnt work, but the left one works fine. neither super key works for shortcuts, and I have disabled all related alt/super combos from compiz.

The issues again are still there with metacity in XGL. Help please?

---

### Post by matko on 2006-07-13
> **lungdart said:**
> Bump:

It turns out the right alt key doesnt work, but the left one works fine. neither super key works for shortcuts, and I have disabled all related alt/super combos from compiz.

The issues again are still there with metacity in XGL. Help please?

hello. i have xgl/compiz and works fine. perfect.
have two question.
2. i am connected with ssh now. i start xgl compiz manually by typing "thefuture". how can i set to start automaticly after login?
(remember i am away connected only with ssh)
1. i would like also choose between xgl/compiz or no. is it possible to choose in login screen?

thanx very much

---

### Post by lungdart on 2006-07-18
To start compiz automaticly you could add "thefuture" to the startup section of system-preferences-sessions on your menu.

I have XGL as a session you can choose at login. to do this:

```

$ sudo gedit /usr/bin/startxgl.sh

```

and put this in it

```

Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
# Start GNOME
exec gnome-session 

```

Also create this file

```

$ sudo gedit /usr/share/xsessions/xgl.desktop

```

```

[Desktop Entry]
Encoding=UTF-8
Name=XGl
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application 

```

After this XGL will be available as a session in the login. After that I use gset-compiz and startcompiz.py to load Compiz on top of it. Gset-compiz lets me change the settings and switch back to metacity on the fly. theres tuts around for that. just google it.

---
Back on topic. I have upgraded all XGL/Compiz compenants and still have the same problem. If I login with XGL (where the above script loads XGL instead of X) I still have no function from either super key or the right alt key. This is a big problem, will someone PLEASE help me out

Thank you

---

### Post by autocrosser on 2006-07-18
If you take a look at Poofy's tut--there is another step you need to do--Are you adding the xmod keymap? I'm at work right now so I can't see my set-up, but I added a gnome-sesson item to start compiz & set the xmod key map---
 
As per Poofy's guide:
 
"in a terminal---Code:
 
[LEFT]xmodmap /usr/share/xmodmap/xmodmap.<language>[/LEFT]
 
 
replacing you country code for language. For US English I use this command:
 
 
Code:
[LEFT]xmodmap /usr/share/xmodmap/xmodmap.us"[/LEFT]
 
 
 
So in gnome-session I put:
 
thefuture xmodmap /usr/share/xmodmap/xmodmap.us
 
& run it that way---hope this helps!!! (this is as best as I can remember here--try it & post--I'll look when I get home in about 4/5 hrs)

---

### Post by utnubu001 on 2006-07-18
i hope all questions are answerd here...

why dose compiz only work if i use    sudo

if idont i lose my window borders

---

### Post by autocrosser on 2006-07-18
Ok--Taking a look at my gnome-sessions, I added /usr/bin/thefuture  
&  
xmodmap /usr/share/xmodmap/xmodmap.us  
on seperate lines--try that.

utnubu001--I'm afraid that I don't know--I'm sure that Poofy would have the answer--You might goto to his thread & ask...I'm sure that you have installed something with sudo & your user is not allowed to access that part...As a thought----You might goto System/administration/Users and Groups---make sure that you are a administrator--not just a regular user. (Users (your user)/User privileges tab)

---

