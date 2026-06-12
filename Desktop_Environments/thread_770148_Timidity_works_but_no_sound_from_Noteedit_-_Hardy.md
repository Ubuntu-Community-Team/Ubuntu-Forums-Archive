---
title: "Timidity works but no sound from Noteedit - Hardy"
date: 2008-04-27
forum: Desktop Environments
---

### Post by Patb on 2008-04-27
I have a "tailor-made" minimal Hardy install with Noteedit and Timidity.  While Timidity happily plays any midi file, I cannot get any sound when I try to play a score using Noteedit.  I have tried all combinations of sequencers and port options under the Noteedit sound menu but no luck.  Searches of the forums and Google have not revealed anything useful.  My sound card is not capable of hardware midi synthesis but it played scores fine using Noteedit under Gutsy.  

Any suggestions would be much appreciated.  For reference, here is a list of installed modules.  Cheers, Pat.

```
pat@ubuntulite:~$ lsmod | grep snd
snd_intel8x0           35356  0 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
```

---

### Post by Patb on 2008-04-29
Bump.  No hints?  

Cheers, Pat.

---

### Post by loell on 2008-04-29
and the timidity server is running before launching noteedit?

---

### Post by Patb on 2008-04-30
Yes Loell, it is.  Thanks for the suggestion.  

I suspect there is something I have not yet installed on my minimal install, but I cannot think what it might be.  I still have the 7.10 version on a dual-boot too, so I can compare the installed programs in each version but cannot see any differences of significance.  

Cheers, Pat.

---

### Post by loell on 2008-04-30
i'm not sure if this even relates,in standard install PulseAdiou is installed. though i really can't see how this would affect a minimal install.

---

### Post by Patb on 2008-05-01
Thanks again Loell.  Tried pulseaudio but still no sound from Timidity.  

Cheers, Pat.

---

### Post by john_navarro on 2008-05-23
I have the same issue - very frustrating

---

### Post by wgroth2 on 2008-08-17
Me too. Anyone?

---

### Post by GoLinux on 2008-12-08
Hello all,

in case you still need help, I was able to make it work on my Ubuntu 8.10 Intrepid Ibex.

1. Launch Timidity++ as server with this command from Terminal:

timidity -iA -B2,8 -Os -EFreverb=0 2>&1 &

2. Open NoteEdit, go to Setting -> Configure -> Sound and select "Timidity port 0 128:0", "Apply" then "OK"

Now pressing the play button it should work.

Found this here:

[http://alsa.opensrc.org/index.php/Timidity#How_to_use_Timidity_with_Noteedit](http://alsa.opensrc.org/index.php/Timidity#How_to_use_Timidity_with_Noteedit)

Rock On!!! :guitar:

---

### Post by hansum_rahul on 2008-12-12
Well stuff works with **[SIZE="4"]sudo[/SIZE]**

---

### Post by lloydkuhnle on 2009-02-22
> **GoLinux said:**
> Hello all,

in case you still need help, I was able to make it work on my Ubuntu 8.10 Intrepid Ibex.

1. Launch Timidity++ as server with this command from Terminal:

timidity -iA -B2,8 -Os -EFreverb=0 2>&1 &

2. Open NoteEdit, go to Setting -> Configure -> Sound and select "Timidity port 0 128:0", "Apply" then "OK"

Now pressing the play button it should work.

Found this here:

[http://alsa.opensrc.org/index.php/Timidity#How_to_use_Timidity_with_Noteedit](http://alsa.opensrc.org/index.php/Timidity#How_to_use_Timidity_with_Noteedit)

Rock On!!! :guitar:

Ok, Thanks for the solution to this.
Now, why do I have to reconfigure the sound every time I open up NoteEdit?
Why doesn't the configure hold forever, until I change it?

---

### Post by hg21 on 2009-05-15
[QUOTE=GoLinux;6334754]Hello all,

in case you still need help, I was able to make it work on my Ubuntu 8.10 Intrepid Ibex.

1. Launch Timidity++ as server with this command from Terminal:

timidity -iA -B2,8 -Os -EFreverb=0 2>&1 &

2. Open NoteEdit, go to Setting -> Configure -> Sound and select "Timidity port 0 128:0", "Apply" then "OK"

Now pressing the play button it should work.

Found this here:

[http://alsa.opensrc.org/index.php/Timidity#How_to_use_Timidity_with_Noteedit](http://alsa.opensrc.org/index.php/Timidity#How_to_use_Timidity_with_Noteedit)
=======================================================

Thanks this worked for me but I have puzzles.

When I tried Noteedit without timidity as server I had timidity port 128:0 to 3 showing in Noteedit which didn't work.

With timidity as server I still had timidity port 128:0 to 3 which still didn't work but also port 130:0 to 3 which did
  
Even more puzzling, my Roland piano, connected via USB, hadn't worked for MIDI playback before but does with timidity as server?!?

(I'm using Jaunty/Kubuntu)

---

### Post by drop2it on 2010-09-07
If Timidity plays midi files but nted does not, run

CODE:

timidity -iA -B2,8 -Os -EFreverb=0 2>&1 &

in Terminal.

Open nted. Edit>Preferences>Configure Midi Out>128:0 Timidity

Leave echo midi checked.

This works well, but must be done every time the system is booted. A nice work-around can be found using System>Preferences>Start Up Applications.

Simply click "Add" and insert the above code in the command box. Add an appropriate title, eg, nted midi support, and you're good to go.

---

### Post by Jack Brown on 2010-10-08
works!

In lucid & nted (1.9.16 by Joerg Anders)

 1. install timidity (if not yet installed)
 2. Open terminal and run: timidity -iA -B2,8 -Os -EFreverb=0 2>&1 &

terminal will display something like: Requested buffer size 2048, fragment size 1024
ALSA pcm 'default' set buffer size 2048, period size 680 bytes
TiMidity starting in ALSA server mode
Opening sequencer port: 131:0 131:1 131:2 131:3

and a flashing cursor

3. go to nted menu: EDIT->Preferences > configure midi out
- i think u can select any of the ports displayed on your terminal.  i tried: 131:0 Timidity and 131:1 Timidity, both worked.

now the next step would be to make it work the first time nted is run on the session (ideally not on startup: keeping it lean.)  

how do we do that?

---

