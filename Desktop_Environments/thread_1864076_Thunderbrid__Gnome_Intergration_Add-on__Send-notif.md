---
title: "Thunderbrid / Gnome Intergration Add-on / Send-notify"
date: 2011-10-18
forum: Desktop Environments
---

### Post by oliv66 on 2011-10-18
Hi all, 

I am under Ubuntu 11.10 with Gnome Shell 3. I use Thunderbird 7.0.1 with gnome integration add-on. 

With Send-notify I have  an icon onto the notification panel.These build up over time and are a pain to clear out each requiring a right click and the selection of remove from the context menu. If you've just logged into your email for the first time after your holidays this is a nightmare. It is also the case  just because you receive a lot of messages.

How could I remove all the messages? I haven't found any setting to fix it.

Thanks for your help,

Olivier

---

### Post by crdlb on 2011-10-18
See this review for an explanation of the problem: [https://addons.mozilla.org/en-US/thunderbird/addon/gnome-integration/reviews/314931/](https://addons.mozilla.org/en-US/thunderbird/addon/gnome-integration/reviews/314931/)

[Another review]("https://addons.mozilla.org/en-US/thunderbird/addon/gnome-integration/reviews/316008/") gives a clever workaround that you can use until the extension is fixed. Create a wrapper script, ~/bin/transient-notify-send ```
#!/bin/bash
notify-send --hint int:transient:1 "$@"
```
Then make it executable (chmod +x ~/bin/transient-notify-send), and set the full, expanded path instead of notify-send in the extension's preferences.

---

### Post by oliv66 on 2011-10-19
thanks a lot for your quick reply.

---

