---
title: "kubuntu splashy killed by update"
date: 2008-02-19
forum: Desktop Effects &amp; Customization
---

### Post by ingo on 2008-02-19
Hi,

I've got Kubuntu 7.10 purring along on one of my boxes and decided to give splashy a try 'cos I wanted an attractive and individual boot up process.

After some tinkering I got it to work and everything was hunky dory until the last Kubuntu update incl. kernel and headers.

I booted up, no splashy. I did a ```
sudo update-initramfs -u
```but that didn't get my splashy back either :(

Any ideas out there???

---

### Post by ingo on 2008-02-20
Wow, not all at once, please!

After some research I am now attempting the following:

add "vga=792 quiet splash" not to the relevant kernel line of /boot/grub/menu.lst but to the line starting # kopt=root=UUID=blablabla

As far as I understand this has an effect on grub's default behaviour and is not kernel specific. 

And wish me luck :)

---

### Post by ingo on 2008-02-20
Fun monologue...

First I found that the link from /etc/splashy/themes to /usr/share/splashy/themes wasn't valid anymore. I restored it and now I get the following error:

couldn't start splashy error -2

I'd be loathed to simply purge and reinstall splashy (which would probably work) 'cos I want to understand what happened. Will a new kernel update kill it again? If so, how can I circumvent this???

---

