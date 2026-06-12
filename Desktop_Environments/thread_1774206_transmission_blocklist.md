---
title: "transmission blocklist?"
date: 2011-06-03
forum: Desktop Environments
---

### Post by de1337ed on 2011-06-03
Hey guys,
I'm trying to install a blocklist, and I looked online on how to do so. I can't find the .config folder they keep asking for. I can't find any blocklist folder at all. I even tried the given /var/ paths. Can anyone guide me in how to install blocklists for transmission? thank you.

---

### Post by mikewhatever on 2011-06-03
There is nothing to install really. In transmission, open Edit->Preferences->Privacy, add the URL from below and click Update.
```
http://list.iblocklist.com/?list=bt_level1&fileformat=p2p&archiveformat=gz
```

---

### Post by de1337ed on 2011-06-03
> **mikewhatever said:**
> There is nothing to install really. In transmission, open Edit->Preferences->Privacy, add the URL from below and click Update.
```
http://list.iblocklist.com/?list=bt_level1&fileformat=p2p&archiveformat=gz
```

hmm, I couldn't find a place to put that url. It just says enable blocklist and it says 'contains 224,994 rules', does this mean that its already doing it?:guitar:

---

### Post by mikewhatever on 2011-06-03
Yes, that means there is a blocklist enabled.
You've not mentioned the version of Transmission (*buntu) you use so it's hard to tell why you lack the interface option. Perhaps some of the older versions didn't have the URL field.

---

### Post by elliotstan on 2011-06-18
This was exactly what I was after. Thanks for answering the other guys question. :p

---

### Post by Enigmapond on 2011-06-18
> **mikewhatever said:**
> There is nothing to install really. In transmission, open Edit->Preferences->Privacy, add the URL from below and click Update.
```
http://list.iblocklist.com/?list=bt_level1&fileformat=p2p&archiveformat=gz
```

HEY! Thank you for this mikewhatever!

---

### Post by altjx on 2011-07-26
> **mikewhatever said:**
> There is nothing to install really. In transmission, open Edit->Preferences->Privacy, add the URL from below and click Update.
```
http://list.iblocklist.com/?list=bt_level1&fileformat=p2p&archiveformat=gz
```

Thank you for this dude. I wish this was more easier to find on google. Just wanted to know what blocklist it used to use prior to making it an editable textbox.

---

### Post by mikewhatever on 2011-07-27
> **altjx said:**
> Thank you for this dude. I wish this was more easier to find on google. Just wanted to know what blocklist it used to use prior to making it an editable textbox.

There used to be a blocklist at [http://update.transmissionbt.com/level1.gz](http://update.transmissionbt.com/level1.gz), but apparently, not any more.

---

