---
title: "Change emerald theme back to default"
date: 2010-06-05
forum: Desktop Environments
---

### Post by lol768 on 2010-06-05
Have recently installed emerald and downloaded and imported a new theme, however I know want to go back to the default theme (I believe it is called Beryl Red). How would I go about doing this?

---

### Post by Barafu Albino Cheetah on 2010-06-05
Find it and install. Emerald theme management in Lynx is really buggy. It used to work better years ago.

---

### Post by lol768 on 2010-06-05
As far as I know this theme is not available for download. I have tried removing the current theme but it is still used.

---

### Post by lol768 on 2010-06-05
I decided to try and reinstall emerald to see if this would remove the theme, but this did nothing so I randomly removed anything to do with emerald on my computer and now the windows are broken and the control box floats above the window.

Is there a way to remove all of the configuration files for it and start again?

Edit: Going to re-install kubuntu now - hopefully that will fix it :)

---

### Post by Barafu Albino Cheetah on 2010-06-05
You could try locating and deleting emerald's folder in your /home. It couldn't store themes anywhere else.

---

### Post by lol768 on 2010-06-06
I should have thought of that, thanks. Anyway fixed it by reinstalling kubuntu (3rd reinstall this week :)) . It looks as if the themes manager just overwrites the image files in the /home/user/.emerald/theme directory, and even doing a complete unuinstall in synaptic didn't delete those files.

Thanks again

---

### Post by pallgone on 2010-07-30
wow, drastic measurements...
next time try copying the default theme from /usr/share/emerald/theme to ~/.emerald/theme

cheers,
pall

PS: you know, gnu/linux isn't windows, you don't have to reinstall everything when something breaks. usually you can fix it up. unlike windows which totally lacks transparency, so you often can't find out where or why the stuff is broken

---

