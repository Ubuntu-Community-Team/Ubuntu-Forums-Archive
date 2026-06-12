---
title: "no windows in compiz"
date: 2007-09-23
forum: Desktop Effects &amp; Customization
---

### Post by DOH on 2007-09-23
after installing envy and getting the lastest drivers for my card I got compiz. when i run it in alt-f2 my borders to my windows dissapear but when i minimize or maximize I get great effects.  when i run the command compiz --replace in the terminal this is what comes up.

crake@destroyerofhope:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:8830): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8830): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8830): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8830): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8830): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8830): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8830): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8830): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8830): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8830): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8830): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:8830): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure

I would appreciate any help. Thanks.

---

### Post by ev5unleash1 on 2007-09-23
Ok, If you have compiz config manager. Go onto that and make sure Window Decorator is enabled or something around that. And if you have emerald with it do emerald --replace in the terminal (a separate one) and you will get one.

---

### Post by DOH on 2007-09-23
yeah i have the config manager i went in and window decorations are enabled...In the guide I was using it said to type

gtk-window-decorator 

in the command line.

I don't have emerald downloaded...do i need it?

---

### Post by Islington on 2007-09-23
yup you need emerald.

sudo apt-get or synaptic it.

---

### Post by ev5unleash1 on 2007-09-23
No you do not need emerald. IT will just use a defalt Metacity theme or compiz will use it's own. But emerald is a nice touch.

---

### Post by DOH on 2007-09-24
so if i get emerald i just type emerald in the command line for the window decorator inside the compiz manager right?

I tried that and it still takes away my window borders.
Any ideas?

---

### Post by haZZe08 on 2007-09-24
i get this 



usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libccp.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'ccp'

---

### Post by haZZe08 on 2007-09-24
i checked to see if i had direct rendering on and it says no, how do i turn it on?

---

### Post by ev5unleash1 on 2007-09-24
Oh, If you don't have direct rendering you will have to reset up your video card. Open a terminal and type in ```
sudo sudo dpkg-reconfigure xserver-xorg
``` this will open a wizard that will ask you what kind of card you have and all of that stuff. You usually have problems if you don't have that enabled.

---

### Post by haZZe08 on 2007-09-24
k, direct rendering is on

when i run compiz --replace it gives me this

Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.


oh and i still dont have window borders when i start with gnome with xgl and the window gets stuck in the upper left hand corner

i have to start session with gnome only


here are my specs
intel 2.4 
ati radeon x700 pro 
1 gb ram
500gb hd
syncmaster 940bw 19in

---

### Post by haZZe08 on 2007-09-24
emerald opens if that makes any difference, but compiz does not

---

### Post by DOH on 2007-09-25
k i have emerald.

and i have emerald running in the command line in compiz window decorator...is this right?
or should i run emerald independently and put gtk-window-decorator in the command line?

anyway when i alt-f2 compiz --replace it takes away my window borders.

---

### Post by patang on 2007-09-26
I have no window borders in compiz with emerald, but it works fine with gtk-window-decorator. 

Hope this helps

---

