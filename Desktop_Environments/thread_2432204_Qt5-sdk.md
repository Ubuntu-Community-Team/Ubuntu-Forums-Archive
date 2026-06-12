---
title: "Qt5-sdk"
date: 2019-11-28
forum: Desktop Environments
---

### Post by vidar-vidnes on 2019-11-28
Following a tutorial to build "Labtool" from ,embedded artists An older sw from 2016, I need qt5-sdk. However, it seems it is no longer available in the repository. 
The tutorial said to install qt5-sdk package but there is no such thing anymore. Could I add the repos from older Ubuntu versions and download qt5-sdk from there?

---

### Post by spjackson on 2019-12-01
I'm not sure which version of Ubuntu you are on. For 18.04 the following should be sufficient. The same list may also work with 19.
```

sudo apt install build-essential qttools5-dev-tools qt5-qmake qttools5-dev-tools-dev qtbase5-dev qtbase5-dev-tools

```

---

