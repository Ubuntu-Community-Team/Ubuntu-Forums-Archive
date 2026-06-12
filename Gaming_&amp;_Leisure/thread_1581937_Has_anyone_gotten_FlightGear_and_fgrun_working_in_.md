---
title: "Has anyone gotten FlightGear and fgrun working in 10.04?"
date: 2010-09-25
forum: Gaming &amp; Leisure
---

### Post by cjmabry25 on 2010-09-25
I have tried and tried and tried. I've been compiling FlightGear from source and trying to get 2.0 to work for 4 or 5 hours, and I finally got it working with the PlayDeb .deb. Now to fgrun. I've tried compiling but on make I get, after some succesful things:

```
/fgrun_pty.Tpo"; exit 1; fi
g++ -DLOCALEDIR=\"/usr/local/share/locale\" -g -O2   -o fgrun  wizard.o wizard_funcs.o advanced.o advanced_funcs.o AirportBrowser.o AirportTable.o Fl_Table.o Fl_Table_Row.o Fl_OSG.o Fl_Heading_Dial.o main.o io.o fgfsrc.o logwin.o parkingloader.o settings.o util.o run_posix.o fgrun_pty.o -lsgmodel -lsgscreen -lsgprops -lsgxml -lsgdebug -lsgbvh -lsgmaterial -lsgmodel -lsgutil -lsgstructure -lsgprops -lsgtgdb -lsgmath -lsgmisc -lsgbvh -lsgio -lsgbucket -lsgmodel -lsgutil -lplibsg -lplibul -lplibnet -losgParticle -losgSim -losgViewer -losgGA -losgText -losgDB -losgUtil -losg -lOpenThreads -lfltk_gl -lpthread -lfltk -lGL -lXmu -lXt -lSM -lICE -lXi -lXext -lX11  -lm -lz -lutil -losgFX
/usr/bin/ld: cannot find -lsgbvh
collect2: ld returned 1 exit status
make[2]: *** [fgrun] Error 1
make[2]: Leaving directory `/usr/local/src/fgrun-1.5.2/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/local/src/fgrun-1.5.2/src'
make: *** [all-recursive] Error 1

```

And I'm stuck. Any suggestions? Also, when I run nice *terrasync -p 5500 -S -d "$HOME/fgfsScenery"* as stated to do here -[http://wiki.flightgear.org/index.php/TerraSync]("http://wiki.flightgear.org/index.php/TerraSync"), nothing happens, and I'm guessing it's because of the playdeb install. I ditched my succesful Arch install to get this working because I had no luck in Arch. I hope I can get it working haha

Thanks

**EDIT:** I realize this may not have been the best place to post this so I will post it elsewhere. Feel free to still answer thought.

---

### Post by mickeoliver on 2010-09-26
I had a lot of trouble installing FlightGear myself, I could only find version 1.9. After hours of frustration, I eventually realized that fgfs 2.0 was available in the synaptic package manager. (I've only used ubuntu for a week) Is there a reason why you want to compile from source?

---

### Post by Sealbhach on 2010-10-01
I use Brisa's compilation script. Works like a charm for me in 10.04. 

[http://wiki.flightgear.org/index.php/Scripted_Compilation_on_Linux_Debian/Ubuntu](http://wiki.flightgear.org/index.php/Scripted_Compilation_on_Linux_Debian/Ubuntu)

Just download the script, make it executable and run it. The script does everything else.

.

---

