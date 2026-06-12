---
title: "How to increase the size of top menu bar"
date: 2022-11-27
forum: Desktop Environments
---

### Post by satimis on 2022-11-27
Hi all,

Ubuntu 22.04 Desktop

How to increase the size of top menu bar and its font size ?

I already have following packages installed.

1)
$ apt policy gnome-tweaks ```

gnome-tweaks:
  Installed: 42~beta-1ubuntu2
  Candidate: 42~beta-1ubuntu2
  Version table:
 *** 42~beta-1ubuntu2 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages
        100 /var/lib/dpkg/status
     42~beta-1ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe i386 Packages

```

2)
$ apt policy chrome-gnome-shell```

chrome-gnome-shell:
  Installed: 10.1-5
  Candidate: 10.1-5
  Version table:
 *** 10.1-5 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe i386 Packages
        100 /var/lib/dpkg/status

```

3)
$ apt policy gnome-shell-extensions```

gnome-shell-extensions:
  Installed: 42.1-0ubuntu1
  Candidate: 42.1-0ubuntu1
  Version table:
 *** 42.1-0ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages
        100 /var/lib/dpkg/status
     42.0-1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe i386 Packages

```

$ gnome-shell --version```

GNOME Shell 42.5

```

I can't do it on Gnome-tweaks.  Please refer to attached screenshots

I found my old posting;
[https://ubuntuforums.org/archive/index.php/t-2451133.html](https://ubuntuforums.org/archive/index.php/t-2451133.html)

It seems not much help.  Please advise.  Thanks

Regards

---

### Post by tea for one on 2022-11-28
In Ubuntu 22.04, gnome-tweaks does not control gnome-extensions.
Info here [https://github.com/mjakeman/extension-manager](https://github.com/mjakeman/extension-manager) and [https://github.com/mjakeman/extension-manager/wiki/Known-Issue:-Updates](https://github.com/mjakeman/extension-manager/wiki/Known-Issue:-Updates)

Dash-to-panel and Just Perfection can manipulate the size of the top bar.

---

### Post by Dennis N on 2022-11-28
The top bar is configured by gnome-shell.css in the gnome-shell theme's folder. I increase the font size which also increases the width of the top bar to accommodate. For the the Yaru themes in Ubuntu 22.04, the gnome-shell folder is in **/usr/share/gnome-shell/theme**

Look for this near the top of the gnome-shell.css file:

```
/* Global Values */
stage {
  font-size: 12pt;
  color: #F7F7F7; }

```

The default was 10pt, I change it to 12pt. A side effect of this is that the font size in any gnome-shell drop-down menus and notifications increases too, so making it too big is undesirable. 
You may find another section of the file that sets panel witdth, but I haven't looked for it, since my objective was to just increase the font size.

---

### Post by satimis on 2022-11-28
> **Dennis N said:**
> The top bar is configured by gnome-shell.css in the gnome-shell theme's folder. I increase the font size which also increases the width of the top bar to accommodate. For the the Yaru themes in Ubuntu 22.04, the gnome-shell folder is in **/usr/share/gnome-shell/theme**

Look for this near the top of the gnome-shell.css file:

```
/* Global Values */
stage {
  font-size: 12pt;
  color: #F7F7F7; }

```

The default was 10pt, I change it to 12pt. A side effect of this is that the font size in any gnome-shell drop-down menus and notifications increases too, so making it too big is undesirable. 
You may find another section of the file that sets panel witdth, but I haven't looked for it, since my objective was to just increase the font size.
Thanks for your advice.

$ ls /usr/share/gnome-shell/theme/```

classic-process-working.svg      Yaru-dark                Yaru-purple-dark
gnome-classic.css                Yaru-magenta             Yaru-red
gnome-classic-high-contrast.css  Yaru-magenta-dark        Yaru-red-dark
Yaru                             Yaru-olive               Yaru-sage
Yaru-bark                        Yaru-olive-dark          Yaru-sage-dark
Yaru-bark-dark                   Yaru-prussiangreen       Yaru-viridian
Yaru-blue                        Yaru-prussiangreen-dark  Yaru-viridian-dark
Yaru-blue-dark                   Yaru-purple

```
No such a file.

I tried gnome-classic.css

```

/* Global Values */
stage {
  font-size: 11pt;
  color: rgba(0, 0, 0, 0.8); }

```

change 
font-size: 15pt

No effect even after reboot Ubuntu 22.04

Regards

[B][COLOR="#FF0000"]Edit
====[/COLOR][/B]
$ sudo nano /usr/share/gnome-shell/theme/Yaru/gnome-shell.css
```

/* Global Values */
stage {
  font-size: 11pt;
  color: #3D3D3D; }

```
Change 11pt to 15pt

No effect even after reboot

---

### Post by satimis on 2022-11-28
> **tea for one said:**
>  - snip -

Dash-to-panel and Just Perfection can manipulate the size of the top bar.
Could you please explain in more detail.

Thanks

Regards

---

### Post by Dennis N on 2022-11-28
> No effect even after reboot Ubuntu 22.04
Unless you are using gnome classic, gnome-classic.css is not going to have any effect.
Most of the output in your post #4 display are theme folders (for example, Yaru-bark-dark is a theme folder). Look inside them:

```

dmn@Sydney-vm:~$ cd /usr/share/gnome-shell/theme/Yaru-bark-dark

dmn@Sydney-vm:/usr/share/gnome-shell/theme/Yaru-bark-dark$ ls
calendar-today-light.svg            gnome-shell-start.svg
calendar-today.svg                  pad-osd.css
checkbox-bark-dark.svg              process-working.svg
checkbox-focused-bark-dark.svg      running-indicator.svg
checkbox-off-bark-dark.svg          toggle-off-bark-dark.svg
checkbox-off-focused-bark-dark.svg  toggle-on-bark-dark.svg
dash-placeholder.svg                workspace-placeholder.svg
[COLOR="#FF0000"]**gnome-shell.css**[/COLOR]
```

Edit the red file.

---

### Post by satimis on 2022-11-28
> **Dennis N said:**
> Unless you are using gnome classic, gnome-classic.css is not going to have any effect.
Most of the output in your post #4 display are theme folders (for example, Yaru-bark-dark is a theme folder). Look inside them:

```

dmn@Sydney-vm:~$ cd /usr/share/gnome-shell/theme/Yaru-bark-dark

dmn@Sydney-vm:/usr/share/gnome-shell/theme/Yaru-bark-dark$ ls
calendar-today-light.svg            gnome-shell-start.svg
calendar-today.svg                  pad-osd.css
checkbox-bark-dark.svg              process-working.svg
checkbox-focused-bark-dark.svg      running-indicator.svg
checkbox-off-bark-dark.svg          toggle-off-bark-dark.svg
checkbox-off-focused-bark-dark.svg  toggle-on-bark-dark.svg
dash-placeholder.svg                workspace-placeholder.svg
[COLOR="#FF0000"]**gnome-shell.css**[/COLOR]
```

Edit the red file.

$ sudo nano /usr/share/gnome-shell/theme/Yaru-bark-dark/gnome-shell.css 
```

stage {
  font-size: 11pt;
  color: #F7F7F7; }

```

Change 11pt
to 15pt

No effect even after reboot

---

### Post by tea for one on 2022-11-28
> **satimis said:**
> Could you please explain in more detail.
The links have all the detail needed.
The main point is that gnome-tweaks is not used to manage extensions in Ubuntu 22.04.
Dash-to Panel and Just Perfection have settings to adjust the size of the top panel.
You have previously installed Dash-to-Panel, so you must be aware how to change the size of the top menu bar?

---

### Post by Dennis N on 2022-11-28
Your command in post #7:
```
sudo nano /usr/share/gnome-shell/theme/Yaru-bark-dark/gnome-shell.css 
```
Are you using Yaru-bark-dark gnome-shell theme? Otherwise, the command has no effect. You must choose the folder that matches your gnome-shell theme. 
Find the gnome-shell theme in **Tweaks > Appearance**. If there is none shown, first install **user themes** gnome-shell extension, and then you can select a gnome-shell theme from the drop-down list.

The Yaru themes are the only ones that use the accent color selected in Settings > Appearance!

---

### Post by satimis on 2022-11-28
> **Dennis N said:**
> Your command in post #7:
```
sudo nano /usr/share/gnome-shell/theme/Yaru-bark-dark/gnome-shell.css 
```
Are you using Yaru-bark-dark gnome-shell theme? Otherwise, the command has no effect. You must choose the folder that matches your gnome-shell theme. 
Find the gnome-shell theme in **Tweaks > Appearance**. If there is none shown, first install **user themes** gnome-shell extension, and then you can select a gnome-shell theme from the drop-down list.

The Yaru themes are the only ones that use the accent color selected in Settings > Appearance!
It is very strange to me.

Appearance -> Shell```

Shell user-theme extension theme not enabled

```

$ apt policy gnome-shell-extensions```

gnome-shell-extensions:
  Installed: 42.1-0ubuntu1
  Candidate: 42.1-0ubuntu1
  Version table:
 *** 42.1-0ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages
        100 /var/lib/dpkg/status
     42.0-1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe i386 Packages

```
Already installed

This is a fresh installed Ubuntu 22.04 desktop on Ubuntu 22.04 USB boot stick, after failing to restore on a backup image running dd.  I ran fdisk to create a single partition on the 2TB NVME Gen 3 SSD

Regards

---

### Post by deadflowr on 2022-11-28
> Shell user-theme extension theme not enabled
Extensions are enabled in the Extensions app.
Should be installed already.
A few releases back they moved the extensions setting from Tweaks into it's own app.

---

### Post by Dennis N on 2022-11-29
Dealing with the gnome-shell extensions can be confusing.

"gnome shell-extensions" is a .deb package providing a collection of gnome-shell-extensions.
"gnome-shell-extension-manager" is a .deb package needed to handle installation and management of extensions. 

I don't see either of these on the Ubuntu 22.04 manifest, so I assume they are not installed by default (On my Ubuntu 22.04 I don't have either one installed as a .deb, but I did install the 2nd as a Flatpak). You need at least the 2nd package. 

```
dmn@Sydney-vm:~$ apt show gnome-shell-extension-manager
Package: gnome-shell-extension-manager
Version: 0.3.0-0ubuntu2.1
Priority: optional
Section: universe/gnome
Origin: Ubuntu
Description: Utility for managing GNOME Shell Extensions
 The GNOME shell extension manager is a tool for helping you manage your
 installed GNOME shell extensions.

dmn@Sydney-vm:~$ apt show gnome-shell-extensions
Package: gnome-shell-extensions
Version: 42.1-0ubuntu1
Priority: optional
Section: universe/gnome
Origin: Ubuntu
Description: Extensions to extend functionality of GNOME Shell...
```

The "user themes" extension might be in the "gnome-shell extensions" package. If not, it can be installed with the "gnome-shell-extension-manager" app.

In Ubuntu Software, install the one with the blue icon. (see screenshot)

---

### Post by satimis on 2022-11-30
> **Dennis N said:**
> Dealing with the gnome-shell extensions can be confusing.

"gnome shell-extensions" is a .deb package providing a collection of gnome-shell-extensions.
"gnome-shell-extension-manager" is a .deb package needed to handle installation and management of extensions. 

I don't see either of these on the Ubuntu 22.04 manifest, so I assume they are not installed by default (On my Ubuntu 22.04 I don't have either one installed as a .deb, but I did install the 2nd as a Flatpak). You need at least the 2nd package. 

```
dmn@Sydney-vm:~$ apt show gnome-shell-extension-manager
Package: gnome-shell-extension-manager
Version: 0.3.0-0ubuntu2.1
Priority: optional
Section: universe/gnome
Origin: Ubuntu
Description: Utility for managing GNOME Shell Extensions
 The GNOME shell extension manager is a tool for helping you manage your
 installed GNOME shell extensions.

dmn@Sydney-vm:~$ apt show gnome-shell-extensions
Package: gnome-shell-extensions
Version: 42.1-0ubuntu1
Priority: optional
Section: universe/gnome
Origin: Ubuntu
Description: Extensions to extend functionality of GNOME Shell...
```

The "user themes" extension might be in the "gnome-shell extensions" package. If not, it can be installed with the "gnome-shell-extension-manager" app.

In Ubuntu Software, install the one with the blue icon. (see screenshot)
$ apt show gnome-shell-extension-manager```

Package: gnome-shell-extension-manager
Version: 0.3.0-0ubuntu2.1
Priority: optional
Section: universe/gnome
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 429 kB
Depends: libadwaita-1-0 (>= 1.0.1), libc6 (>= 2.34), libglib2.0-0 (>= 2.63.3), libgtk-4-1 (>= 4.6.0), libjson-glib-1.0-0 (>= 1.5.2), libsoup-3.0-0 (>= 3.0.3), libtext-engine-0.1-0 (>= 0.1.1), dconf-gsettings-backend | gsettings-backend, gnome-shell
Homepage: https://github.com/mjakeman/extension-manager
Download-Size: 90.4 kB
APT-Sources: http://hk.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
Description: Utility for managing GNOME Shell Extensions
 The GNOME shell extension manager is a tool for helping you manage your
 installed GNOME shell extensions.

N: There is 1 additional record. Please use the '-a' switch to see it

```

$ apt show gnome-shell-extension-manager -a > gsemanager.txt
```

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

```

The file gsemanager.txt is attached here.

$ sudo apt show gnome-shell-extensions```

Package: gnome-shell-extensions
Version: 42.1-0ubuntu1
Priority: optional
Section: universe/gnome
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 1,165 kB
Depends: gir1.2-adw-1, gir1.2-atk-1.0, gir1.2-glib-2.0, gir1.2-gmenu-3.0, gir1.2-graphene-1.0 (>= 1.10.2), gir1.2-gtk-4.0, gir1.2-pango-1.0, gnome-session-bin (>= 3.8), gnome-settings-daemon (>= 3.24), gnome-shell (<< 43~), gnome-shell (>= 42~), gvfs (>= 1.16.0), dconf-gsettings-backend | gsettings-backend
Recommends: gnome-shell-extension-prefs
Breaks: gnome-shell-common (<< 3.18)
Replaces: gnome-shell-common (<< 3.18)
Homepage: https://wiki.gnome.org/Projects/GnomeShell/Extensions
Download-Size: 171 kB
APT-Manual-Installed: yes
APT-Sources: http://hk.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
Description: Extensions to extend functionality of GNOME Shell
 The GNOME Shell redefines user interactions with the GNOME desktop. In
 particular, it offers new paradigms for launching applications,
 accessing documents, and organizing open windows in GNOME. Later, it
 will introduce a new applets eco-system and offer new solutions for
 other desktop features, such as notifications and contacts management.
 The GNOME Shell is intended to replace functions handled by the GNOME
 Panel and by the window manager in previous versions of GNOME. The GNOME
 Shell has rich visual effects enabled by new graphical technologies.
 .
 GNOME Shell is extensible using extensions. This package contains
 official GNOME Shell extensions.

N: There is 1 additional record. Please use the '-a' switch to see it

```

$ apt show gnome-shell-extensions -a >  gsextension.txt```

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

```
The file is attached here.

Would it be the problem of "gnome-tweaks"?

Can I run following command on Terminal to uninstall it?
$ sudo apt remove gnome-tweaks -y

Regards

---

### Post by Dennis N on 2022-11-30
> Would it be the problem of "gnome-tweaks"?

Sorry, this isn't clear to me. What does 'it' refer to? Are you referring to the "WARNING: apt does not have a stable CLI interface. Use with caution in scripts."? If so, it a message you get with apt. I've seen it many times. Just ignore it.

Now, I must ask: Did you install the two packages**&#8595;** mentioned in post #12?

"gnome shell-extensions" is a .deb package providing a collection of gnome-shell-extensions.
"gnome-shell-extension-manager" is a .deb package needed to handle installation and management of extensions. 

If you have them installed, use the second one to examine the installed gnome-shell extensions and be sure "User Themes" is installed and turned ON. Then you should be able to select a gnome-shell theme from the drop box shown in post #9 attachment. They are all Yaru color themes. For uniformity, you first pick a color from Settings > Appearance. This automatically sets the Application and Icon theme to the Yaru theme with same accent color. For the gnome-shell theme, you have to manually select the matching Yaru gnome-shell theme. (Note: if your color is orange, the matching theme is just "Yaru" instead of "Yaru-orange".

---

### Post by satimis on 2022-11-30
> **Dennis N said:**
> Sorry, this isn't clear to me. What does 'it' refer to? Are you referring to the "WARNING: apt does not have a stable CLI interface. Use with caution in scripts."? If so, it a message you get with apt. I've seen it many times. Just ignore it.

Now, I must ask: Did you install the two packages**&#8595;** mentioned in post #12?

"gnome shell-extensions" is a .deb package providing a collection of gnome-shell-extensions.
"gnome-shell-extension-manager" is a .deb package needed to handle installation and management of extensions. 
I just follow you on #12 to run those 2 commands

```

Package: gnome-shell-extension-manager
Version: 0.3.0-0ubuntu2.1
Priority: optional
Section: universe/gnome
Origin: Ubuntu
....
....

```

```

Package: gnome-shell-extensions
Version: 42.1-0ubuntu1
Priority: optional
Section: univer
....
....

```

> 
If you have them installed, use the second one to examine the installed gnome-shell extensions and be sure "User Themes" is installed and turned ON. Then you should be able to select a gnome-shell theme from the drop box shown in post #9 attachment. They are all Yaru color themes. For uniformity, you first pick a color from Settings > Appearance. This automatically sets the Application and Icon theme to the Yaru theme with same accent color. For the gnome-shell theme, you have to manually select the matching Yaru gnome-shell theme. (Note: if your color is orange, the matching theme is just "Yaru" instead of "Yaru-orange".
Yes I did it as advised.  Please refer to "$ sudo apt show gnome-shell-extensions" on post #13 above

It seems it has been installed ?  But I can't select the items on Settings > Appearance
It is strange to me?  Clicking them without response

Sorry I don't know how to check;
"User Themes" turned ON ?

That was why in my previous posting asking whether I need to uninstall "gnome-tweakers" ?

Thanks 

Regards

---

### Post by Dennis N on 2022-12-01
> It seems it has been installed ? But I can't select the items on Settings > Appearance
No problem. Access Settings dialog from upper-right system menu (see screenshot 1)
Then choose "Appearance" from the left-side menu. (see screenshot 2)
Choose a Style (light or dark), then click on a color circle to select.
Quit Settings.
Open Extension Manager and check for "User Themes". Be sure it's on (see screenshot 3)
Quit Extension Manager.
Open Tweaks > Appearance. 
Choose the gnome-shell theme that matches your selected style and color.
Done.

Now you can fix the width of the top bar. Follow the previous instructions of posts #3 and #6.

---

### Post by satimis on 2022-12-01
> **Dennis N said:**
> No problem. Access Settings dialog from upper-right system menu (see screenshot 1)
Then choose "Appearance" from the left-side menu. (see screenshot 2)
Choose a Style (light or dark), then click on a color circle to select.
Quit Settings.
Open Extension Manager and check for "User Themes". Be sure it's on (see screenshot 3)
Quit Extension Manager.
Open Tweaks > Appearance. 
Choose the gnome-shell theme that matches your selected style and color.
Done.

Now you can fix the width of the top bar. Follow the previous instructions of posts #3 and #6.
Thanks for your advice.

Install gnome-shell-extension-manager

$ apt policy gnome-shell-extension-manager```

gnome-shell-extension-manager:
  Installed: (none)
  Candidate: 0.3.0-0ubuntu2.1
  Version table:
     0.3.0-0ubuntu2.1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
     0.3.0-0ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
```

Performed steps as advised.  Please refers to;
screenshot-1_55.png
screenshot-2.png
screenshot-3_user_themes.png

I select Yaru-light but can't find it on Shell -> screenshot-4.png

Only Yaru-dark there

Regards

---

### Post by Dennis N on 2022-12-01
From what I see in your images, i think you mean the style is set to light. I can also see the color is set to "Bark". So when you use Tweaks > Appearance, you see Yaru-bark automatically set as the application theme and icon theme. To match that, you want to select Yaru-bark as the shell theme as well. That gives a uniform accent color in most places. 

The exception I notice is that gnome-shell extensions don't use the selected accent color. Probably because most extensions are not made by gnome developers, and have to work with any Linux distro using gnome, not just Ubuntu.

You are free to change the icon theme to something other than a Yaru icon theme. I need to do that to get flat monochrome icons for the Audacious music player.  

Did you fix the panel width?

---

### Post by satimis on 2022-12-01
> **Dennis N said:**
> From what I see in your images, i think you mean the style is set to light. I can also see the color is set to "Bark". So when you use Tweaks > Appearance, you see Yaru-bark automatically set as the application theme and icon theme. To match that, you want to select Yaru-bark as the shell theme as well. That gives a uniform accent color in most places. 

The exception I notice is that gnome-shell extensions don't use the selected accent color. Probably because most extensions are not made by gnome developers, and have to work with any Linux distro using gnome, not just Ubuntu.

You are free to change the icon theme to something other than a Yaru icon theme. I need to do that to get flat monochrome icons for the Audacious music player.  
Noted and thanks

> 
Did you fix the panel width?
No

Tweaks
-> Top Bar
No item for changing the panel width.

Besides another strange thing happens.  The left menu bar on the screen disappears

Regards

---

### Post by Dennis N on 2022-12-02
> Tweaks
-> Top Bar
No item for changing the panel width.

Yes, there's no option to do that from Tweaks. It would be nice if there was. You have to go back to the method described in post #3 and post #6. For example, IF you have selected the light style and set the color to Bark in Settings>Appearance, and set the gnome shell theme to Yaru-bark with Tweaks, then you edit **/usr/share/gnome-shell/theme/[COLOR="#FF0000"]Yaru-bark[/COLOR]/gnome-shell.css** and make the changes to font size shown in post #3.

Other Examples:
If you chose **light style** and **Olive** as the color, then set gnome shell theme to Yaru-olive and change the folder in red in the path above to **Yaru-olive**.
If you chose** dark style** and** Olive** as the color, then set gnome shell theme to Yaru-olive-dark and change the folder in red in the path above to **Yaru-olive-dark**

Then the gnome-shell components agree with your applications theme. Harmony is good.

---

### Post by satimis on 2022-12-02
> **Dennis N said:**
> Yes, there's no option to do that from Tweaks. It would be nice if there was. You have to go back to the method described in post #3 and post #6. For example, IF you have selected the light style and set the color to Bark in Settings>Appearance, and set the gnome shell theme to Yaru-bark with Tweaks, then you edit **/usr/share/gnome-shell/theme/[COLOR="#FF0000"]Yaru-bark[/COLOR]/gnome-shell.css** and make the changes to font size shown in post #3.

Other Examples:
If you chose **light style** and **Olive** as the color, then set gnome shell theme to Yaru-olive and change the folder in red in the path above to **Yaru-olive**.
If you chose** dark style** and** Olive** as the color, then set gnome shell theme to Yaru-olive-dark and change the folder in red in the path above to **Yaru-olive-dark**

Then the gnome-shell components agree with your applications theme. Harmony is good.
Performed following steps

$ sudo nano /usr/share/gnome-shell/theme/**[COLOR="#FF0000"]Yaru-dark[/COLOR]**/gnome-shell.css```

.......
/* \Global Values */
stage {
  font-size: 11pt;
  color: #F7F7F7; }
........

```

change : 11pt
to : 30pt
(This is a 4K 32" Dell display)

save and exit

Reboot.  Now it works.  The width of the top bar increased.

Thanks

But another strange thing happened;
The left vertical menu bar on the screen disappears.  I have to click "Activities" then the menu bar appears at the bottom of the screen.

Any solution?  Thanks in advance.

Regards

---

### Post by Dennis N on 2022-12-02
> Reboot. Now it works. The width of the top bar increased.
That's good to hear. As to the new question, I think you should make a new thread since it is unrelated to the topic of this thread.

---

### Post by Claus7 on 2022-12-02
Hello,

another solution to the issue of top bar (panel) would be to go to: Settings->Accessibility and from there to enable Large text. The thing is that the enlargement achieved this way is not so great, yet it might be a compromise so as not to lose sight of the menu you mention.

Regards!

---

### Post by satimis on 2022-12-04
> **Claus7 said:**
> Hello,

another solution to the issue of top bar (panel) would be to go to: Settings->Accessibility and from there to enable Large text. The thing is that the enlargement achieved this way is not so great, yet it might be a compromise so as not to lose sight of the menu you mention.

Regards!
Hi,

Thanks for your advice.

I have tried this settings many time before, not much improvement.. This PC is connected to a Dell 32" display.

Anyway thx again for your advice

Regards

---

### Post by satimis on 2023-01-09
Hi Dennis,
 
 Again.  Just installed an Ubuntu 22.04 VM on ubuntu-22.04.1-desktop-amd64.iso
 
I can't increase the size of top menu bar
 
 $ apt policy gnome-shell-extension-manager```

gnome-shell-extension-manager:
  Installed: 0.3.0-0ubuntu2.1
  Candidate: 0.3.0-0ubuntu2.1
  Version table:
 *** 0.3.0-0ubuntu2.1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     0.3.0-0ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages

```
Already installed.

sudo nano /usr/share/gnome-shell/theme/Yaru-dark/gnome-shell.css
```

.......
/* \Global Values */
stage {
  font-size: 11pt;
  color: #F7F7F7; }
........

```

Change 11pt to 35pt

Save and exit

Reboot VM.  But there is no change on the size of top menu bar

Any suggestion?  Thanks

Regards

---

### Post by Dennis N on 2023-01-09
> Any suggestion? Thanks
Try font scaling in Tweaks > Fonts. I recently used it to make the font of the top bar larger - the width also increased. Then I needed to adjust down the other font sizes in Tweaks > Fonts. 
I now think this a better way than editing the css file.

---

### Post by satimis on 2023-01-09
> **Dennis N said:**
> Try font scaling in Tweaks > Fonts. I recently used it to make the font of the top bar larger - the width also increased. Then I needed to adjust down the other font sizes in Tweaks > Fonts. 
I now think this a better way than editing the css file.
I have to adjust;
Scaling Factor = 2.50
Font = 22

This is 4K 32" display.

Ubuntu 22.04 installed on different ISO looks differently.  I don't know why adjusting .css file without effect

Regards

---

### Post by boogaloo2 on 2023-02-12
I've tried everything in this post and many others. Spent a day trying to make the stage use Ubuntu Light AND to change the font-size. I have all the extension stuff mentioned so I am fairly certain nothing is missing... except I am running Ubuntu 18.04 LTS on i686 32-bit. So my Gnome-Shell is v3.28.4 and the extensions for shell are similar... nothing at all close to any 4.*+

My Gnome-Shell theme seems to be here: 
/usr/share/gnome-shell/theme/gnome-shell.css (and supporting icons and etc). There are no folders in /usr/share/gnome-shell/theme/ and since all that's in there are the files, it probably seems proper that no others would/should exist.

BUT -- in Tweaks under Appearance, at first the Shell option had the red triangle with !. And it didn't even drop down since "nothing was there".
So after I made sure to have all the extension stuff installed I added my own theme in /usr/share/themes/. Once I put it there, _Tweaks recognized it_ and the warning icon was gone and the dropdown was alive and listed my theme:
/usr/local/themes/Jamie-Theme/
/usr/local/themes/Jamie-Theme/gnome-shell/
/user/local/themes/Jamie-Theme/gnome-shell/gnome-shell.css

I added the css just for the stage (commented line is native from /usr/share/gnome-shell/theme/gnome-shell.css)
stage {
  font-family: Ubuntu Light, Sans-Serif;
  /* font-family: Cantarell, Sans-Serif; */
  font-size: 11pt;
  font-weight: normal;
  color: #eeeeec; }

I am using Adwaita-dark theme and while trying stuff in this thread I also added a gnome-shell/gnome-shell.css inside it after nothing else was working. Tweaks ALSO recognized that but still nothing changes the top bar font... ya, I logged out/back-in, completely rebooted et;al ad-nauseum  :)

What can I do? Even though this system is dated, it seems that I should be able to override it and things I've done have been recognized by Tweaks but nothing changes.
[I]
*The "None" button on the Shell line for theme allows me to directly assign a CSS file (such as Adwaita-dark/gnome-shell/gnome-shell.css) but after relogin and reboot it is blank again. The theme dropdown stays with what I set it at (Adwaita-dark, or my Jamie-Theme).[/I]

Appreciate any help!

---

### Post by deadflowr on 2023-02-12
Been a while since I've played with this stuff so anyway What I found was

1)enable user themes in Extensions.

2) create a file called gnome-shell.css
add this to it
```
@import url("/usr/share/gnome-shell/theme/gnome-shell.css");

#panel {
    background-color: black; 
    font-weight: bold;
    font-size: ##pt;
    height: ##pt;
}
```
Replace the ## with the number you desire.
(I believe the panel is set at around 24pt for height. for the default so adjust accordingly to what you think you want.)

Then save it into a new folder called gnome-shell and save that to a folder called my-theme.
And then save that inside of either the ~/.themes folder or ~/.local/share/themes folder

So basically the file path would be
Home > User > .themes > my-theme > gnome-shell > gnome-shell.css
or
Home > User > .local/share/themes > my-theme > gnome-shell > gnome-shell.css

After saving the file open Gnome tweaks and if you have enabled User themes it should allow you to toggle the user theme option.
Your new mytheme should now be listed.
Set the theme and see if it shows the new panel you set.

If you want to adjust it more, just edit the file and save it, then you need to toggle the theme in tweaks to a different them and then back to your mytheme again.
Or
I think you can reset gnome-shell by pressing alt+F2 and [s]typing R.[/s] Type killall -3 gnome-shell

Either way the edits will not take affect until the desktop is reset or the theme is reset.

---

### Post by boogaloo2 on 2023-02-12
Thanks for the help!

But... lol

I don't have a Home > User > .themes (does not exist)
or a
Home > User > .local/share/themes

.local/share does exist but there is no themes dir in there.

Also, in the native gnome-shell.css file the css has no class or container ID delimiter it is just  "panel { font-family... etc etc }" with no dot or #
I tried adding the # but nothing.

I also tried switching themes and back to Adwaita-dark but nothing changes.

The ONLY thing I noticed is that when I go back to Tweaks after relogin or reboot the Shell line now keeps the name of the css file I choose when clicking the button. So /usr/share/themes/Adwaita-dark/gnome-shell/gnome-shell.css stays there instead of disappearing as it was before.

Thanks again!

---

### Post by Dennis N on 2023-02-12
After I suggested modifying .css file in this thread from November, I now advocate an easier way to do this without editing any files.
1) Use the font scaling feature in Tweaks Tool > Fonts. This makes the top bar height increase along with the font.
2) Since this also increases the application fonts, compensate for this by decreasing the font size of the four items at the top of the fonts dialog.
(I now do it this way myself.)

---

### Post by satimis on 2023-02-12
> **Dennis N said:**
> After I suggested modifying .css file in this thread from November, I now advocate an easier way to do this without editing any files.
1) Use the font scaling feature in Tweaks Tool > Fonts. This makes the top bar height increase along with the font.
2) Since this also increases the application fonts, compensate for this by decreasing the font size of the four items at the top of the fonts dialog.
(I now do it this way myself.)
Hi,

Thanks for your update

I have to select 3.00 max on my 4K display.

Regards

---

