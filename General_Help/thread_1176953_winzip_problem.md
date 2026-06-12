---
title: "winzip problem"
date: 2009-06-02
forum: General Help
---

### Post by Jae99 on 2009-06-02
I just booted ubuntu and went to create a .winzip archive. Why can I not split that archive when creating it even though its in the options?

[IMG]http://farm4.static.flickr.com/3414/3590346949_5afb152c2d.jpg?v=0[/IMG]

---

### Post by michy99 on 2009-06-02
Does Zip support split volumes? Try using RAR instead. You may have to install it if it is not already installed.

---

### Post by Jae99 on 2009-06-02
It must support split files because its one of the options. Is there an install I need?

---

### Post by michy99 on 2009-06-02
Archive Manager can use a lot of different formats. The options may not be supported in all formats. In your picture, the split option appears greyed out, which is why I wondered if it is supported in zip. When I select different formats, it seems to be choosable in some but not in others. You will probably have to use a different format if you need to split the archive.

---

### Post by Jae99 on 2009-06-02
OK, I see what you mean. But there should be a update for that. Also is there a command line manual for winzip? I downloaded winrar and it seems to support multi files and it was really easy to install.

[http://ubuntumanual.org/posts/100/how-to-install-winrar-in-ubuntu](http://ubuntumanual.org/posts/100/how-to-install-winrar-in-ubuntu)

Thanks for the help.

---

### Post by michy99 on 2009-06-02
After a little research, it seems that you can split zip files from the command line, but it is not supported in the Archive Manager. To see the options for zipsplit, enter```
zipsplit -h
```To see the manual for zip enter```
man zip
```Personally, I always use rar.

---

