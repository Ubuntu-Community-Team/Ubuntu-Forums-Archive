---
title: "ALSA Settings Cannot Be Saved"
date: 2005-06-08
forum: Desktop Environments
---

### Post by palsyboy on 2005-06-08
I've tried playing with alsactl, and of course, alsaconf isn't available.  I've used alsactl as root and as a normal user.  No matter what, everytime I log in, I have to run alsamixer to set unmute the Tone setting on my Audigy so that I can control bass and treble on the fly via the Sound Mixer applet.

Can someone please point me in the right direction?

---

### Post by dejitarob on 2005-06-08
Just for the sake of checking, how are you "using alsactl"?

---

### Post by palsyboy on 2005-06-09
Good question.  As a normal user, I ran alsamixer and set everything the way I want it.  I then ran "alsactl store" and logged out.  Upon logging back in, my savings were not set.  I ran alsamixer as root and ran "alsactl store" as root, and that didn't work, either.

---

### Post by Seti on 2005-06-09
Check the manpage for alsactl. I'm not sure how to use -d as the debug flag. Also look at your /var/lib/alsa/asound.state. Permissions maybe?

---

### Post by dejitarob on 2005-06-09
sudo alsactl store worked for me on one of my boxes that needed it. Perhaps kmixer is overriding it?

---

### Post by palsyboy on 2005-06-11
[QUOTE=dejitarob]Perhaps kmixer is overriding it?[/QUOTE]
That's a great idea.  I was just about to test it out but I logged out of my normal user profile, and when I returned, the settings were preserved just fine.  It was a strange spontaneous fix, though the Sound Mixer applet was showing three more bars that I'd previously told it to hide.  I re-hid them and continued with my day.

Bizarre.  Maybe some random combination of package upgrades fixed it or something, because I sure as hell didn't do anything. :-k

Thanks for the help. :)

---

