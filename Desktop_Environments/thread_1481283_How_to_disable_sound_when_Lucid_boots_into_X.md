---
title: "How to disable sound when Lucid boots into X"
date: 2010-05-12
forum: Desktop Environments
---

### Post by cci[RR]us on 2010-05-12
Hi,

I would like to disable the start up sound when Lucid boots up and enters X. I have already unticked:

System, Administration, Login Screen: [ ] Play Login Sound

Yet I still get the login sound.

Please advise. Thank you!

---

### Post by utnubuuser on 2010-05-12
I'm not in Lucid at the moment, but is there a System>>Sound...

worst comes to worst, you could always locate and remove/replace the sound-file with a empty file.

---

### Post by cci[RR]us on 2010-05-13
> **utnubuuser said:**
> I'm not in Lucid at the moment, but is there a System>>Sound...

worst comes to worst, you could always locate and remove/replace the sound-file with a empty file.
I was there but found nothing that I could do to disable start up sound.

---

### Post by Tragos on 2010-05-13
*System -> Preferences -> Startup Applications*,
uncheck *GNOME Login Sound*.

---

### Post by infamous-online on 2010-05-13
> **Tragos said:**
> *System -> Preferences -> Startup Applications*,
uncheck *GNOME Login Sound*.

I was wondering, could you change the default sound to something else just wondering?

---

### Post by JustinR on 2010-05-13
Yes, when you click the GNOME Startup Sound from the Startup Programs window, click edit and replace the ubuntu startup sound file with your own sound.

---

### Post by cci[RR]us on 2010-05-14
> **Tragos said:**
> *System -> Preferences -> Startup Applications*,
uncheck *GNOME Login Sound*.
Thank you!!! It's amazing that there are so many possible locations to disable start up sound! It's a service now?!

---

### Post by infamous-online on 2010-05-14
What file formats must the audio be in order for Ubuntu to use it? I just tried an 3 second mp3 and it didn't work?

---

### Post by kio_http on 2010-05-15
Under startup settings, disable GNOME login sound. This should work.

---

