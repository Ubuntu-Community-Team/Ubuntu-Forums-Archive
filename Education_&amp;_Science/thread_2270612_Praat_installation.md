---
title: "Praat installation"
date: 2015-03-24
forum: Education &amp; Science
---

### Post by Sigma1 on 2015-03-24
Hello,
Has anybody managed to get praat working properly on 14.04? Praat is phonetics software included in the packages, site here: [http://www.fon.hum.uva.nl/praat/](http://www.fon.hum.uva.nl/praat/), which suggests it ought to work, but while it installs there is 1) no sound, and there are 2) no phonetics symbols showing (although I've installed the required fonts).
I did get things working a while ago, on 11.04, but cannot remember the procedure.
Any help would be appreciated.

---

### Post by Sigma1 on 2015-03-24
Update: I have got the sound working, following advice here, [https://bbs.archlinux.org/viewtopic.php?id=177296](https://bbs.archlinux.org/viewtopic.php?id=177296), in particular just pasting this
```
options snd_hda_intel enable=0,1
options snd slots=snd_hda_intel 
options snd_hda_intel index=0
```
into /etc/modprobe.d/alsa-base.conf and rebooting.
I am still stuck regarding the fonts, however...

---

### Post by Sigma1 on 2015-03-24
Second update: it looks like the phonetic symbols are working. However, the BNC TextGrid transcriptions I was downloading from [http://www.phon.ox.ac.uk/AudioBNC](http://www.phon.ox.ac.uk/AudioBNC) include specific ASCII codes to correspond to IPA symbols (correspondence here: [http://www.phon.ox.ac.uk/files/docs/BNC_transcription_alphabet.html](http://www.phon.ox.ac.uk/files/docs/BNC_transcription_alphabet.html)). Typing the symbols into Praat is an art in itself: most of the non alphabetic symbols are accessed using coding conventions standard to Praat, apparently (e.g.\ew for schwa cf. [http://www.fon.hum.uva.nl/praat/manual/Phonetic_symbols__vowels.html](http://www.fon.hum.uva.nl/praat/manual/Phonetic_symbols__vowels.html) or [http://www.fon.hum.uva.nl/praat/manual/Phonetic_symbols__consonants.html](http://www.fon.hum.uva.nl/praat/manual/Phonetic_symbols__consonants.html))
I hope this might help somebody else in a similar predicament.

---

