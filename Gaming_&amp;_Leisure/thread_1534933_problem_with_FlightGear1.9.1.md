---
title: "problem with FlightGear1.9.1"
date: 2010-07-20
forum: Gaming &amp; Leisure
---

### Post by haweg on 2010-07-20
Hi,
I ran fgfsv1.9 on Ubuntu9.04 with no problems at all and with the expected frame rate of approx. 18-20 fps.
After upgrading to 10.04 and new installation of fgfs the program still runs but with a frustrating FR of 3-7.
3D accel. otherwise ok,
Any idea about  this problem.

---

### Post by lkjoel on 2010-07-20
Could you give me the output of the application when you run it in the Terminal?
And could you give me the output of: [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by haweg on 2010-08-02
This I see in the terminal:

[I]haweg@udesk:~$ fgfs --aircraft=c172p-2dpanel --airport=EDWO --timeofday=noon --log-level=alert
  Model Author:  Unknown
  Creation Date: 2002-01-01
  Version:       $Id: c172p.xml,v 1.20 2008/09/01 15:14:33 torsten Exp $
  Description:   Cessna C-172
FGMultiplayMgr - No receiver port, Multiplayermode disabled
KI266 dme indicator #0 initialized
Initializing Nasal Electrical System
power up
[/I]
With higher log-levels there is too much of output to quote.
Then:

[I]./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation C68 [GeForce 7050 PV / nForce 630a] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
[/I]
Without anything new for me.
What is funny: 

*driconf*             and
*xdriinfo *            say[I]
libGL is too old.
[/I]
without telling me what they expect.
All very confusing.

---

### Post by lkjoel on 2010-08-02
Could you give me the output of this command for me please?
```
sudo apt-cache search libgl
```
This is what I have:
```
gle-doc - OpenGL tubing and extrusion library documentation
libglade2-0 - library to load .glade files at runtime
libglade2-dev - development files for libglade
libglade2.0-cil - CLI binding for the Glade libraries 2.6
libglade2.0-cil-dev - CLI binding for the Glade libraries 2.6
libglademm-2.4-1c2a - C++ wrappers for libglade2 (shared library)
libglademm-2.4-dbg - C++ wrappers for libglade2 (debug symbols)
libglademm-2.4-dev - C++ wrappers for libglade2 (development files)
libglademm-2.4-doc - C++ wrappers for libglade2 (documentation)
libgladeui-1-9 - GTK+ User Interface Build core library
libgladeui-1-dev - GTK+ User Interface Build core library (development files)
libgle3 - OpenGL tubing and extrusion library
libgle3-dev - OpenGL tubing and extrusion library development files
libglib-perl - Perl interface to the GLib and GObject libraries
libglib2.0-cil - CLI binding for the GLib utility library 2.12
libglib2.0-cil-dev - CLI binding for the GLib utility library 2.12
libglitz-glx1 - Glitz OpenGL library GLX backend
libglitz-glx1-dev - Glitz OpenGL library GLX backend development libraries and headers
libglitz1 - Glitz OpenGL image compositing library
libglitz1-dev - OpenGL image compositing library development libraries and headers
libglu1-xorg-dev - transitional package for Debian etch
libgluezilla - glue library to embed Gecko in Mono's WebControl
libmono-webbrowser0.5-cil - Mono Web Browser library
cairo-clock - An analog clock drawn with vector-graphics
cairo-clock-hildon - An analog clock drawn with vector-graphics
gazpacho - GTK+ User Interface Designer
glade - GTK+ 2 User Interface Builder
glade-gnome - GTK+ 2 User Interface Builder (with GNOME 2 support)
glew-utils - The OpenGL Extension Wrangler - utilities
guile-gnome2-gtk - Guile bindings for GTK+, libglade, Pango and ATK
libghc6-glade-dev - A GUI library for Haskell (Gtk2Hs) -- libglade bindings
libgl2ps-dev - Lib providing high quality vector output for OpenGL application
libgl2ps0 - Lib providing high quality vector output for OpenGL application
libgl2ps0-dbg - Lib providing high quality vector output for OpenGL application
libglacier2-33 - Libraries implementing a firewall service for ZeroC Ice
libglade2-ruby - Libglade 2 bindings for the Ruby language
libglade2-ruby1.8 - Libglade 2 bindings for the Ruby language
libglade2-ruby1.8-dbg - Libglade 2 bindings for the Ruby language
libglazedlists-java - java list transformation library
libglazedlists-java-doc - java list transformation library (documentation)
libglbsp-dev - node builder library for OpenGL-based Doom-style games (headers)
libglbsp3 - node builder library for OpenGL-based Doom-style games
libglc-dev - An implementation of SGI's OpenGL Character Renderer (GLC)
libglc0 - QuesoGLC GLC implementation
libglew1.5 - The OpenGL Extension Wrangler - runtime environment
libglew1.5-dev - The OpenGL Extension Wrangler - development environment
libglewmx1.5 - The OpenGL Extension Wrangler - runtime environment
libglewmx1.5-dev - The OpenGL Extension Wrangler - development environment
libglfw-dev - portable framework for OpenGL application development
libglfw2 - portable framework for OpenGL application development
libglib2-ruby - Glib 2 bindings for the Ruby language
libglib2-ruby1.8 - Glib 2 bindings for the Ruby language
libglib2-ruby1.8-dbg - Glib 2 bindings for the Ruby language
libglibmm-utils-dev - utility functions, classes and widgets written on top of glibmm
libglibmm-utils2 - utility functions, classes and widgets written on top of glibmm
libglide2 - graphics library for 3Dfx Voodoo based cards - shared libraries
libglide2-dev - graphics library for 3Dfx Voodoo based cards - development files
libglide3 - graphics library for 3Dfx Voodoo based cards - shared libraries
libglide3-dev - graphics library for 3Dfx Voodoo based cards - development files
libglobus-authz-callout-error-dev - Globus Toolkit - Globus authz error library Development Files
libglobus-authz-callout-error-doc - Globus Toolkit - Globus authz error library Documentation Files
libglobus-authz-callout-error0 - Globus Toolkit - Globus authz error library
libglobus-authz-dev - Globus Toolkit - Globus authz library Development Files
libglobus-authz-doc - Globus Toolkit - Globus authz library Documentation Files
libglobus-authz0 - Globus Toolkit - Globus authz library
libglobus-callout-dev - Globus Toolkit - Globus Callout Library Development Files
libglobus-callout-doc - Globus Toolkit - Globus Callout Library Documentation Files
libglobus-callout0 - Globus Toolkit - Callout Library
libglobus-common-dev - Globus Toolkit - Common Library Development Files
libglobus-common-doc - Globus Toolkit - Common Library Documentation Files
libglobus-common0 - Globus Toolkit - Common Library
libglobus-data-conversion-dev - Globus Toolkit - Data Conversion Development Files
libglobus-data-conversion2 - Globus Toolkit - Data Conversion
libglobus-duct-common-dev - Globus Toolkit - Globus Duct Common Development Files
libglobus-duct-common2 - Globus Toolkit - Globus Duct Common
libglobus-duct-control-dev - Globus Toolkit - Globus Duct Control Development Files
libglobus-duct-control2 - Globus Toolkit - Globus Duct Control
libglobus-duroc-common-dev - Globus Toolkit - DUROC Common Library Development Files
libglobus-duroc-common2 - Globus Toolkit - DUROC Common Library
libglobus-duroc-control-dev - Globus Toolkit - DUROC Control Library Development Files
libglobus-duroc-control2 - Globus Toolkit - DUROC Control Library
libglobus-ftp-client-dev - Globus Toolkit - GridFTP Client Library Development Files
libglobus-ftp-client-doc - Globus Toolkit - GridFTP Client Library Documentation Files
libglobus-ftp-client1 - Globus Toolkit - GridFTP Client Library
libglobus-ftp-control-dev - Globus Toolkit - GridFTP Client Control Library Development Files
libglobus-ftp-control-doc - Globus Toolkit - GridFTP Client Control Library Documentation Files
libglobus-ftp-control1 - Globus Toolkit - GridFTP Client Control Library
libglobus-gass-cache-dev - Globus Toolkit - Globus Gass Cache Development Files
libglobus-gass-cache5 - Globus Toolkit - Globus Gass Cache
libglobus-gass-copy-dev - Globus Toolkit - Globus Gass Copy Development Files
libglobus-gass-copy-doc - Globus Toolkit - Globus Gass Copy Documentation Files
libglobus-gass-copy2 - Globus Toolkit - Globus Gass Copy
libglobus-gass-server-ez-dev - Globus Toolkit - Globus Gass Server_ez Development Files
libglobus-gass-server-ez2 - Globus Toolkit - Globus Gass Server_ez
libglobus-gass-transfer-dev - Globus Toolkit - Globus Gass Transfer Development Files
libglobus-gass-transfer-doc - Globus Toolkit - Globus Gass Transfer Documentation Files
libglobus-gass-transfer2 - Globus Toolkit - Globus Gass Transfer
libglobus-gfork-dev - Globus Toolkit - GFork Development Files
libglobus-gfork0 - Globus Toolkit - GFork
libglobus-gram-client-dev - Globus Toolkit - GRAM Client Library Development Files
libglobus-gram-client-doc - Globus Toolkit - GRAM Client Library Documentation Files
libglobus-gram-client3 - Globus Toolkit - GRAM Client Library
libglobus-gram-job-manager-callout-error-dev - Globus Toolkit - Globus GRAM Jobmanager Callout Errors Development Files
libglobus-gram-job-manager-callout-error-doc - Globus Toolkit - Globus GRAM Jobmanager Callout Errors Documentation Files
libglobus-gram-job-manager-callout-error0 - Globus Toolkit - Globus GRAM Jobmanager Callout Errors
libglobus-gram-protocol-dev - Globus Toolkit - GRAM Protocol Library Development Files
libglobus-gram-protocol-doc - Globus Toolkit - GRAM Protocol Library Documentation Files
libglobus-gram-protocol3 - Globus Toolkit - GRAM Protocol Library
libglobus-gridftp-server-control-dev - Globus Toolkit - Globus GridFTP Server Library Development Files
libglobus-gridftp-server-control0 - Globus Toolkit - Globus GridFTP Server Library
libglobus-gridftp-server-dev - Globus Toolkit - Globus GridFTP Server Development Files
libglobus-gridftp-server0 - Globus Toolkit - Globus GridFTP Server
libglobus-gsi-callback-dev - Globus Toolkit - Globus GSI Callback Library Development Files
libglobus-gsi-callback-doc - Globus Toolkit - Globus GSI Callback Library Documentation Files
libglobus-gsi-callback0 - Globus Toolkit - Globus GSI Callback Library
libglobus-gsi-cert-utils-dev - Globus Toolkit - Globus GSI Cert Utils Library Development Files
libglobus-gsi-cert-utils-doc - Globus Toolkit - Globus GSI Cert Utils Library Documentation Files
libglobus-gsi-cert-utils0 - Globus Toolkit - Globus GSI Cert Utils Library
libglobus-gsi-credential-dev - Globus Toolkit - Globus GSI Credential Library Development Files
libglobus-gsi-credential-doc - Globus Toolkit - Globus GSI Credential Library Documentation Files
libglobus-gsi-credential1 - Globus Toolkit - Globus GSI Credential Library
libglobus-gsi-openssl-error-dev - Globus Toolkit - Globus OpenSSL Error Handling Development Files
libglobus-gsi-openssl-error-doc - Globus Toolkit - Globus OpenSSL Error Handling Documentation Files
libglobus-gsi-openssl-error0 - Globus Toolkit - Globus OpenSSL Error Handling
libglobus-gsi-proxy-core-dev - Globus Toolkit - Globus GSI Proxy Core Library Development Files
libglobus-gsi-proxy-core-doc - Globus Toolkit - Globus GSI Proxy Core Library Documentation Files
libglobus-gsi-proxy-core0 - Globus Toolkit - Globus GSI Proxy Core Library
libglobus-gsi-proxy-ssl-dev - Globus Toolkit - Globus GSI Proxy SSL Library Development Files
libglobus-gsi-proxy-ssl-doc - Globus Toolkit - Globus GSI Proxy SSL Library Documentation Files
libglobus-gsi-proxy-ssl1 - Globus Toolkit - Globus GSI Proxy SSL Library
libglobus-gsi-sysconfig-dev - Globus Toolkit - Globus GSI System Config Library Development Files
libglobus-gsi-sysconfig-doc - Globus Toolkit - Globus GSI System Config Library Documentation Files
libglobus-gsi-sysconfig1 - Globus Toolkit - Globus GSI System Config Library
libglobus-gss-assist-dev - Globus Toolkit - GSSAPI Assist library Development Files
libglobus-gss-assist-doc - Globus Toolkit - GSSAPI Assist library Documentation Files
libglobus-gss-assist3 - Globus Toolkit - GSSAPI Assist library
libglobus-gssapi-error-dev - Globus Toolkit - GSSAPI Error Library Development Files
libglobus-gssapi-error-doc - Globus Toolkit - GSSAPI Error Library Documentation Files
libglobus-gssapi-error2 - Globus Toolkit - GSSAPI Error Library
libglobus-gssapi-gsi-dev - Globus Toolkit - GSSAPI library Development Files
libglobus-gssapi-gsi-doc - Globus Toolkit - GSSAPI library Documentation Files
libglobus-gssapi-gsi4 - Globus Toolkit - GSSAPI library
libglobus-io-dev - Globus Toolkit - uniform I/O interface Development Files
libglobus-io3 - Globus Toolkit - uniform I/O interface
libglobus-libtool - Globus Toolkit - Globus libtool package
libglobus-libtool-dev - Globus Toolkit - Globus libtool package Development Files
libglobus-mp-dev - Globus Toolkit - Message Passing Library Development Files
libglobus-mp2 - Globus Toolkit - Message Passing Library
libglobus-nexus-dev - Globus Toolkit - Nexus Library Development Files
libglobus-nexus6 - Globus Toolkit - Nexus Library
libglobus-openssl - Globus Toolkit - Openssl Library
libglobus-openssl-dev - Globus Toolkit - Openssl Library Development Files
libglobus-openssl-module-dev - Globus Toolkit - Globus OpenSSL Module Wrapper Development Files
libglobus-openssl-module-doc - Globus Toolkit - Globus OpenSSL Module Wrapper Documentation Files
libglobus-openssl-module0 - Globus Toolkit - Globus OpenSSL Module Wrapper
libglobus-rls-client-dev - Globus Toolkit - Replica Location Service Client Development Files
libglobus-rls-client-doc - Globus Toolkit - Replica Location Service Client Documentation Files
libglobus-rls-client5 - Globus Toolkit - Replica Location Service Client
libglobus-rsl-assist-dev - Globus Toolkit - RSL Manipulation Library Development Files
libglobus-rsl-assist2 - Globus Toolkit - RSL Manipulation Library
libglobus-rsl-dev - Globus Toolkit - Resource Specification Language Library Development Files
libglobus-rsl2 - Globus Toolkit - Resource Specification Language Library
libglobus-scheduler-event-generator-dev - Globus Toolkit - Scheduler Event Generator Development Files
libglobus-scheduler-event-generator-doc - Globus Toolkit - Scheduler Event Generator Documentation Files
libglobus-scheduler-event-generator0 - Globus Toolkit - Scheduler Event Generator
libglobus-usage-dev - Globus Toolkit - Usage Library Development Files
libglobus-usage0 - Globus Toolkit - Usage Library
libglobus-xio-dev - Globus Toolkit - Globus XIO Framework Development Files
libglobus-xio-doc - Globus Toolkit - Globus XIO Framework Documentation Files
libglobus-xio-gsi-driver-dev - Globus Toolkit - Globus XIO GSI Driver Development Files
libglobus-xio-gsi-driver-doc - Globus Toolkit - Globus XIO GSI Driver Documentation Files
libglobus-xio-gsi-driver0 - Globus Toolkit - Globus XIO GSI Driver
libglobus-xio-popen-driver-dev - Globus Toolkit - Globus XIO Pipe Open Driver Development Files
libglobus-xio-popen-driver0 - Globus Toolkit - Globus XIO Pipe Open Driver
libglobus-xio0 - Globus Toolkit - Globus XIO Framework
libglom-1.12-0 - Glom library (a database designer and user interface) - library
libglom-1.12-dev - Glom library (a database designer and user interface) - header files
libgloox-dbg - C++ jabber/xmpp library debug symbols
libgloox-dev - C++ jabber/xmpp library devel files
libgloox-doc - C++ jabber/xmpp library API documentation
libgloox7 - C++ jabber/xmpp library
libglpk-dev - linear programming kit - development files
libglpk-java - Java binding to the GNU Linear Programming Kit
libglpk0 - linear programming kit with integer (MIP) support
libglpk0-dbg - linear programming kit - debugging symbols
libglpng - PNG loader for OpenGL
libglpng-dev - PNG loader for OpenGL - development files
libglrr-glib-dev - Development library of Grift (glib)
libglrr-glib0 - Utility functions for glib of Grift
libglrr-gobject-dev - Development library of Grift (gobject)
libglrr-gobject0 - Utility functions for gobject of Grift
libglrr-gtk-dev - Development library of Grift (gtk)
libglrr-gtk0 - Utility functions for gtk+ of Grift
libglrr-widgets-dev - Development library of Grift's widgets
libglrr-widgets0 - Miscellaneous gtk+ widgets for Grift
libglu1-xorg - transitional package for Debian etch
libglui-dev - A GLUT-based C++ user interface library
libglui2c2 - GLUI, a C++ GLUT based GUI library - Runtime support
libglusterfs-dev - GlusterFS development libraries and headers (development files)
libglusterfs0 - GlusterFS libraries and translator modules
libglut3 - the OpenGL Utility Toolkit
libglut3-dev - development libraries and headers for GLUT
libglw1-mesa - A free implementation of the OpenGL API -- runtime
libglw1-mesa-dev - A free implementation of the OpenGL API -- development files
libgnomeada2.14.2-dbg - Debugging symbols for libgnomeada2
libgnomeada2.14.2-dev - Development files for libgnomeada2
libgtk2-gladexml-perl - Perl interface to use user interfaces created with glade-2
libgtkada2-doc - Documentation for libgtkada2
libgtkada2.14.2-dbg - Debugging symbols for libgtkada2
libgtkada2.14.2-dev - Development files for libgtkada2
libgtkdatabox-0.9.0-1-libglade - A Gtk+ library to display large amounts of numerical data
vim-syntax-gtk - Syntax files to highlight GTK+ keywords in vim
libgl1-mesa-dev - A free implementation of the OpenGL API -- GLX development files
libgl1-mesa-dri - A free implementation of the OpenGL API -- DRI modules
libgl1-mesa-dri-dbg - Debugging symbols for the Mesa DRI modules
libgl1-mesa-glx - A free implementation of the OpenGL API -- GLX runtime
libgl1-mesa-glx-dbg - Debugging symbols for the Mesa GLX runtime
libgl1-mesa-swx11 - A free implementation of the OpenGL API -- runtime
libgl1-mesa-swx11-dbg - A free implementation of the OpenGL API -- debugging symbols
libgl1-mesa-swx11-dev - A free implementation of the OpenGL API -- development files
libgl1-mesa-swx11-i686 - Mesa OpenGL runtime [i686 optimized]
libglib2.0-0 - The GLib library of C routines
libglib2.0-0-dbg - The GLib libraries and debugging symbols
libglib2.0-data - Common files for GLib library
libglib2.0-dev - Development files for the GLib library
libglib2.0-doc - Documentation files for the GLib library
libglibmm-2.4-1c2a - C++ wrapper for the GLib toolkit (shared libraries)
libglibmm-2.4-dbg - C++ wrapper for the GLib toolkit (debug symbols)
libglibmm-2.4-dev - C++ wrapper for the GLib toolkit (development files)
libglibmm-2.4-doc - C++ wrapper for the GLib toolkit (documentation)
libglu1-mesa - The OpenGL utility library (GLU)
libglu1-mesa-dev - The OpenGL utility library -- development files
libglib2.0-0-refdbg - The GLib library of C routines - refdbg library
openoffice.org - office productivity suite
libgluon-dev - Gluon is a high-level game development library for the KDE
libgluonaudio0 - Gluon is a high-level game development library for the KDE
libgluoncore0 - Gluon is a high-level game development library for the KDE
libgluongraphics0 - Gluon is a high-level game development library for the KDE
libgluoninput0 - Gluon is a high-level game development library for the KDE

```

---

