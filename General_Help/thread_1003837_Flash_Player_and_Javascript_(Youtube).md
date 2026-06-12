---
title: "Flash Player and Javascript (Youtube)"
date: 2008-12-06
forum: General Help
---

### Post by sam1993 on 2008-12-06
I installed Adobe Flash Player using Synaptic, but when I visit Youtube and got to watch a video it says that I either have Javascript turned off or, an old version of Adobe Flash Player. As I have installed the latest Adobe Flash Player available on Synaptic, it cant be an old version of Adobe Flash Player, I must have Javascript turned off. How do I turn Javascript on?

---

### Post by dmancini on 2008-12-06
I had this same issue.  It is one of the few things that i have been able to fix myself.  I simply restarted my computer after installing adobe flash player 10.

---

### Post by robomoon on 2008-12-19
Regarding Flash and Javascript on Xubuntu Hardy: There was Firefox 3. So I tried various Flash-plugins by usage of Synaptic and Package Manager. Nothing in Flash (together with Javascript) worked to enable the uploading of files to archives like cyberev.org and immortalspace.com or, for comparison, the multi file uploader at scribd.com/upload or other storage portals. Wherever there was anything else but a single file uploader, there was no function in Javascript with Flash to open a file selection window for a file upload. With other Mozilla-based browsers, no multi file uploader too. So I removed Firefox 3 with apt-get and installed Firefox 2. No uploader. So I installed Flash from Adobe. There is Flash in "about:plugins", but still no function to open the file upload interface. Immortalspace.com requires Javascript enabled, no function for file uploading. Further, I turned off the software firewall, installed and booted KDE, and changed plugins in  /usr/lib/mozilla/plugins and /usr/lib/firefox/plugins where libflash-mozplugin.so was the last one before I gave up further efforts. Perhaps the missing function has something to do with applications I installed with AptOnCD or whatever.

---

