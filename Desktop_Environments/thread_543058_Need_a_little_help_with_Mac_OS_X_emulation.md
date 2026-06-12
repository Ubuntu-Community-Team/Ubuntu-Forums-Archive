---
title: "Need a little help with Mac OS X emulation"
date: 2007-09-04
forum: Desktop Environments
---

### Post by toecutter on 2007-09-04
I followed the directions on Taimila's original mac os x emulation page (here's the link to the new version: [http://www.taimila.com/?q=node/11](http://www.taimila.com/?q=node/11) the old instructions aren't available any more).

I'm not a Mac superfan but I like the environment and design, so I just wanted to copy a few elements of it. 

Here's what I want to do, and where I'm having trouble:
[LIST]
[*]I've made the lower taskbar autohide, and originally had various startup icons there. I've since removed the icons (I want to use the OS X type dock from the above link) and use the Applications menu for now. However, I can't remove the Wastebasket yet because I can't find where the 'original' startup menu location for it is - can anyone tell me? I just want to be able to delete stuff I've sent there :)
[*]How can I get Swiftweasel and Beryl to start automatically? I can't seem to find the commands for these. I've gotten Gaim, Gmail notifier to start up so I know where to go in the menu, I just don't know the right commands.
[*]How can I delete the Screenlets app? I installed it a long time ago but it won't update with the automatic updater (it tells me it can't download the new file, or something), and I can't apt-get uninstall' it. For that matter, I want to uninstall DeVeDe, ToVid, ToDisc and SwiftFox but I haven't tried everything yet to get rid of them![/LIST]

Thanks for any help!

---

### Post by astralsin on 2007-09-04
if you installed them through aptitude you should be able to do it either from the command line or through Synaptic Package Manager in System->Administration.  if you installed them from source, you'd have to delete the binaries (and anything else it installed) by hand unless they came with an uninstall script.

---

### Post by toecutter on 2007-09-05
From the screenlets web page I found instructions to remove various directories, apparently there's no uninstall script - but after restarting, the Updates still tells me that screenlets has updates, and of course they still can't be downloaded, which was why I was wanting to remove it anyway :-/ oh well...

Can anyone else help, at least with the wastebasket location in the menu system, or how to start Swiftweasel, Beryl and AWN automatically?

---

### Post by llamakc on 2007-09-05
If the system is telling you that there are available updates then you DID install something through one of the package management frontends (APT-GET, Synaptic, Aptitude, etc). 

Start Synaptic and search for screenlets. Uninstall whatever packages you want to remove.

---

### Post by toecutter on 2007-09-06
Awesome, that did it! Was able to get rid of a couple of other things as well but I suppose I'll have to do a bit more googling to get rid of some of these other programs I've tried but don't like.

Now, can anyone tell me where the wastebasket is in the menu? :)

---

### Post by Inxsible on 2007-09-07
> **toecutter said:**
> Awesome, that did it! Was able to get rid of a couple of other things as well but I suppose I'll have to do a bit more googling to get rid of some of these other programs I've tried but don't like.

Now, can anyone tell me where the wastebasket is in the menu? :)
Since you are using AWN, it has its own Trash Applet that you can use. It will create a link to the Trash in your AWN bar.

if you need to remove anything you can do ```
sudo aptitude remove <package-name>
```

---

### Post by Inxsible on 2007-09-07
As for the removal of screenlets, do this

```
sudo aptitude remove screenlets
```After you have done this, go to your home folder in nautilus and hit Ctrl + H. This will show you all the hidden folders. Then delete all the screenlet related entries.

Places to look would be /home/USER/.screenlets, /home/USER/.config/screenlets, /home/USER/.gconf/apps/screenlets

Replace USER with your username. These are just some of the locations. you might wanna do a thorough search by using this command```
find / -iname screenlet*
```It will give you a list of all the places where screenlet occurs. You can then delete those files through nautilus.

Actually you can also delete them through the 'find' command by using the -exec parameter if you want.

---

### Post by toecutter on 2007-09-27
Thanks Inxsible, I followed your tips and was able to get rid of screenlets once and for all :) plus a few other things!


Can anyone tell me what command to use in System > Preferences > Sessions > Startup Programs to get Beryl (or Compiz, since that's going to be standard in 7.10 apparently) and AWN to start automatically?

---

