---
title: "Frozen Linux"
date: 2009-03-26
forum: General Help
---

### Post by Elenath89 on 2009-03-26
Hi there!
First of all I'm not really an expert in Linux and I guess sometimes I try to do things really out of my possibilities and now the result is that I can't possibly use Linux! Everything seems to work fine at the beginning but after few minutes the terminal, skype and file manager windows pop up and everything freezes. I can still move the mouse around but the keyboard is practically useless. I think it all started when I followed these instructions
[http://lulzicon.com/?page_id=77](http://lulzicon.com/?page_id=77)
Because after that my synaptic package manager stopped to work and adept package manager showed only the already installed packages.
Any idea on how I could solve the problem?
Thank You In Advance

---

### Post by khelben1979 on 2009-03-26
Backup your data and then reinstall Linux, would be my recommendation, however, what happens when you try to go to a text console from the x server?

```
ctrl + alt + f1
```
get's you to the first text console.

If this works you do have several possibilites in hacking around with text files to see what has happened, but if you're a newbie like you said, a pure reinstall would be the best choice and be more careful next time you do things which you don't master. :)

---

### Post by kuja on 2009-03-26
Try running the following in konsole and post the output of each here.

```
sudo apt-get check
sudo apt-get -f install
sudo dpkg --configure -a
```

---

