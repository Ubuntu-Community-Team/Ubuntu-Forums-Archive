---
title: "Get KDE to open shell scripts with bash by default"
date: 2013-07-08
forum: Desktop Environments
---

### Post by Stonecold1995 on 2013-07-08
It use to be that shell scripts would be run by bash when double clicked in Dolphin (or when "kde-open script.sh" is run), but now for some reason it opens it by default in a text editor.  How can I change this back to the way it was?  My scripts in ~/.kde/Autostart are no longer running because KDE tries to open them with Kate upon login, which somehow causes the rest of KDE to lock up.

I tried right-clicking, going to Properties>General>File Type Options>General and adding bash as the default program to use, but that doesn't seem to work...

EDIT: I'm an idiot, I forgot that I was experimenting with the noexec mount option.  Also I still forget how to mark threads as solved or delete threads. :/

---

