---
title: "No borders in compiz after upgrade to intrepid"
date: 2008-12-21
forum: General Help
---

### Post by octoberdan on 2008-12-21
If I disable effects, the borders display just fine. I wasn't having this problem before.

```
daniel@dana-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5954 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
/usr/bin/gtk-window-decorator: symbol lookup error: /usr/bin/gtk-window-decorator: undefined symbol: decor_blend_top_border_picture

```

---

### Post by gettinoriginal on 2008-12-21
This should help: In terminal type:  :P

sudo apt-get install xserver-xgl

Then

compiz --replace

---

### Post by octoberdan on 2008-12-21
```

daniel@dana-desktop:~/Desktop/backup/DanUtil$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xgl

```

---

### Post by octoberdan on 2008-12-21
```

daniel@dana-desktop:~/Desktop/backup/DanUtil$ dpkg -l | grep compiz | sort
ii  compizconfig-backend-gconf                 0.7.8-0ubuntu1                     Settings library for plugins - OpenCompositi
ii  compiz-core                                1:0.7.4-0ubuntu7                   OpenGL window and compositing manager
ii  compiz-gnome                               1:0.7.4-0ubuntu7                   OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.7.4-0ubuntu7                   OpenGL window and compositing manager - plug
ii  libcompizconfig0                           0.7.4-0ubuntu1                     Settings library for plugins - OpenCompositi
rc  compiz-fusion-plugins-extra                0.7.4-0ubuntu1                     Collection of extra plugins from OpenComposi
rc  compiz-fusion-plugins-main                 0.7.4-0ubuntu5                     Collection of plugins from OpenCompositing f

```

---

### Post by chenguo4 on 2008-12-21
Check to see if you have emerald running? And if not, if you manually start emerald, do you still not have window decorations?

---

### Post by gettinoriginal on 2008-12-21
If the package cannot be found, then it is not available.  Check your software sources and see if all the appropriate repositories are checked.  If they are, try typing:
sudo apt-get update

---

