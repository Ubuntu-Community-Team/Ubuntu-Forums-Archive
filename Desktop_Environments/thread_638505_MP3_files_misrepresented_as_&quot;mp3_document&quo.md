---
title: "MP3 files misrepresented as &quot;mp3 document&quot;, give errors on double click - Fix"
date: 2007-12-12
forum: Desktop Environments
---

### Post by Tweenk on 2007-12-12
There is a strange and recurring problem in GNOME about file associations in Nautilus. Something (I haven't traced the guilty package or application) is changing the MIME type of MP3 files from "audio/mpeg" to "application/x-extension-mp3", which prevents them from being opened from Nautilus by double-clicking them (there is a security warning instead). This is caused by a bogus MIME database entry. Here are the steps needed to fix this:
- Open you home folder
- Show hidden files (Ctrl+H)
- Go to <your home directory>/.local/share/mime/packages
- Open the file Override.xml with a text editor
- There should be an entry for a mime type "application/x-extension-mp3". Delete or comment out this entry (it's delimited by <mime-type ...> ... </mime-type>). If there are no other entries, you can also delete the entire file.
- In a terminal, run:
```

update-mime-database ~/.local/share/mime

```
- Log out and back again.
The problem should be fixed by now.

---

