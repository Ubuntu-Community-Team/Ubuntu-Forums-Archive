---
title: "Murrine-SVN question"
date: 2009-03-03
forum: General Help
---

### Post by Krause on 2009-03-03
Heya giys, i just installed murrine-svn from the newest source after uninstalling intrepid's murrine package, and im having a some issues.

I followed the directions outlined in this post here:
> **perfectska04@hotmail.com said:**
> You can either try my .debs like Ub1476 mentioned, since I always upload the latest revision soon after it's out. You can also do this (it's what I use to build them):

1. Remove any previous version you installed with make install
2. Install Checkinstall (sudo apt-get install checkinstall)
3. svn checkout [http://svn.gnome.org/svn/murrine/trunk/](http://svn.gnome.org/svn/murrine/trunk/) murrine 
4. cd murrine 
5. ./autogen.sh --prefix=/usr --enable-animation
6. make
7. sudo checkinstall
8. It's important that you edit the checkinstall info. Make the name of the package gtk2-engines-murrine and use a numerical value for version and release number. Someting like version 0.60 and release 1 should work, just make sure to choose higher version/release number than the one you already have installed.

Edit: Also make sure any murrine theme you're using doesn't have the "style" option anywhere. This option was deprecated and is now replaced by "profile". Any murrine theme with "style" on it will not work in newer versions of Murrine SVN.


My issue is that after installing murrine themes, i can select them as options to edit normal metacity themes in gnome, but the murrine configurator on the murrine site doesnt really work, the preview doesnt apply any changes, it just always shows the current theme features your using, and then when you save/apply it seems to change it to the devault GTK gray theme.

I wanted to try murrine because I read that you can enable RGBA transparency with it on murrine themes, which i assumed you configure through the murrine configurator, anyone have any ideas/help for me on my issue?

thank you.

---

