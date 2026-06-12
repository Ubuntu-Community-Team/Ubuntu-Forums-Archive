---
title: "Gnome search can not be configured: Ubuntu 20.04"
date: 2020-06-11
forum: Desktop Environments
---

### Post by ubname on 2020-06-11
Hi,

using Ubuntu 20.04, I'd like to have search results only about files in my "Document" folder, so I disabled search for any other folder (Download, Home etc...),
but when I search using the super key, search results include files from every directory; also tried to restart but search is on for all folders even if you disable them,
is this a bug? Any way to fix ?

thanks.

---

### Post by vanadium on 2020-06-12
You could consider this a bug, but I think the reason is that these files you excluded from search are still present in the tracker index. That is not changed by changing the search preferences. The latter merely changes where tracker will pick up files in the future to index.

Unless someone has a better solution, you may need to delete the existing index and have tracker reindex. It should now only include the files from your new settings. I did not test, but following series of command should 1) stop all tracker services 2) delete the index and 3) restart all services, after which indexing will resume:

```

systemctl --user stop tracker-store.service tracker-miner-fs.service tracker-miner-rss.service tracker-extract.service tracker-miner-apps.service tracker-writeback.service
tracker reset --hard
systemctl --user start tracker-store.service tracker-miner-fs.service tracker-miner-rss.service tracker-extract.service tracker-miner-apps.service tracker-writeback.service

```

---

### Post by ubname on 2020-06-12
Hi,
I did some tests and what you describe is not what is happening, search settings are ignored, not because files are in the tracker system, also brand new files show up even if they are in a different folder (that should not be tracked).
I'll try using English,  maybe the tracker is confused by a different language/translations.

Just verified with English, Gnome search just does not work as it is supposed, any setting is simply ignored, you can only turn on search or turn off, any folder selection filtering is ignored.

---

### Post by tea for one on 2020-06-12
The package **gnome-search** is not available for 20.04. The last package was for 16.04.

How did you install it?

As an alternative, there is a reasonable search tool within Files (nautilus).

Simply, click on your Documents folder and use the Search icon (magnifier) in the top bar.

---

### Post by ubname on 2020-06-12
> **tea for one said:**
> The package **gnome-search** is not available for 20.04. 

Hi, I'm not talking about gnome-search package, I'm talking about searching with the Gnome shell,
in settings there is a search tab where you should be able to configure what to search.

---

### Post by tea for one on 2020-06-12
> **ubname said:**
> Hi, I'm not talking about gnome-search package, I'm talking about searching with the Gnome shell,
in settings there is a search tab where you should be able to configure what to search.

OK, I understand.

I simply use the search facility in Files because my search requirements are never too onerous.

---

