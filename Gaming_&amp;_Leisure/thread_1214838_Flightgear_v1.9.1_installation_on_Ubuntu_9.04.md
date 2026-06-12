---
title: "Flightgear v1.9.1 installation on Ubuntu 9.04"
date: 2009-07-16
forum: Gaming &amp; Leisure
---

### Post by caco on 2009-07-16
Hello everyone, please could someone help in posting a detailed instruction on how to get Flightgear v1.9.1 installed on ubuntu jaunty.
I presently have the Ubuntu official 1.0.0-3ubuntu1 installed but it is way behind in recent features updates...;)

Thanks in advance :D

[[IMG]http://brainstorm.ubuntu.com/idea/20470/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/20470/)

---

### Post by caco on 2009-07-17
Presently downloading source files for flightgear and it's dependencies.
Would try compiling these source files ... :confused: 
Info on failure or success later:)

---

### Post by Col-1023 on 2009-07-18
The good news is Flightgear 1.91 will be in Karmic, [https://launchpad.net/ubuntu/karmic/+package/flightgear](https://launchpad.net/ubuntu/karmic/+package/flightgear).

---

### Post by caco on 2009-07-18
Thank for the info.
I guess I've to have a little bit of patience then:D:popcorn:

---

### Post by caco on 2009-07-18
Good evening folks I am cleared to Flightgear v1.9.1 ... :D

I succeeded in getting flightgear v1.9.1 working in Jaunty, after a lot of failed attempts, that included the download_and_compile.sh script.

I simply followed the instruction found here [http://wiki.flightgear.org/index.php/Building_Flightgear_-_Debian]("http://wiki.flightgear.org/index.php/Building_Flightgear_-_Debian") :)

I ignored the "Add backports.org repository" part though

for OpenSceneGraph I used OpenSceneGraph-2.8.1.zip

I'm having problems with the fgrun part

Have fun with the improved spectacle ...

---

### Post by caco on 2009-07-24
I got fgrun compiled using fgrun-1.5.1.tar.gz.:P

I still can't run Map or Atlas, keep getting
... Failed to read palette file '/home/caco/fgfs/data/Atlas/Palettes/default.ap'

... Palettes::load: error loading palette file '/home/caco/fgfs/data/Atlas/Palettes/default.ap': failed to open file
Palettes::load: error loading palette file '/home/caco/fgfs/data/Atlas/Palettes/home/caco/fgfs/data/Atlas/Palettes/default.ap': failed to open file
/home/caco/fgfs/bin/Atlas: Failed to read palette file '/home/caco/fgfs/data/Atlas/Palettes/default.ap'

help :confused:

Please can someone upload a working copy of default.ap if possible

---

