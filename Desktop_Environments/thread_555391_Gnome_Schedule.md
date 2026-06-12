---
title: "Gnome Schedule"
date: 2007-09-20
forum: Desktop Environments
---

### Post by illopos on 2007-09-20
Hi,

I have a slow internet connection so, I usually download packages and any other big downloads in big chunks at night. But I don't want my internet connection to continue after the downloads are done. Right now I use Gnome Schedule to automatically shutdown the system. I use the following script:
sudo halt
"my password"
This seems to work fine. The active user applications are usually 'wvdial' to connect, synaptic package manager, may be a browser (firefox) and its downloader.

What I want to know is if what I am doing is safe. If not is there a safer method to do it?

Thanks

-illopos

---

### Post by dcstar on 2007-09-20
> **illopos said:**
> Hi,

I have a slow internet connection so, I usually download packages and any other big downloads in big chunks at night. But I don't want my internet connection to continue after the downloads are done. Right now I use Gnome Schedule to automatically shutdown the system. I use the following script:
sudo halt
"my password"
This seems to work fine. The active user applications are usually 'wvdial' to connect, synaptic package manager, may be a browser (firefox) and its downloader.

What I want to know is if what I am doing is safe. If not is there a safer method to do it?

Thanks

-illopos

"halt" calls all the appropriate scripts to shut things down correctly, so I wouldn't be too concerned as any running process should be terminated in an acceptable fashion.

You seem to have a solution that works for you and I can't see any issues with it.

---

### Post by illopos on 2007-09-23
Thanks a lot.

---

