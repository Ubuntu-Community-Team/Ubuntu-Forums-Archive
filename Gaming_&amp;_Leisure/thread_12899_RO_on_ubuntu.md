---
title: "RO on ubuntu ?"
date: 2005-01-27
forum: Gaming &amp; Leisure
---

### Post by II_pretender_II on 2005-01-27
[COLOR=SlateGray]
Hey guys, I ws just wondering if anyones been succesfull on running ragnarok on ubuntu ?
Ragnarok is a MMORPG. [ [www.ragnarokonline.com](www.ragnarokonline.com) ]
I play on the indian server. [ [www.ragnarok.co](www.ragnarok.co) in ]
I was succesfull in getting the game to run on FC2 using wine. 
But then there were color corruptions an a whole lot of garbage :D.
Anyone got it to work on ubuntu ?  :!: 
[/COLOR]

---

### Post by fng on 2005-01-27
i suggest cedega for running windows games.  Haven't tried RO so i dont know if it works.

---

### Post by gn0me on 2005-05-11
I've currently got it running in Hoary with WINE.

But all the layers in the ddraw seem to flicker.. I mean, it works, but everything's like an epileptic fit.

- Installed Hoary
- Installed wine-20050419 from source
- Installed fglrx from synaptic
- Installed winetools to install the Windows Installer and stuff
- Installed Ragnarok Online..

```
################################################
# Ragnarok Online
# Attempts at a config by gn0me <me@gn0me.org>
################################################
[AppDefaults\\Setup.exe\\x11drv]
"Desktop" = "1024x768"          ; Video modes in the setup list..

[AppDefaults\\ragexe.exe\\x11drv]
"Managed" = "Y"
"Desktop" = "1024x768"
```
Made those changes, because you need a desktop for the setup.exe to detect possible resolutions or something.  And the Ragexe.exe doesn't NEED to be put in a desktop, but I do it because I'm cool like that.

Current problems:
- Crazy flickering on all the layers of the ddraw
```
err:ddraw:d3ddevice_lock_update Wrong surface type for locking !
err:ddraw:d3ddevice_unlock_update Wrong surface type for locking !
err:ddraw:d3ddevice_lock_update Wrong surface type for locking !
err:ddraw:d3ddevice_unlock_update Wrong surface type for locking !
fixme:ddraw:Main_DirectDraw_WaitForVerticalBlank (0x77c7e890)->(flags=0x00000001,handle=(nil))

.. Spammed over and over.
```
- TTF fonts don't seem to want to work, even though they're in the ~/.wine/c/windows/fonts directory.  Not a huge deal, just aesthetics.

---

### Post by ldoria on 2005-06-01
Hi guys,

I'm just a newbie at linux and I use Hoary but I can't make ragnarok works on ubuntu.
I use a via s3 unichrome and I've downloaded some packages from debian to install, because I can't find the right drive at synaptic.
So I got xlibmesa-gl1-dri-trunk_2005.02.08-1_i386.deb, drm-trunk-module-src_2005.02.08-1_all, xserver-xfree86-dri-trunk_2005.02.08-1_i386 but I couldn't install through dpkg. I always have the same error.

luciana@Garfield:~/Desktop$ sudo dpkg -i xlibmesa-gl1-dri-trunk_2005.02.08-1_i386.deb
(Lendo banco de dados ... 71439 arquivos e diretórios atualmente instalados.)
Descompactando xlibmesa-gl1-dri-trunk (de xlibmesa-gl1-dri-trunk_2005.02.08-1_i386.deb) ...
Leaving `diversion of /usr/X11R6/lib/libXxf86vm.so.1.0 to /usr/X11R6/lib/libXxf86vm-no-dri-trunk.so.1.0 by xlibmesa-gl1-dri-trunk'
Leaving `diversion of /usr/X11R6/lib/libXxf86vm.so.1 to /usr/X11R6/lib/libXxf86vm-no-dri-trunk.so.1 by xlibmesa-gl1-dri-trunk'Leaving `diversion of /usr/X11R6/lib/libXxf86vm.so to /usr/X11R6/lib/libXxf86vm-no-dri-trunk.so by xlibmesa-gl1-dri-trunk'
Leaving `diversion of /usr/X11R6/lib/libGL.so.1.2 to /usr/X11R6/lib/libGL-no-dri-trunk.so.1.2 by xlibmesa-gl1-dri-trunk'
Leaving `diversion of /usr/X11R6/lib/libGL.so.1 to /usr/X11R6/lib/libGL-no-dri-trunk.so.1 by xlibmesa-gl1-dri-trunk'
Leaving `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/libGL-no-dri-trunk.so.1.2 by xlibmesa-gl1-dri-trunk'
Leaving `diversion of /usr/lib/libGL.so.1 to /usr/lib/libGL-no-dri-trunk.so.1 by xlibmesa-gl1-dri-trunk'
dpkg: erro processando xlibmesa-gl1-dri-trunk_2005.02.08-1_i386.deb (--install):
 tentando sobrescrever `/usr/X11R6/bin/xdriinfo', que também está no pacote xbase-clients
Erros foram encontrados durante processamento de:
 xlibmesa-gl1-dri-trunk_2005.02.08-1_i386.deb

someone has any idea how to install this package?

Tks a lot.

---

