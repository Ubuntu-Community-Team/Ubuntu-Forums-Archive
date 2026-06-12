---
title: "sudo dpkg = where did the files go?"
date: 2006-01-12
forum: Desktop Environments
---

### Post by Autolycus on 2006-01-12
I want to use Bittorrent 4.2.2 instead of those bittorrent programns that came with Ubuntu. I downloaded the program from the web. It came across as a .deb file....No problem..

Using Terminal I entered the following:

cd Desktop (that is where the .deb file was)
sudo dpkg -i [filename]


Everything seemed to work alright as I received no error messages...

My question is this: Where did the program go so that I can select it from the ".torrent" file that I download from the web?

Also...in the future, should I download .deb files from the web, where do the files go after 'sudo dpkg'?

---

### Post by cwaldbieser on 2006-01-12
[QUOTE=Autolycus]I want to use Bittorrent 4.2.2 instead of those bittorrent programns that came with Ubuntu. I downloaded the program from the web. It came across as a .deb file....No problem..

Using Terminal I entered the following:

cd Desktop (that is where the .deb file was)
sudo dpkg -i [filename]


Everything seemed to work alright as I received no error messages...

My question is this: Where did the program go so that I can select it from the ".torrent" file that I download from the web?

Also...in the future, should I download .deb files from the web, where do the files go after 'sudo dpkg'?[/QUOTE]

This will show you all the files installed by the package:
```

$ dpkg -L <package-name>

```

---

### Post by kaamos on 2006-01-12
And the executable you are looking for is usually in /usr/bin or /usr/local/bin.

---

### Post by schilcha on 2006-01-12
There's another thread [here]("http://www.ubuntuforums.org/showthread.php?t=116238") that deals with a similar problem. 

If you want to always open torrent-files with some app, navigate to a torrent-file in nautilus (file-browser) -> right-click a torrent-file -> "open with other application" -> "Use a custom command" (at the bottom)

---

