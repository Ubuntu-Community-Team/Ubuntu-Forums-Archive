---
title: "How do I install programs"
date: 2005-12-24
forum: General Help
---

### Post by gamer46290 on 2005-12-24
I downloaded firefox to my desktop, even though I am having problems with the unknown host thing. How do I install though???

---

### Post by mrmcctt on 2005-12-24
Try [THIS LINK]("https://wiki.ubuntu.com/FirefoxNewVersion?").

I used it for my new Firefox install and everything went great.

---

### Post by sciurus on 2005-12-24
Since you are using Kubuntu, not Ubuntu, all you need to do is

Download firefox-1.5.tar.gz from mozilla.org. Open your terminal/console program, Konsole, and change to the directory you downloaded it to. In your case, this probably means enter the command 'cd ~/Desktop' without the quotes. Then run the following commands

sudo cp firefox-1.5.tar.gz /opt/
cd /opt
sudo tar xzvf firefox-1.5.tar.gz
sudo rm firefox-1.5.tar.gz
sudo ln -s /opt/firefox/firefox /usr/bin/firefox

The first time you use sudo it will ask you for your password.

If you don't need a specific feature of Firefox 1.5, or if you plan to install any Gnome/Ubuntu software, you should use the version in the repositories. This can be installed at a terminal with the command 'sudo apt-get install firefox'

---

### Post by The Warlock on 2005-12-24
[QUOTE=gamer46290]I downloaded firefox to my desktop, even though I am having problems with the unknown host thing. How do I install though???[/QUOTE]

Unless you really really need the absolute latest version of Firefox, it will be much easier to use the version in the repositories.

Just open a terminal and type in ```
sudo apt-get install firefox
```

And then it will be downloaded and installed, right there.

---

### Post by briancurtin on 2005-12-25
read some threads, try some things, etc

its not windows, it doesnt do everything for you

---

