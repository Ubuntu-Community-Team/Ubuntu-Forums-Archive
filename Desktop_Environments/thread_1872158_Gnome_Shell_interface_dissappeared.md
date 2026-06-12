---
title: "Gnome Shell interface dissappeared"
date: 2011-10-30
forum: Desktop Environments
---

### Post by Tempest42 on 2011-10-30
I'm not sure whether this problem has been posted about before, but I've been searching for a solution for a while and haven't found one.

Out of frustration with a few of the bugs associated with 11.10's Unity sidebar, I thought I'd give Gnome shell a try. In installed it without an issue through the software centre, logged out, selected the GNOME option in lightdm and then logged back in. I spent some time changing the window appearances and installed a few extensions, logging out and logging in again a few times to reset gnome shell, all without a problem.

I logged out and logged back in without changing any settings, the Gnome Shell bar flashed at the top of the screen, and then disappeared. The Nautilus menu for the desktop folder is at the top of the screen, and no other parts of the Gnome Shell interface are visible. The windows of startup applications (the only applications I can get to run) have no borders or title bars, and while they can be used for a while, they eventually they become unresponsive.  I've logged out and logged back in, reset the computer, but the problem remains.  I remember having a similar issue with Unity when I first installed 11.10, but I simply reinstalled it then, which fixed the problem.

I'm still able to log into Unity without any trouble. Is my best bet simply to re-install gnome-shell?

---

### Post by Tempest42 on 2011-10-30
When I run
```

gnome-shell --replace
```I get the following:

```
(gnome-shell:2067): Clutter-CRITICAL **: clutter_text_get_editable: assertion `CLUTTER_IS_TEXT (self)' failed

(gnome-shell:2067): Clutter-CRITICAL **: clutter_text_get_text: assertion `CLUTTER_IS_TEXT (self)' failed

(gnome-shell:2067): Clutter-CRITICAL **: clutter_text_set_text: assertion `CLUTTER_IS_TEXT (self)' failed

St-ERROR **: st_widget_get_theme_node called on the widget [0xa8c5b78 StButton.status-chooser-user-icon] which is not in the stage.

Trace/breakpoint trap
```

---

### Post by kurt18947 on 2011-10-30
I would guess one of the extensions you installed may be conflicting.  I'd think remove, restart then reinstall would be a good place to start.  That may or may not fix the conflict but it'd be an easy place to start.

---

### Post by cbowman57 on 2011-10-30
Try logging into Gnome classic & open gnome-tweak-tool, set your theme to the default, Adwaita.

Tell me what happens when you try the shell after changing the theme.

---

### Post by LinuxFan999 on 2011-10-30
I have heard that this is a common problem with 11.10.
 
Do you have the latest updates?

---

### Post by Tempest42 on 2011-10-30
> **kurt18947 said:**
> I would guess one of the extensions you installed may be conflicting.  I'd think remove, restart then reinstall would be a good place to start.  That may or may not fix the conflict but it'd be an easy place to start.

I agree, and I'll probably do this if I can't find any other solution, but I might try some other stuff first.

> **cbowman57 said:**
> Try logging into Gnome classic & open gnome-tweak-tool, set your theme to the default, Adwaita.

Tell me what happens when you try the shell after changing the theme.

I'm actually unable to install gnome-session-fallback. I get the following error after "sudo apt-get install gnome-session-fallback":

```
The following packages have unmet dependencies:
 gnome-session-fallback : Depends: gnome-session-common (= 3.2.0-0ubuntu1) but 3.2.0-0ubuntu3 is to be installed.
Unable to correct problems, you have held broken packages.
```I assumed this was unrelated, but perhaps it isn't?

> **LinuxFan999 said:**
> I have heard that this is a common problem with 11.10.
 
Do you have the latest updates?

I updated right before I installed gnome-shell earlier today.

---

### Post by cbowman57 on 2011-10-30
Boot into Recovery mode & run the option that fixes broken packages.  Sounds like something went wrong along the way.  sudo apt-get install gnome-shell should have pulled in gnome-session-fallback with it.

Are you also using some ppa's?

---

### Post by Tempest42 on 2011-10-30
> **cbowman57 said:**
> Boot into Recovery mode & run the option that fixes broken packages.  Sounds like something went wrong along the way.  sudo apt-get install gnome-shell should have pulled in gnome-session-fallback with it.

Are you also using some ppa's?

Sorry, I'm not sure which option you mean. When I boot into recovery mode, there's no option to fix broken packages. I've tried running "sudo apt-get -f install", but it does nothing.

In addition to the defaults, I'm using the following ppas:

[LIST]
[*]ppa:atareao-atareao
[*]ppa:ferramroberto-gnome3
[*]ppa:ferramroberto-java
[*]ppa:hotot-team
[*]ppa-indicator-multiload-stable-daily
[*]ppa:nilarimogard-webupd8
[*]ppa:webupd8team-jupiter
[/LIST]

---

### Post by cbowman57 on 2011-10-30
You have to run the fsck option first, after it checks the drive the dpkg option shows up.

---

### Post by Tempest42 on 2011-10-30
> **cbowman57 said:**
> You have to run the fsck option first, after it checks the drive the dpkg option shows up.

How long should fsck take? I've had it running for more than an hour on a 250 mb hard drive, and the computer doesn't appear to be doing anything (no hard-drive activity etc).

---

### Post by cbowman57 on 2011-10-30
Shouldn't take long at all.  

Was there any activity or did it just hang from the start?

---

### Post by Tempest42 on 2011-10-30
Never mind. It hadn't taken long at all, but the was stopping after fsck was finished.

I removed gnome-session-common, and re-installed it, which allowed me to install the gnome-fallback-session. I chose the "GNOME Classic" session and used the tweak tool to change the theme back to Adwaita as you suggested, but when I went back to Gnome Shell, the only difference was that instead of the nautilus menu at the top of the screen being black, it was now white.

I'm going to try removing gnome-shell and re-installing it.

---

### Post by Tempest42 on 2011-10-30
I removed and reinstalled gnome-shell, and it worked fine the first time I used it. However, after I added ppa:ferramroberto/gnome3 to the software sources and installed some of its Gnome extensions (see [here]("http://www.techdrivein.com/2011/10/7-best-gnome-shell-extensions-install.html")), I ended up with the same broken session as before. I used ppa-purge to remove the ppa and the packages, but the problem persists. Obviously they're incompatible with something, but I have no idea what that might be, and why it continues to cause problems after the extensions have been removed.

---

### Post by cbowman57 on 2011-10-30
Ok, you might want to use the Webupd8 ppa's, they haven't broken anything for me yet. :)

---

### Post by Tempest42 on 2011-10-30
As a matter of fact, I did that of my own accord, and they work fine :) Fingers crossed I don't run into any more problems. Thanks for all your help!

---

### Post by cbowman57 on 2011-10-30
Glad it's working for you.

---

### Post by brambu on 2011-11-01
Quick and dirty fix: 
ssh in remotely and run: 
```
sudo apt-get remove gnome-shell-extensions-*
```
then
```
DISPLAY=:0 gnome-shell --replace & 
```

---

