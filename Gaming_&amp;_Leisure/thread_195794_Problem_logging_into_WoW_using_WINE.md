---
title: "Problem logging into WoW using WINE"
date: 2006-06-13
forum: Gaming &amp; Leisure
---

### Post by sgtBiafra on 2006-06-13
Up until yesterday I had been running WoW on WINE. It seems that they've implemented some sort of hardware "survey" (a.k.a. mandatory, invasive scan) that happens when you connect to the authentication server. This is causing my machine to hang after alternating between the messages "Downloading" and "Submitting non-personal system specification".

Is anyone else experiencing this?

Granted it's weekly maintenance time for North America servers at the moment so you may not be able to login at the moment, but this happened all last night to me.

---

### Post by eqisow on 2006-06-13
You could try downloading the patch manually (if there is a patch). This may bypass the hardware survey. My other guess would be that there is some kind of setting in one of the WoW config files that tells it whether the survey has been completed or not. You could try mucking about in the config files and seeing what you can find.

Edit: FYI, Wine is currently crashing on me as well, it wasn't the other day. Cedega doesn't crash, but it doesn't show any servers up either. But server maintanence and patches are on Tuesday, right?

---

### Post by sgtBiafra on 2006-06-13
The 1.11 content patch is imminent which is the reason why they configured the Background Downloader app to pull down the patch files. I'm not sure if that was slated for release during today's maintenance.

I tried to find an indicator (i.e. Survey "1") for completion of both the download and execution of the survey but found none on a Windows machine that runs next to my Ubuntu box. Maybe I just missed it somehow.

I'll update this thread with anything I find... perhaps Blizzard might even reply to the thread I created on their Tech Support forum (though it's not likely). :D

---

### Post by eqisow on 2006-06-13
After you successfuly run the survey on your WIndows box, try pulling the config files from Windows to Ubuntu. If that works, you should post your config files.

BTW, on Cedega, where WoW isn't crashing, I have yet to see the hardware survey you speak of. Did it happen before or after server log in?

P.S. - Kind of unrelated, but the background downloader always annoyed me, and WoW runs fine if you rename it to BackgroundDownloader.exe_backup.

Edit: On my computer, Cedega and Wine run WoW from the same directory, so if I can get past the survey/patch on Cedega and get WoW to run on Wine after that, then I'll post my entire config folder as a zip file.

---

### Post by sgtBiafra on 2006-06-13
The survey runs just after you authenticate. There is a brief step that displays "Downloading" (that I believe pulls down Survey.mpq to the WDB folder) and then a following step "Submitting non-personal system specification". Under WINE, those steps seem to get repeated about 4 or 5 times before the WINE session just locks up.

Their utility annoyed me as well so I disabled it.  While it is running, you can go to File->Preferences... and turn off the 2nd option "Background downloading". Of course renaming the executable works just as well.

Hopefully this can be solved with a Config setting. Thanks for looking into it eqisow!

---

### Post by sgtBiafra on 2006-06-13
Found a fix for this (delete WDB/Survey.mpq and make the WDB folder read-only during login).

See this thread ([http://www.ubuntuforums.org/showthread.php?t=196199](http://www.ubuntuforums.org/showthread.php?t=196199)) for further discussion).

---

