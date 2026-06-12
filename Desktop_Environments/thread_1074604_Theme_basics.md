---
title: "Theme basics"
date: 2009-02-19
forum: Desktop Environments
---

### Post by Arch_NME on 2009-02-19
This is a very basic question. How do I add themes?

I have download some themes from [http://gnome-look.org/](http://gnome-look.org/) but I can seem to figure out how to use them. 

I go to system>preferences>appearance and I see a Themes tab with an install button but when I point it to the dir where I extracted the themes I downloaded it's not finding what it's looking for. which is "theme packages". The themes I downloaded seem to be an xml files with some png images. 

Also, can anyone point me to a maybe a guide that kinda breaks down what is gtk, metacity, gnome, as far as how they relate to desktop appearance?

---

### Post by BrandonBan6 on 2009-02-19
Hi Arch,

Here's a simple guide for emerald.
[http://www.associatedcontent.com/article/806947/how_to_install_themes_on_ubuntu.html](http://www.associatedcontent.com/article/806947/how_to_install_themes_on_ubuntu.html)

GTK themes need the "GTK Engine" to run, here's a thread with more info on that:
[http://ubuntuforums.org/showthread.php?t=340330](http://ubuntuforums.org/showthread.php?t=340330)

With metacity themes, I've always just selected System > Preferences > Appearance, and then clicked the install button, and browsed to my unzipped theme download location and selected it. I'm not really into chasing eye candy myself, so I am far from an expert, but I hope that at least provides you with some starting points.

---

### Post by Therion on 2009-02-19
If it's a standard theme package it should download a *.tar.gz file, for example: ** TotallyCoolTheme.tar.gz**

Download this file to your desktop.

Open the Appearance Manager.
Click on the Themes tab.
Drag TotallyCoolTheme.tar.gz ONTO the Theme Manager window and Drop it there.  
You should get a dialog window from Ubuntu saying the theme has been installed.

If that's not working, post a link to the specific theme you're having trouble with so we can see what's up with it.

---

### Post by Arch_NME on 2009-02-19
Thanks. I see what I was doing now. I was extracting the packages before trying to install the theme when I should have just been trying to open the package files themselves.

Thanks for the links also.

---

### Post by mcduck on 2009-02-19
You can also extract the themes directly into correct places. (Actually sometimes you *have* to do this since the theme creator either didn't package the theme correctly or the package includes more than one theme).

In this case extract GTK and Metacity themes into ~/.themes and icon themes into ~/.icons.

Compiz/Emerald themes are best installed using the emerald theme manager, and they are also interchangeable, just rename the theme package depending on what you need.

GDM themes are installed GDM setup, in SYstem/Administration/Login Window. Go to Local-tab and click the "Add"-button and find the theme archive.

For USplash themes (the screen during boot process) I recommend installing StartUp Manager. It can also be used to configure Grub themes and colors.

---

