---
title: "I do not understand the google repositories."
date: 2011-05-25
forum: Desktop Environments
---

### Post by sefs on 2011-05-25
Here are the google repositories
```

deb http://dl.google.com/linux/deb/ stable non-free
deb http://dl.google.com/linux/chrome/deb/ stable main
deb http://dl.google.com/linux/talkplugin/deb/ stable main
deb http://dl.google.com/linux/earth/deb/ stable main

```

Google says that when I install an application, say the google chrome browser, that it will magically install the repo for me to keep it update.  This is true.

After doing this, I had a look at /etc/apt/sources.list, but the google repo for chrome is nowhere to be seen at all.

However if I go into synaptic and look at the repo list in there sure enough I can see the google for chrome in there.  Not only that, it is unchecked meaning it is disabled.  Yet in this state somehow ubuntu detects new updates from the google chrome repository.

Exactly how does this work?

---

### Post by tgm4883 on 2011-05-25
> **sefs said:**
> Here are the google repositories
```

deb http://dl.google.com/linux/deb/ stable non-free
deb http://dl.google.com/linux/chrome/deb/ stable main
deb http://dl.google.com/linux/talkplugin/deb/ stable main
deb http://dl.google.com/linux/earth/deb/ stable main

```

Google says that when I install an application, say the google chrome browser, that it will magically install the repo for me to keep it update.  This is true.

After doing this, I had a look at /etc/apt/sources.list, but the google repo for chrome is nowhere to be seen at all.

However if I go into synaptic and look at the repo list in there sure enough I can see the google for chrome in there.  Not only that, it is unchecked meaning it is disabled.  Yet in this state somehow ubuntu detects new updates from the google chrome repository.

Exactly how does this work?

/etc/apt/sources.list is for standard Ubuntu repositories.

The /etc/apt/sources.list.d/ contains .list files for each 3rd party repo

---

### Post by PhilGil on 2011-05-25
Not every repository you add using a is written to the /etc/apt/sources.list file. In Debian, I have a folder called /etc/apt/sources.list.d that can also contain references to repositories - there's probably something similar in Ubuntu. I expect you'll find your Google repo in a similar folder.

As far as why it's not checked in Synaptic... not sure about that one.

---

### Post by sefs on 2011-05-25
Aha!  That's it.  Thanks very much.

---

