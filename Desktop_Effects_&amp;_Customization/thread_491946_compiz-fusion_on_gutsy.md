---
title: "compiz-fusion on gutsy"
date: 2007-07-04
forum: Desktop Effects &amp; Customization
---

### Post by chrroessner on 2007-07-04
Hi,

On my develop-machine, I switched from feisty to gutsy. So far so good. Unfortunatly, compiz-fusion does not work and I can not find out why.

```

 glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
...

```

```

 aptitude search compiz
i   compiz                                                                                 - OpenGL window and compositing manager                                                            
p   compiz-bcop                                                                            - Compiz option code generator                                                                     
p   compiz-compcomm-plugins-main                                                           - Collection of plugins from OpenCompositing for Compiz                                            
i A compiz-core                                                                            - OpenGL window and compositing manager                                                            
p   compiz-dev                                                                             - OpenGL window and compositing manager - development files                                        
i   compiz-fusion-plugins-extra                                                            - Collection of extra plugins from OpenCompositing for Compiz                                      
i A compiz-fusion-plugins-main                                                             - Collection of plugins from OpenCompositing for Compiz                                            
i A compiz-gnome                                                                           - OpenGL window and compositing manager - GNOME window decorator                                   
p   compiz-kde                                                                             - OpenGL window and compositing manager - KDE window decorator                                     
i A compiz-plugins                                                                         - OpenGL window and compositing manager - plugins                                                  
i   compizconfig-settings-manager                                                          - Compiz configuration settings manager                                                            
v   gcompizthemer                                                                          -                                                                                                  
ci  gnome-compiz-manager                                                                   - Compiz Gnome Manager                                                                             
i A libcompizconfig-backend-gconf                                                          - Settings library for plugins - OpenCompositing Project                                           
i   libcompizconfig0                                                                       - Settings library for plugins - Compiz Fusion Project                                             
p   libcompizconfig0-dev                                                                   - Development file for plugin settings - OpenCompositing Project                                   
ciA libgnome-compiz-manager0                                                               - Compiz Gnome Manager                                                                             
p   libgnome-compiz-manager0-dev                                                           - Compiz Gnome Manager                                                                             
i A python-compizconfig                                                                    - Compiz configuration system bindings

```

Using nvidia-glx-new

Trying to start from console:

```

compiz --replace
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Converting gconf plugin list: '' 
Checking for nVidia: present. 
Checking for Xgl: not present. 

***MEMORY-WARNING***: gtk-window-decorator[7683]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...
Segmentation fault (core dumped)

***MEMORY-WARNING***: metacity[7659]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...

```

My machine is an AMD64 3200+ with a NVidia Geforce 6800GT.

I would so much like to have compiz-fusion run, because I need the neg-plugin for my eyes. I have really big problems on reading/writing on a white background and I love this plugin as most of all plugins :-)

Kind regards

Christian

---

### Post by RebounD11 on 2007-07-04
It might be the gtk windows decorator... I have problems with it too :( it crashes before it starts...
Try installing emerald and try 

compiz --replace -c emerald & 

instead of 

compiz--replace

---

### Post by chrroessner on 2007-07-04
Hi,

thanks. I switched over to beryl and I will have a focus on the update-manager :-)

Regards

Christian

---

