---
title: "Realplayer and .rmvb files"
date: 2005-10-21
forum: Desktop Environments
---

### Post by joplass on 2005-10-21
I am starting this thread because I could not play rmvb files in Breezy.  I search the forum and I googled a few times without success.  I also noticed that some of us were have trouble installing realplayer.  I must admit that the version of realplayer included in Breezy's repo did not work for me like it did not work for some others.  I was able to install realplyer which provided me the proper plugin for xine.  Now I can play rmvb with realplayer and zine.  This is what I did:

In synaptic install libstdc++5 (very important step)
Create /usr/realplayer
Download the .bin file of Realplayer10 and save in /usr/realplayer

Next steps could be found on realnetworks site:
You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

- Enjoy your RealPlayer10 for Linux!

I hope this helps someone else.

---

