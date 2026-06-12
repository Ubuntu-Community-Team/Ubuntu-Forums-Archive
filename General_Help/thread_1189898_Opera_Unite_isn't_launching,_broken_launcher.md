---
title: "Opera Unite isn't launching, broken launcher?"
date: 2009-06-17
forum: General Help
---

### Post by DemonParasite on 2009-06-17
I recently downloaded Opera Unite, and was using it until I booted up my computer this morning. Clicking on the launcher does nothing, and I am not sure what to do to fix it. I have tried re-installing Opera Unite, and it still doesn't work. Under the launcher properties, the command is "opera %u", should it be something else? I am thinking maybe fixing a broken launch command will help.

---

### Post by DemonParasite on 2009-06-17
I have tried uninstalling Opera completely, re-installing the pre-Unite build, and it STILL won't work. I think I'm using a bad launcher. Can someone please help?

---

### Post by DemonParasite on 2009-06-17
I tried launching it from the terminal, and get "/home/smith/lib/opera/10.00/opera: 1: Syntax error: word unexpected (expecting ")")", what does this mean?

---

### Post by DemonParasite on 2009-06-17
It's not working with Opera 9.64 either.

---

### Post by Arup on 2009-06-17
Do a sudo apt-get --purge remove opera, go to your home folder, press ctrl+h and delete opera folder, install Opera, should work fine.

---

### Post by DemonParasite on 2009-06-17
I removed with apt-get, and then re-installed it using the .deb file from their site, but it did not install the .opera folder, and now there isn't one. Do I have to re-do this and install with apt-get?

---

### Post by DemonParasite on 2009-06-17
I've re-installed it with apt-get and there still isn't a .opera folder in ~/

---

### Post by DemonParasite on 2009-06-17
I fixed it now, I had to go and redirect Opera so that it would launch from the appropriate version of the binaries.

---

### Post by pglucas68 on 2009-07-11
How did you do this?  I'm not sure what redirecting opera to launch from the appropriate directories.

---

### Post by pglucas68 on 2009-07-11
Thanks, this worked for me.

---

