---
title: "Window Manager-Screwed up bigtime"
date: 2011-01-11
forum: Desktop Environments
---

### Post by dolarodus on 2011-01-11
I was trying out the Kubuntu environment but I did not like it and had some big troubles right off the bat. I came back to ubuntu but i wound up with a bunch of kubuntu programs I didnt want. I tried to get rid of them but I went about it in a very stupid way-i just deleted about anything I thought was KDE related. Im usually not anywhere near that stupid.

Unfortunately its done. It would not be quite as much of a problem if it had not caused metacity and my wifi program to stop working. Also the load up logo is kubuntu instead of ubuntu. Is there a way to reset without reinstalling?.

The immediate problem is that I can make metacity take over and get my bars back but only if i keep a terminal open with the command metacity --replace. I close it the bars disappear. What do I do?

Update:
After reading more on the forums I was able to understant that I needed to re-add metacity to start applications-what specifically took it out of there I have no clue. Unfortunately I still dont know exactly what I should do about the wireless. What is the program that runs wireless connections on ubuntu by default?
Update 2:
Installed Network manager and got it working properly. Still dont know how to get kubuntu off my loading screen.

The kubuntu screen can be removed by removing the package via the Synaptic Package Manager

It is named
plymouth-theme-kubuntu-logo

Uninstalling it seems to be the ONLY way to revert it to ubuntu that works with the current system.

---

### Post by TechnikAlsace on 2011-01-11
Instead of typing metacity --replace in a terminal, just open a simple command line with Alt+F2 and type metacity --replace there. So there is no need to keep the terminal open.

---

### Post by dolarodus on 2011-01-11
Yes there was, if I closed it the process stopped-the bars went away. This is no longer a problem.

---

