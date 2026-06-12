---
title: "[SOLVED] problem with a personalized action in konqueror"
date: 2007-12-27
forum: Desktop Effects &amp; Customization
---

### Post by g.a. on 2007-12-27
Hi,

I'm adding a custom "action" in my konqueror under kubuntu 7.10

I have a couple of problems and wonder if someone can help. Here is the content of the file scilab.desktop saved in the proper directory:

[Desktop Entry]
ServiceTypes=all/allfiles
Actions=OpenScilab;

[Desktop Action OpenScilab]
Name=Open Scilab
Icon=/home/scilab/scilab-4.1.2/X11_defaults/scilab.xpm
Exec=/home/scilab/scilab-4.1.2/bin/scilab

This action is correctly associated to all the files in all the directories and the icon is loaded, the problems are:

1. the application does not start. If I write the command from a shell it starts correctly. I can see that the app. tries to start since, if a write a command with a syntax error I receive a coherent message. How can I verify why the app does not start? how can eventually read some output?

2. what is the correct syntax to associate the action only to the files .sce and .sci (ascii files)?

thanks,
g.

---

