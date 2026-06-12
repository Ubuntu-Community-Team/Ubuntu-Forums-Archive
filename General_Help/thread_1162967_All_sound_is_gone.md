---
title: "All sound is gone"
date: 2009-05-18
forum: General Help
---

### Post by stuart.reinke on 2009-05-18
I just noticed that my computer has no sound. 

It could have been this way for a while as I usually have the speakers off.

Last I remember, it worked before I decided to try and set up the Movie Player to play DVDs (Haven't been able to get that to work either)

I installed libdvdcss2 and Ubuntu Restricted extras.

I have removed both packages but no sound returned.

I'm not even sure installing those packages had anything to do with my sound loss.

Where do I begin to trouble shoot this problem?

Any and all help is appreciated.

---

### Post by fung on 2009-05-18
try this [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems) ?

---

### Post by DLG102282 on 2009-05-18
Have you check the volume manager to make sure it isn't on mute or the sound is turned all the way down?

---

### Post by stuart.reinke on 2009-05-18
DLG102282: Yes, checked that first.

Fung: Thanks for the link, I'll see if it helps.

thanks for the suggestions

---

### Post by stuart.reinke on 2009-05-18
Problem solved:

I found the control panel for various devices.  Master volume was on but pcm, line in, and cd were all on mute.

Learned something new today, thanks again for the help.

---

