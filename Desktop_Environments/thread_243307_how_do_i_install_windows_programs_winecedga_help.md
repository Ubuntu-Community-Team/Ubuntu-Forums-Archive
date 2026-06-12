---
title: "how do i install windows programs wine/cedga help"
date: 2006-08-24
forum: Desktop Environments
---

### Post by aceofskies04@comcast.net on 2006-08-24
Ok im trying to install the metacafe client for windows. so i got wine and installed metacafe. But then it said it required ie6 to run so i went and downloaded ie6 and installed it but it wouldnt open for me it would open the box but then would basicly freeze. Ao then i tried cedega but i dont know how to install programs with cedega.... so my question is can some one help me install ie6 and metacafe on my system with wine/ or cedaga

---

### Post by zxee on 2006-08-24
Wine can be fussy. Have you gone to the winehq website? You may want to check this page out: [http://www.winehq.com/site/docs/wineusr-guide/config-wine-main](http://www.winehq.com/site/docs/wineusr-guide/config-wine-main)
At least try to run winecfg. I've been playing around with a recent release of wine-not sure which version comes with apt-get. The version I'm using is Wine 0.9.19
If you find gui easier try running winefile from the terminal it will open up a gui that you can use to launch programs with. Hope that helps.

---

### Post by aceofskies04@comcast.net on 2006-08-24
well how do i install program with wine

---

### Post by zxee on 2006-08-24
> **aceofskies04@comcast.net said:**
> well how do i install program with wine

From a terminal do > winecfg there's an add program tab in the small gui window that opens.

---

### Post by aceofskies04@comcast.net on 2006-08-24
do i add the .exe

---

### Post by zxee on 2006-08-24
in the terminal there is commandline completion. Which means you only need to partially type in the comand/filename just press the tab key and the full filename will be inserted. Sorry long answer but wine will need the executable so yes the exe is required. I told you the previous stuff because it's better to just partially type and then press tab to see if wine is even reading the correct directory.
Once you get it installed you can run > winefile from which you can run the app you installed. Hope that helps.

---

