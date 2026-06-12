---
title: "Rosegarden4 Error"
date: 2005-05-24
forum: Desktop Environments
---

### Post by Crunch on 2005-05-24
Hi.  I am fairly new to linux and Ubuntu.  When starting rosegarden4 from the command line I get this;


geargolem@ubuntu:~$ rosegarden
kbuildsycoca running...
rosegarden: main: Showing startup logo
geargolem@ubuntu:~$ rosegarden (sequence manager): getSequencerPlugins - getting plugin information
PluginFactory::instance(ladspa): creating new LADSPAPluginFactory
[/home/geargolem/.ladspa] [/usr/local/lib/ladspa] [/usr/lib/ladspa]
rosegarden (sequencer): SequencerMmapper : setting size of /tmp/kde-geargolem//rosegarden_sequencer_timing_block to 91012
rosegarden (sequencer): SequencerMmapper : mmap size : 91012 at 0xb640f000
rosegarden (sequencer): SequencerMmapper::init()
rosegarden (sequencer): Registering with DCOP server
Rosegarden 1.0 - AlsaDriver - alsa-lib version 1.0.8

JackDriver::initialiseAudio - JACK server not running
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
rosegarden (sequence manager): got 66357 pieces of plugin data at GUI side
Profiler : id = querying plugins - elapsed = 1150ms CPU,  2.743357000R real
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up

and from there it keeps repeating the last message.  I tried $sudo modprobe snd-seq-midi upon direction from the people at .freenode but it didn't help.  What must I do to correct this?

---

### Post by 23meg on 2005-05-24
it seems you haven't installed [JACK](http://jackit.sourceforge.net/) or have to launch it before launching soundgarden. if it's not installed, enter "sudo apt-get install jackd" in a terminal window to install it. then you'll have to configure it with command line parameters or qjackctl, which is a gui frontend for JACK.

---

