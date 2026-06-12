---
title: "GVim---Text not showing up?"
date: 2009-01-28
forum: General Help
---

### Post by Felixworks on 2009-01-28
I downloaded GVim from the repositories and when I fire it up and get past the main screen, the text is invisible.  In insert mode I can see the...blinky line and I can type, but the text is still invisible.  If I frantically highlight random lines, I can see the text for a split second.  What's up with this?  I've reinstalled it twice with the same results.

---

### Post by Felixworks on 2009-01-30
Bumppity.  No help?  I've searched through Google and much documentation but no help there either...

---

### Post by Neural oD on 2009-01-30
have u checked that your font colour is not the same as the background colour?

---

### Post by Felixworks on 2009-01-30
Yes I just checked that now.  It happens with any and every color font/background.

---

### Post by fulano on 2009-03-10
I'm seeing the same behavior on a newly installed 8.10.  I've tried uninstalling and reinstalling most of the vim packages in Synaptic, with the same results.  As noted in one of the few other posts I found about this, if you minimize and then maximize the gvim window the text reappears and then disappears when you go back into insert mode.  If you hold down the control+L keys you can see the text flickering.

This isn't a text color problem - changing the color scheme doesn't help.

---

### Post by fulano on 2009-03-12
In my case, at least, this turns out to have been an issue with the NVidia
96.43.xx driver, as mentioned in this thread:

[http://ubuntuforums.org/showthread.php?p=6230724#post6230724](http://ubuntuforums.org/showthread.php?p=6230724#post6230724)

which I found when I noticed a similar problem in OpenOffice.

Adding the line:

     Option "RenderAccel" "False"

the the "Device" section of my xorg.conf file fixed the problem in
both gvim and OpenOffice.

---

