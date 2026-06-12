---
title: "Running an application as another user?"
date: 2005-06-02
forum: Desktop Environments
---

### Post by thinusp on 2005-06-02
Hi

I'd like to run an X application as another user from within my current X session. Is this possible?

Thanx
Thinus

---

### Post by dave9191 on 2005-06-02
You can 

su username

to get a command like with the other user logged in and run any application as that user in your current x session.

Dave

---

### Post by thinusp on 2005-06-02
Tried that, got a error about the display. In the meantime I tracked down something through google.

[http://www.xs4all.nl/~zweije/xauth-7.html](http://www.xs4all.nl/~zweije/xauth-7.html) 

a wrapper script that takes care of the xauth stuff

Cheers
T

---

### Post by shakin on 2005-06-02
```

$ sudo -u username appname

```

or for a Gnome gui prompt...
```

$ gksudo -u username appname

```

or for a KDE gui prompt...
```

$ kdesu -u username appname

```

---

### Post by thinusp on 2005-06-02
[QUOTE=shakin]```

$ sudo -u username appname

```

or for a Gnome gui prompt...
```

$ gksudo -u username appname

```

or for a KDE gui prompt...
```

$ kdesu -u username appname

```[/QUOTE]

In the first case I get
```

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(pan:13572): Gtk-WARNING **: cannot open display:

```

Second one gives
```

Xlib: connection

(pan:13595): Gtk-WARNING **: cannot open display:

```

I actually found a solution. See my post a little way up.

Cheers
T

---

### Post by Alexander Kirillov on 2005-06-02
[QUOTE=thinusp]Tried that, got a error about the display. In the meantime I tracked down something through google.

[http://www.xs4all.nl/~zweije/xauth-7.html](http://www.xs4all.nl/~zweije/xauth-7.html) 

a wrapper script that takes care of the xauth stuff

Cheers
T[/QUOTE]
 Another method is to run (as yourself, not as another user) 
xhost +local:

You only need to do it once - you can add this to your session startup programs, if you want.

---

