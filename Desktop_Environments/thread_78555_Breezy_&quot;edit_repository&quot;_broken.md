---
title: "Breezy: &quot;edit repository&quot; broken?"
date: 2005-10-18
forum: Desktop Environments
---

### Post by ad noiseam on 2005-10-18
Hello,

Just installed Breezy from scratch and I have a problem with the repository.

If I go to "Software Preferences" (from Synaptic or from the Update manager) and click on "add" to add a repository, I get a window with a list of four items to check:
-officially supported
-restricted copyright
-community maintained
-non-free

The first two option are always checked. If I check the other two and click "ok", these repository are not added. Whatever I check or uncheck here, it does not change a thing.

So... is there a GUI way to add these repositories?

Nicolas

---

### Post by Dr. Nick on 2005-10-18
you mean a non gui?

Open up a terminal and type ```
sudo gedit /etc/apt/sources.list
``` and their should be 2 lines to uncomment (remove #) read that file and you should see how to do it. Save it and run ```
sudo apt-get update
``` and see what happens, Their has been problems lately downloading the package list, IF you have trouble re-open sources.list and remove "us" or your 2 digit country code from all lines and try again

---

### Post by ad noiseam on 2005-10-18
[QUOTE=Dr. Nick]you mean a non gui?[/QUOTE]

No, I mean a GUI one. I know about the command line thing, but, not being a nerd, I really prefer to click on icons that type long commands.

I guess that it should work with this "edit repository" window, but it doesn't for me. Can you reproduce this bug?

---

### Post by Dr. Nick on 2005-10-18
Those should work, I cant reproduce it as mine have been checked for along time, I updated over the net, not from a cd. Sometimes using a terminal is easier but if you want you can go to the same windows and edit the "Breezy Badger" (Binary) entry and add this > main restricted multiverse universe under sections. That may be all you need, you may have to add it to other entrys aswell but try that one first as it may have all the the stuff you want. Anyone know what all you have to add "community and multiverse" to? , its been awhile since Ive done it, once your done hit "Reload" did you do that before?, it may have been a problem

---

