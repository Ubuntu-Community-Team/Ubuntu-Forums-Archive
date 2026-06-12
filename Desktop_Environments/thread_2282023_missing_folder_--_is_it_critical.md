---
title: "missing folder -- is it critical?"
date: 2015-06-11
forum: Desktop Environments
---

### Post by Lloydb39 on 2015-06-11
After an automatic backup, I got a message that said it could not back this file "/home/lloyd/.config/nautilus-actions" and advised me to make sure I could open it. Turns out I couldn't find a lloyd folder at all, but there is a config folder in "home" with a "nautilus-actions" file, which I couldn't open because it said I do not have the permissions.
Obviously something is wrong and I'm wondering if it is related to the error message about a bad file I get on every reboot. In any case, does anyone have a fix or do I even need one?

---

### Post by steeldriver on 2015-06-11
The directory that nautilus displays as **Home** (note the capital H) is actually the current user's **/home/username/** directory - so it sounds like it's the right file, but the wrong permissions (or ownership): what do you get if you open a terminal (Ctrl-Alt-t) and enter

```

ls -l /home/lloyd/.config/nautilus-actions

```

---

### Post by Lloydb39 on 2015-06-11
I get:
ls: cannot open directory /home/lloyd/.config/nautilus-actions: Permission denied

---

### Post by steeldriver on 2015-06-11
OK then try

```

ls -ld /home/lloyd/.config/nautilus-actions

```

or 

```

ls -l /home/lloyd/.config | grep nautilus-actions

```

or just

```

ls -l /home/lloyd/.config

```

and look to see the owner and permission flags: basically everything inside /home/lloyd should be owned by 'lloyd', if it's not then we will need to fix that

---

### Post by Lloydb39 on 2015-06-11
lloyd@linux:~$ ls -l /home/lloyd/.config
```
total 212
drwxrwxr-x 2 lloyd lloyd  4096 Jun 11 08:16 akonadi
drwx------ 2 lloyd lloyd  4096 Apr  7  2014 autostart
drwxrwxr-x 2 lloyd lloyd  4096 May 31  2014 backintime
drwx------ 2 lloyd lloyd  4096 Jun  1  2014 bleachbit
drwx------ 7 lloyd lloyd  4096 May 20 21:26 chromium
drwx------ 3 lloyd lloyd  4096 Dec 25  2012 compiz-1
drwx------ 2 lloyd lloyd  4096 Jun 11 08:18 dconf
drwx------ 2 lloyd lloyd  4096 Dec 25  2013 Empathy
drwx------ 2 lloyd lloyd  4096 Dec 26  2012 enchant
drwx------ 2 lloyd lloyd  4096 Feb  4 19:13 eog
drwx------ 2 lloyd lloyd  4096 Jun  9 11:57 evince
drwx------ 3 lloyd lloyd  4096 Nov  1  2014 evolution
drwxr-xr-x 2 lloyd lloyd  4096 Mar 27  2014 gedit
drwxr-xr-x 3 lloyd lloyd  4096 Dec 25  2012 gnome-control-center
drwxr-xr-x 3 lloyd lloyd  4096 Dec 25  2012 gnome-disk-utility
drwxrwxr-x 4 lloyd lloyd  4096 Apr 16 07:41 gnome-mplayer
drwxr-xr-x 3 lloyd lloyd  4096 Dec 25  2012 gnome-session
drwxr-xr-x 2 lloyd lloyd  4096 Nov  1  2014 goa-1.0
drwxrwxr-x 2 lloyd lloyd  4096 Dec 25  2013 Google
drwx------ 9 lloyd lloyd  4096 Jun 11 08:18 google-chrome
drwx------ 2 lloyd lloyd  4096 Jun  4  2014 google-googletalkplugin
drwx------ 2 lloyd lloyd  4096 Jun 10 14:10 gtk-2.0
drwxrwxr-x 2 lloyd lloyd  4096 Jun 11 08:17 gtk-3.0
drwxrwxr-x 2 lloyd lloyd  4096 Oct 27  2013 hotkeys
drwx------ 3 lloyd lloyd  4096 Dec 25  2012 ibus
drwxr-xr-x 2 lloyd lloyd  4096 Nov  1  2014 libaccounts-glib
drwxr-xr-x 2 lloyd lloyd  4096 Jul 28  2014 libimobiledevice
drwxrwxr-x 4 lloyd lloyd  4096 Nov  2  2014 libreoffice
drwx------ 3 lloyd lloyd  4096 May 20 16:45 menus
drwxr-xr-x 2 lloyd lloyd  4096 Jun 11 08:18 nautilus
d-wxr-xr-T 2 lloyd lloyd  4096 Jun 11 08:18 nautilus-actions
-rw------- 1 lloyd lloyd    30 Jul  5  2014 pavucontrol.ini
drwx------ 2 lloyd lloyd  4096 Nov  1  2014 pulse
drwx------ 2 lloyd lloyd  4096 Dec 27  2012 Skype
drwxrwxr-x 2 lloyd lloyd  4096 May 20 15:28 software-center
drwxr-xr-x 2 lloyd lloyd  4096 Nov  1  2014 synapse
drwx------ 2 lloyd lloyd  4096 May  5 11:23 totem
drwxr-xr-x 5 lloyd lloyd  4096 Jun  6  2013 transmission
-rw-rw-r-- 1 lloyd lloyd 21274 Jun 10 08:51 Trolltech.conf
drwx------ 2 lloyd lloyd  4096 Dec 25  2012 ubuntuone
drwxrwxr-x 2 lloyd lloyd  4096 Nov  3  2014 ubuntu-ui-toolkit
drwxrwxr-x 2 lloyd lloyd  4096 Apr 24 06:13 unity
drwx------ 2 lloyd lloyd  4096 Dec 25  2012 update-notifier
drwx------ 2 lloyd lloyd  4096 Nov  1  2014 upstart
-rw------- 1 lloyd lloyd   632 Dec 25  2012 user-dirs.dirs
-rw-rw-r-- 1 lloyd lloyd     5 Dec 25  2012 user-dirs.locale
drwxrwxr-x 2 lloyd lloyd  4096 Mar 19 07:21 vlc
drwxrwxr-x 2 lloyd lloyd  4096 Feb  1  2013 yelp
lloyd@linux:~$ 
```
It doesn't show on this but in the terminal "nautilus-actions" is highlighted....

---

### Post by Lloydb39 on 2015-06-11
and this is what grep produced:
d-wxr-xr-T 2 lloyd lloyd  4096 Jun 11 08:18 nautilus-actions

---

### Post by steeldriver on 2015-06-11
Hmm... that seems to be a [bug]("https://answers.launchpad.net/ubuntu/+source/nautilus-actions/+question/194838") (or at least an acknowledged issue)

I don't know why that directory should have such (on the face of it) strange permission bits. Let's see if someone more knowledgeable can chime in.

---

### Post by Lloydb39 on 2015-06-11
Should I try "chmod u+r $HOME/.config/nautilus-actions/" ?

---

### Post by steeldriver on 2015-06-11
Yes that should work (as far as the original backup error is concerned) - I was just reluctant to suggest it without understanding *why *the permissions are set that way - I don't know what the contents of that directory are used for

---

### Post by Lloydb39 on 2015-06-11
After trying it, I got the same response to grep. I guess I'm stuck with it.

---

### Post by mc4man on 2015-06-11
Typically it just contains nautilus-actions.conf which  it's just a default + any user changes config file. The permissions are usually drwxr-x---
I'd just delete the folder, open nautilus-actions & it will create a new one. 
(- actions are stored elsewhere so deleting the folder &  .conf has no effect there..

---

### Post by Habitual on 2015-06-12
```
ls -ld /home/lloyd/.config
``` output please sir.

---

