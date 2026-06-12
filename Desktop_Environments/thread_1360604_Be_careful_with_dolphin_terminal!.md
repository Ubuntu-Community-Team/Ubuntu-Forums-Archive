---
title: "Be careful with dolphin terminal!"
date: 2009-12-21
forum: Desktop Environments
---

### Post by lovinglinux on 2009-12-21
I wasn't sure if this is the best place to post this, anyway here is the situation...

Dolphin and Konqueror have a nice docked terminal, that really helps on some file related tasks. But today I have extracted a file with special characters in a sub-folder name and I couldn't get rid of it. I knew I could remove with rm, so I copied the folder and typed rm -fr into dolphin terminal, then pasted. I don't know why, but the content of the clipboard wasn't the folder path, so it looked like this:

```
rm -fr somethingelse
```

So I clicked the Desktop folder in dolphin's file browser, to copy the parent folder of the problematic one. The problematic folder path was like this:

```
/home/lovinglinux/Desktop/extracted_folders/problematic_folder
```

The real problem begins now. Whenever you open a folder in dolphin, it enters the **cd** command in the terminal. It seems the terminal is integrated with dolphin. So when I opened the Desktop folder, it entered **cd /home/lovinglinux/Desktop** into the terminal. Since there was already a command waiting there, the result was something like this:

```
rm -fr somethingelse[COLOR="Red"]cd /home/lovinglinux/Desktop[/COLOR]
```

The worst thing is that when you change directory in the file browser, the **cd** command is executed automatically. So the result was having my entire Desktop folder completely wiped. Fortunately, there wasn't anything important there, just a video that I have spent most of my Sunday trying to re-encode due to some weird encoding issues. The thing is that if I had switched to home in dolphin file browser I would have lost EVERYTHING.

I just wanted to let other users know about this, to avoid such accidents.

---

### Post by drinkmilk on 2010-09-11
Hey,

I just checked with my Kubuntu 10.04 having and KDE 4.4.2 and the problem you describe doesn't happen there. It probably was fixed since.

---

### Post by lovinglinux on 2010-09-12
> **drinkmilk said:**
> Hey,

I just checked with my Kubuntu 10.04 having and KDE 4.4.2 and the problem you describe doesn't happen there. It probably was fixed since.

The embedded terminal doesn't even exist on KDE 4.5.

---

### Post by xircon on 2010-09-12
Err yes it does:

---

### Post by lovinglinux on 2010-09-12
> **xircon said:**
> Err yes it does:

There is something wrong with mine then. BTW, my Dolphin is crashing and freezing a lot.

How do access it?

---

### Post by xircon on 2010-09-12
Press F4

---

### Post by ankspo71 on 2010-09-12
I have similar problems like LovingLinux.

I don't like having my .macromedia there in my home folder (privacy concerns), so I tried to use the embedded terminal in dolphin to remove it. First I typed rm -rf in the terminal, then tried to drag and drop the .macromedia folder into the terminal to finish the command.

What I was expecting to find was this:
```
rm -rf '/home/james/.macromedia'
``` 
and it would have worked in any other terminal.
But what I ended up with was this :
```
rm -rf /home/james/.macromedia
```
Which would have worked too, but after pressing Enter I got this:
```
rm -rf /home/james/.macromedia^C
cd /home/james/.macromedia

```
Note that the ^C didn't appear until after I pressed Enter, and .macromedia never got deleted. No harm was done to my computer though, but I think it is a better I idea for me to stick to the separate terminal because I am accident prone. :D I think the trouble is Dolphin always assumes I am changing directories and inserts a hidden ^C in my commands.

This was done with Kubuntu Maverick Beta with KDE 4.5.1

---

### Post by lovinglinux on 2010-09-12
> **xircon said:**
> Press F4

Thanks. The shortkey works, but there is not toolbar icon anymore, even when customizing it. Do you have it?

---

### Post by ankspo71 on 2010-09-12
Hi LovingLinux,
The terminal icon in the Dolphin toolbar is not displayed by default on my Kubuntu/KDE version, but the terminal icon for Dolphin's toolbar can be enabled by right clicking on the toolbar, then click on 'Configure Toolbars', then add 'Open Terminal', however this icon only opens a new (separate) terminal window using the current directory, not the embedded terminal. 

So if you would like to launch the embedded terminal from Dolphin's toolbar you would need to add the 'panels' menu button instead so you can choose which panel to add to the GUI. (attached screenshot)

The embedded terminal can also be accessed from 
View > Panels > Terminal (F4)

Hope this helps.

---

### Post by lovinglinux on 2010-09-12
> **ankspo71 said:**
> Hi LovingLinux,
The terminal icon in the Dolphin toolbar is not displayed by default on my Kubuntu/KDE version, but the terminal icon for Dolphin's toolbar can be enabled by right clicking on the toolbar, then click on 'Configure Toolbars', then add 'Open Terminal', however this icon only opens a new (separate) terminal window using the current directory, not the embedded terminal. 

So if you would like to launch the embedded terminal from Dolphin's toolbar you would need to add the 'panels' menu button instead so you can choose which panel to add to the GUI. (attached screenshot)

The embedded terminal can also be accessed from 
View > Panels > Terminal (F4)

Hope this helps.

Weird. The "View > Panels >..." shows nothing, but I can access that menu if I click on an empty area of the main toolbar. I guess I need to purge my dolphin config files.

---

