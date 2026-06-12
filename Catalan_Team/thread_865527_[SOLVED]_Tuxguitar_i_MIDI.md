---
title: "[SOLVED] Tuxguitar i MIDI"
date: 2008-07-20
forum: Catalan Team
---

### Post by LitusMayol on 2008-07-20
Bones genteta!

A veure... tinc ordinador nou! I serà el primer ordinador per a casa meva que NOMÉS tindrà **Ubuntu**. Ara estava instal·lant els programes que estic més avessat a usar i m'he trobat amb un problema.

Jo utilitzo el **TuxGuitar** i ara l'he instal·lat. M'he baitxat el paquet *Ubuntu-x86 Binary Package *[d'aquí]("http://www.tuxguitar.com.ar/download.html")(el web oficial). La instal·lació ha seguit correctament. He engegat el programa i aparenment funcionava bé. I aleshores he premut per reproduir la partitura i em diu:

```
[CENTER]**Error**
MIDI System is unavailable[/CENTER]
```

No sé pas què ha fallat. Aquí teni el que apareix al terminal si obro el **TuxGuitar**, obro la partitura i dono al *Play*:

```
litus@mayolets-desktop:~$ tuxguitar
javax.sound.midi.MidiUnavailableException: Audio Device Unavailable
	at com.sun.media.sound.MixerSynth.implOpen(MixerSynth.java:165)
	at com.sun.media.sound.AbstractMidiDevice.doOpen(AbstractMidiDevice.java:144)
	at com.sun.media.sound.AbstractMidiDevice.open(AbstractMidiDevice.java:108)
	at org.herac.tuxguitar.player.impl.jsa.midiport.MidiPortSynthesizer.getSynthesizer(Unknown Source)
	at org.herac.tuxguitar.player.impl.jsa.midiport.MidiPortSynthesizer.open(Unknown Source)
	at org.herac.tuxguitar.player.base.MidiPlayer.loadPort(Unknown Source)
	at org.herac.tuxguitar.player.base.MidiPlayer.openPort(Unknown Source)
	at org.herac.tuxguitar.player.base.MidiPlayer.addPortProvider(Unknown Source)
	at org.herac.tuxguitar.gui.system.plugins.base.TGMidiPortProviderPlugin.addPlugin(Unknown Source)
	at org.herac.tuxguitar.gui.system.plugins.base.TGMidiPortProviderPlugin.setEnabled(Unknown Source)
	at org.herac.tuxguitar.gui.system.plugins.base.TGPluginList.setEnabled(Unknown Source)
	at org.herac.tuxguitar.gui.system.plugins.TGPluginManager.openPlugins(Unknown Source)
	at org.herac.tuxguitar.gui.TuxGuitar.displayGUI(Unknown Source)
	at org.herac.tuxguitar.gui.TGMain.main(Unknown Source)
javax.sound.midi.MidiUnavailableException: Audio Device Unavailable
	at com.sun.media.sound.MixerSynth.implOpen(MixerSynth.java:165)
	at com.sun.media.sound.AbstractMidiDevice.doOpen(AbstractMidiDevice.java:144)
	at com.sun.media.sound.AbstractMidiDevice.open(AbstractMidiDevice.java:108)
	at org.herac.tuxguitar.player.impl.jsa.midiport.MidiPortSynthesizer.getSynthesizer(Unknown Source)
	at org.herac.tuxguitar.player.impl.jsa.midiport.MidiSynthesizer.getChannels(Unknown Source)
	at org.herac.tuxguitar.player.impl.jsa.midiport.MidiSynthesizer.sendAllNotesOff(Unknown Source)
	at org.herac.tuxguitar.player.impl.jsa.sequencer.MidiSequencerImpl.reset(Unknown Source)
	at org.herac.tuxguitar.player.impl.jsa.sequencer.MidiSequencerImpl.stop(Unknown Source)
	at org.herac.tuxguitar.player.base.MidiPlayer.stop(Unknown Source)
	at org.herac.tuxguitar.player.base.MidiPlayer.stop(Unknown Source)
	at org.herac.tuxguitar.player.base.MidiPlayer.play(Unknown Source)
	at org.herac.tuxguitar.gui.actions.transport.TransportPlayAction.execute(Unknown Source)
	at org.herac.tuxguitar.gui.actions.Action$1.run(Unknown Source)
	at org.herac.tuxguitar.gui.helper.SyncThread$1.run(Unknown Source)
	at org.herac.tuxguitar.util.TGSynchronizer$TGSynchronizerTask.run(Unknown Source)
	at org.herac.tuxguitar.gui.TuxGuitar$1$1.run(Unknown Source)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:123)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3157)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2859)
	at org.herac.tuxguitar.gui.TuxGuitar.displayGUI(Unknown Source)
	at org.herac.tuxguitar.gui.TGMain.main(Unknown Source)
javax.sound.midi.MidiUnavailableException: Audio Device Unavailable
	at com.sun.media.sound.MixerSynth.implOpen(MixerSynth.java:165)
	at com.sun.media.sound.AbstractMidiDevice.doOpen(AbstractMidiDevice.java:144)
	at com.sun.media.sound.AbstractMidiDevice.open(AbstractMidiDevice.java:108)
	at org.herac.tuxguitar.player.impl.jsa.midiport.MidiPortSynthesizer.getSynthesizer(Unknown Source)
	at org.herac.tuxguitar.player.impl.jsa.midiport.MidiSynthesizer.getChannels(Unknown Source)
	at org.herac.tuxguitar.player.impl.jsa.midiport.MidiSynthesizer.sendAllNotesOff(Unknown Source)
	at org.herac.tuxguitar.player.impl.jsa.sequencer.MidiSequencerImpl.reset(Unknown Source)
	at org.herac.tuxguitar.player.impl.jsa.sequencer.MidiSequencerImpl.stop(Unknown Source)
	at org.herac.tuxguitar.player.base.MidiPlayer.stop(Unknown Source)
	at org.herac.tuxguitar.player.base.MidiPlayer.stop(Unknown Source)
	at org.herac.tuxguitar.player.base.MidiPlayer.play(Unknown Source)
	at org.herac.tuxguitar.gui.actions.transport.TransportPlayAction.execute(Unknown Source)
	at org.herac.tuxguitar.gui.actions.Action$1.run(Unknown Source)
	at org.herac.tuxguitar.gui.helper.SyncThread$1.run(Unknown Source)
	at org.herac.tuxguitar.util.TGSynchronizer$TGSynchronizerTask.run(Unknown Source)
	at org.herac.tuxguitar.gui.TuxGuitar$1$1.run(Unknown Source)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:123)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3157)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2859)
	at org.herac.tuxguitar.gui.TuxGuitar.displayGUI(Unknown Source)
	at org.herac.tuxguitar.gui.TGMain.main(Unknown Source)
org.herac.tuxguitar.player.base.MidiPlayerException: MIDI System is unavailable
	at org.herac.tuxguitar.player.base.MidiPlayer.play(Unknown Source)
	at org.herac.tuxguitar.gui.actions.transport.TransportPlayAction.execute(Unknown Source)
	at org.herac.tuxguitar.gui.actions.Action$1.run(Unknown Source)
	at org.herac.tuxguitar.gui.helper.SyncThread$1.run(Unknown Source)
	at org.herac.tuxguitar.util.TGSynchronizer$TGSynchronizerTask.run(Unknown Source)
	at org.herac.tuxguitar.gui.TuxGuitar$1$1.run(Unknown Source)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:123)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3157)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2859)
	at org.herac.tuxguitar.gui.TuxGuitar.displayGUI(Unknown Source)
	at org.herac.tuxguitar.gui.TGMain.main(Unknown Source)
Caused by: org.herac.tuxguitar.player.base.MidiPlayerException: MIDI System is unavailable
	at org.herac.tuxguitar.player.impl.jsa.midiport.MidiPortSynthesizer.check(Unknown Source)
	... 12 more


```

Perdoneu que us ho posi tot, però no sé diferenciar què és l'error del que és normal... :S


Merci a tots/es!


:guitar:

---

### Post by CarlesOriol on 2008-07-21
Insta&#320;la i configura el timidity

---

### Post by LitusMayol on 2008-07-21
Renoi Carles!

Curt, fàcil, ràpid i solucionat! 
Merci!

---

### Post by LitusMayol on 2008-07-21
Rectifico...

He reengegat l'ordinador  i al probar de reproduir la tablatura m'he trobat que m'apareixia el mateix missatge d'error. 

He executat un "*purge*" i un altre "*install*" al **timidity** i ara no funciona... **CarlesOriol** (o qui sigui) algú em pot ajudar a instal·lar i configurar correctament el **Timidity**?

Merci de nou!
(gràcies de totes maneres Carles)

---

### Post by orestesmas on 2008-07-22
A veure, hauries de tenir executant-se en segon pla un procés anomenat timidity. El tens? Per saber-ho, obre un terminal i escriu:
```

ps axf |grep timidity

```

T'hauria de sortir quelcom similar a això:
```

orestes@raimon:~$ ps axf |grep timidity
 6176 ?        S      0:00 /usr/bin/timidity -Os -iAD
 9718 pts/1    S+     0:00          \_ grep timidity

```

Si no et surt, o et surt diferent, avisa. Si això és correcte haurem de veure si funciona amb altres programes, i, si ho fa, aleshores serà cosa del TuxGuitar

---

### Post by LitusMayol on 2008-07-22
> **orestesmas said:**
> A veure, hauries de tenir executant-se en segon pla un procés anomenat timidity. El tens? Per saber-ho, obre un terminal i escriu:
```

ps axf |grep timidity

```

T'hauria de sortir quelcom similar a això:
```

orestes@raimon:~$ ps axf |grep timidity
 6176 ?        S      0:00 /usr/bin/timidity -Os -iAD
 9718 pts/1    S+     0:00          \_ grep timidity

```

Si no et surt, o et surt diferent, avisa. Si això és correcte haurem de veure si funciona amb altres programes, i, si ho fa, aleshores serà cosa del TuxGuitar


Mira **orestesmas** m'ha sortit això:
```
litus@mayolets-desktop:~$ ps axf |grep timidity
 6160 pts/0    S+     0:00          |                   \_ grep timidity
 5497 ?        S      0:00 /usr/bin/timidity -Os -iAD
litus@mayolets-desktop:~$ 

```

És normal?


Merci !;)

---

### Post by orestesmas on 2008-07-22
> **LitusMayol said:**
> Mira **orestesmas** m'ha sortit això:
```
litus@mayolets-desktop:~$ ps axf |grep timidity
 6160 pts/0    S+     0:00          |                   \_ grep timidity
 5497 ?        S      0:00 /usr/bin/timidity -Os -iAD
litus@mayolets-desktop:~$ 

```

És normal?


Si, tens el timidity executant-se en segon pla, a l'espera de ser utilitzat.

Com que això funciona, obre el TuxGuitar i mira a l'apartat "Settings" -> Sound que tinguis seleccionat com a sortida algun dels canals del Timidity (assegura't que no ho tens configurat a "MIDI Through" o quelcom així.

Ja diràs si funciona.

---

### Post by LitusMayol on 2008-07-22
Grandíssim Orestes: MERCI!

A "*Herramientas>Preferencias>Audio*" tenia posat "Java Sound Synthetizer"(o una cosa semblant) enlloc del **Timidity**.

Merci, ara ja funciona! ;)

---

