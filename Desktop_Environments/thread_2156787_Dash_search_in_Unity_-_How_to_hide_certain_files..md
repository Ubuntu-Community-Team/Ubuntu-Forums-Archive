---
title: "Dash search in Unity - How to hide certain files."
date: 2013-06-23
forum: Desktop Environments
---

### Post by larekare on 2013-06-23
Whenver I press the button to the top left, certain files appear. These files are some videos that I would not like people to see immediatly after they borrow my laptop yet I still want them saved on my hard drive. 

So I Googled a little and people kept reffering to the privacy settings so I had a look at the privacy settings and did the following:

*"Delete history" in "recent items"
*"Selected don't record activity for" "video"
*I added the folder in which I keep the videos to the "don't record activity list"
*I switched record activity to Off. 

Yet the files still either show up right away or as soon as I type in a letter which is in the filename in one of the files.

What should I be doing? 

I'm on Ubuntu 13.04.

---

### Post by stinkeye on 2013-06-23
Dash also uses "locate" during searches to find files even if they're not logged by Zeitgeist.
You can turn off the "locate" search in dconf-editor.
or
Using terminal:
Get current setting...
```
gsettings get com.canonical.Unity.FilesLens use-locate
```

Disable use-locate search...
```
gsettings set com.canonical.Unity.FilesLens use-locate false
```

To reset to default (true)...
```
gsettings reset com.canonical.Unity.FilesLens use-locate
```

The changes happen immediately.

You may want to clear recent files as well when lending your laptop.
This command will do that...
```
echo > ~/.local/share/recently-used.xbel
```

---

