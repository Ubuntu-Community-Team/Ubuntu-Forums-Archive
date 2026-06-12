---
title: "SuperTuxKart problem."
date: 2022-02-25
forum: Gaming &amp; Leisure
---

### Post by Autodave on 2022-02-25
I had to reinstall Xubuntu a couple weeks ago.  Install went fine.  Installed STK with no errors.  But, when entering the game, it tells me that I have no internet or a firewall is blocking the game.  I have tried reinstalling several times both from Synaptic and Snap.  Keep coming up with the same problem.  I would *really *like to get some of my favorite tracks back!

This is a wired internet connection and obviously I had internet to d-l and install the game multiple times.

---

### Post by mastablasta on 2022-03-09
try running it from terminal, see what it throws out.

otherwise i believe you can manually download the tracks and add them.

---

### Post by Autodave on 2022-04-05
The only thing that I really saw was this:

[info   ] HTTPRequest: Downloading [https://online.supertuxkart.net/dl/xml/online_news.xml](https://online.supertuxkart.net/dl/xml/online_news.xml)
[error  ] news: Error downloading news: 'SSL peer certificate or SSH remote key was not OK'.

Any ideas?

---

### Post by mastablasta on 2022-04-07
isn't there a binaries version for "install" where you just extract all the files and launch them? i believe i used that one last time i played. i never used snap.

---

### Post by ajgreeny on 2022-04-07
I occasionally play it but I also use the downloaded archive and run it directly from that after extraction  without installing anything.
I have removed the snap infrastructure totally from my machines.

I will look for the site I used to download and report back with a link for you.

[https://sourceforge.net/projects/supertuxkart/](https://sourceforge.net/projects/supertuxkart/)
This is the one I use: it runs very well even using my integrated Intel graphics.

---

### Post by Autodave on 2022-04-07
OK.  I d-[ed it.  But this is where my ignorance comes in.....what do I do with it next?  I unpacked it, but what next?

---

### Post by #&amp;thj^% on 2022-04-07
Right click on the .tar and extract to your preferred location.
in this case Downloads, then cd to:
```
cd /Downloads/SuperTuxKart-1.3-linux-64bit
```
then run:
```
sh run_game.sh

```
Make sure you wear your helmet....LOL

---

### Post by DuckHook on 2022-04-09
I have no idea how the snap version would behave. If you are installing the snap version, it would not surprise me that some things are wonky or off balance.

In my campaign to keep to .debs, this is what I've done—and the only reason I'm suggesting it at all is because you are an old hand at Linux and will know all about the security ramifications and the system risks:

I've installed the xtradeb games PPA. In my case, it's installed into a LXD container for security sandboxing, but, yes, I've gone and installed a PPA (!):```
sudo add-apt-repository ppa:xtradeb/play
```

Here's their site: [https://xtradeb.net/](https://xtradeb.net/)

The PPA is well maintained and has the most current versions of not just SuperTuxKart but also old gems like Wesnoth, 0AD, OpenTTD, Warzone 2200 and especially FlightGear.

Of course, the usual paranoia/warnings apply. It's a PPA. You are extending your trust to these guys (strangers, essentially) and anything could get installed into your system. For that reason alone, I recommend installing it into a VM if your system is powerful enough, or a container like LXD or Docker.

---

### Post by agentl074 on 2022-05-31
I installed the non snap version from the app store, and it would not launch. I had to remove it via app store. It was a shame, but I have not attempted to install manually. It seems that things work better if I install from OEM repositories via command rather than using the app store... however, I have no problems with the snapcraft versions, either.

---

### Post by #&amp;thj^% on 2022-05-31
Believe it or Not, The Flatpak version has been the best experience I've seen.

---

### Post by agentl074 on 2022-06-27
On Mint, the deb version works very well.

---

### Post by Claus7 on 2022-06-28
Hello,

during development of 22.04, there was an issue of stk and ubuntu flashback: while trying to start the game it complained about some engine issue, something like: Antarctica Rendering Engine 2.0, and it didn't launch, if I recall correctly. The issue was fixed close to stable release, having installed the game under synaptic. Checking from regular ubuntu the issue was less frequent. No problems from stable release of jammy till today.

Regards!

---

