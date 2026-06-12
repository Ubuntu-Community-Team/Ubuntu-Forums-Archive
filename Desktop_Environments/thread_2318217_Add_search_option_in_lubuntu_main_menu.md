---
title: "Add search option in lubuntu main menu"
date: 2016-03-24
forum: Desktop Environments
---

### Post by pranish on 2016-03-24
The default main menu that lubuntu provides doesn't have an application search option which is terrible. I have installed cairo dock but it consumes 100+ MB RAM. Tried synaptic and xfce whisker menu but doesn't work properly. Please suggest me how to add a search option in the main menu. xubuntu's and mate's main menus would be prefered. 

Thank you

---

### Post by mörgæs on 2016-03-24
Have you considered just installing Xubuntu? I find that the search field works fine.

---

### Post by vasa1 on 2016-03-24
> **pranish said:**
> The default main menu that lubuntu provides doesn't have an application search option which is terrible. I have installed cairo dock but it consumes 100+ MB RAM. Tried synaptic and xfce whisker menu but doesn't work properly. Please suggest me how to add a search option in the main menu. xubuntu's and mate's main menus would be prefered. 

Thank you
What exactly do you mean by "an application search option"? Can you not find an application you've installed from the menu tree? What is your actual difficulty? Are you trying to find software you've installed without using the software center or apt-get?

As for synapse (_not_ synaptic), I'm not sure it's being developed any more. At least it's not available in 14.04's software center.

If you like the main menus of some other distro, just install that particular distro. Mixing-n-matching may turn out to be non-optimal.

And if you want to conserve RAM, there's always [dmenu]("https://wiki.archlinux.org/index.php/Dmenu") :)

Is your present question related to [http://ubuntuforums.org/showthread.php?t=2317759](http://ubuntuforums.org/showthread.php?t=2317759) ? It's always better to provide some context so that people can help you effectively rather than having to guess what the issue is :)

---

### Post by Dennis N on 2016-03-24
A file search is done from the PCManFM file manager from it's tools menu. You can also install a dedicated search tool like Catfish. I think the LXDE developers want to keep their desktop environment lightweight, so some judgment calls have to be made on more added features that duplicate what can already be done. There is no end to the "add more features" path.

---

### Post by vasa1 on 2016-03-24
Well, the good thing about this thread is that it made me look at *dmenu* once again :)

I'll be able to free up quite a few keyboard shortcuts that were otherwise tied up to launch apps:
```
dmenu_run -b -nb '#222222' -nf '#888888' -sb '#090834' -sf '#aaaaaa' -fn '-adobe-courier-medium-r-normal--0-0-0-0-p-0-iso8859-1'
```

---

### Post by Dennis N on 2016-03-24
Yes, good ideas and advice here. dmenu I have never heard of before now. I'm not much into keyboard shortcuts except basic things like copy, paste, and save, and the single-key shortcuts for audacious control which I find very useful.

---

### Post by vasa1 on 2016-03-24
> **Dennis N said:**
> ... dmenu I have never heard of before now. ...
I hang around the BunsenLabs forum (related to Crunchbang) because they use Openbox and they mention dmenu quite a bit.

Anyway, here's a link ([http://akuederle.com/awesome-dmenu](http://akuederle.com/awesome-dmenu)) and a quote from there:> If you are using any modern Linux Distro, it has probably some kind of application launcher already included. To name a few, GNOME Do, Synapse, or xfce4-appfinder all work the same way. You press a button, the launcher appears, and you can quickly select a application to launch by typing its initial letters. In its default configuration Dmenu works no different; **however, it can be used to make a quick selection from any given list and not just the default list of applications**. Therefore, Dmenu is practical as a custom launcher for nearly everything and even as a way to get a user input for a bash or python script.
I'll eventually look at the part in bold text because that's what I use Kupfer for.

---

