---
title: "Firefox Bookmarks, Settings, etc. Disappear after Update"
date: 2009-01-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yakker.yak on 2009-01-10
If you've recently updated your Dell Ubuntu 8.04, you may have noticed that your bookmarks and other settings have disappeared.

To restore your settings, you need to do the following:

Open up Terminal (*Accessories->Terminal*)

Copy-and-paste the following, one line at a time, hit Enter after each line:
```
cd .mozilla
mv firefox web\ browser
```

(That's a forward slash followed by a space)

Close the Terminal

Start/Restart Firefox.

The above will simply rename your Firefox directory to the new name, which Firefox expects and where your Firefox user profile is stored.

Thanks feranick for tracking this down. More info [here]("https://bugs.launchpad.net/dell-mini/+bug/315723").

---

### Post by feranick on 2009-01-10
> **yakker.yak said:**
> If you've recently updated your Dell Ubuntu 8.04, you may have noticed that your bookmarks and other settings have disappeared.

To restore your settings, you need to do the following:

Open up Terminal (*Accessories->Terminal*)

Copy-and-paste the following, one line at a time, hit Enter after each line:
```
cd .mozilla
mv firefox web\ browser
```

(That's a forward slash followed by a space)

Close the Terminal

Start/Restart Firefox.

The above will simply rename your Firefox directory to the new name, which Firefox expects and where your Firefox user profile is stored.

Thanks feranick for tracking this down. More info [here]("https://bugs.launchpad.net/dell-mini/+bug/315723").

An alternative way to fix this is to create a symbolic link.

Browse "Home Folder"
View -> Show hidden Files
Open ".mozilla"
Right-click "firefox" -> Make link
Rename link "web browser"

This solution allows you to keep your folder named firefox, and have a "web browser" link to it. This will help in the future if dell decides to use firefox instead of the web browser branding.

---

