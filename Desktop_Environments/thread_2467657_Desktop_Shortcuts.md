---
title: "Desktop Shortcuts"
date: 2021-10-03
forum: Desktop Environments
---

### Post by angel mike on 2021-10-03
What is the best way to create web desktop shortcuts with Ubuntu 20.04?

---

### Post by grahammechanical on 2021-10-03
Here is how to do it with Firefox

[https://support.mozilla.org/en-US/kb/create-desktop-shortcut-website](https://support.mozilla.org/en-US/kb/create-desktop-shortcut-website)

Regards

---

### Post by angel mike on 2021-10-04
Thanks Grahammechanical - I have tried that but although it drags the URL to the desktop it does not 'stick'. Any reason for that?
Regards

---

### Post by angel mike on 2021-10-04
There are several comments on the web that say Ubuntu 20.04 does not support 'drag and drop'
The alternatives get quite complicated and there are several of them!

---

### Post by grahammechanical on 2021-10-04
Nothing is easy with the Gnome Desktop Environment. I will give you that. You are right. Drag and Drop of the web site address does not work. On the other hand, we can use Files>Copy to>Desktop to put a text file on the desktop. A script is a text file with the .sh extension. It will need to have Permissions set to Execute.

I have messed around for several minutes trying to create a script that will load Firefox at the chosen web site and I have failed miserably. I can get the script on to the desktop. Sometimes a reboot is needed to get it to appear. I have failed. I am completely lacking in any scripting expertise. Sorry.

Regards

---

### Post by angel mike on 2021-10-04
Yes I managed to get a script file on the desktop but did not find it useful. The answer seems to be to use another File Manager which supports 'drag and drop' but finding one that integrates well with Ubuntu is difficult! I did not find Nemo very useful.
There must be someone in the forum that knows
Thanks for replying

---

### Post by T6&amp;sfpER35% on 2021-10-04
> [COLOR=#000000]What is the best way to create web desktop shortcuts with Ubuntu 20.04?[/COLOR]

Xubuntu 20.04

---

### Post by angel mike on 2021-10-04
Thanks 3rd - thats useful- was hoping to stick with Ubuntu will try the suggested flavour Xubuntu.

---

### Post by ajgreeny on 2021-10-04
I do not use Ubuntu for the main reason that I think gnome has just about killed any pretence of a useful DE, and has removed so many useful features that for me it has become impossible to use, at least it has in its default state.

I think I'm right in saying that to put desktop shortcuts (launchers) on the gnome desktop there is a need to use an extension but as I don't use gnome I am not sure  exactly how that is done or which extension you will need to add.

---

### Post by grahammechanical on 2021-10-04
> I think I'm right in saying that to put desktop shortcuts (launchers) on  the gnome desktop there is a need to use an extension but as I don't  use gnome I am not sure  exactly how that is done or which extension you  will need to add.

Ubuntu developers have a Gnome extension that does this. It is installed by default. I have three icons on my desktop. A folder icon that opens the file manager at my home folder. Courtesy of Ubuntu developers. An icon for the rubbish bin. In Ubuntu 21.10 it gets transferred on to the launcher. And an icon for a Windows program that I am running through Wine.

This Windows program will load from the launcher icon. To get it loading from the desktop icon I had to click it and select Allow Launching. Perhaps that is what I am failing to do in my experiments. And they are just that. Experiments. I am not the OP.

Regards

---

### Post by grahammechanical on 2021-10-04
I really do not know why I am experimenting with this. Perhaps I am transitioning from depression to manic. Do not worry. Mr Grumpy will be back tomorrow. Oh, it is already tomorrow where I am. Grrr. :)

I have had partial success. I can get a working Firefox icon on the desktop but I cannot get it to load to a particular web address. Perhaps the answer is to install another web browser and change it's home page to the particular web site.

Use the file manager (Files) and go to /usr/share/applications/firefox.desktop. Use Files Copy to>Desktop. That will put a Firefox icon on the Desktop. Click the icon and select Allow Launching. Now you have a Firefox icon on the desktop that launches Firefox. The file firefox.desktop is a text file so it can be edited to change the icon name. Look for [Desktop Entry]. Under that look for Name=  edit what comes next to your preferred icon name.

Under the heading [Desktop Action new-window] I have tried adding Exec=https://www.web site address. But that does not work. It has been an interesting distraction. And to think that I do not particularly like icons on the desktop!

Regards

---

### Post by monkeybrain20122 on 2021-10-04
Well I don't like littering my desktop with random launcher icons like Windows and I use unity. But as an experiment I logged into gnome shell just  for the hack of it (man it is so sluggish and awkward). It doesn't work with nautilus, but it works if you use nemo to handle the desktop. I made a desktop launcher to google earth from Firefox like grahammechanical's link and it works if nemo is made to handle the desktop.

Instructions [here]("https://www.reddit.com/r/UsabilityPorn/comments/a3fnoa/gnome_tip_using_nemo_as_a_desktop_icons_manager/"). It is really pretty simple. You need this additional step to make nemo the default file manager. In the terminal run

```
xdg-mime default nemo.desktop inode/directory application/x-gnome-saved-search
```

If nemo is not refreshing after contents of folder change,

add this line to /etc/sysctl.conf and reboot


```
fs.inotify.max_user_watches=524288
```


BTW nemo is just a fork of old nautilus before gnome ripped out all the useful functions and made it a pain to use. So it certainly integrates well and is much more functional.

P.S the desktop icons work in unity, I think because I already made nemo the default file manager and it was configured to autostart when unity was installed, but I had to do it again in gnome session.
There is an option in gnome-tweak-tools to enable desktop icons but only for file manager and trash. I never know what is the use for trash anyway and  file is already pinned to the dock so that is kind of useless.

---

### Post by angel mike on 2021-10-05
Thanks all for taking the time to reply. I have been using Ubuntu for a number of years but I think it's time for a change! Cannot agree more with ajgreeny comments so will give Xubuntu a go.
Will make this reluctantly  'solved' 
Thanks again

---

### Post by angel mike on 2021-12-15
I have finally solved the ' Drag & Drop' from a web page to the desktop in Ubuntu 20.04 using the method in this link [https://sudofry.com/2020/06/02/restore-drag-drop-in-ubuntu-20-04](https://sudofry.com/2020/06/02/restore-drag-drop-in-ubuntu-20-04). It uses nemo.

---

