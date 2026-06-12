---
title: "close button in details window takes very  long time to do action"
date: 2015-07-20
forum: Desktop Environments
---

### Post by claracc on 2015-07-20
Hello, 

Ubuntu 14.04.2 gnome-flashback dual boot with win vista in hpcompaq  6720s laptop fully updated. I observed that when I click on close button in window system tools--> system settings --> details the window is closed after more than 20 seconds after clicking. Minimize button works inmediatly but no close button.

Is there any workaroud?

Thanks in advance

---

### Post by claracc on 2015-07-21
Bump

I add more information about the theme I use:

---

### Post by claracc on 2015-07-27
Re Bump

I have found the same delayed behaviour in the close button of the window ubuntu software centre, but no in minimize or maximize buttons.

have anybody found this problem in 14.04 flashback?

It doesn't seem to be related to the theme of desktop.

This is what I have now: See attached

---

### Post by claracc on 2015-07-29
As I got no answers to my problem with this thread , I please ask a moderator if it could be possible to move the questions in this thread to this other: [http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264).

It seems to be a more proper and specific one to fix problems with 14.04 flasback desktop problems in spite of being dated in september 2014.

Thanks in advance

---

### Post by vasa1 on 2015-08-03
> **claracc said:**
> Hello, 

Ubuntu 14.04.2 gnome-flashback dual boot with win vista in hpcompaq  6720s laptop fully updated. I observed that when I click on close button in window system tools--> system settings --> details the window is closed after more than 20 seconds after clicking. Minimize button works inmediatly but no close button.

Is there any workaroud?

Thanks in advance
Hi, what happens if you try a keyboard route? Alt+spacebar followed by pressing "c" without quotes? That should rule out anything to do with themes. 

Have you tried another window manager?

Do windows of all applications show this lag or only a certain category of applications?

Could it be that when certain applications are being closed, some file has to be written to or some database has to be updated?

What happens if you open your troublesome application via the terminal? Do you get any useful diagnostic information there?

I noticed in your other thread that your home folder has a lot of files!

---

### Post by claracc on 2015-08-04
> **vasa1 said:**
> Hi, what happens if you try a keyboard route? Alt+spacebar followed by pressing "c" without quotes? That should rule out anything to do with themes. 

Have you tried another window manager?

Do windows of all applications show this lag or only a certain category of applications?

Could it be that when certain applications are being closed, some file has to be written to or some database has to be updated?

What happens if you open your troublesome application via the terminal? Do you get any useful diagnostic information there?

I noticed in your other thread that your home folder has a lot of files!

Hello vasa1, thanks for answering. I have delayed to answer because I have been trying to fix the problem.

I will try to answer your questions:

The "weird"behaviour window is de details one: applications-->system tools -->preferences --> details, in any of the tabs, when I try to close window, I click on button and the window closes after about 2 minutes, if hay try to close by means of alt+f4 or alt, spacebar y select close,  the behaviour is the same: Delay for about 2 minutes. If I minimize or maximize the window the behaviour is snap and normal. 

I had a similar behaviour in software centre window but when I renamed my hidden .config file in /home/clara this behaviour was fixed only in this window.

I use metacity, and assure my self to put "metacity" in gconf-editor: /desktop/gnome/session/required_components/windowmanager
also, with dconf editor in /org/gnome/desktop/wm/preferences/button-layout I have menu:minimize,maximize,close

For launching the "details" window from xterm I need to know which is the name of the process, but unfortunately I don't know which is . Do you know what is it?

I have seen my .xsession-errors file and here it is the output:
```
openConnection: connect: No existe el archivo o el directorio
cannot connect to brltty at :0
Script para ibus iniciada en run_im.
init: indicator-bluetooth main proceso terminado, reiniciando
init: indicator-application main proceso terminado, reiniciando
init: indicator-bluetooth main proceso terminado, reiniciando
init: indicator-application main proceso terminado, reiniciando
init: indicator-bluetooth main proceso terminado, reiniciando
init: indicator-application se está reiniciando demasiado rápido, detenido
init: indicator-bluetooth main proceso terminado, reiniciando
init: indicator-bluetooth main proceso terminado, reiniciando
init: indicator-bluetooth main proceso terminado, reiniciando
init: indicator-bluetooth main proceso terminado, reiniciando
init: indicator-bluetooth main proceso terminado, reiniciando
init: indicator-bluetooth main proceso terminado, reiniciando
init: indicator-bluetooth main proceso terminado, reiniciando
init: indicator-bluetooth se está reiniciando demasiado rápido, detenido

```

Now, I am going to try to close the details window in the ubuntu unity desktop, I will report results later

Yes I have my /home/clara folder polluted wit a lot of files I will try to clean it but it scares me a little.

Regards

---

### Post by claracc on 2015-08-04
I have closed my session in gnome flashback and login in my ubuntu unity (default) desktop.

When I launch the "Details" window, it minimizes inmediatly on clicking the button, but when I click on close button, it appears a new window saying "This window no responds.¿Do you want to force the close or prefer to wait till close?" I click on forced close and it closes in mediatly ¿¿¿¿????.

Here it is the output of .xsession-errors file:

openConnection: connect: No existe el archivo o el directorio
cannot connect to brltty at :0
Script para ibus iniciada en run_im.
init: at-spi2-registryd main proceso terminado, reiniciando
init: at-spi2-registryd main proceso terminado, reiniciando
init: at-spi2-registryd main proceso terminado, reiniciando
init: at-spi2-registryd main proceso terminado, reiniciando
init: at-spi2-registryd main proceso terminado, reiniciando
init: at-spi2-registryd main proceso terminado, reiniciando
init: at-spi2-registryd main proceso terminado, reiniciando
init: at-spi2-registryd main proceso terminado, reiniciando
init: at-spi2-registryd main proceso terminado, reiniciando
init: at-spi2-registryd main proceso terminado, reiniciando
init: at-spi2-registryd se está reiniciando demasiado rápido, detenido

---

### Post by claracc on 2015-08-04
I have just found which is the application which launches the details window:

It is unity-control-center info

If I launch this application in a xterm, here it is what is obtained:

```
clara@clara1:~$ unity-control-center info
java version "1.7.0_79"
OpenJDK Runtime Environment (IcedTea 2.5.6) (7u79-2.5.6-0ubuntu1.14.04.1)
OpenJDK Server VM (build 24.79-b02, mixed mode)
(npviewer.bin:14592): GnomeShellBrowserPlugin-DEBUG: plugin loaded
java version "1.7.0_79"
OpenJDK Runtime Environment (IcedTea 2.5.6) (7u79-2.5.6-0ubuntu1.14.04.1)
OpenJDK Server VM (build 24.79-b02, mixed mode)
Terminado (killed)
clara@clara1:~$ *** NSPlugin Viewer  *** ERROR: rpc_end_sync called when not in sync!
*** NSPlugin Viewer  *** ERROR: rpc_end_sync called when not in sync!
*** NSPlugin Viewer  *** *** NSPlugin Viewer  *** *** NSPlugin Viewer  *** *** NSPlugin Viewer  *** *** NSPlugin Viewer  *** ERROR: rpc_end_sync called when not in sync!
ERROR: rpc_end_sync called when not in sync!
ERROR: rpc_end_sync called when not in sync!
*** NSPlugin Viewer  *** ERROR: rpc_end_sync called when not in sync!
ERROR: rpc_end_sync called when not in sync!
ERROR: rpc_end_sync called when not in sync!

```

I have click on close button in details window and the window saying this window no responds appears, the I click on forced close.

What does it means?, is it the NSPlugin Viewer the culprit?

Thanks in advance

---

### Post by vasa1 on 2015-08-04
When I run apt-cache show **unity-control-center**, the depends or recommends do not list anything with **java** or **icedtea** or **nsplugin**.

And I don't think any basic Unity/GNOME program needs java or icedtea.

When you moved to 14.04 was it a clean install or an upgrade?

Do you really need NSPlugin Viewer? Where did you get it from? It seems to be a "wrapper" of some sorts.

And here's someone with the same (?) rpc error: [http://www.len.ro/work/xubuntu-14-04-trusty-tahr/](http://www.len.ro/work/xubuntu-14-04-trusty-tahr/)
```
*** NSPlugin Viewer *** ERROR: rpc_end_sync called when not in sync!
```

---

### Post by claracc on 2015-08-04
Well Vasa1, you are right, culprits of delaying the close action of details windows are nspluginviewer and nspluginwrapper.

I have tried to remove them and certainly, details window close inmediatly but now, it takes a long time delay to launch, please see the errors given on running unity-control-center-info in xterm without the plugins:


```
clara@clara1:~$ unity-control-center info
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
*** NSPlugin Wrapper *** ERROR: failed to execute NSPlugin viewer
*** NSPlugin Wrapper *** ERROR: failed to initialize plugin-side RPC client connection
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.4.4/src/npw-wrapper.c:3556):invoke_NP_Initialize: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
*** NSPlugin Wrapper *** ERROR: failed to execute NSPlugin viewer
*** NSPlugin Wrapper *** ERROR: failed to initialize plugin-side RPC client connection
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.4.4/src/npw-wrapper.c:3556):invoke_NP_Initialize: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
*** NSPlugin Wrapper *** ERROR: failed to execute NSPlugin viewer
*** NSPlugin Wrapper *** ERROR: failed to initialize plugin-side RPC client connection
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.4.4/src/npw-wrapper.c:3556):invoke_NP_Initialize: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
*** NSPlugin Wrapper *** ERROR: failed to execute NSPlugin viewer
*** NSPlugin Wrapper *** ERROR: failed to initialize plugin-side RPC client connection
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.4.4/src/npw-wrapper.c:3556):invoke_NP_Initialize: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
*** NSPlugin Wrapper *** ERROR: failed to execute NSPlugin viewer
*** NSPlugin Wrapper *** ERROR: failed to initialize plugin-side RPC client connection
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.4.4/src/npw-wrapper.c:3556):invoke_NP_Initialize: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
*** NSPlugin Wrapper *** ERROR: failed to execute NSPlugin viewer
*** NSPlugin Wrapper *** ERROR: failed to initialize plugin-side RPC client connection
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.4.4/src/npw-wrapper.c:3556):invoke_NP_Initialize: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
*** NSPlugin Wrapper *** ERROR: failed to execute NSPlugin viewer
*** NSPlugin Wrapper *** ERROR: failed to initialize plugin-side RPC client connection
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.4.4/src/npw-wrapper.c:3556):invoke_NP_Initialize: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
*** NSPlugin Wrapper *** ERROR: failed to execute NSPlugin viewer
*** NSPlugin Wrapper *** ERROR: failed to initialize plugin-side RPC client connection
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.4.4/src/npw-wrapper.c:3556):invoke_NP_Initialize: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
*** NSPlugin Wrapper *** ERROR: failed to execute NSPlugin viewer
*** NSPlugin Wrapper *** ERROR: failed to initialize plugin-side RPC client connection
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.4.4/src/npw-wrapper.c:3556):invoke_NP_Initialize: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
*** NSPlugin Wrapper *** ERROR: failed to execute NSPlugin viewer
*** NSPlugin Wrapper *** ERROR: failed to initialize plugin-side RPC client connection
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.4.4/src/npw-wrapper.c:3556):invoke_NP_Initialize: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
sh: 1: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found
*** NSPlugin Wrapper *** ERROR: failed to execute NSPlugin viewer
*** NSPlugin Wrapper *** ERROR: failed to initialize plugin-side RPC client connection
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.4.4/src/npw-wrapper.c:3556):invoke_NP_Initialize: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))

```

This is the output when nspluginviewer ans nspluginwrapper are installed and I launch unity-control-center info:

```
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libjavaplugin.so: undefined symbol: _ZTVN10__cxxabiv120__si_class_type_infoE
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libjavaplugin.so: undefined symbol: _ZTVN10__cxxabiv120__si_class_type_infoE
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libjavaplugin.so: undefined symbol: _ZTVN10__cxxabiv120__si_class_type_infoE
*** NSPlugin Wrapper *** ERROR: failed to initialize plugin-side RPC client connection
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.4.4/src/npw-wrapper.c:3556):invoke_NP_Initialize: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
(npviewer.bin:9910): GnomeShellBrowserPlugin-DEBUG: plugin loaded

```

In the meantime, I get remove openjdk7 and icedtea plugin in case the problem would be related to them and install oracle java jre.

This ubuntu 14.04 is certainly upgraded from ubuntu precise 12.04 one month ago.

What could I do to solve the problem?

---

### Post by vasa1 on 2015-08-04
> **claracc said:**
> ...
What could I do to solve the problem?
@claracc, I'm not at all an expert in troubleshooting in such depth. Plus, I don't use Unity. I will PM someone who uses Unity now to look at your problem :)

---

### Post by claracc on 2015-08-04
> **vasa1 said:**
> @claracc, I'm not at all an expert in troubleshooting in such depth. Plus, I don't use Unity. I will PM someone who uses Unity now to look at your problem :)

Thak you very much for your help vasa1.

I add the output of running unity-control-center info in a xterm, knowing that I have installed nspluginviewer and nspluginwrapper, as you know, I have to force the close of the no responding window.

```
lara@clara1:~$ unity-control-center info
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libjavaplugin.so: undefined symbol: _ZTVN10__cxxabiv120__si_class_type_infoE
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libjavaplugin.so: undefined symbol: _ZTVN10__cxxabiv120__si_class_type_infoE
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libjavaplugin.so: undefined symbol: _ZTVN10__cxxabiv120__si_class_type_infoE
*** NSPlugin Wrapper *** ERROR: failed to initialize plugin-side RPC client connection
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.4.4/src/npw-wrapper.c:3556):invoke_NP_Initialize: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
(npviewer.bin:13400): GnomeShellBrowserPlugin-DEBUG: plugin loaded
*** NSPlugin Viewer  *** ERROR: rpc_end_sync called when not in sync!
*** NSPlugin Viewer  *** ERROR: rpc_end_sync called when not in sync!
Terminado (killed)
clara@clara1:~$ *** NSPlugin Viewer  *** ERROR: rpc_end_sync called when not in sync!
*** NSPlugin Viewer  *** *** NSPlugin Viewer  *** *** NSPlugin Viewer  *** *** NSPlugin Viewer  *** ERROR: rpc_end_sync called when not in sync!
*** NSPlugin Viewer  *** ERROR: rpc_end_sync called when not in sync!
ERROR: rpc_end_sync called when not in sync!
ERROR: rpc_end_sync called when not in sync!
ERROR: rpc_end_sync called when not in sync!
^C

```

Regards

---

### Post by vasa1 on 2015-08-05
You could also read this article: [https://bryanquigley.com/uncategorized/debug-performance-issues-with-strace](https://bryanquigley.com/uncategorized/debug-performance-issues-with-strace)
> Have you ever been asked why is this program running so slowly?  Or why does it take 15 seconds to startup?

Strace might be the tool for you.  It’s a system call tracer which let’s you see what this program is requesting from the system.

---

### Post by claracc on 2015-08-09
Well, it is a configuration problem which I supposse occur when upgraded from 12.04 to 14.04 with configuration files in my /home folder.

It affects to evolution (takes a lot to boot, and also if it is running and I logout from session clicking on menu  it takes a lot to close), the info window of unity-control-center (only) and software-center. 

It is related too with two plugins: nspluginwrapper and nspluginviewer. All the forementioned apps try to load them (I suppose some configuration file indicates it). 

When I have uninstalled completely these two plugins, the problem of delay on close button to do action disappears, but evolution or software-center or unity-control-center info try to load these plugins, so the apps take a lot of time to boot although finally run and work well.

¿Could someone indicates what configuration or .so file could be the culprit to remove or to configure properly?, or what more could I try... a reinstallation of 14.04?

Thanks in advance

@Vasa1 Thankyou for the link, but it is a little difficult for me

---

### Post by claracc on 2015-09-01
Well, at last, I decided to leave gnome-flashback desktop and log in in gnome shell desktop.

It is more user friendly than I had thought and more responsive in my laptop than flashback desktop 14.04. No problems with close button in details window any more.

Any case, software center is loading slowly and I have to force quit to close, but I think it is inherent to this software package in 14.04.

Gnome shell desktop rendering  has surprised my very favourably

---

