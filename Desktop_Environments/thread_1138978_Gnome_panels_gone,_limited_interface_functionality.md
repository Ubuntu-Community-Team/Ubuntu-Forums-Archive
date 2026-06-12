---
title: "Gnome panels gone, limited interface functionality - 9.04 netbook remix"
date: 2009-04-26
forum: Desktop Environments
---

### Post by Fletch1 on 2009-04-26
This afternoon, I installed Jaunty netbook remix on my Acer Aspire One. Very smooth install, installed wireless driver, XP working well on the other side of the partition--good stuff. Installed Opera, Tweetdeck, Bluefish, Dropbox, and Filezilla. I switched to the classic view, because I'm still adjusting to the netbook layout. Everything's running fine, I switch back over to XP for the 2nd or third time to check something--switch back and there is nothing but my three desktop shortcuts.

I was able to use the terminal (TG I'd put a shortcut on the desktop) to start Firefox, but it only opened as a 1/4 size window in the upper left-hand corner. I couldn't drag it, did not have resize buttons and had to close it to get back to the terminal, which was underneath it.

I restarted, of course, but that didn't work.

I'm not sure if the best solution for all this is uninstalling and reinstalling gnome--I'm a bit leery of that, but willing to do it. I tried a few fixes suggested in other threads with people having similar problems (though no one seemed to be having the problems with the windows as well). I'm also willing to reinstall the netbook remix, as it's only got a few hours of changes in it, but I'd really rather not.

Has anyone run into this before? Any fixes other than reinstall? :?

Limited Ubuntu experience--I've been using it on my old laptop for a few months, so I'm familiar with the terminal, the command-line interface, but not very used to it.

---

### Post by Fletch1 on 2009-04-26
Kept looking, didn't find anything that worked so I just went ahead and reinstalled the whole thing. Seems to be working ok, but if anyone happens to know what went wrong, I'd be interested in hearing it--for curiosity and because I don't know what happened the first time, so still feeling a bit unresolved.

---

### Post by themayor87 on 2009-04-26
having the same problems right now. running on an eee900. 
At first, i thought it was still loading, but then I noted that the screen dimmed, which told me that at least the power regulating program ( i forget the name) was running. It's as if the gnome panels just aren't loading. At first the title bars weren't loading, so i went to change desktop background -> desktop effects, and upon toggling between normal and none the title bar loaded on the windows, but still no panel. very suprised to see that it connected to my wifi connection. i was able to get to firefox by right-clicking and creating a launcher. i would like to avoid reinstalling if possible. any suggestions?

---

### Post by redDEADresolve on 2009-04-26
This isn't elegant but I got my desktop back by loading into a failsafe terminal. launching into nautilus and deleting my .gnome2, .gconf, and .gconfd folders. I'm not sure which folder did it but I was in a rush and angry so I deleted them all. 

I lost my custom menu setup but everything returned to default (menu were configured like a new install) but I got my desktop back.

---

### Post by Mr_Crimson on 2009-04-27
I am experiencing the very same issue with 9.04 on my eee PC 900 after switching to Classic.

It's fine until you reboot, then, no panels.  I've not tried deleting the config files as prescribed above yet.  Does anyone have other suggestions or fixes?

-Crim

---

### Post by Niniel on 2009-04-28
I just had/am having the same issue on my desktop. 
The problem is that the window manager Metacity isn't running. I couldn't just enter "metacity" in a terminal though because it wouldn't accept any input. Fortunately, I still had the Run applet in the panel, although at first that wouldn't let me enter any text either. But I was able to type in FF, so I wrote metacity in there, copied it, pasted it into the run box, and voila, desktop restored. 
Now I just need to figure out how to make the OS load the WM automatically. :)

---

### Post by siddboots on 2009-04-29
I am having this exact problem also, on a friend's computer.

As per those before me, this is on an eeepc 900 and occured on the first restart after switching from netbook mode to "Classic". 

I can get everything back by switching back to netbook, and then back to Classic. However this solution does not last through subsequent logins.

I have also tried deleting .gconf/ and .gconfd/ etc, to no avail.

---

### Post by alien21010 on 2009-04-29
Hey guys,

I too was having this problem, but found that you can repair the damage done by the switch pretty easily.  If you are already to the point where nothing is displaying on the screen, either go to a fail-safe terminal (CTRL+ALT+F2), or make a new launcher on the desktop (depending on which mode you got stuck in).  In this terminal, delete all the configuration folders listed below:

.gconfd
.gconf
.gnome2
.gnome2_private
.config

You can remove them by using the command: rm -r foldername

Once they are removed, reboot using the command: sudo shutdown -r now

It seems to be linked to the .config folder, and removing that one might solve the problem by itself. The config folders will rebuild themselves once they are removed, restoring the system to defaults.

---

### Post by Visceral Monkey on 2009-04-30
> **alien21010 said:**
> Hey guys,

I too was having this problem, but found that you can repair the damage done by the switch pretty easily.  If you are already to the point where nothing is displaying on the screen, either go to a fail-safe terminal (CTRL+ALT+F2), or make a new launcher on the desktop (depending on which mode you got stuck in).  In this terminal, delete all the configuration folders listed below:

.gconfd
.gconf
.gnome2
.gnome2_private
.config

You can remove them by using the command: rm -r foldername

Once they are removed, reboot using the command: sudo shutdown -r now

It seems to be linked to the .config folder, and removing that one might solve the problem by itself. The config folders will rebuild themselves once they are removed, restoring the system to defaults.

Thanks, that worked, but I want to use classic and everytime we switch it appears to bork on the next reboot.

---

### Post by PaulWhipp on 2009-05-01
Thanks alien21010, that workaround got things sorted for me too!

Has anyone reported this as a bug so it can be fixed?

---

### Post by digiapb on 2009-06-03
Thanks, alien21010

that worked for me as well.

does anyone know if this will happen anytime I switch between classic and netbook mode?

FYI, there is a bug reported for this. See:
[https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519](https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519)

thanks again.

---

### Post by avc on 2009-06-14
> **alien21010 said:**
> 
.gconfd
.gconf
.gnome2
.gnome2_private
.config

You can remove them by using the command: rm -r foldername

Once they are removed, reboot using the command: sudo shutdown -r now

Thanks alien. I did a little less than what you listed here, and it cleaned up my top gnome-panel, which I messed up by trying to move the battery and wireless network indicator (the bars) causing both to disappear. I did:

Log into failsafe terminal.
rm -R .gconf .gconfd .config
exit
Log in to Gnome normally.

---

### Post by thedharmablues on 2009-06-26
Thanks for this fix. I am an Ubuntu newbie, so this was really useful.

Sincerely,
Ryan

---

### Post by OM NOM NOM on 2009-06-30
Yes kudos - worked like a charm fo rme!

---

### Post by baruch60610 on 2009-07-15
There is a fix for this, at [http://ubuntuforums.org/showpost.php?p=7081942&postcount=8.]("http://ubuntuforums.org/showpost.php?p=7081942&postcount=8")

Basically you need to enter a command, depending in whih desktop mode you're in.  If you're in the new "Netbook" mode, enter the following command:

gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel"]

If you're in the older, "Classic" mode, the command is slightly different:

gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel","filemanager"]

I found that this worked fine for me.

If you're already stuck without panels, then right-click on the desktop and create a launcher (that will be one of the option on the menu).  Select "application in a terminal", and for the command, enter 'gnome-terminal'.  This will at least let you run a terminal, which will allow you to enter one of the commands above.

---

### Post by rv65 on 2009-07-29
I have no gnome panels and no ALT+F2 functionality. I have Ubuntu 9.04 x86_64.

---

### Post by rv65 on 2009-07-29
Tried using the failsafe gnome and still no panel. I've tried everything but no luck? Any solution.

---

### Post by PaulWhipp on 2009-08-02
Follow up the fix in baruch60610's post. You have to fish around for the deb file for the desktop-switcher but once its installed and the instructions are followed the Dell Mini 9.04 UNR is sorted.

One word of caution - we have noticed that the UNR menu page seems to slow down on its updates after this fix.

---

