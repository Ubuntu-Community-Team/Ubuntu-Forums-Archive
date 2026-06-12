---
title: "OpenGL2 with PCSX"
date: 2015-10-01
forum: Emulators
---

### Post by GeorgeLSpencer on 2015-10-01
I downloaded the driver for Pete's OpenGL2, extracted the files, but seem to be missing one of the required files. The documentation that came with the download says that there will also be a third file, but in this instance the file was missing. The PCSX program correctly identifies the graphics driver, but does not give a configuration screen. I tried copying the .cfg file into the .pcsx/plugins/cfg directory but this has no effect. Copying the file to the .pcsx or the .pcsx/plugins directories also have no effect. Has anyone found out where the .cfg file and the configPeteXGL2 program are supposed to be installed?

I have had limited success with PCSX. Many modern ROMS are protected and the SBI files do not appear to work with PCSX. The older games play reasonably, but I was hoping to learn a little more about plugins and play at full screen by installing the OpenGL2 driver. Unfortunately, this turned out to be somewhat problematic.

---

### Post by GeorgeLSpencer on 2015-10-09
Had little luck with configuring the drivers supplied by Peter as these use libgtk-1.2 and this is not easily installed any more. It would appear that ubuntu does not want us installing this software, even if it is required by some applications. I am running Ubuntu 14.04.3 and even linking the names to the more modern libraries only stopped the error messages, when the configuration application is run under terminal, it did not enable the configuration programs to run.

I was able to download the latests source code for PCSX-reloaded, and both 1.9.93 and 1.9.94 compiled on my computer. This involved a number of files from the Ubuntu Software Centre, the Synaptic Package Manager, and apt-get; however, the end result was definitely worth it. The latest versions of PCSX-reloaded will play more games than the commonly available ubuntu centre version. I have since found that these versions are available via launchpad, so I would suggest either of these as being an improvement on version 1.9.92.

---

