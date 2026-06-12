---
title: "no sound, but no errors"
date: 2006-02-06
forum: Desktop Environments
---

### Post by chruiserc on 2006-02-06
i've got a problem with my soundsystem.

although audioplayers (totem, vlc) don't complain and seem to play files i throw at them, i can't hear anything; ubuntu's volumemeter doesn't say it plays sound, either.

the soundcard (fortemedia fm801) is alsa-driven and is correctly recognized at startup. (i've already had it working on a previous kubuntu installation)


any ideas where the sound gets lost?

---

### Post by LordBug on 2006-02-06
Best guess is your sound is muted in a mixer.  I've had this before.  Check the alsamixer settings on your outputs.

---

### Post by chruiserc on 2006-02-06
you're right; wave was muted. thanks.

---

