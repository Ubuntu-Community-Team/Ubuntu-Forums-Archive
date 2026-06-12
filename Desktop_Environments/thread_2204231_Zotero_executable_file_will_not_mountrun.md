---
title: "Zotero executable file will not mount/run"
date: 2014-02-07
forum: Desktop Environments
---

### Post by shuukazedojo on 2014-02-07
Hello. I just installed the new UbuntuGnome 13.10 (64bit) after a clean wipe of an old 12.04LTS install. Although the environment is different, I'm finding my way around. However, I'm having some issues installing Zotero. I downloaded the tar.bz2 file from their site and opened it with archive manager. There is no install button as might be available in 12.04 so I extracted the contents. There's an executable file called 'zotero' so I double clicked it and nothing happened. I right clicked and selected 'Run' but again nothing happened. Why am I not able to run this executable file? I looked for the File Manager Behavior settings, but I guess Files doesn't offer a File | Edit | ... menu setup?!?!?!?!? ((Would love to enable that, if possible)). Thank you in advance for the help on this one!

---

### Post by stinkeye on 2014-02-07
Don't use Zotero but isn't the easiest way to use as a firefox extension.

---

### Post by shuukazedojo on 2014-02-07
The idea is to use the extension in Firefox (or Chrome in my case) to add the citation data to a personal Zotero library. Then, when writing a paper, be able to pull it up and insert the citation. To do this, however, I need to install Zotero and the included Libreoffice plugin. Anyone else have ideas on why the file won't execute?

---

### Post by cybergalvez on 2014-02-12
> **shuukazedojo said:**
> Hello. I just installed the new UbuntuGnome 13.10 (64bit) after a clean wipe of an old 12.04LTS install. Although the environment is different, I'm finding my way around. However, I'm having some issues installing Zotero. I downloaded the tar.bz2 file from their site and opened it with archive manager. There is no install button as might be available in 12.04 so I extracted the contents. There's an executable file called 'zotero' so I double clicked it and nothing happened. I right clicked and selected 'Run' but again nothing happened. Why am I not able to run this executable file? I looked for the File Manager Behavior settings, but I guess Files doesn't offer a File | Edit | ... menu setup?!?!?!?!? ((Would love to enable that, if possible)). Thank you in advance for the help on this one!

First make sure that zotero runs (it runs on my set up so it should) by running it from a terminal window. Second the new default behaviour for is for shell files not to run when you double click them. To change that, click on the application title in the top bar, that should bring up a menu goto preferences > behavior and select "Ask each time"

that should get you what you need

---

