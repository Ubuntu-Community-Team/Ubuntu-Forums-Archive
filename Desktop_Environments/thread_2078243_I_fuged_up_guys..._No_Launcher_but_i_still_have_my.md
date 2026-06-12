---
title: "I fuged up guys... No Launcher but i still have my Window Menu"
date: 2012-10-30
forum: Desktop Environments
---

### Post by thomas07vt on 2012-10-30
[SOLVED]
Ok guys... i messed up somehow. So recently i upgraded my ubuntu 12.04 with a ton of items (it was long overdue). After i updated and rebooted my machine, i noticed that the workspaces icon on the launcher re-appeared. I had previously removed it from the launcher by editing the /usr/share/unity-2d/launcher/Launcher.qml file as described here:

askubuntu.com/questions/38789/remove-the-workspace-switcher-launcher-from-unity-launcher

Since the workspaces icon was on my launcher, I tried to find the above URL, however i was unable to find it in a timely fashion, but i did find an article telling me that compizconfig-setting-manager could remove this icon. So i ran this command in my terminal:

sudo apt-get install compizconfig-settings-manager python-compizconfig compiz-fusion-plugins-extra compiz-fusion-bcop compiz-fusion-plugins-main compizconfig-backend-gconf

After i ran this command, i managed to find the URL listed above so I decided to edit the Launcher.qml directly as before.

Here is what went wrong... As the article describes i needed to edit this:

Component.onCompleted: {
items.appendModel(bfbModel);
items.appendModel(applications);
items.appendModel(workspaces);
items.appendModel(devices);
shelfItems.appendModel(trashes);
}

with This:

Component.onCompleted: {
items.appendModel(bfbModel);
items.appendModel(applications);
/* items.appendModel(workspaces);*/
items.appendModel(devices);
shelfItems.appendModel(trashes);
}

BUT... what i actually did was edit it with this:

Component.onCompleted: {
items.appendModel(bfbModel);
items.appendModel(applications);
/* items.appendModel(workspaces);
items.appendModel(devices);
shelfItems.appendModel(trashes);
}

So, i forgot the end of my comment, so i guess that commented out the bottom portion of this file.

I rebooted the machine, and when I did... my entire launcher was missing. So i opened the terminal and tried to edit launcher.qml file again (to include the end " */ "), which i thought i did. I saved and exited. I rebooted my machine, but my launcher was still gone. I then tried to check the Launcher.qml file to see if the edit was saved, however the Launcher.qml file was not there anymore.
So, at this point i decided to log in, using the guest account, and using the terminal, found the Launcher.qml file. I ended up saving the Launcher.qml file to my admin desktop, then logged back into my admin account. I tried opening the 
/usr/share/unity-2d/launcher/
directory, however it did not exist. /usr/share/unity-2d/ existed, however the /usr/share/unity-2d/launcher/ folder did not exist. So i created the folder, and then added the Launcher.qml file which i copied over from the guest account to my desktop.

I rebooted my machine, but the Launcher is still not there. I tried enabling the Unity Plug-In in the ccms, however it still does not show up. Thinking that perhaps the compiz settings were the issue, I did some searching and tried these commands, to hopefully reset compiz

mv ~/.compiz-1 ~/.compiz-1.BACKUP
mv ~/.config/compiz-1 ~/.config/compiz-1.BACKUP

rebooted - still no launcher

I just tried reinstalling Unity using this command:
sudo apt-get install --reinstall unity && sudo reboot

Still no launcher... So any ideas?
Does anyone know what files should be in the 
/usr/share/unity-2d/launcher/
directory?

---

### Post by stinkeye on 2012-10-30
Compiz does not run in unity2d.
If your in the **ubuntu 2d** session, anything you change using ccsm
or moving compiz configs has no effect.

Check your session...
```
echo $DESKTOP_SESSION
```

When you say you upgraded, do you mean you upgraded to 12.10.
12.10 no longer installs unity 2d and there is no **ubuntu 2d** session to choose at the greeter.

---

### Post by thomas07vt on 2012-10-30
I ran echo $DESKTOP_SESSION and it returned:

ubuntu-2d

I checked and I am still running 12.04.

---

### Post by thomas07vt on 2012-10-30
also, i tried logging out of my user name, and loggin back in with ubuntu, rather than ubuntu-2d , however the $DESKTOP_SESSION still returned ubuntu-2d

---

### Post by thomas07vt on 2012-10-30
I FIXED IT!!!!!!!!!!
Ok... so, as i mentioned before that the directory
/usr/share/unity-2d/launcher/
no longer existed.. so apparently I was getting my information from a couple of different sources. I initially edited this file:
/usr/share/unity-2d/shell/launcher/Launcher.qml
NOT this file:
/usr/share/unity-2d/launcher/Launcher.qml

So when i edited the file from the guest account to include the "*/" and then transferred it over to my admin account.. I transferred it to the wrong location.
I just checked the 
/usr/share/unity-2d/shell/launcher/Launcher.qml
file, and it indeed had only the opening /* and not the closing */
I added that, rebooted and my desktop is back to normal!
Sorry for such a long post with such a dumb resolution.

---

