---
title: "Boson crash"
date: 2006-07-12
forum: Gaming &amp; Leisure
---

### Post by shugie on 2006-07-12
Boson refuses to let me play a game. The main menu opens fine, but when it starts to load a mission I get a KDEcrash diaglog saying the I got a signal 11 (SIGSEGV). In the console I get a bunch of errors of missing sound files.

Boson Sound: ERROR: [bool BosonAudioAL::loadFileToBuffer(ALuint, const QString&)] alutLoadVorbis_LOKI failed for file /usr/share/apps/boson/themes/species/human/sounds/order_move_0.ogg
Boson Sound: ERROR: [void BoPlayObject::reload()] unable to load file /usr/share/apps/boson/themes/species/human/sounds/order_move_0.ogg
Boson Sound: WARNING: [virtual void BosonSound::addEventSound(const QString&, const QString&)] NULL sound /usr/share/apps/boson/themes/species/human/sounds/order_move_0.ogg for order_move
alsa_blitbuffer: Could not write audio data to sound device: Input/output error
ALSA lib pcm_direct.c:1136:(snd_pcm_direct_set_timer_params) unable to set timer parameters
KCrash: Application 'boson' crashing...

Thanks

---

### Post by Adrian_b on 2006-07-12
I think you're missing the ogg-vorbis codecs..
Do an 'sudo apt-cache search ogg vorbis' and then 'sudo apt-get install' the packages..

---

### Post by shugie on 2006-07-12
I have the vorbis codec libraries installed.

---

### Post by computx on 2006-09-19
I had this same problem. Installing libvorbis-dev fixed it for me.

---

### Post by MaximB on 2006-10-01
> **computx said:**
> I had this same problem. Installing libvorbis-dev fixed it for me.

ok, I'm in the middle of dependencies hell :
I want to install "libvorbis-dev"
synoptic says :
"libogg-dev:
  Depends: libogg0 (=1.1.3-0ubuntu3) but 1.1.3-2 is to be installed"
I don't see libogg0 1.1.3 to install.

what to do ?

---

### Post by MaximB on 2006-10-01
done.
by "force version".

---

### Post by cesarespcab on 2008-09-06
thanks!!! it fixed it for me too

---

