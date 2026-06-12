---
title: "GNOME changed theme and background after I restarted"
date: 2011-09-24
forum: Desktop Environments
---

### Post by CrimpJiggler on 2011-09-24
Yesterday I spent ages downloading themes and modifying GNOMEs appearance and eventually had it looking cool. Now I booted up my comp and everything has changed. The GTK theme has changed to a boring gray theme with the default icons. Weirdly enough the background picture didn't revert to the default Ubuntu background, instead it changed to a background I downloaded and tested yesterday. Also there are no icons on my Desktop, if I point nautilus to /home/me/Desktop then I can see all the folders and stuff on it but when I minimize all the windows and look at the desktop normally, its empty.  When I booted my comp up I got a message saying something like "You're graphics hardware may not be able to support GNOME 3" or something. I tried rebooting but it didn't change anything. 

[IMG]http://img16.imageshack.us/img16/9869/screenshotjt.png[/IMG]
as you can see there, I'm only running GNOME 2.32.1, I suspect this is the problem, maybe when I set the appearance yesterday, I was using GNOME 3. See the workspace selector at the bottom right corner of the screen? The one I had yesterday was the newer one where the squares are 2x2 rather than 1x4.  Heres another screenshot:
[IMG]http://img27.imageshack.us/img27/4390/screenshot2hp.png[/IMG]
as you can see there are no folders or files showing up on my Desktop, just the background image but when I go to the desktop with nautilus, you can see all the items. The background picture, I found out its stored in my home folder as Firefox_wallpaper.png. Yesterday I couldn't change the wallpaper directly from firefox, instead I had to save the picture then use image viewer to set it as my background. The problem must be that Ubuntu has reverted to using GNOME 2 instead of 3 for some reason. Any idea how to fix this?

---

### Post by user sam on 2011-09-24
Um, I'm not entirely understanding. Are you saying you tried to upgrade to gnome3? Gnome3 doesn't like to be configured at this point. It might help if you detailed exactly what it was that you did, though I could be mistaken.
Sorry, you seemed to have changed it just as I posted.
Try looking at gconf-editor. go to the nautilus section, I believe it is under apps, and make sure the "manage desktop" thing works. Sorry, I'll have to get back to you with more information if I get it.

---

### Post by Blasphemist on 2011-09-24
Since we know one of the things you last messed with was Grub, let's start there unless you know what else you may have changed. Did you change any kernel mode settings for graphics in Grub? These days graphics settings get passed from bios to grub to the kernel and on. In grub2 the file where you should change these settings if needed is /etc/default/grub

This is the grub2 current documentation. [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

This is the grub2 bible thread. [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Blasphemist on 2011-09-24
I didn't see your edit before my first post. What version of Ubuntu are you using? Did you install Gnome shell yourself at some point? If you are running oneiric and installed gnome shell in that, how did you do it?

---

### Post by CrimpJiggler on 2011-09-24
> **user sam said:**
> Um, I'm not entirely understanding. Are you saying you tried to upgrade to gnome3? Gnome3 doesn't like to be configured at this point. It might help if you detailed exactly what it was that you did, though I could be mistaken.
Sorry, you seemed to have changed it just as I posted.
Try looking at gconf-editor. go to the nautilus section, I believe it is under apps, and make sure the "manage desktop" thing works. Sorry, I'll have to get back to you with more information if I get it.
No I just installed Ubuntu 11.04 yesterday and I modified its appearance. To modify its appearance I downloaded a few GTK2 and GTK3 themes from gnome-looks.org and installed them. To modify the login screens background I installed ubuntu-tweak. Does GNOME 3 come with Ubuntu 11.04?

> **Blasphemist said:**
> Since we know one of the things you last  messed with was Grub, let's start there unless you know what else you  may have changed. Did you change any kernel mode settings for graphics  in Grub? These days graphics settings get passed from bios to grub to  the kernel and on. In grub2 the file where you should change these  settings if needed is /etc/default/grub

No, I reinstall Ubuntu every couple of months or so that GRUB problem I had was on a previous install. The problem I have now is with Ubuntu 11.04 that I installed yesterday.

> **Blasphemist said:**
> I didn't see your edit before my first post.  What version of Ubuntu are you using? Did you install Gnome shell  yourself at some point? If you are running oneiric and installed gnome  shell in that, how did you do it?
Yesterday I was trying to install custom login screens from gnome-looks.org but found out that I can't do that with the new version of GNOME or whatever. I started following a tutorial which supposedly tells you how to install custom login screens on Ubuntu 11.04, heres the command history:
>   31  sudo apt-get install gnome-tweak-settings
   32  sudo add-apt-repository ppa:ricotz/testing
   33  sudo add-apt-repository ppa:gnome3-team/gnome3
   34  sudo apt-get update
   35  sudo apt-get install gnome-tweak-settings
   36  sudo apt-get install gnome-tweak-tool

The gnome-tweak-settings package couldn't be found even after adding those repositories. I dunno what the hell that ricotz/testing repository is. gnome-tweak-tool installed but I don't know what it is, there was more to this tutorial I just stopped at that cuz I was tired and went to bed.

---

### Post by CrimpJiggler on 2011-09-24
I just came across this article:
[http://www.techdrivein.com/2011/05/do-not-install-gnome-shell-in-ubuntu.html](http://www.techdrivein.com/2011/05/do-not-install-gnome-shell-in-ubuntu.html)
according to that article, GNOME 3 isn't installed in Ubuntu 11.04 by default. I checked to see if gnome-shell is installed and it is. Is this the problem? I really don't wanna reinstall Ubuntu again. Took me ages to do it yesterday cuz I setup a few VMs too. 

EDIT: I installed ppa-purge and am gonna get rid of those 2 repositories (ppa:ricotz/testing and ppa:gnome3-team/gnome3) that I added yesterday. Worst comes to worst I'll just reinstall Ubuntu but I'd prefer not to so if theres any potentially destructive solution you may have, please share them cuz I have nothing to lose at this point.

---

### Post by Blasphemist on 2011-09-24
> **CrimpJiggler said:**
> No I just installed Ubuntu 11.04 yesterday and I modified its appearance. To modify its appearance I downloaded a few GTK2 and GTK3 themes from gnome-looks.org and installed them. To modify the login screens background I installed ubuntu-tweak. Does GNOME 3 come with Ubuntu 11.04?

No, Gnome 3 does not come with 11.04. It is being tested and made available with 11.10 that will release in about 3 weeks but is beta now. I don't think I'd recommend it for you. I don't know how you went about installing Gnome 3 and the only time I tried it with 11.04 I installed an live cd that already had it added, and that still broke for me.
> No, I reinstall Ubuntu every couple of months or so that GRUB problem I had was on a previous install. The problem I have now is with Ubuntu 11.04 that I installed yesterday.
I misunderstood your problem.
> Yesterday I was trying to install custom login screens from gnome-looks.org but found out that I can't do that with the new version of GNOME or whatever. I started following a tutorial which supposedly tells you how to install custom login screens on Ubuntu 11.04, heres the command history:
I'd hold off on that if I were you. 11.10 is moving from GDM to LDM for that screen. I haven't tried modifying that screen myself.
> The gnome-tweak-settings package couldn't be found even after adding those repositories. I dunno what the hell that ricotz/testing repository is. gnome-tweak-tool installed but I don't know what it is, there was more to this tutorial I just stopped at that cuz I was tired and went to bed.
I think you were getting some Gnome 2 and some Gnome 3 things mixed. I'm not surprised there are some issues now. Given that you just installed yesterday, I think I'd reinstall. If you want the latest and greatest including Gnome 3 (I do run it and like it on 11.10 but I don't use it as my main disto), install 11.10 beta 2. If you want Gnome 2 and the ability to use more documentation from the longer use it has had, install 11.4. 11.4 also includes unity. Have you tried it?

I guess my summary is reinstall and then be careful and understand your customization efforts as you do it.

---

### Post by CrimpJiggler on 2011-09-24
Yeah I tried unity and I hate it. Probably like using macs, I'm just not used to it so have to learn everything from scratch.

---

### Post by CrimpJiggler on 2011-09-25
I deleted those packages and now when I boot up my comp, the correct modified login screen background shows up but now theres a new problem. There is no top bar or bottom bar anymore. ALT + F2 won't work so to start programs I have to go into usr/bin and launch gnome-terminal from there. Luckily ALT + TAB works so I can switch between programs. In the past I've ran into this problem from time to time but all I had to do was reboot my comp and the top bar + bottom bar would come back. Any of you know what program is responsible for the top bar and bottom bar as well as the ALT + H2 shortcut? I can use all the programs normally its just I'm kinda crippled without the taskbars especially since ALT + F2 doesn't work.

EDIT: I'm googling to try and find info on this specific problem and noticed someone mentioned gnome-panel. I checked to see if it was running on my comp but it wasn't even installed. Just installed it and ran it and now everything is working again!

---

