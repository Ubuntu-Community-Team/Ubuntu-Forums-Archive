---
title: "Gaim icon missing..."
date: 2005-09-24
forum: Desktop Environments
---

### Post by YourSurrogateGod on 2005-09-24
You know when you start up gaim in Gnome and there is a little gaim icon at the top-right corner of the screen that shows that gaim is working? Well, I messed with that (I don't remember what I did) and now when I start up gaim, it's not there anymore, any ideas on how to get it back?

---

### Post by greenstar on 2005-09-24
Open Gaim,

click preferences on the bottom center of the login screen,

then in the left column of the preferences dialog,

click plugins,

scroll down until you find Sysem Tray Icon and check it

then click close on preferences

greenstar

---

### Post by YourSurrogateGod on 2005-09-24
[QUOTE=greenstar]Open Gaim,

click preferences on the bottom center of the login screen,

then in the left column of the preferences dialog,

click plugins,

scroll down until you find Sysem Tray Icon and check it

then click close on preferences

greenstar[/QUOTE]
I just did that, but it didn't work, I still don't see the little picture.

---

### Post by YourSurrogateGod on 2005-09-24
Ok, I figured "Screw it." I backed up my gaim logs and decided to get rid of the gaim directory and simply re-install gaim (not too much of a problem, just start anew.)

Now whenever I try to re-install gaim in synap, I get prompted that it needs to install a gaim-data dependency, to which I agree. Now, when I agree to this, I get the below error message. What's going on?
```
gaim:
  Depends: gaim-data (=1:1.4.0-1ubuntu1~5.04ubp1) but 1:1.1.4-1ubuntu4.4 is 
to be installed
```
What's wrong?

---

### Post by YourSurrogateGod on 2005-09-24
Well, I just did a complete removal of gaim and gaim-data and still no go. I got the below error while trying to install gaim...
```
gaim:
 Depends: gaim-data but it is not going to be installed
```
Damn it, I shouldn't have fucked with gaim in the first place :roll: .

---

### Post by imagine on 2005-09-24
[QUOTE=][/QUOTE]
 What exactly did you type?

And concerning your icon: You didn't delete the notification area in the panel, did you? Are the others icons, like update-manager or rhythmbox still showing up in the panel?

---

### Post by YourSurrogateGod on 2005-09-24
[QUOTE=imagine]What exactly did you type?[/quote]
Well, I did it all through synap and I simply removed gaim and then deleted the /home/~/.gaim directory (thinking that when I re-install things it will be back.)
[quote=imagine]And concerning your icon: You didn't delete the notification area in the panel, did you? Are the others icons, like update-manager or rhythmbox still showing up in the panel?[/QUOTE]
What's a notification area? And to answer your question, no I don't see the update-manager.

---

### Post by khc on 2005-09-24
You are using ubuntu backports? It seems like you have a conflict between that and your standard repository.
Right click your panel->Add to panel->Notification area, if you don't already have one.

---

### Post by YourSurrogateGod on 2005-09-24
[QUOTE=khc]You are using ubuntu backports? It seems like you have a conflict between that and your standard repository.[/quote]
How do I solve this problem?
[quote=khc]Right click your panel->Add to panel->Notification area, if you don't already have one.[/QUOTE]
Ohh... ok, gotcha.

---

### Post by imagine on 2005-09-24
[QUOTE=][/QUOTE]
 Tried to uninstall gaim-data and then reinstalling gaim?

---

### Post by YourSurrogateGod on 2005-09-24
[QUOTE=imagine]Tried to uninstall gaim-data and then reinstalling gaim?[/QUOTE]
Yep.

---

### Post by YourSurrogateGod on 2005-09-24
[QUOTE=imagine]Tried to uninstall gaim-data and then reinstalling gaim?[/QUOTE]
I tried that and it gave me an error saying that gaim-data wouldn't be installed and then promptly exitted. I then tried to install gaim-data and then gaim, but then I got...
```
gaim:
  Depends: gaim-data (=1:1.4.0-1ubuntu1~5.04ubp1) but 1:1.1.4-1ubuntu4.4 is 
to be installed
```

---

### Post by imagine on 2005-09-24
[QUOTE=][/QUOTE]
 Have you added hoary-backports to your repositories and made an apt-get update?

You can also manually get gaim-data, but that shouldn't be necessary:
```
wget http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/gaim_1.4.0-1ubuntu1~5.04ubp1_i386.deb
sudo dpkg --install gaim_1.4.0-1ubuntu1~5.04ubp1_i386.deb
```

I hope you're using the i386-install of Ubuntu.

---

### Post by YourSurrogateGod on 2005-09-24
[QUOTE=imagine]Have you added hoary-backports to your repositories and made an apt-get update?

You can also manually get gaim-data, but that shouldn't be necessary:
```
wget http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/gaim_1.4.0-1ubuntu1~5.04ubp1_i386.deb
sudo dpkg --install gaim_1.4.0-1ubuntu1~5.04ubp1_i386.deb
```

I hope you're using the i386-install of Ubuntu.[/QUOTE]
I tried that, I got a broken package, had to remove the installed piece of software...

The irony is that the version that I got from the link that's inside of the command that you showed me is the same as the one that is in synap, but it still didn't work.

Just curious, but does the program regenerate the .gaim folder that I previously deleted?

---

### Post by YourSurrogateGod on 2005-09-25
So I take there is no way for me to install gaim again without having a broken package?

---

### Post by khc on 2005-09-25
The .gaim folder is generated by gaim itself, not any packages. You can try to remove the backports repository, then apt-get update && apt-get install gaim.

---

