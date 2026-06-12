---
title: "Metacity WM hangs"
date: 2005-11-19
forum: Desktop Environments
---

### Post by johan_olsen on 2005-11-19
Hi,
My Ubuntu 5.10 hangs for several minutes when I log in, the splash screen shown after logging in halts showing the message "Metacity vindushåndterer" (Norwegian for WM). After some minutes it logs in well. If I log in as a different user everything is normal. I tried to delete the files under .metacity/sessions, but problem remains. Any ideas og what to do?

Johan, Norway.

---

### Post by frodon on 2005-11-19
Do you run xcompmgr ? if yes removing it from the session start-up programs list will solve the problem.

---

### Post by johan_olsen on 2005-11-19
[QUOTE=frodon]Do you run xcompmgr ? if yes removing it from the session start-up programs list will solve the problem.[/QUOTE]

No, I don't, but here is some lines from my  .xsession-errors file:

This message comes three times:
Advarsel fra vindushåndterer: Feil under lesing av lagret sesjonsfil /home/xt/.metacity/sessions/1132090184-8475-2875186702.ms: Feil under åpning av fil «/home/xt/.metacity/sessions/1132090184-8475-2875186702.ms»: Ingen slik fil eller filkatalog

---
I use Norwegian language, translation is something like this:
Warning from window manager: Error reading saved session file /home/xt/.metacity/sessions/1132090184-8475-2875186702.ms: Error opening file 
«/home/xt/.metacity/sessions/1132090184-8475-2875186702.ms»: No such file or directory.
---
Also two times this:
(gnome-terminal:9042): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
---

Since a recently created user works well, what files and directories is read during logging in? I could copy them to my home directory.


Johan.

---

### Post by ColdWind on 2005-11-19
It's not a real solution, but maybe you're interested in [this howto]("http://doc.gwos.org/index.php/Openbox_Gnome").

---

### Post by kagashe on 2005-11-19
> Also two times this:
(gnome-terminal:9042): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failedDid you create this userid in earlier version of Ubuntu?

kagashe

---

### Post by johan_olsen on 2005-11-19
[QUOTE=kagashe]Did you create this userid in earlier version of Ubuntu?

kagashe[/QUOTE]

No, but the same user name is used on another installation (5.04) located on /dev/hda5 which is mounted during boot. It has been like this since I installed the 5.10, but the Metacity problem startet some time after that. 

And I have tried the Openbox and need help here; where do I configure my Ubuntu to use Openbox as a standard instead of Metacity?

Johan.

---

### Post by ColdWind on 2005-11-19
[QUOTE=johan_olsen]
And I have tried the Openbox and need help here; where do I configure my Ubuntu to use Openbox as a standard instead of Metacity?
[/QUOTE]

Type in terminal:
sudo cp /usr/share/gnome/default.session ~/.gnome2/session
sudo gedit ~/.gnome2/session

Search a line like this:
1,RestartCommand=gnome-wm --sm-client-id default1  

And change for:
1,RestartCommand=gnome-wm --default-wm openbox --sm-client-id default1

---

### Post by johan_olsen on 2005-11-20
Thanks, but same thing happens - after login the text "Vindusbehandler" (Window manager) appears for several minutes before proceeding. So, may e nothing is wrong with the Metacity WM? 

Johan.

---

### Post by johan_olsen on 2005-11-26
Thanks, but the thing that seemed to work was the latest upgrade - now everything works normal. I am happy!

Johan.

---

### Post by cvmostert on 2006-02-12
you seem to be happy, but i just also got the same problem and i have all the latest breezy updates... :-) and all i did to deserve it is move my pc table to another room! hopefully it dissapears... the problem that is :-)

---

### Post by Phalanx747 on 2006-05-20
Johan_Olsen: I'm glad that the latest updates seem to have solved your problem, but unfortunately this didn't work for me. I have all of the latest updates but the problem still persists: after logging into Ubuntu, it hangs for 2 to 3 minutes on loading Metacity Window Manager. I did the same thing you did, and I took a look at .xsession-errors. The result is as follows:

> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "phalanx"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/PHALANX-PC:/tmp/.ICE-unix/5937
**Window manager warning: Failed to read saved session file /home/phalanx/.metacity/sessions/1130767604-9464-1585532277.ms: Failed to open file '/home/phalanx/.metacity/sessions/1130767604-9464-1585532277.ms': No such file or directory**
You can only run one xsettings manager at a time; exiting

(gnome-panel:6020): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -6 and height 24

** (gksudo:6109): WARNING **: Could not load icon file: Failed to open file '/usr/share/pixmaps/update-manager': No such file or directory
  warnings.warn("apt API not stable yet", FutureWarning)

Here you can clearly see that I have some of the same errors as Johan_Olsen. Does anyone have any ideas on what may cause this problem?

---

