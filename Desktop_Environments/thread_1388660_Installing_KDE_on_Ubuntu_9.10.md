---
title: "Installing KDE on Ubuntu 9.10"
date: 2010-01-23
forum: Desktop Environments
---

### Post by dancewithpratik on 2010-01-23
Hi folks,
    Please tell me how to install KDE on Ubuntu 9.10.
I tried with "sudo apt-get install kubuntu-desktop" but installation couldnt complete due to proxy server on my Internet Connection which prevents access to *torrent*.

Also tried with,
sudo add-apt-repository ppa:kubuntu-ppa/beta
  but got the error 
               <urlopen error [Errno 111] Connection refused>

Please Help me .... Waiting

---

### Post by XubuRoxMySox on 2010-01-23
Try it using Synaptic Package Manager. Find "kubuntu-desktop" and click "Mark for Installation," then "Apply."

It may only be that the server for your location is down for the moment, or too busy.

Synaptic works great!

When you log out after its installation, find the Options button on the Login screen and select KDE as your Session.

Enjoy!

-Robin

---

### Post by nothingspecial on 2010-01-23
```
sudo apt-get install kde-core
```

You don`t have to install the whole of kubuntu

---

### Post by lovinglinux on 2010-01-23
> **nothingspecial said:**
> ```
sudo apt-get install kde-core
```

You don`t have to install the whole of kubuntu

The *kde-core* no longer exists on Karmic. The equivalent is *kde-minimal*, which is the one I use, plus *kdeplasma-addons*.

---

### Post by nothingspecial on 2010-01-23
> **lovinglinux said:**
> The *kde-core* no longer exists on Karmic. The equivalent is *kde-minimal*, which is the one I use, plus *kdeplasma-addons*.

Oh - sorry,

Not on karmic right now.

I would like to reinforce my point though, that you don`t need to install kubuntu-desktop or xubuntu-desktop and everything else that goes along with them just to try another DE.

---

### Post by lovinglinux on 2010-01-23
> **nothingspecial said:**
> Oh - sorry,

Not on karmic right now.

No problem. Is hard to keep tabs on such changes.

> **nothingspecial said:**
> I would like to reinforce my point though, that you don`t need to install kubuntu-desktop or xubuntu-desktop and everything else that goes along with them just to try another DE.

I agree. I have a command-line Ubuntu installation, with kde-minimal, kdplasma-addons and just the applications I need. It works like a charm.

---

### Post by vikjon0 on 2010-03-20
Edit: my bad 
kdebase-workspace-bin or --no-install-recommends kde-minimal works pretty good. I would say the latter is closest to gnome-core.

---

