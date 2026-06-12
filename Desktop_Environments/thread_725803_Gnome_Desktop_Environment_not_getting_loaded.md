---
title: "Gnome Desktop Environment not getting loaded"
date: 2008-03-16
forum: Desktop Environments
---

### Post by harisankar98 on 2008-03-16
Hi..
      Me installed ubuntu hardy alpha5 .. then installed nvidia drivers which needed a kernel update.. after that i installed some gstreamer packages and restarted ma system.. only to find tht the desktop environment is not loading.. 
            The wallpaper appears and then an error concerning the trash applet appeared...it asked me to delete or not.. and it flashed and went away.. then only wallpaper is to be seen and nothing else loads.. Right click also not working.. Ctrl+Alt+Del will bring the Turn-Off Menu..
      Then I logged onto failsafe terminal and deleted the Trash applet file from /.gconf/apps/panel/..  
        I searched for gnome desktop environment in synaptic which i could start from the terminal only to find that it has got unmet dependencies on
  gnome-keyring-manager.. but keyring manaer is not getting installed... i tried installing Seahorse which is the keyring replacement.. but of no use..
     Now everytime I bootup , the panel shows up for an instant and then disappears ... pls help me...

---

### Post by harisankar98 on 2008-03-16
No one to help me.. eh??

---

### Post by harisankar98 on 2008-03-16
I tried reinstalling ubuntu and after installing gstreamer, i got the error message , that totem cannot connect to stream.. no sound cards found.. then i rebooted only to find that the desktop is not loading... once again... oh... 
        and no one yet to help me???????
 me gonna get rid of ubuntu today itself..

---

### Post by Herr Otto on 2008-03-16
Hey there,

For what it's worth, I've been having the same problem. For unrelated reasons I decided to reinstall gnome from scratch, but then the package manager wouldn't install gnome anymore (and i had to install KDE instead) because it has a dependency to Gnome Desktop Environment.

This package needs the keyring manager, and that doesn't appear to have the version required for Hardy.

Before that, I already noticed a lot of problems running administrative tasks and all that. The window that asks for your password would only pop up every now and then.

It appears this keyring package has not been updated to the required release for Hardy yet, while Gnome needs it badly.

This, I"m all saying as a relative noob following the error messages, but something seems to be up with the keyring manager and a lot of applications suffer from it.

I hope it's fixed soon and it's all back to Gnome happiness.

Any workarounds for this anyone? At this point, Gnome just doesn't tinstall at all!

Maybe I should make this a separate entry, but this problem appeared related to me. As well as it appears related to other's having problems with running administrative tools.

Otto

---

### Post by Tom G Marseille on 2008-03-26
I think you have probably identified the source of my worries too.  My desktop toolbars disappeared "suddenly" (lol) but I think it was just after having had problems connecting to my home wifi which requires access to the keyring applet you mentioned.

My current workaround is to run gnome-panel in a terminal.  It isn't sticky ie I have to do it at each session, so I am looking for a longer term solution.

Thus problem has been an opportunity for me, complete linux newbie, to discover a lot more, so every cloud ... etc, but I have also discovered the limits of forums as a source of solutions, which when you use your pc for work can be a bit stressful :-(

---

