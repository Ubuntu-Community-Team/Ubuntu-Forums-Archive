---
title: "Reinstalling 9.04 - how to make make working flash player in firefox 3.0.10?"
date: 2009-05-13
forum: General Help
---

### Post by neotester on 2009-05-13
1. I have installed 9.04. Bluetooth worked just fine and faster booting, faster shut down.
2. I have entered an audio/video streaming site, something like Youtube but in my own language. Firefox said to me I needed 3 plugins. I have installed them. Nice. Now, I still can't listen to music. It just won't load the progress bar of the song.
3. I'm going to reinstall Ubuntu 9.04, I can't give up on it so fast. I like it. I want Firefox 3.0.10 to work with flash player, I don't want any problems.
4. How could I do that?

Please, I'm going to follow you, step by step if you tell me how to get it right from the second time. 
Thank you.

---

### Post by albert ozzy on 2009-05-13
First of all don't ever give up on Ubuntu. And you dont need a format.Now for your problem:

Firefox showed you 3 possibilities for flash player. You should install only one of them. I personally use Adobe's non-free flash player not Gnash nor swfdec. It's up to you to choose whatever you want. to make it work smoothly i suggest you to uninstall whole 3 and install the one you want.

Let's say you want to install Adobe's non-free flash player:

1-) Uninstall other flash players with these commands or with unchecking them in synaptic package manager
> 
sudo apt-get remove swfdec-mozilla
sudo apt-get remove gnash
2-) install your flash player:
> 
sudo apt-get install adobe-flashplugin


That's it.

Note: You can also do these from Synaptic Package Manager without writing any commands.

---

### Post by neotester on 2009-05-14
Thank you **albert ozzy**. That woked for me just fine. You are a genius to me. Thank you so much.

---

### Post by hyperdude111 on 2009-05-14
If you want other codecs java,flash,mp3,divx,mp4 ect.............

sudo apt-get install ubuntu-restricted-extras

---

### Post by neotester on 2009-05-14
Thank you also **hyperdude111**. I might need a few extra codecs in the future. Thanks man.

---

### Post by st1100pilot on 2009-05-15
Thanks! Worked for me too. It also made Google Street View work for me.

---

### Post by baker126 on 2009-06-29
I think I am experiencing the same issues...is there anyway to determine which flash player is installed?  I think I installed more than one and it is causing an issue.

---

### Post by albert ozzy on 2009-06-29
type this on a command line
> dpkg -l | grep flash
it'll show you the installed plugin.Alternatively you can use Synaptic Package Manager and search for adobe-flashplugin,gnash, swfdec-mozilla. Checked items are installed on your computer.

---

