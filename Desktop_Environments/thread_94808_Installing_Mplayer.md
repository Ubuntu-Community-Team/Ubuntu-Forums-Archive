---
title: "Installing Mplayer"
date: 2005-11-24
forum: Desktop Environments
---

### Post by jackgnat on 2005-11-24
I'm mostly new to Linux and I'm trying to understand how to install Mplayer and the correspoding plugin for Firefox.

I've only been able to find cryptic explanations on the net, and nothing I can understand. Any idiot proof guides or tips?

---

### Post by oskude on 2005-11-24
have you tried to search this forum, or this [https://wiki.ubuntu.com/MplayerInstallHowto?highlight=%28mplayer%29](https://wiki.ubuntu.com/MplayerInstallHowto?highlight=%28mplayer%29)

---

### Post by Xian on 2005-11-24
From the Wiki: [How-To Install Mplayer and Plugin](https://wiki.ubuntu.com/MplayerInstallHowto)

---

### Post by jackgnat on 2005-11-24
Sorry, I seem to be completely useless at this.

I've read through the HOWTO and this is what I'm supposed to do from what I understand:

-Download the package I need (mplayer-586)
-Go to the terminal and type in [sudo apt-get install mplayer-586]

I don't know where to place the package or anything, and typing that in just says its not there, but is referred to by another source.

Any help?

---

### Post by oskude on 2005-11-24
did you skip this [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto) ?

---

### Post by bored2k on 2005-11-24
[list=1]
[*]**Getting the right codecs.**
Several ways to do this. By not knowing them all, you chose the hardest. There's this french repository called the Ubuntu PLF (last time i checked, it meant Penguin Liberation Front - don't ask) which stores these for you. We could add their repositories but they are not stable at the moment so I suggest manually download it from them.
[INDENT][LIST]
[*][w32codecs]("ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/pool/non-free/w32codecs/") (playback of almost everything)
[*][libdvdcss2]("ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/pool/free/libdvdcss2/") (DVD playback)

Here you will download the **.deb** files (skip the libdvdcss2-dev one)for them. To install them, close anything using apt-get (apt-get/Synaptic/Adept/aptitude/*etc*) and type this from a terminal (I'm using the names of the ones there at the moment):
```
sudo dpkg -i w32codecs_20050412-1plf4_i386.deb
```
```
sudo dpkg -i libdvdcss2_1.2.9-1ubuntu2_i386.deb
```
If everything went as planned, you have now installed  the codecs you'll need. 
Go treat yourself with a glass of water (H2O = Life).
[/LIST][/INDENT]
[*]**Getting the correct repositories.**
Before the next step, you need to have a decent repository file on your computer. So grab mine **[here]("http://nopaste.php-q.net/173438")** . After you replace yours with this command (thinking yours aren't really good):
```
sudo gedit /etc/apt/sources.list
```Issue the following:
```
sudo apt-get update
```
[*]**Getting good media players.**
You want to get a decent totem player, so ```
sudo apt-get install totem-xine
```Now you want MPlayer
```
sudo apt-get install mplayer-386 mplayer-fonts mozilla-mplayer
```
Note: this is the ugly as a monkey's butt MPlayer, but  it's the easiest one to get.
[*]**Configuring MPlayer.**
Once you open the ugly thing, go to its preferences, and under video select XV. Now under audio, select ESD (if you have a more or less default Ubuntu these are the audio and video output that will work). Restart MPlayer, and try running a movie (note: you need to install the codecs before opening mplayer).[/list]

---

### Post by Canuckelhead on 2005-11-25
Running Automatix, which is mentioned in these forums soooo many times will also install any plugins you need etc....

---

