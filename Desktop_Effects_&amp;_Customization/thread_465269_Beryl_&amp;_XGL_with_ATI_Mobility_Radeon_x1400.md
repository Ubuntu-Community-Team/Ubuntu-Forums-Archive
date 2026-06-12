---
title: "Beryl &amp; XGL with ATI Mobility Radeon x1400"
date: 2007-06-05
forum: Desktop Effects &amp; Customization
---

### Post by bated_breath on 2007-06-05
Hi All,

I have recently taken the proverbial plunge and installed XGL and Beryl on my Lenovo Z61m laptop.  On the whole  I am really impressed with the end result.  I have one issue which I am not sure that I understand to do with my system fonts.

After installing XGL and Beryl the fonts on the panels and application menu jumped from the normal 10pt to around 14/16pt. I tried playing with the Sytem > Preferences > Font but this had no effect on the system fonts, only the applications.  I also played with various options using: 

[INDENT]sudo dpkg-reconfigure fontconfig-config [/INDENT]

I have managed to kinda resolve this by adding the /usr/bin/gnome-settings-daemon to my session startup programs (System > Sessions > Startup Programs). I say "kinda" because the system font is now 8pt which I can live with.

Would be interested to know if this approach (ie loading the gnome settings daemon) is correct or is there another way to resolve this problem?

TIA

---

### Post by Darkjasper on 2007-06-05
You could install a emerald theme and change the font size in the emerald settings. That should fix the problem of your apps having weird font sizes.

---

### Post by kpolice on 2007-06-05
Yes loading the gnome-settings-daemon is correct, for some reason in some systems it doesn't start when you autostart bery so you have to do it manually.

---

### Post by bated_breath on 2007-06-06
> **kpolice said:**
> Yes loading the gnome-settings-daemon is correct, for some reason in some systems it doesn't start when you autostart bery so you have to do it manually.

Thank you for your reply.

Still doesnt explain why when I load the  gnome-settings-daemon my font sizes are now 8pt when they used to be 10pt before I installed Beryl.  Any ideas?

---

### Post by kpolice on 2007-06-06
gnome settings daemon will set the fonts according to what you set in the Font Preferences app that comes with gnome.

---

### Post by hkahwaji on 2007-06-07
Were you able to get Beryl working on Fiesty or Edgy. Please let me know the what instruction did you follow.

Thanks

---

### Post by bated_breath on 2007-06-11
> **hkahwaji said:**
> Were you able to get Beryl working on Fiesty or Edgy. Please let me know the what instruction did you follow.

Thanks

I have got it working on Edgy - try this url: [http://www.linux.org.mt/node/82](http://www.linux.org.mt/node/82) (there is a section "15. Beryl - fancy 3D desktop").

HTH

---

### Post by mtbsoft on 2007-07-29
> **hkahwaji said:**
> Were you able to get Beryl working on Fiesty or Edgy. Please let me know the what instruction did you follow.
I have a Dell Inspiron 9400 which has the ATI X1400 and I'm running 7.04 - I just used the following instructions to install Beryl completely successfully.

[http://www.linuxquestions.org/questions/showthread.php?t=555247](http://www.linuxquestions.org/questions/showthread.php?t=555247)

I too have noticed all the font sizes have increased - this doesn't appear to be a Beryl issue but an xlg issue as it is the same whether I start Beryl or not.  I've used the gnome-settings-daemon tip below and it seems to work well, thanks bated_breath.

Now for the noob question!  Can someone please tell me how to start Beryl automatically?  I guess I need to add an entry in the System > Sessions > Startup Programs but I'm damned if I can find the file to add to the new entry.  Help... please!

Edit: not to worry, I finally tracked down the necessary link for Beryl and it now starts automatically - just beautiful.

---

