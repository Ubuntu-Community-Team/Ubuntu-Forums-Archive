---
title: "Help With Installing Flight Gear?"
date: 2006-02-20
forum: Gaming &amp; Leisure
---

### Post by jimscullion on 2006-02-20
Hi,

I'm new to the whole *nix thing, and I find some of it quite daunting.  I've used Synaptic to install Flight Gear, but when I try to run it everything just locks up and I have to do a hard reboot.

The FG manual syas I need to set environment variables:

 "Before you can run FlightGear, you need to have a couple of environmental
variables set.

   • You must add /usr/local/share/FlightGear/lib to your LD_LIBRARY_PATH
   • FG_HOME must be set to the root of your FlightGear installation. e.g.
      /usr/local/share/FlightGear.
   • FG_ROOT must be set to the date directory of your FlightGear installation.
      e.g. /usr/local/share/FlightGear/data.
   • FG_SCENERY should be a list of scenery directories, separated by ”:”. This
      works like PATH when searching for scenery.
      e.g. $FG_ROOT/Scenery:$FG_ROOT/WorldScenery.

To add these in the Bourne shell (and compatibles):
LD_LIBRARY_PATH=/usr/local/share/FlightGear/lib:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH
FG_HOME=/usr/local/share/FlightGear
export FG_HOME
FG_ROOT=/usr/local/share/FlightGear/data
export FG_ROOT
FG_SCENERY=$FG_ROOT/Scenery:$FG_ROOT/WorldScenery
export FG_SCENERY

or in C shell (and compatibles):
setenv LD_LIBRARY_PATH=\
   /usr/local/share/FlightGear/lib:$LD_LIBRARY_PATH
setenv FG_HOME=/usr/local/share/FlightGear
setenv FG_ROOT=/usr/local/share/FlightGear/data
setenv FG_SCENERY=\
   $FG_HOME/Scenery:$FG_ROOT/Scenery:$FG_ROOT/WorldScenery"

My shell is set to bin/bash, and I have no idea how to do the above.  Can anyone help?

Thanks in advance.

Jim

---

### Post by Russ[] on 2006-02-22
I suggest compiling it by source. The version the repo has is old.

---

