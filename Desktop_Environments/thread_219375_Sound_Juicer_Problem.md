---
title: "Sound Juicer Problem"
date: 2006-07-19
forum: Desktop Environments
---

### Post by Athanasius on 2006-07-19
When I try to rip a cd into wav format I get an error message that says: > Sound Juicer could not extract this CD.
Reason: Could not link pipeline
How can this be fixed?

---

### Post by swamytk on 2006-07-20
Other mutlimedia applications are working properly? I mean mp3,ogg files played, you are getting audio? if it is ok, Check with System->Preference->Multimedia Selector, try with alternate settings.

---

### Post by StefanoCole on 2006-07-20
Hello Athanasius, I have exactly the same problem with Soundjuicer. I was not able to solve it, but I have found a backup solution using the program "cdparanoia" from terminal. For instance:

$cdparanoia -B && eject

will rip the current CD in the drive to the current directory, in separate WAV files.

Stefano

---

### Post by Athanasius on 2006-07-20
Thank you Stefano, I will try it.

---

### Post by Athanasius on 2006-09-16
Actually RipperX from the repository is great, it even encodes to mp3

---

