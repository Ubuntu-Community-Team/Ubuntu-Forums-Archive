---
title: "The classic Totem problem..."
date: 2009-03-08
forum: General Help
---

### Post by pacificflows on 2009-03-08
After loading up some libdvdcss packages into the terminal in order to get Totem to play commercial DVDs at all, the big labowski gives me an error message that says, "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?" at about six minuets into the film.

Can anyone please help? I am so close to being able to watch movies on Ubuntu. I should probably state that I'm a complete noob to the OS, so any jargon you may drop will fly over my head completely.

Thanks in advance for any help.

---

### Post by ad_267 on 2009-03-08
This page should contain everything you need to know: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

An important step is running this from a terminal:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Then Totem should be able to play any DVDs, but won't be able to navigate well or show the main menu.

VLC or Xine are probably better for DVD playback. I've found one DVD that Totem and VLC had problems with but Xine seemed to play without any issues.

---

### Post by pacificflows on 2009-03-09
Epic Fail.

Same problem.

That guide sucks.

---

### Post by ad_267 on 2009-03-09
Have you tried VLC or Xine?

---

