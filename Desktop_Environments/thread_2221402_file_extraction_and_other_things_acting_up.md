---
title: "file extraction and other things acting up"
date: 2014-05-02
forum: Desktop Environments
---

### Post by nLpPyXR on 2014-05-02
So yeah, I'm on Lubuntu Core 14.04 and for whatever reason, despite the fact that I have p7zip-full installed, there is no "Extract Here" option in my context menus when I right-click over a compressed file.

Plus, in order to extract a file with a space in its filename I have to type a backslash before the actual space, example:

```
p7zip -d /home/Downloads/my\ file.7z
```

And while these are things I won't die about, they strike me as very odd since Lubuntu 13.10 didn't act this way...

Basically what I'm asking is this: does someone know what package(s) Lubuntu Core is missing that make it act unlike the 13.10 Desktop version? below are the package details of Lubuntu Core so that someone more savvy/educated can point this newbie in the right direction.

[http://packages.ubuntu.com/trusty/lubuntu-core](http://packages.ubuntu.com/trusty/lubuntu-core)

Thanks :smile:

---

### Post by vasa1 on 2014-05-02
Are you having constraints of space or RAM? Why did you choose Lubuntu Core? I went with the full install and removed various programs I don't use.
> in order to extract a file with a space in its filename I have to type a backslash before the actual spaceis normal behavior. Otherwise, the shell thinks the space is separating files: "my" being one file and "file" being the other. This is the Bible: mywiki.wooledge.org/BashGuide

---

### Post by nLpPyXR on 2014-05-02
After a little experimentation I discovered the package I needed to have Core act the same way as Desktop is called "file-roller".

Thread marked as solved.

---

