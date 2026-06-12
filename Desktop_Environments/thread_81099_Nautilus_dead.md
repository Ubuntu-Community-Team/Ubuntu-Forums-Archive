---
title: "Nautilus dead"
date: 2005-10-23
forum: Desktop Environments
---

### Post by Jenda on 2005-10-23
My desktop fails to work for some reason.
It was working quite OK till a while ago:
I opened my home folder in nautilus. Nothing appeared and it didn't respond. I could move the window around and all, but the contents stayed blank. When I force closed it, it just kept reappearing. When I try to browse anything but my home folder, no problem.
I thought I would fix it by rebooting (first by restarting gdm), but the problem stayed, and in addition, there is no background image and my panels returned to default. (No wait - they're back, but it took about five minutes since boot up - wtf?) The home folder still don't work.

Please, can any of the more savvy Ubuntuers help me?

---

### Post by LorenzoD on 2005-10-23
Could you check ~/.xsession-errors to see if there is anything there that is nautilus related?

---

### Post by Jenda on 2005-10-23
> manager.c/557: setting[3]: string: autoburn_photo_cd_command = nautilus --no-desktop burn:
manager.c/557: setting[4]: string: autoburn_data_cd_command = nautilus --no-desktop burn:> ** (gnome-cups-icon:8588): WARNING **: IPP request failed with status 1030
The application 'nautilus' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
No more mentions of nautilus. And nothing suspicious to me.

---

### Post by LorenzoD on 2005-10-23
Do you have a lot of files in your $HOME? It can take a while for nautilus to parse in that case. You said it only hangs when opening your home directory? What happens if you try accessing any other directory that should be reasonably large, such  as /usr/lib?

The reason why nautilus keeps restarting when you kill it is that it is set to restart itself any time it dies.

---

### Post by Jenda on 2005-10-24
> Do you have a lot of files in your $HOME? It can take a while for nautilus to parse in that case. You said it only hangs when opening your home directory? What happens if you try accessing any other directory that should be reasonably large, such as /usr/lib?
Yes I do. But it worked a while ago and most of the files are hidden. All other folders work OK, except kinda slow. I don't think the files cause that because I left it on all night and it still hangs. It also eats up a huge amount of CPU power. Damn this is annoying

> The reason why nautilus keeps restarting when you kill it is that it is set to restart itself any time it dies.
Indeed. Is there a way to turn this off? Just to save my CPU the pain.

---

### Post by bvc on 2005-10-24
logout and rename (i.e...mv -fr .gnome2 gnome2BAK) .gnome, .gnome2, .gconf, .gconfd, .metacity
and try to login again (this will reset everything to the default)

---

### Post by Jenda on 2005-10-24
Yup. That fixed it. Thanx a bunch!
But what now? Should I try renaming them back one by one and retrying after each to find out where the problem was?

---

### Post by Jenda on 2005-10-24
I would like my settings back, you know...

---

### Post by Wolki on 2005-10-24
You can try copying the files back one by one to see which one caused the error.

Yes, it's a big pain, but rumor tells me that a gnome configuration/data backup utility is in the works. Maybe we'll see something for Gnome 2.14.

---

### Post by Jenda on 2005-10-24
Alrighty... That'll take a while.

---

### Post by Jenda on 2005-10-24
EEK!
I copied them all back, and no preblem.
Except: my panels are gone! Where would panel gonfig be stored? I had two extra side panels and some configuration on all four. Where would these be?

---

### Post by Jenda on 2005-10-24
Nevermind. Found it: Home/.gconf/apps/panel/toplevel - just as in config editor.
But they're not being loaded. Is there a way to fix this?

---

### Post by Jenda on 2005-10-24
Wrong again.
Rebooted the machine: the panels are back and so are the troubles.
I repeated the inquiry rebboting several times and ended up singling out a strange directory: /home/jenda/.gconf/Desktop
This directory is strange, because there is also another directory /home/jenda/.gconf/desktop
They are almost identical, except the fact that the "d" one has more content - the "D" one anly contains ./%gconf.xml ./gnome/%gconf.xml and ./gnome/volume_manager/%gconf.xml - the latter is the cause, I suspect...

Anyone have a clue what I'm talking about and describing here?

---

