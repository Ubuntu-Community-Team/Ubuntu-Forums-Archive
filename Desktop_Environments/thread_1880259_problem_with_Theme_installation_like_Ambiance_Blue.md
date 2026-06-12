---
title: "problem with Theme installation like Ambiance Blue"
date: 2011-11-13
forum: Desktop Environments
---

### Post by alain.roger on 2011-11-13
Hi,

i have some trouble to install the following theme ([http://satya164.deviantart.com/art/Ambiance-Blue-Theme-Suite-196833665](http://satya164.deviantart.com/art/Ambiance-Blue-Theme-Suite-196833665)) under Ubuntu 11.10.

1. Has someone already installed this theme ?

Moreover, and this is a rookie question, on Desktop there are 2 "buttons" (applications and windows).

2. From where are they ?

thx.

A.

---

### Post by BillyBoa on 2011-11-13
As I understand you are using Gnome 3.

In the first question you can create at home directory a new folder with the name .themes and just drop there the theme you downloaded from the site. (unziped).

The second question is about Gnome 3 which still is on a beta stage and many strange things occur. I cannot help you.

And I'm not sure if your theme is working on Gnome 3 either.

---

### Post by Frogs Hair on 2011-11-13
The current Gnome 3 is not a beta release it is a final release , which will continue to improve   . I Just installed that theme a few minutes ago and it seems to work fine . The  window buttons can be configured from advanced settings  under  shell  , Logout and in after making changes .

---

### Post by alain.roger on 2011-11-14
> **Frogs Hair said:**
> The current Gnome 3 is not a beta release it is a final release , which will continue to improve   . I Just installed that theme a few minutes ago and it seems to work fine . The  window buttons can be configured from advanced settings  under  shell  , Logout and in after making changes .

Hi Fogs Hair,
I must do something wrong because i have several issues... let's take an example with theme and tutorial available on [http://www.techdrivein.com/2011/10/how-to-install-and-manage-gnome-shell.html](http://www.techdrivein.com/2011/10/how-to-install-and-manage-gnome-shell.html)

I already had install Gnome Tweak Tool, so i directly from a terminal session, typed the 3 commands:
```
sudo add-apt-repository ppa:ferramroberto/gnome3
sudo apt-get update
sudo apt-get install gnome-shell-extensions-user-theme
```

after that i open Gnome Tweak Tool and as you can see on both attachements there are several issues:
1. Shell extensions tab shows NOTHING :-(
2.Theme tab has some icon issue with Shell extension listbox :-(
3. as you can see on screenshot of ambiance theme(	[ambiance_blue_theme_suite_by_satya164-d396ttt.jpg]("http://ubuntuforums.org/attachment.php?attachmentid=207163&stc=1&d=1321288816")), i stroke in red the button i was talking about and that i'm not able to see them on my desktop.

Please could you help me ?
thx.

A.

---

### Post by Frogs Hair on 2011-11-14
I am not familiar with that extensions  PPA , I use the extensions at the link  [http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html](http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html)

The  same problem was reported on another thread and I don't know if it was resolved .

---

### Post by werewolves on 2011-11-14
> **Frogs Hair said:**
> I am not familiar with that extensions  PPA , I use the extensions at the link  [http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html](http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html)

The  same problem was reported on another thread and I don't know if it was resolved .

I'd definitely switch to the WebUpd8 PPA, I've had no problems with it.  They also have a theme PPA.

---

### Post by alain.roger on 2011-11-14
> **werewolves said:**
> I'd definitely switch to the WebUpd8 PPA, I've had no problems with it.  They also have a theme PPA.

so i did everything written on [http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html](http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html) and everything run well. However i still have the same issue.

any idea from where it can come ?

---

### Post by Frogs Hair on 2011-11-14
> **alain.roger said:**
> so i did everything written on [http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html](http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html) and everything run well. However i still have the same issue.

any idea from where it can come ?

The other thread is not resolved either , so all I can suggest is to enable the command prompt from keyboard  > shortcuts > system and use Alt +F2 as the shortcut .

Open Looking Glass from the command prompt with the following command .```
lg
```
From there you can check for errors . Use Esc to close Looking Glass . [http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)

---

### Post by alain.roger on 2011-11-15
Everything works fine and worked fine...i was just under the Gnome fallback due to not present video driver. I installed the recommended drivers and suddenly everything works as planned.

---

