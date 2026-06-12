---
title: "Beryl"
date: 2007-12-29
forum: Desktop Effects &amp; Customization
---

### Post by myst1c on 2007-12-29
I have an Nvidia GeForce FX 5200 and dual monitors... I have Beyrl installed, and the beryl manager works, but none of the effects actually work... I typed beryl into the terminal, and it told me i was missing RandR, which i learned from google means Resize and Rotate Extension... Can anybody give me a hand and help me to get beryl working?

---

### Post by myst1c on 2007-12-29
bump for help?

---

### Post by roaldz on 2007-12-29
Do you have a reason to use Beryl instead of Compiz Fusion? I´d really recommend to use Compiz..

---

### Post by Joeb454 on 2007-12-29
If possible I'd recommend using Compiz-Fusion, as it's the actively supported and developed version of Beryl (Beryl & Compiz were merged).

If that isn't an option then try Google again and search for the extension :)

---

### Post by Forlong on 2007-12-29
If you are really running Ubuntu Gutsy (not Kubuntu or Xubuntu) it comes with Compiz Fusion pre-installed.
Try
```
compiz
``` in the terminal. If it doesn't work, post the output.

---

### Post by myst1c on 2007-12-29
i assume this is related, so i'll post it...

when i go to the appearance settings, and go to Visual Effects, and i try to pick one of the options, it tells me that visual effects cannot be enabled... the weird thing is, it worked before, but now it doesn't

btw, lovin' the family guy and futurama avatars... two of my favorite shows, especially futurama... too bad adult swim is taking it off the air

---

### Post by Forlong on 2007-12-29
Again: please post the output of ```
compiz
``` in a terminal.

---

### Post by myst1c on 2007-12-29
```
myst1c@Candy:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:09.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2048x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 338 error_code 181 request_code 157 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault (core dumped)

```

that's the output for compiz

---

### Post by Forlong on 2007-12-29
That's most certainly because you have still Beryl installed.

Try this:
```
sudo apt-get remove --purge compiz* beryl* emerald* && sudo apt-get autoremove
```

Then make sure you don't have any third-party repositories regarding Beryl in S*ystem &#8594; Administration &#8594; Software Sources &#8594; Third Party Software*

Then install Compiz again:
```
sudo apt-get install compiz compizconfig-settings-manager
```

---

### Post by myst1c on 2007-12-29
when i run the

```
sudo apt-get remove --purge compiz* beryl* emerald* && sudo apt-get autoremove
```

command you gave me tells me that " package emerald* cannot be found

---

### Post by Forlong on 2007-12-29
Sorry, then just remove that part:
```
sudo apt-get remove --purge compiz* beryl* && sudo apt-get autoremove
```

---

### Post by myst1c on 2007-12-30
ok i ran that command, but i still get the cannot enable desktop effects error... i've followed your directions...

hmm :/

---

### Post by Forlong on 2007-12-30
Post the output of ```
dpkg -l | grep compiz
``` as well as ```
dpkg -l | grep beryl
```

---

### Post by myst1c on 2008-01-01
The compiz output

```
ii  compiz                                     1:0.6.2+git20071119-0ubuntu1~gutsy1       OpenGL window and compositing manager
ii  compiz-core                                1:0.6.2+git20071119-0ubuntu1~gutsy1       OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.6.0+git20071121-0ubuntu1~gutsy1         Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2                Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.2+git20071119-0ubuntu1~gutsy1       OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.2+git20071119-0ubuntu1~gutsy1       OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1                Compiz configuration settings manager
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1                Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3                Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1                Compiz configuration system bindings

```

---

### Post by myst1c on 2008-01-01
btw, i don't get an ouput for the other one

---

### Post by myst1c on 2008-01-02
bump

---

### Post by Forlong on 2008-01-06
Post your sources.list:
```
cat /etc/apt/sources.list
```

---

