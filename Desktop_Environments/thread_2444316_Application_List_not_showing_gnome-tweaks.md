---
title: "Application List not showing gnome-tweaks"
date: 2020-05-28
forum: Desktop Environments
---

### Post by johnnymcc on 2020-05-28
I'm running 20.04 now and didn't like the colors so I installed gnome-tweaks (Name=Tweaks).  It's .desktop file is in "/usr/share/applications" but it isn't listed in the application list.  What determines what applications are in the list?  "/usr/share/applications" has many more desktop files than are in the list.  Any ideas?  I've googled everything I can think of and I get lots of things about how to add a desktop file, but very little on the application list.

Thanks,
John

---

### Post by Dennis N on 2020-05-28
Which applications list? There is an applications menu in the top panel that lists applications by category, and there is the Applications Overview screen you see when pressing "Show Applications" icon on the dock. In the menu, it's under 'Utilities' category - you may have to scroll down to see it. In the Overview, are you using the pager on the right to see additional icons? Is the selector at the bottom set to 'All' and not to 'Frequent'?

As to desktop files, a desktop file can be set not to display the application in menus and search.

---

### Post by Frogs Hair on 2020-05-28
Try to open tweaks from the terminal and post any errors. If the application opens pin to favorites. ```
gnome-tweaks
```

---

### Post by johnnymcc on 2020-05-28
I was referring to the Applications Overview.  I've checked both pages of "All".  It's not there.  If I run the program in terminal, it runs and I can add to favorites, but I really don't want it there.  I can't find the applications menu with categories.

It does show up in Settings > Applications.

---

### Post by Dennis N on 2020-05-28
> **johnnymcc said:**
> I was referring to the Applications Overview.  I've checked both pages of "All".  It's not there.  If I run the program in terminal, it runs and I can add to favorites, but I really don't want it there.  I can't find the applications menu with categories.

It does show up in Settings > Applications.
I think you might find it not listed separately, but under 'Utilities'. I see it there. See screenshot 1 attached. 
Also, the quick way to get to it is to start typing 'Tweaks' in the search box at top of Overview Screen. See screenshot 2 attached.

The 'Applications' menu I referred to I now realize is a gnome-shell extension. You can install it if you like. I think it's useful because it organizes by categories. Get **Applications Menu** by fmuellner

---

### Post by johnnymcc on 2020-05-28
Yes it does show up as soon as I type T in the search box.  But it's not in Utilities for me.  Frankly, Tweaks doesn't seem to allow changing enough to make it all that useful, but I will experiment more.  It's more a mystery now why it doesn't show up and I'm trying to figure out if it's something in the .desktop file that tells it not to appear in the Overview.

---

### Post by Dennis N on 2020-05-28
I think anything with a .desktop file in one of the standard locations for .desktop files would display, as long as the .desktop file itself didn't prohibit the display of that application. Here's an example. Note the line 'NotShowIn=KDE;GNOME;' keeps this application from showing in the Gnome applications list. Instead, it is found under Settings.


```
dmn@Sydney-VM:/usr/share/applications$ cat system-config-printer.desktop 
[Desktop Entry]
Name=Printers
GenericName=Printers
X-GNOME-FullName=Printers
Comment=Configure printers
Exec=system-config-printer
Terminal=false
Type=Application
Icon=printer
StartupNotify=true
[COLOR="#FF0000"]NotShowIn=KDE;GNOME;[/COLOR]
X-Ubuntu-Gettext-Domain=system-config-printer
Categories=GNOME;GTK;Settings;HardwareSettings;X-GNOME-Settings-Panel;X-Unity-Settings-Panel;System;Printing;
X-GNOME-Settings-Panel=printing
X-Unity-Settings-Panel=printing
Keywords=Printer;Queue;Print;Paper;Ink;Toner;
X-Desktop-File-Install-Version=0.24


```Sorry, I can't tell you why your Tweaks Icon wouldn't display in the array of application icons. It's not normal. But also check the 'Sundries' icon, although that seems unlikely it would be there.

BTW, the icons like 'Utilities' that group several applications are called AppFolders. You can create them with your own categories, but I haven't done that myself. I usually use the search box to run something.

---

### Post by johnnymcc on 2020-05-29
Here's what installed by default (Sorry I don't know how to make a code box):

```
john@desktop02:/usr/share/applications$ cat org.gnome.tweaks.desktop
[Desktop Entry]
Name=Tweaks
Comment=Tweak advanced GNOME 3 settings
# Translators: Do NOT translate or transliterate this text (this is an icon file name)!
Icon=org.gnome.tweaks
Exec=gnome-tweaks
Terminal=false
Type=Application
StartupNotify=true
StartupWMClass=gnome-tweaks
Categories=GNOME;GTK;Settings;
# Translators: Search terms to find this application. Do NOT translate or localize the semicolons! The list MUST also end with a semicolon!
Keywords=Settings;Advanced;Preferences;Extensions;Fonts;Theme;XKB;Keyboard;Typing;
OnlyShowIn=GNOME;Unity;Pantheon;
X-Ubuntu-Gettext-Domain=gnome-tweaks
```

Thanks for your help anyway.   The way it is isn't killing me.  I've made changes by using gsettings that Tweaks can't do anyhow.  I set my desktop to a fixed color that looks okay and still allows seeing the desktop icon text.

---

### Post by johnnymcc on 2020-05-31
In summary. Gnome works fine in 20.04 but the customization tools need lots of work.  I still don't know the difference between the gnome-tweaks and gnome-tweaks-tools packages.  I have both and only have Extensions in the applications overview.  The Extensions app lists all kinds of extensions that I can't turn on.  I presume it's because they are not installed.  I've tried several things I see on the net to install extensions and usually the procedure doesn't agree with what I see, so I can't follow it.  Hopefully future updates will improve things.  Normally I wouldn't install an LTS so soon after release, but I got a new (used) machine and I didn't want to install 18.04.

---

### Post by Dennis N on 2020-05-31
For 'gnome-tweaks-tools' I get 'no application found' when searching the Software Store so can't duplicate that finding.

In Ubuntu 20.04, extensions can only be installed using your web browser from the gnome-shell extensions web page.  

The extensions app that's included with 20.04 can only configure an extension (if available), or switch it on/off, or remove it. On my system, all the items shown in the Extensions app are installed. There are two groups - manually installed (I added them) and built in. See attached image. I don't have any that can't be switched on (they are all on already) so can't explain that.

Install extensions from this web site:
[Gnome Shell Extensions]("https://extensions.gnome.org/")

---

### Post by johnnymcc on 2020-06-01
Sorry.  It's gnome-tweak-tool.  

john@desktop02:~$ dpkg -l | grep tweak
ii  gnome-tweak-tool                           3.34.0-2ubuntu1                            all          adjust advanced settings for GNOME - transitional package
ii  gnome-tweaks                               3.34.0-2ubuntu1                            all          tool to adjust advanced configuration settings for GNOME
ii  mousetweaks                                3.32.0-2                                   amd64        mouse accessibility enhancements for the GNOME desktop
john@desktop02:~$ 

I've tried the extensions web site.  I don't remember exactly why I bailed on it.  I'll try it again.

---

### Post by Dennis N on 2020-06-01
look at: **apt show gnome-tweak-tool**
Essentially, it's a package that installs gnome-tweaks. It exists just to provide smooth upgrades from previous Ubuntu releases where Gnome Tweaks was named Gnome Tweak Tool.
You can remove gnome-tweak-tool package without any harm.


Extensions that won't turn on: If you upgraded from 19.10 some extensions may carry over and require updating or no longer be supported and should be removed  (check status from the extensions web site, look at 'Installed Extensions'). If so, they might not turn on, but that's just speculation on my part.

---

### Post by johnnymcc on 2020-06-01
My mistake.  it was "gnome-tweak-tool".

In the process of trying to get something working right, I had installed "gnome-shell-extensions".  That's why I had so many extensions listed.  None of them would turn on in the Extensions app.  So I purged gnome-shell-extensions and the list shortened back to what I originally had after the Ubuntu install.  I went into the Extensions web site, found the Applications Menu and installed it.  I can turn the switch to On in the web site, but if I leave the page and go back it's off again.  At the end of the line after the On/Off switch is  a red X box whose hover says Uninstall.  The new extension is listed in the Extensions app but also won't run on there.   I've got to be missing something.

---

### Post by Dennis N on 2020-06-01
When switched on, you should see 'Applications' on the top panel on the left (see screenshot). Sometimes you may have to reboot to get an extension to work. Try that. (Note: 'Places' in the screenshot is from a separate extension that I installed, not part of the applications menu). The 4 dots at extreme left are the shortcut to overview screen.

There are many different menus styles to choose from - all are extensions. Just search for 'menu' on the gnome shell extensions web site to find them.

---

### Post by johnnymcc on 2020-06-01
I can install an extension with the web site, but they won't turn on, even after a reboot.  This is a fresh 20.04 install.   I'm not worried about any tweaks app until I can figure out why I can't get new extensions to work.  I've uninstalled both tweak packages.  Interestingly enough, the Extensions app is still there.

With the extensions web site, there appears to two ways to install an extension.  One is to specify Gnome and extension version and a download of tar starts.  I didn't know what to do with that, but then I found that if you just click the On switch it offers to install the extension.  When I do that it's added to the list and the switch appears to turn on but it's not real.  If I go to my installed list, the switch is off and there's a red X box to uninstall.  Needless to say, I never see the 'Applications' since the extension is never really on.  

Since you've been helping me with this, I assume you've sucessfully done this on 20.04.  There's nothing I can think of to do as far as diagnosing what is happening.  Can you think of anything to check?  If I knew that this was something that doesn't work on 20.04 yet, I could wait, but if this should work for me now, I've got something wrong that could bite me later.

---

### Post by Dennis N on 2020-06-01
> just click the On switch it offers to install the extension.
This is the way to go. It gives you a correct and latest version of the extension to match the gnome-shell version in your Ubuntu. And installs it too, as you said.

If you try a different menu, do you still have a problem?
Try **Arc Menu**. I have it working on another OS. It's similar to Applications Menu (maybe even nicer), and I like it as well.

Other actions:
Wait until another user gives you better advice.
Google your problem and see if anything useful appears.
Drastic, but a reinstall may do it.

---

### Post by johnnymcc on 2020-06-01
I've tried other extensions.  None work.  I Googled first and came here to the forum later.  Your help is greatly appreciated, but I think I have really two options left.  They are to wait and see if updates fix it or reinstall Ubuntu.  Since all of my applications work, I'd rather wait and hope no other issues will appear.  Just a gut feel tells me a reinstall won't be any different.

---

### Post by Dennis N on 2020-06-02
Ubuntu 20.04 comes with Extensions 3.36.1
I notice there is a newer version 3.36.2 available as a Flatpak package. Visit [Flathub]("https://flathub.org/home") for quick Flatpak setup instructions if you want to give it a shot. Possibly a bug fix. I have it installed now. I didn't do anything about the older version, and notice there is still only one 'Extensions' Icon, so the old one is suppressed somehow. Proof of new version attached. This should update as newer versions appear. Ubuntu version may not.

---

### Post by johnnymcc on 2020-06-02
Thanks, I made another thread since this thread started about tweaks.  I'll see if anyone else has any ideas before I try a Flatpak.  I've been using Ubuntu for over 10 years and I've never heard of it.

---

### Post by Dennis N on 2020-06-02
> **johnnymcc said:**
> Thanks, I made another thread since this thread started about tweaks.  I'll see if anyone else has any ideas before I try a Flatpak.  I've been using Ubuntu for over 10 years and I've never heard of it.

I see it. I hope someone steps up. Flatpak is a packaging system similar in purpose to Snap, just made differently. It's well supported by Ubuntu.

---

### Post by johnnymcc on 2020-06-06
Since I've extensions working now, I installed the Application Menu extension and installed gnome-tweaks.  Tweaks show up under System Tools in the Applications list, but still not in the pages of apps when I click Show Applications.  How does gnome know whether an app should show up on those pages or not?  I've looked at many .desktop files and can't see any clue.  Some of the other apps under System Tools are in the "Show Applications" pages.

It appears that the category labeled System Tools in the Application Menu extension is actually defined by category Settings in the .desktop file.

---

### Post by tea for one on 2020-06-06
Show Applications > Utilities > Tweaks (together with Terminal, Calculator, System Monitor and many more)

---

### Post by johnnymcc on 2020-06-06
Thanks, I didn't know I had to scroll down in the Utilities group.   There's no side scroller.  I had to use my mouse wheel.  I figured that out when the 12 items shown ended at "Logs" and were in alphabetical order.  I still would like to know how the Applications Overview knows to put this in the Utilities group.  This info doesn't appear to be in the .desktop file, unless there is is an inference there that I'm not seeing.

---

### Post by tea for one on 2020-06-07
> **johnnymcc said:**
> Thanks, I didn't know I had to scroll down in the Utilities group.   There's no side scroller.  I had to use my mouse wheel.  I figured that out when the 12 items shown ended at "Logs" and were in alphabetical order.  I still would like to know how the Applications Overview knows to put this in the Utilities group.  This info doesn't appear to be in the .desktop file, unless there is is an inference there that I'm not seeing.

I don't know exactly why certain applications are grouped in Utilities but, I would imagine that it is an upstream GNOME decision.

[https://wiki.gnome.org/Apps#Utilities](https://wiki.gnome.org/Apps#Utilities)

---

### Post by Dennis N on 2020-06-07
> **tea for one said:**
> I don't know exactly why certain applications are grouped in Utilities but, I would imagine that it is an upstream GNOME decision.

It's determined by three things:
1) specified by Categories.
2) specified explicitly by Application Name.
3) apps that fit the Categories criteria can be explicitly excluded from showing.

On my system, I found that some specified explicitly were not installed, so don't appear.

See: dconf-editor > /org/gnome/desktop/app-folders/folders/Utilities/

---

### Post by johnnymcc on 2020-06-08
Thanks, Dennis.  So the install process must be inserting things into this list.

---

### Post by Dennis N on 2020-06-08
> **johnnymcc said:**
> Thanks, Dennis.  So the install process must be inserting things into this list.
Yes it should do that if the application installed is a utility.  
Did you know you can also just drag and drop tiles onto the Utilities App Folder tile? Or drag them off the tile to have them display separately? 
Doing these things must cause the list to be updated.

---

