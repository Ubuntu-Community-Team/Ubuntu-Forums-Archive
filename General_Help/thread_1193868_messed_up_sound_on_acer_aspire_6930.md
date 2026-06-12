---
title: "messed up sound on acer aspire 6930"
date: 2009-06-22
forum: General Help
---

### Post by patmalcolm91 on 2009-06-22
Hi, i have an acer aspire 6930-6073. My sound worked mostly on a clean install (except the speakers stayed on when headphones were in and integrated mic didn't work). I was trying to fix these problems and came across this thread: [http://www.linlap.com/wiki/acer+aspire+6930]("http://www.linlap.com/wiki/acer+aspire+6930") and followed the instructions by francois. (search: "Monday 30 of March, 2009 [09:14:35]").

Before, my volume manager had many different controls and all of my speakers worked well. now, after installing the realtek driver, there is only the master and all sound comes out just one speaker.

my question is: is there anyway to "undo" what i've done and get back to the default sound settings for an ubuntu jaunty install? (i don't want to have to reinstall as i don't have the time) OR: is there another way to fix my sound problems? Thank you in advance for any help you can offer.

"lspci | grep -i audio" returns: 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

---

### Post by ashwindatye on 2009-08-31
I have the same model and the same F*-up with realtek. I lost the audio completely. I ended up re-installing. This time around I configured volume control properly (surround etc). Now all the speakers work properly inclusing the TUBA bass. ALso I am happy using the external mic which works fine.

---

### Post by patmalcolm91 on 2009-08-31
I've now got the speakers and tuba bass working (though they are a bit quiet). The only thing that needs fixed is the headphone jack, mic jack, and internal mic. the spdif jack does work.

Does your headphone jack and/or internal mic work? if so, could you somehow tell me what settings you're using. I'm not an expert, but if you could send the contents of /etc/modprobe.d/alsa-base.conf and your System->Preferences->Sound Settings as well as how your volume control dialog looks and any settings in that that might be helpful and how you "properly configured" your sound, i could see how my system differs from yours and maybe figure out how to fix mine.

Thank you in advance for any help you can provide.

Patrick

---

