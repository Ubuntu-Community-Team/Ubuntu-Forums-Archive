---
title: "Installing rezlook...help"
date: 2009-06-20
forum: General Help
---

### Post by akrchstn on 2009-06-20
I'm using this [fluxbox]("http://thrynk.deviantart.com/art/Calla-for-fluxbox-47546045") theme and it says I need a gtk theme with it so I downloaded the [gtk theme]("http://thrynk.deviantart.com/art/Calla-47545886") and extracted it. I have a emerald theme inside of it which I can install fine and a folder called "calla". I moved the folder to my apperence>themes menu and it installed fine but then I get [this error]("http://img132.imageshack.us/img132/3507/callarezlook.png"). The Rezlook file that I downloaded was a .deb so I assumed there was no problems with it. Any help?

---

### Post by akrchstn on 2009-06-20
Anybody?

---

### Post by oldos2er on 2009-06-20
Did you try logging out and logging back in? Or a reboot?

---

### Post by akrchstn on 2009-06-20
I put the theme folder "Calla" in usr/share/themes to see if that would make a difference (I tried before rebooting) and now I want to delete it and just drag the "Calla" folder to my themes window and reboot but I don't have permission to delete the file so I go to terminal and put in ```
sudo rm /usr/share/themes/calla
``` and it says ```
rm: cannot remove `/usr/share/themes/calla': No such file or directory

```

---

### Post by akrchstn on 2009-06-20
Well I gave up on fluxbox and I got that file removed also, but I still need help with the gtk theme using rezlook

---

### Post by akrchstn on 2009-06-20
Okay, I found out how to install rezlooks using this ```
./configure --prefix=/usr
```But it said I needed gtk 2.8 so I went to go get gtk 2.8. Went into terminal and put ```
cd gtk+-2.8.20
./configure
``` and it spit out this ```
No package 'glib-2.0' found
No package 'atk' found
No package 'pango' found
No package 'cairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```I went to go find those packages. I started with atk, downloaded it and did my ./configure and it said ```
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error:
*** GLIB 2.0.0 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/. If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.
```So I said just skip that one for now. Went onto the pango package, did my ./configure etc. And it spit out this ```
checking for X... no
configure: WARNING: X development libraries not found
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for FONTCONFIG... configure: WARNING: No fontconfig found, skipping tests for FreeType and Xft
checking Carbon/Carbon.h usability... no
checking Carbon/Carbon.h presence... no
checking for Carbon/Carbon.h... no
checking for CAIRO... configure: error: *** Didn't find any of FreeType, X11, ATSUI or Win32.
*** Must have at least one backend to build Pango.
```Again I just said skip it for now and went onto the cairo package, put in my ./configure etc and it gave me this ```
cking for cairo's Microsoft Windows backend... 
checking whether cairo's Microsoft Windows backend could be enabled... no (requires a Win32 platform)
checking for cairo's Microsoft Windows font backend... 
checking whether cairo's Microsoft Windows font backend could be enabled... no (requires a Win32 platform)
checking for cairo's PNG backend... 
configure: WARNING: Could not find libpng in the pkg-config search path
checking whether cairo's PNG backend could be enabled... no
configure: error: requested PNG backend could not be enabled
```Basically I'm just going in a circle, somebody please help.

---

