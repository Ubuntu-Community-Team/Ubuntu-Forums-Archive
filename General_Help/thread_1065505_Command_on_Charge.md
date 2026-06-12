---
title: "Command on Charge"
date: 2009-02-09
forum: General Help
---

### Post by dwieeb on 2009-02-09
Hi, I own an eeepc laptop. I removed Evolution from my computer because I use Gmail and don't need it, but whenever I plug in the power cord, a command is given that tries to launch Evolution and it gives an error message. Is there a way to edit the command when I plug in my power cord?

---

### Post by Shazaam on 2009-02-09
Just a guess but go to (silly as it sounds) System>Preferences>Sessions and see if there are any entries for Evolution. If there are any entries uncheck/remove them and see if that fixes the problem. Same with System>Administration>Services.

---

### Post by KeyserSoze93 on 2009-02-10
you could try tricking it:
```
sudo ln /bin/true /usr/bin/evolution
```

Then, when it tries to run evolution, it will just get a successful exit status and hopefully shut up.

---

### Post by dwieeb on 2009-02-11
Shazaam - There was an entry for it in Sessions, not for services. I removed it but problem still existed.
Keyser - Whatever that means, it worked :P

Thanks guys!

---

