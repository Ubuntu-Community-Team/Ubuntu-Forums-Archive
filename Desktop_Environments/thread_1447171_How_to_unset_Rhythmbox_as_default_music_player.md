---
title: "How to unset Rhythmbox as default music player"
date: 2010-04-05
forum: Desktop Environments
---

### Post by mfearby on 2010-04-05
I prefer Audacious to play random files on my hard disk but still use Rhythmbox to manage my library. What I don't want, however, is when I double-click on an MP3 for it to load Rhythmbox and add it (thereby adding mess) to my library. When it comes to sampling some file on my hard disk, I want audacious for quick-and-dirty preview/play-once scenarios. I've already set "audacious2" as my preferred app for music, but Gnome is just ignoring it. How do I set this, and why does Gnome let you set something that it just ignores anyway?

Thanks.

---

### Post by hhh on 2010-04-05
Short answer here, right click the file and choose "Properties" and then choose "Open with..." and set it to Audacious.

---

### Post by mfearby on 2010-04-05
> **hhh said:**
> Short answer here, right click the file and choose "Properties" and then choose "Open with..." and set it to Audacious.

I have been doing that, but it doesn't remember it. I have to right-click every time. Gnome doesn't have a tick-box like Windows to remember the choice.

---

### Post by hhh on 2010-04-05
What file manager are you using? I thought Nautilus (the default Gnome file manager) did have a similar checkbox?

Sorry I can't be of more help, I'm not currently running Gnome. I'll fire up a live CD if I have a chance.

---

### Post by 3Miro on 2010-04-05
Right-click and preferences would let you set the default application for files of this type. Then double-left click will use this app.

Right-click and "open with", will give a list of applications that can open the file and you can select which one you wish to use, but just for this one time.

---

### Post by mfearby on 2010-04-05
> **3Miro said:**
> Right-click and preferences would let you set the default application for files of this type. Then double-left click will use this app.

Right-click and "open with", will give a list of applications that can open the file and you can select which one you wish to use, but just for this one time.

Right you are. Thanks. Didn't try properties on a file itself. Is this a bug whereby the System > Preferences > Preferred Applications is being ignored no matter what you type?

---

### Post by asmoore82 on 2010-04-05
> **mfearby said:**
> Right you are. Thanks. Didn't try properties on a file itself. Is this a bug whereby the System > Preferences > Preferred Applications is being ignored no matter what you type?

I think(not sure) that "Preferred Applications" is for URL handlers,
so in the context of Multimedia is it what a hot-plugged mp3 player will launch.

Right-click -> Properties is for individual filetypes.

And even more, you can go to "Places -> Home" and "Edit -> Preferences"
then click the "Media" tab on the right for Default Apps for Removable Media.

---

### Post by mfearby on 2010-04-06
Thanks for the reply. It's now cleared up in my mind, though I still reckon most people would expect "preferred applications" to set the preferred application for any scenario, not just the one the Gnome devs have in mind but didn't see fit to clear up in the window itself. Thanks.

---

