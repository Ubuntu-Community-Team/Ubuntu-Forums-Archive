---
title: "Adding a Program to Launch on startup"
date: 2009-02-15
forum: General Help
---

### Post by deamon_knight on 2009-02-15
I'm having difficulty setting up Fluidsynth to launch on startup. Frome terminal, I can start Fluidsynth with " fluidsynth /usr/share/sounds/sf2/Unison.SF2 " . Once done, the fluidsynth server starts and I can pass midi to it. The results of "pmidi -l" are:
 Port     Client name                       Port name
 14:0     Midi Through                      Midi Through Port-0
128:0     FLUID Synth (6028)                Synth input port (6028:0)



Before fluidsynth is started "pmidi -l" results:
 Port     Client name                       Port name
 14:0     Midi Through                      Midi Through Port-0

I tried to add fluidsynth to System>Preferences>Sessions with the following command: /usr/bin/fluidsynth  /usr/share/sounds/sf2/Unison.SF2

However, Fluidsynth is not loaded at startup. Any suggestions on what I am doing wrong?

---

