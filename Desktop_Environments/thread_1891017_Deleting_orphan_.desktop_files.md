---
title: "Deleting orphan .desktop files"
date: 2011-12-04
forum: Desktop Environments
---

### Post by blahsnr on 2011-12-04
I've recently converted [Gnome 10.04 to Xubuntu]("http://ubuntuforums.org/showthread.php?t=1887972") and stripped out the Gnome desktop. All is fine with the exception that I now have two ophan entries in the Xfce Applications menu these being for Evolution and Thunderbird.

Tried using Synaptic to remove both items completely, but the menu entries still exist. I have found three .desktop files for each applications. 

saw901@saw901:~$ locate \.desktop | grep -i thunderbird
/home/saw901/.local/share/applications/thunderbird.desktop
/usr/share/app-install/desktop/thunderbird.desktop
/usr/share/xfce4/helpers/thunderbird.desktop
saw901@saw901:~$ locate \.desktop | grep -i evolution
/etc/xdg/autostart/evolution-alarm-notify.desktop
/usr/share/app-install/desktop/evolution.desktop
/usr/share/xfce4/helpers/evolution.desktop
saw901@saw901:~$ 

I'm not planning on ever reinstalling these two email clients so I have two questions:

1) If I delete the desktop files listed above will the orphan Application menu entries be removed?
2) Are there likely to be any side effects of manually deleting these files?

Thanks in advance

---

### Post by ManualSparrow on 2011-12-04
Try xfdesktop --reload, or reboot. Also check in the settings dialog that you're default mail client isn't set to thunderbird or something.


I don't think deleting your .desktop files for those things should be a problem, but if you're worried, try renaming them to 'whatever.desktop-bak' - if something breaks, just fix the names.

---

### Post by oldtimer7777 on 2011-12-04
What I have used when this happens is:

sudo apt-get install deborphan
sudo gtkorphan

> **blahsnr said:**
> I've recently converted [Gnome 10.04 to Xubuntu]("http://ubuntuforums.org/showthread.php?t=1887972") and stripped out the Gnome desktop. All is fine with the exception that I now have two ophan entries in the Xfce Applications menu these being for Evolution and Thunderbird.

Tried using Synaptic to remove both items completely, but the menu entries still exist. I have found three .desktop files for each applications. 

saw901@saw901:~$ locate \.desktop | grep -i thunderbird
/home/saw901/.local/share/applications/thunderbird.desktop
/usr/share/app-install/desktop/thunderbird.desktop
/usr/share/xfce4/helpers/thunderbird.desktop
saw901@saw901:~$ locate \.desktop | grep -i evolution
/etc/xdg/autostart/evolution-alarm-notify.desktop
/usr/share/app-install/desktop/evolution.desktop
/usr/share/xfce4/helpers/evolution.desktop
saw901@saw901:~$ 

I'm not planning on ever reinstalling these two email clients so I have two questions:

1) If I delete the desktop files listed above will the orphan Application menu entries be removed?
2) Are there likely to be any side effects of manually deleting these files?

Thanks in advance

---

### Post by blahsnr on 2011-12-05
> **ManualSparrow said:**
> Try xfdesktop --reload, or reboot. Also check in the settings dialog that you're default mail client isn't set to thunderbird or something.

[snip]
Thanks for your reply, I should have mentioned that the problem is persistent, rebooting makes no difference. Claws Mail is currently the default mail client, changing this (and rebooting) does not make a difference.
Neither do the entries show up in the LXDE Main Menu Editor.

---

### Post by blahsnr on 2011-12-05
> **oldtimer7777 said:**
> What I have used when this happens is:

sudo apt-get install deborphan
sudo gtkorphan
Is this not for removing orphaned packages rather than orphaned .desktop files. Or is a .desktop file regarded a package under linux? 
Is the package removal functionality in gtkorphan similar to that in Ubuntu Tweak?

---

### Post by BobMarleyy on 2011-12-05
> **blahsnr said:**
> 
1) If I delete the desktop files listed above will the orphan Application menu entries be removed?
2) Are there likely to be any side effects of manually deleting these files?
1) I wouldn't delete those desktop files, because you can edit the applications menu. There is a config-file called xfce-applications.menu located in /etc/xdg/xdg-xubuntu/menus/. Try editing it. It might be useful to create a backup of the file before editing it.
2) If you use this method I explained there are no consequences because you can restore the original menu any time.
BTW the menu file links to .desktop files which you can also edit. The .desktop files can be found in the folder: /usr/share/applications.

Cheers,
Bob

---

### Post by blahsnr on 2011-12-06
@bobmarleyy
Thanks for the response. I have edited the main menu file in IceWM in the past but the menu file in Xubuntu you refer to is quite different. I found the .menu file before you posted but it does not define the individual items under the different headings. I could not see how to edit it to remove an orphan entry under "Other" for example. There is no reference directly to the individual items ie Firefox Thunderbird etc in the menu tree. The IceWM file was just a text file with all the apps listed there which was quite easy to edit.

I gave up last night and reinstalled a clean copy of Xubuntu, after I discovered that Gigolo was no longer interested in connecting to networked drives. I guess the switch from Ubuntu to Xubuntu did not go quite as well as I thought. Thanks for all the responses.

---

### Post by beew on 2011-12-06
Weird things (bugs or features?) like this is why I can't feel enthusiastic about xubuntu. About deborphan, you should stay away from it unless you know exactly what you are doing or it will delete half of your system. It by default treats anything that doesn't have anything that depends on it as 'orphan'.

---

### Post by blahsnr on 2011-12-06
> **beew said:**
> Weird things (bugs or features?) like this is why I can't feel enthusiastic about xubuntu. About deborphan, you should stay away from it unless you know exactly what you are doing or it will delete half of your system. It by default treats anything that doesn't have anything that depends on it as 'orphan'.
For me it isn't a question about feeling enthusiastic. Gnome was something I could live with not fantastic but usable. A bit like the Windows UI, few people love it, but it does the job and in all its incarnations is familiar enough to be immediately usable (well up to Win 7).

Thanks for confirming my first impressions of deborphan.

---

