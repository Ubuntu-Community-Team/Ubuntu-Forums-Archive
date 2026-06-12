---
title: "Change default applications in Lubuntu"
date: 2010-10-28
forum: Desktop Environments
---

### Post by Matt Harrison on 2010-10-28
I'm using Lubuntu and I cant figure out how to change the default applications used.

I have (Preferences -> Preferred Applications) in the menu and that lets me set Web Browser and Mail client. I have that set to Chromium, however any links I click open in Opera. I want these to open in Chromium, but I'm not sure how to set that.

Thanks for any help.

---

### Post by ubunterooster on 2010-10-28
Start Chromium, click the tool icon and then options. Under "Basic"  click "Make Chromium my default browser"

---

### Post by Matt Harrison on 2010-10-28
It says in red "Chromium cannot determine or set the default browser."

---

### Post by cavalier911 on 2010-10-28
```
rj@lubuntu:~$ sudo update-alternatives --config x-www-browser
There are 2 choices for the alternative x-www-browser (providing /usr/bin/x-www-browser).

  Selection    Path                       Priority   Status
------------------------------------------------------------
* 0            /usr/bin/opera              90        auto mode
  1            /usr/bin/chromium-browser   40        manual mode
  2            /usr/bin/opera              90        manual mode

Press enter to keep the current choice[*], or type selection number:
``` 

I would choose 1 then press enter to make chromium-browser the default.

See man update-alternatives for more information.

---

### Post by Matt Harrison on 2010-10-28
Thanks cavalier911 that is exactly the tool I was looking for.

---

### Post by inearlygaveup on 2012-08-18
Thanks cavalier911 - I needed to change the default Chromium Browser to Firefox, as any links clicked on in KeepassX opened Chrome.

Thanks for the info

---

