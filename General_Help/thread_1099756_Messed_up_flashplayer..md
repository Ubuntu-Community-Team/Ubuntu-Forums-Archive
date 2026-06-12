---
title: "Messed up flashplayer."
date: 2009-03-18
forum: General Help
---

### Post by Jerfo on 2009-03-18
Ok so this is the latest thing I've messed up, I was tying to update to flashplayer 10, Adobe's site said I should uninstall it first, and so I did, so the link they provide only downloads a file, doesn't provide information, and the file downloaded is a .tar.gz that only contains this a file called 'libflashplayer.so', I tried to get it through the download central and the information they provide include a file called 'flashplayer-installer' as well was the same .so file.

I can't do anything with the first file (at least not as far as my knowledge goes), as for the second one, it does provide information, but that one is for a 32bit architecture and therefore doesn't work... so, how on Earth do I get flashplayer 10 for 64 bit installed?

---

### Post by Vince4Amy on 2009-03-18
Move libflashplayer.so /home/yourusename/.mozilla/plugins, If you have more than one user you can move it to /usr/lib/firefox/plugins.

---

### Post by taurus on 2009-03-18
Is the libflashplayer.so for 32bit or 64bit?  You could just move it to /usr/lib/mozilla/plugins and restart firefox.

```
sudo mv libflashplayer.so /usr/lib/mozilla/plugins
ls -la /usr/lib/mozilla/plugins
```

---

### Post by Jerfo on 2009-03-19
Ohhh thank you very much! Now Flash is working wonders, no more 1 fps or lagging issues!

---

