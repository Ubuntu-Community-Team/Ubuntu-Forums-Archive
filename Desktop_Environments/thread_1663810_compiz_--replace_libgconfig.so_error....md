---
title: "compiz --replace libgconfig.so error..."
date: 2011-01-10
forum: Desktop Environments
---

### Post by adduds on 2011-01-10
While changing themes and icons i noticed my minimize/maximize, close windows options were on the right hand side, couldn't figure out how to change it rebooted now the whole bar above file edit view...etc is gone.....

two outputs for compiz....

```
toews@desktop:~$ compiz-decorator --replace
Couldn't find a perfect decorator match; trying all decorators
```


```
toews@desktop:~$ compiz --replace
libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory
kde-window-decorator(3872) KWD::KDecorationPlugins::loadPlugin: kwin : path  ""  for  "kwin3_oxygen"
kde4-window-decorator: Could not enable decorations on display ":0.0"
kde-window-decorator(3874) KWD::KDecorationPlugins::loadPlugin: kwin : path  ""  for  "kwin3_oxygen"
kde4-window-decorator: Could not enable decorations on display ":0.0"

```

thanks.

---

### Post by adduds on 2011-01-10
bump

---

### Post by adduds on 2011-01-10
can someone please help :( this is really s****y

---

### Post by adduds on 2011-01-10
now it does this...

```
toews@desktop:~$ compiz --replace
Starting gtk-window-decorator
```

but i have to leave the terminal running for this to work

---

### Post by adduds on 2011-01-10
k so i got it down to every re-b00t i've gotta type compiz in terminal 

to get window borders effects etc....

output as follows

```
toews@desktop:~$ compiz
Starting gtk-window-decorator
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

```

---

