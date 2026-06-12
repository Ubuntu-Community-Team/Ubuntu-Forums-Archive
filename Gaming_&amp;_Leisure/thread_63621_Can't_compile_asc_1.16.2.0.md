---
title: "Can't compile asc 1.16.2.0"
date: 2005-09-08
forum: Gaming &amp; Leisure
---

### Post by Titeuf on 2005-09-08
I'm trying to compile the latest version of advanced strategic command from sources.
I've installed every -dev package it requires, and configure runs fine.
But make gives an error:
```

g++ -I/usr/include/SDL -D_REENTRANT -Dsgmain -DNEWKEYB -I/usr/include/paragui -I/usr/include/freetype2 -I/usr/include/SDL -D_REENTRANT -I/usr/lib/sigc++-1.2/include -I/usr/include/sigc++-1.2 -g -O2 -Wno-sign-compare -funsigned-char -D_UNIX_ -D_SDL_ -o asc unitctrl.o soundList.o typen.o strtmesg.o stack.o spfst.o sgstream.o sg.o pd.o palette.o newfont.o network.o misc.o loadpcxc.o loaders.o loadbi3.o gui.o gamedlg.o dlg_box.o dialog.o controls.o building.o basestrm.o basegfx.o attack.o CLoadable.o Property.o PropertyGroup.o gameoptions.o Named.o astar2.o vehicletype.o buildingtype.o containerbase.o mapalgorithms.o viewcalculation.o gamemap.o password.o password_dialog.o replay.o research.o mapdisplay.o resourcenet.o dashboard.o ascstring.o graphicset.o vehicle.o buildings.o networkdata.o textfileparser.o terraintype.o objecttype.o textfiletags.o itemrepository.o stringtokenizer.o music.o messages.o paradialog.o textfile_evaluation.o containerbasetype.o messagedlg.o simplestream.o mappolygons.o prehistoricevents.o gameevents.o gameeventsystem.o gameevent_dialogs.o statisticdialog.o clipboard.o  ../../../source/libs/triangul/.libs/libtriangul.a ../../../source/ai/.libs/libai.a -L/usr/lib -L/usr/X11R6/lib ../../../source/libs/sdlmm/src/.libs/libSDLmm.a ../../../source/sdl/.libs/libsdl.a /usr/lib/libSDL_image.so -ltiff -lpng /usr/lib/libSDL_mixer.so /usr/lib/libvorbisfile.so /usr/lib/libvorbis.so /usr/lib/libogg.so /usr/lib/libsmpeg.so /usr/lib/libjpeg.so /usr/lib/libparagui.so -lvga /usr/lib/libphysfs.so /usr/lib/libexpat.so /usr/lib/libfreetype.so -lz -lstdc++ ../../../source/libs/bzlib/libbz2.a /usr/lib/libsigc-1.2.so /usr/lib/libSDL.so -laudio -lXt -lX11 -lXext /usr/lib/libaa.so -lncurses -lslang /usr/lib/libasound.so -lm -ldl -lpthread
/usr/bin/ld: cannot find -lvga
collect2: ld returned 1 exit status
make[5]: *** [asc] Fout 1
make[5]: Leaving directory `/home/titeuf/asc/asc-1.16.2.0/source/unix/asc'
make[4]: *** [all-recursive] Fout 1
make[4]: Leaving directory `/home/titeuf/asc/asc-1.16.2.0/source/unix/asc'
make[3]: *** [all-recursive] Fout 1
make[3]: Leaving directory `/home/titeuf/asc/asc-1.16.2.0/source/unix'
make[2]: *** [all-recursive] Fout 1
make[2]: Leaving directory `/home/titeuf/asc/asc-1.16.2.0/source'
make[1]: *** [all-recursive] Fout 1
make[1]: Leaving directory `/home/titeuf/asc/asc-1.16.2.0'
make: *** [all] Fout 2

```
So this gives an error, anyone know how to fix this ?

---

### Post by invalid on 2005-09-08
This looks more like a compiler issue, than a gaming issue - try that forum and you may get a better response.

Cheers,
Cb.

---

### Post by Harleen on 2005-09-08
The package libsvga1 provides the required libvga.so. I don't know, why asc should need this, because it's used for showing graphics in console mode, but installing it should solve your linker error.

---

### Post by Titeuf on 2005-09-08
[QUOTE=Harleen]The package libsvga1 provides the required libvga.so. I don't know, why asc should need this, because it's used for showing graphics in console mode, but installing it should solve your linker error.[/QUOTE]
Ok, thanks for that.

---

