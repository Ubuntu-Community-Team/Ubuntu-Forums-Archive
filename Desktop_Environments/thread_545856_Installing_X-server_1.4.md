---
title: "Installing X-server 1.4"
date: 2007-09-08
forum: Desktop Environments
---

### Post by PmDematagoda on 2007-09-08
I just downloaded the 1.4 version of X-server.

When I unpacked it and tried to ./configure it using the terminal I got this message:

```
checking for authdes_create... yes
checking for library containing getsecretkey... none required
checking if Secure RPC authentication ("SUN-DES-1") should be supported... yes
checking for NONE/share/sgml/X11/defs.ent... no
checking for linuxdoc... no
checking for ps2pdf... /usr/bin/ps2pdf
checking Whether to build documentation... no
checking Whether to build pdf documentation... yes
checking for PIXMAN... configure: error: Package requirements (pixman-1 >= 0.9.5) were not met:

No package 'pixman-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PIXMAN_CFLAGS
and PIXMAN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

Does anyone know why this occurred?:(

I can give anyone the full output of the ./configure command if they want it.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-08
Hi PmDematagoda, how do you do? :)

[QUOTE=PmDematagoda]
```

No package 'pixman-1' found

```
[/QUOTE]

I believe you must install the libpixman-dev packages.
```

sudo apt-get install libpixman-dev

```

---

### Post by PmDematagoda on 2007-09-08
Hey Milk & Toast & Honey, nice to hear from you, I'm fine except my computer isn't, you can find out from my thread in General Help. I'm trying X-server 1.4 so as to try to fix that problem.

Thanks for your help.:)

---

### Post by PmDematagoda on 2007-09-08
There's another problem now, as anyone who read my thread in General Help knows, I can't access my normal Ubuntu Account which means I need to use Recovery Mode. The thing is I don't know how to get to the Folder containing the X-server 1.4 files from the terminal where I start. :confused::confused:

The X-server folder is found in my home folder.

---

### Post by maybeway36 on 2007-09-08
From the terminal, try:
```
su -l your-username
```

---

### Post by PmDematagoda on 2007-09-08
Nope, I still hit the same problem I faced in my first post.

---

### Post by PmDematagoda on 2007-09-21
Hello, I just need to know the way to install x-server 1.4, out of curiosity as I would like to have "Bullet-proof X" a little quicker in order to help me do more things with Ubuntu with fewer risks of completely losing the GUI.

Thanks.:)

---

