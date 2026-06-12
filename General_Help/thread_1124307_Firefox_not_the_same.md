---
title: "Firefox not the same"
date: 2009-04-13
forum: General Help
---

### Post by eutu on 2009-04-13
I booted up my pc and ubuntu did a disk check now firefox will not work properly. It opens to the ubuntu start page and will not let me save my home page all my bookmarks are gone and i can not import any bookmarks.
It also does not display any thing in the addres bar. I tried using synnaptic to completely remove firefox and reinstall but same proplem.

---

### Post by lovinglinux on 2009-04-13
This sounds like a corrupted profile.

Run the following command in the terminal:

```
firefox - P
```

Create a new profile, then go to your bookmarks backup folder on old profile at *~/.mozilla/firefox/*******/bookmarkbackups* and copy the newest .json file from there to the corresponding folder on your new profile.

Then open Firefox using the new profile and try to restore the bookmarks backup.

You could also try to install [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109) extension on your current setup and backup the bookmarks, the preferences and other stuff individually, then restore them to a new profile

---

