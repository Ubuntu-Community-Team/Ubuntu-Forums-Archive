---
title: "Cinnamon disable Hot corners"
date: 2013-04-12
forum: Desktop Environments
---

### Post by Redalien0304 on 2013-04-12
Trying to turn off Hot Corners in Cinnamon on Ubuntu cannot get Cinnamon settings to Run to turn off Hot Corners there, i know there is option on Cinnamon Settings but will not run. Found this but did not Work [http://misha.beshkin.lv/disable-hot-corner-hover-action-in-linux-mint-12/](http://misha.beshkin.lv/disable-hot-corner-hover-action-in-linux-mint-12/). I Know it says for Linux Mint 12 but in  the comment this is mentioned "In Mint 13, where they moved from gnome-shell to cinnamon, the configuration file is /usr/share/cinnamon/js/ui/layout.js" so i went with that. Logged out & back in nodda still there so Rebooted Hot Corner still there. Anyone any ideas? 


Dell latitude D600 2Gb Ram Ubuntu 12.04

---

### Post by Redalien0304 on 2013-04-12
So no one knows how to Disable Cinnamon Hot Corners when you cannot access the Cinnamon Settings Panel??

---

### Post by deppgirl on 2013-04-21
Right click on the menu and go to settings> all settings> Hot Corners ... you can disable it there.

---

### Post by debodas on 2013-04-21
RIght click on the panel, and there should be a way to access the cinnamon settings from there.

---

### Post by Redalien0304 on 2013-04-23
Ended up doing a Full Clean Reinstall of Ubuntu 12.04. problem now solved with hot corners. Also Power Icon shows up now on Login screen.

---

### Post by flanagan on 2013-05-17
Sorry you had to resort to going back to 12.04. I, too, feel that hot corners are a huge annoyance and waste of time. WAY too easy to accidentally hover over one, then you have to click your way out. For me, hot corners are the ultimate in lame.

That said, I edited the cinnamon layout file using "gksu gedit /usr/share/cinnamon/js/ui/layout.js" and edited the line in the init function:

From:

  this.hotCornerManager = new HotCorner.HotCornerManager();

To:

  //this.hotCornerManager = new HotCorner.HotCornerManager();

thereby commenting it out and effectively disabling the hot corner manager.


None of the other answers here make any sense, since they apply to a bygone day when there actually was a Hot Corner setting under Cinnamon Settings. I would like to know what happened to it. I would also like to find a way, if any, to make my disabling of the hot corner in the /usr/share file apply just to my account and not the other members of my family who might be annoyed with my disabling of the hot corner annoyance. (I think that would also make my change a bit more permanent for me, since undoubtedly my edit to layout.js will be overwritten once there is another system upgrade.)


Edit: Oh, and by the way, if I want to manage my workspaces I just use Ctrl-Alt-Up. I cannot think of any good reason to make workspace management a hot corner function. Then again, I cannot think of any function that would be suitable for a hot corner. But that's just me.

---

### Post by pischta on 2013-05-24
In system settings, there is an icon in the uppper right corner of the window. Click on it, and change to advanced mode. You can modify more things, for example hot corners.

---

### Post by rewyllys on 2013-05-24
In my installation of Linux Mint 13 with Cinnamon (the version is, I think, 1.2), clicking, in the Menu, on Cinnamon Settings yields a window with an icon labelled "Hot corner".  

Clicking on this icon opens another window, in which you can uncheck the option labelled "Hot corner enabled".  With that done, you've liberated yourself from the nuisance of a hot corner.  (Of course, if you like being able to switch among two or more desktops, don't uncheck the "Hot corner enabled" option.:wink:)

---

### Post by flanagan on 2013-05-24
Thanks @pischta. I did not know about the normal vs. advanced mode of system settings. That works great with no need to manually edit layout.js.

And thanks to rewyllys: I also have Linux Mint 13 on my other old laptop and the Hot Corner icon does indeed work there without unhiding it. I still disable the hot corner and use Ctrl-Alt-Up for switching between workspaces.

---

