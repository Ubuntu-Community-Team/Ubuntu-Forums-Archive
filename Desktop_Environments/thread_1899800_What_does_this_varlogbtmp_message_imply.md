---
title: "What does this /var/log/btmp message imply?"
date: 2011-12-24
forum: Desktop Environments
---

### Post by arroy_0209 on 2011-12-24
I am using ubuntu 10.04 LTS and I am confused over an issue. I have created an icon on the panel for the log file viewer. Sometimes when I click on the icon, the message viewer opens with a message on top (inside a rectangular area) which states:
```

/var/log/btmp
The file is not a regular file or is not a text file. [CLOSE]

```
The above "close" is a button to be clicked so that the message disappears and then only I can watch the log files contents. I do not understand why this is displayed sometimes when I click the log file viewer icon on the panel and sometimes it is not displayed. 

In my previous installation, this was always displayed rather that being displayed at times and not other times, as it is now. Why is this happening and do I need to do anything about it?

---

### Post by Paddy Landau on 2011-12-24
I don't know why it's doing it, but I can guess.

Linux tries to work out the type of a file by its contents, not by its extension. I suppose that sometimes you try to open the file, and Linux sees that it is text; other times, perhaps while something is busy writing to it, the file seems to be some other type of file.

That's my guess. If it is working for you anyway, don't worry about it.

---

