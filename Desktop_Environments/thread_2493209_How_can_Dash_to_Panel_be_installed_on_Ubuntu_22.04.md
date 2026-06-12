---
title: "How can Dash to Panel be installed on Ubuntu 22.04.3?"
date: 2023-12-06
forum: Desktop Environments
---

### Post by kotgc on 2023-12-06
[COLOR=#0C0D0E][FONT=-apple-system][https://extensions.gnome.org/extension/1160/dash-to-panel/](https://extensions.gnome.org/extension/1160/dash-to-panel/)[/FONT][/COLOR]

[LIST]
[*]I've installed gnome extensions or shell.
[*]I've downloaded the Dash to Panel zip file. This file is downloaded dash-to-paneljderose9.github.com.v59.shell-extension.zip
[*]I've rebooted Ubuntu
[*]there's no option to move the Top Bar thingy into the Dock down the bottom...it wastes previous space and blocks dragging windows along monitors.
[*]The documentation doesn't help, just says how to use CLI to install gnome shell or extensions.
[*]Can't find a clear video guide on it, the install just works on videos but not on my Ubuntu.
[*]Chromium browser has GNOME Shell installed.
[*]Ubuntu Dock has been moved by Ubuntu's Settings to the bottom and autohide
[*]It's this superfluent Dash Panel thingy at the top of Ubuntu, taking up valuable monitor space and bumps windows when I drag them from monitor 1-3 and vice versa. The top panel thingy needs to be merged into the Dock at the bottom.
[*]The Dash-to-panel website says I've install GNOME Shell integration is running.
[*]I ran: sudo apt-get install chrome-gnome-shell sudo apt-get install gnome-browser-connector
[*]Chrome extensions says: GNOME Shell extensions website Has access to this site
[*]I'm researching what Extension Manager is [https://itsfoss.com/extension-manager/](https://itsfoss.com/extension-manager/), however this seems to not solve the issue and rather than this work-around, I'm sure there's a clearer path with fewer steps to install and run.
[/LIST]

---

### Post by Dennis N on 2023-12-07
First, install **gnome-shell-extension-manager**
Open it, and use the "browse" button on top bar to search for the "Dash to Panel" Extension (see screenshot)
Click on "install".
To configure the extension, click on the "installed" button on top bar and locate the extension. Click the gear icon to configure.
Switch it on if it's not already on.

---

### Post by kotgc on 2023-12-08
I think gnome-shell-extension-manager is installed.
As per Dash-to-Panel [website]("https://extensions.gnome.org/extension/1160/dash-to-panel/"), it asks you to install this Gnome Extension thingy. So I did that and the website confirms this Gnome Extension thingy is installed and running.
[IMG]https://i.imgur.com/IO8936v.png[/IMG]

I then also view the Browser Extensions window which shows:
Gnome Shell Extensions is installed (shown below). When I select this extension, this extension opens the Dash-to-Panel website (shown above):
[IMG]https://i.imgur.com/a9OZdSw.png[/IMG]

None of these windows show any option to turn on/toggle on anything?

---

### Post by Dennis N on 2023-12-08
That image is not from Gnome Shell Extension Manager. To be sure you have it, run:
```
sudo apt install gnome-shell-extension-manager
```
If you have it already, it will tell you it's already installed. Otherwise you need to go ahead and install it.

When launched,  Gnome Shell Extension Manager will first show a window like the attached image below.
Follow the steps in post #2 to install the Dash to Panel extension.

The instructions you are looking at are obsolete. Disregard them. That was the way it was done several years ago. It doesn't work any longer with the Firefox browser that Ubuntu supplies. So now we use this new utility which is much easier.

---

### Post by kotgc on 2023-12-09
Yes, gnome-shell-extension-manager is installed.
Although I'm not sure if it's running? In Chromium browser, I select Extensions -> GNOME Shell integration.
I don't see that screenshot you have shown?

---

### Post by Dennis N on 2023-12-09
> **kotgc said:**
> Yes, gnome-shell-extension-manager is installed.
Although I'm not sure if it's running? In Chromium browser, I select Extensions -> GNOME Shell integration.
I don't see that screenshot you have shown?
The gnome shell extension manager is not part of any browser. It's a separate application. You would launch it from the Activities Overview. See the screenshot. If you see two icons like the screenshot, launch the blue one labeled "Extension Ma..". The name is truncated to fit. 

The green one is an older application that can't search for and install extensions as the blue one can. (I should really uninstall it)

---

### Post by kotgc on 2023-12-10
Yes, Ubuntu 22.04.3 shows the Extension Manager is install, although a search for 'dash to panel' has no results?
[IMG]https://i.imgur.com/frExiWA.png[/IMG]
[IMG]https://i.imgur.com/vZKiHxY.png[/IMG]
[IMG]https://i.imgur.com/a4HadkF.png[/IMG]

---

### Post by tea for one on 2023-12-10
> **kotgc said:**
> Yes, Ubuntu 22.04.3 shows the Extension Manager is install, although a search for 'dash to panel' has no results?
The search box is not the most accurate in this 22.04 extension, but it is improved in later versions.

Open the Extension Manager (Blue Icon as mentioned by Dennis N)
Choose [COLOR="#0000FF"]Browse[/COLOR] mode.
To the right of the search box, there is a drop down arrow.
Select [COLOR="#0000FF"]Name[/COLOR] or [COLOR="#0000FF"]Downloads[/COLOR]
Type Dash in the search box.
Any good?

---

### Post by Dennis N on 2023-12-10
If it helps you find the extension, I get it to show as the first result when I sort by Relevance.

---

### Post by tea for one on 2023-12-10
@Dennis N
Which version of gnome-shell-extension-manager do you have?

On Ubuntu 22.04, I have version 0.3 and it only displays four search options:-
Popularity
Downloads
Recent
Name

---

### Post by Dennis N on 2023-12-10
> **tea for one said:**
> @Dennis N
Which version of gnome-shell-extension-manager do you have?

On Ubuntu 22.04, I have version 0.3 and it only displays four search options:-
Popularity
Downloads
Recent
Name

When I checked, I discovered I had installed it as a Flatpak. It is version 0.4.3:

```
         ID: com.mattjakeman.ExtensionManager
         Ref: app/com.mattjakeman.ExtensionManager/x86_64/stable
        Arch: x86_64
      Branch: stable
     Version: 0.4.3

```

Looking further, the Flatpak was last updated Nov 8, 2023, while the Ubuntu repository shows: 0.3.0-0ubuntu2.1

If necessary, the OP could remove the repository version and install the Flatpak.

---

### Post by tea for one on 2023-12-10
> **Dennis N said:**
> When I checked, I discovered I had installed it as a Flatpak. It is version 0.4.3:
I have the regular deb package 0.3 in Ubuntu 22.04

I notice from the developer's website [https://github.com/mjakeman/extension-manager](https://github.com/mjakeman/extension-manager)
Version 0.4.0 in 23.04
Version 0.4.2 in 23.10
> **Dennis N said:**
> If necessary, the OP could remove the repository version and install the Flatpak.
Yes, indeed, the website mentions "Flatpak is the recommended way to install Extension Manager"

---

### Post by Dennis N on 2023-12-10
Follow up:

If you want to continue, and install the Flatpak version of gnome-shell-extension-manager, let us know for info on how to switch.

---

### Post by kotgc on 2023-12-21
This fixed it (as per Post 8).
I had to select Downloads and enter Dash To Panel.
By Name, there were no results.
I installed and fixed.
Now just need the website to update the steps into a quick easy setup, rather than this epic support post.
Thanks!

---

### Post by pantazi on 2023-12-21
There are many YouTube videos on this, e.g.  [https://www.youtube.com/watch?v=erwrZe_REYw](https://www.youtube.com/watch?v=erwrZe_REYw)

---

### Post by kotgc on 2023-12-21
Yes, I watched a bunch of videos, but here's the most concise process I wrote up:
[h=1][COLOR=#000000][FONT=Arial]Top bar (Dash To Panel):[/FONT][/COLOR][/h][h=2][COLOR=#000000][FONT=Arial]Move to bottom of primary monitor:[/FONT][/COLOR][/h][COLOR=#000000][FONT=Arial]Do not use the website, due to wrong and missing steps. [/FONT][/COLOR][[COLOR=#1155CC][FONT=Arial]https://extensions.gnome.org/extension/1160/dash-to-panel/[/FONT][/COLOR]]("https://extensions.gnome.org/extension/1160/dash-to-panel/")
[h=3][COLOR=#434343][FONT=Arial]Install Gnome Shell Extension Manager:[/FONT][/COLOR][/h][COLOR=#000000][FONT=Arial]Ubuntu -> Terminal -> sudo apt install gnome-shell-extension-manager.[/FONT][/COLOR]
[h=3][COLOR=#434343][FONT=Arial]Download Dash To Panel:[/FONT][/COLOR][/h][COLOR=#000000][FONT=Arial]Ubuntu -> Dock -> select Show Applications -> select Extension Manager -> select Browse -> select Downloads -> enter dash to panel -> select Install -> automatically merges dash into the Dock.[/FONT][/COLOR]
[h=3][COLOR=#434343][FONT=Arial]Hide Dock:[/FONT][/COLOR][/h][COLOR=#000000][FONT=Arial]Right click on Dock -> select Dash to Panel Settings -> Position -> Panel -> Panel Intellihide: turn on.[/FONT][/COLOR]

---

### Post by werewulf75 on 2024-05-24
Thank goodness for a good search. :) This thread solves my problem. Shall install Flatpack.

---

