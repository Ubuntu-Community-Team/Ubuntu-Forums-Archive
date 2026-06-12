---
title: "No Menu, no F2, no panels"
date: 2009-05-15
forum: General Help
---

### Post by randiroo76073 on 2009-05-15
Not sure what happened but I don't have any of the above, can get to terminal thru nautilus(desktop home folder, nautilus scripts), but have no clue what to do. Any help would be appreciated, thanks.

PS: running Jaunty 9.04 amd64

---

### Post by soro2005 on 2009-05-15
Is it always like that? Or did it just die once? You could post the contents of the file ~/.xsession-errors so that we can see what's the issue.

---

### Post by randiroo76073 on 2009-05-15
Thanks for reply, sorry I took so long getting back. Do you want whole file? It's pretty long, 934 entries. Just happened yesterday, I had burned 9.10 alpha to disk and rebooted to cd, only cd didn't start, hung at blank screen w/cursor flashing. After about 4-5 mins I hit reset and booted to 9.04 and that is how it came up, I have everything, background, desktop icons and can access most everything thru backdoor of Nautilus/scripts, but have no menu, alt-F2, panels. I'm no guru but couldn't see anything in xsession-errors???

PS: Typing "cli" at cursor had no effect, no cd or hdd activity

---

### Post by randiroo76073 on 2009-05-16
OK, here's a fresh xsession-errors:
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
GNOME_KEYRING_SOCKET=/tmp/keyring-9gIiAg/socket
SSH_AUTH_SOCK=/tmp/keyring-9gIiAg/socket.ssh
GNOME_KEYRING_PID=3607

(gnome-settings-daemon:3606): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:3606): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
x-session-manager[3489]: WARNING: Could not launch application 'nm-applet.desktop': Unable to start application: Failed to execute child process "nm-applet" (No such file or directory)
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
x-session-manager[3489]: WARNING: Could not launch application '103d323a8f3493697e124236263054487200000034740034.desktop': Unable to start application: Failed to execute child process "evolution-exchange-storage" (No such file or directory)
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
** (deja-dup-monitor:3624): DEBUG: monitor.vala:219: Waiting 397568 seconds until next backup.
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
x-session-manager[3489]: WARNING: Could not launch application '103d323a8f3493697e12423626422774000000034740037.desktop': Unable to start application: Failed to execute child process "fast-user-switch-applet" (No such file or directory)
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
kget(3647) GenericModelObserver::addedTransferGroupEvent: OBSERVER :: Adding group  0xea4ad0
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action

** (nautilus:3615): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1e00048 (Buddy List)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1e00048 (Buddy List)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Exiting because another libpurple client is already running.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1e00048 (Buddy List)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
[Error 09:34:11.654] Could not load desktop item: File 'file:///usr/share/applications/Internet/WebHTTrack-Websites.desktop' is not a regular file or directory.
[Error 09:34:11.664] Could not load desktop item: File 'file:///usr/share/applications/Internet/WebHTTrack.desktop' is not a regular file or directory.
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
[B]
```
I've never run into this prob before so any advise is greatly appreciated, thanks for all help[/B]

---

### Post by soro2005 on 2009-05-16
It's not finding that Global Menu thingy, whatever that is. You probably know how you've installed it, so you could uninstall it, or else open a terminal, type
```
gconf-editor
```
locate the key /apps/gnome_settings_daemon/gtk-modules/globalmenu-gnome, and uncheck it. Log out, log in, report back. :popcorn:

---

### Post by randiroo76073 on 2009-05-16
Hi soro2005, thanks for reply, unfortunatly that wasn't it, I'm still w/o all, I thought synaptic had removed that, it was a holdover from ver. 8.10 but was supposed to have been removed when I was still running 8.10 . Os's, like life, ain't perfect :)

---

### Post by randiroo76073 on 2009-05-16
Fresh exsession-errors:
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
GNOME_KEYRING_SOCKET=/tmp/keyring-LpwDuO/socket
SSH_AUTH_SOCK=/tmp/keyring-LpwDuO/socket.ssh
GNOME_KEYRING_PID=4195

(gnome-settings-daemon:4194): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:4194): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
x-session-manager[4077]: WARNING: Could not launch application 'nm-applet.desktop': Unable to start application: Failed to execute child process "nm-applet" (No such file or directory)
x-session-manager[4077]: WARNING: Could not launch application '103d323a8f3493697e124236263054487200000034740034.desktop': Unable to start application: Failed to execute child process "evolution-exchange-storage" (No such file or directory)
** (deja-dup-monitor:4212): DEBUG: monitor.vala:219: Waiting 364451 seconds until next backup.
x-session-manager[4077]: WARNING: Could not launch application '103d323a8f3493697e12423626422774000000034740037.desktop': Unable to start application: Failed to execute child process "fast-user-switch-applet" (No such file or directory)
kget(4226) GenericModelObserver::addedTransferGroupEvent: OBSERVER :: Adding group  0x23f31c0
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action

** (nautilus:4203): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1a00048 (Buddy List)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1a00048 (Buddy List)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1a00048 (Buddy List)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Exiting because another libpurple client is already running.
[Error 18:46:11.933] Could not load desktop item: File 'file:///usr/share/applications/Internet/WebHTTrack-Websites.desktop' is not a regular file or directory.
[Error 18:46:11.943] Could not load desktop item: File 'file:///usr/share/applications/Internet/WebHTTrack.desktop' is not a regular file or directory.
```

---

### Post by randiroo76073 on 2009-05-17
Hmm, no other ideas? I'm bout ready to go to full re-install, have re-installed ubuntu desktop, gnome panels. Nothing works yet.

---

### Post by randiroo76073 on 2009-05-17
Lots of looks, no one willing to jump in with suggestions/help???

---

### Post by soro2005 on 2009-05-17
There are a lot of the standard applets that don't start because the executables are not found. Like the network manager applet, evolution, etc. Looks like somebody has poked around a little too much in the installation. You could reinstall network-manager, network-manager-applet, evolution, evolution-data-server and evolution-indicator (and all other evolution related packages), fast-user-switch-applet (those are the ones that fail according to the log, there might be more), and you could get rid of /usr/share/applications/Internet/WebHTTrack-Websites.desktop which is also causing a problem there.

Also try to kill the gnome panel from a terminal (killall gnome-panel) and see whether it comes back that way.

If you don't care about your customization of your gnome panel, reset it with
```
gconftool-2 --recursive-unset /apps/panel
```

Also, and although this is unlikely to yield something useful, show us the output of
```
ps aux | grep -w Z
```

Your Gnome and Nautilus seem to start okay, but hang at some point. To question is to identify the process that's hanging. Unfortunately, that's not that easy.

---

### Post by Brandon Williams on 2009-05-17
In the future, when you've got lots of log output, please mark it as code. It makes it easier to scroll through the posts. Now to try and be helpful ...

Is gnome-panel running? Try 'ps -fC gnome-panel'. Is a process listed there?

If not, then run the following commands:
```
$ gconftool-2 --get /desktop/gnome/session/required_components_list
[windowmanager,filemanager,panel]
$ gconftool-2 --get /desktop/gnome/session/required_components/panel
gnome-panel
```

Is "panel" in the required_components_list? And does the second command say "gnome-panel"?

If the answer to either of these questions is "no", then you can fix it with the following commands:
```
$ gconftool-2 --set /desktop/gnome/session/required_components_list --type=list --list-type=string '[windowmanager,filemanager,panel]'
$ gconftool-2 --set /desktop/gnome/session/required_components/panel --type=string gnome-panel
```

If the gnome-panel is already running and/or both of the gconf keys has the expected values, then there is some other problem.

One additional thing to try, if the above doesn't help, is to create a new user account on the system and log in as that user. Does that user get the expected panels? If so, then at least you have an alternative to reinstall.

PS: The Alt+F2 and menu problems are a result of the missing panel. Once the panel comes back, those two issues will also be resolved.

---

### Post by randiroo76073 on 2009-05-17
Thanks to both of you,soro2005 & Brandon Williams for your replies, will try them and reply back tomorrow, wife has me for today/nite :D

---

### Post by randiroo76073 on 2009-05-19
@-Brandon
Here's output of "ps -fc gnome-panel"
```
UID        PID  PPID  C STIME TTY          TIME CMD
```
Output of other cmmds was normal, my cli-ing takes me a little longer than it used to due to a brainphart(short-term mem-module is wonky)..LOL 
Thanks for your help, my patients is such that I'm considering a re-install, but will try to hold off and work thru this learning experience;)

---

### Post by geirha on 2009-05-19
Have you uninstalled anything recently?

Try installing the [ubuntu-desktop](apt:ubuntu-desktop) package to make sure all the packages needed for a standard ubuntu desktop to function is installed.
```
sudo aptitude install ubuntu-desktop
```

---

### Post by randiroo76073 on 2009-05-19
Thanks for reply geirha, have already done re-install of ubuntu-desktop & related, no joy there :(

PS: what would be alternative to: "gksu control-panel" as I get no response from that. Am trying to set up another user account.

---

### Post by geirha on 2009-05-19
> **randiroo76073 said:**
> Thanks for reply geirha, have already done re-install of ubuntu-desktop & related, no joy there :(

PS: what would be alternative to: "gksu control-panel" as I get no response from that. Am trying to set up another user account.

"users-admin", or alternatively "sudo adduser *new_username*" to do it in the terminal.


Let's take a specific line from you xsession-errors file. ```
x-session-manager[4077]: WARNING: Could not launch application 'nm-applet.desktop': Unable to start application: Failed to execute child process "nm-applet" (No such file or directory)
```

It can't find the network-manager applet.
```

$ which nm-applet
/usr/bin/nm-applet
$ dpkg -S /usr/bin/nm-applet
network-manager-gnome: /usr/bin/nm-applet
$ aptitude search network-manager-gnome
...

```

Is the network-manager-gnome package installed? (from the output of aptitude, it is installed if the first character is **i**. **p** means purged, and **c** means uninstalled, but configuration still around.)

---

### Post by randiroo76073 on 2009-05-19
@-soro2005
Here's output from "ps aux | grep -w Z"
```
28763  0.0  0.0   7524   960 pts/0    S+   07:17   0:00 grep -w Z
```


"Looks like somebody has poked around a little too much in the installation."
Ya, I have a leaning that way, but have always used "Synapic" and never ran into problem till now, with wonky live cd.

---

### Post by randiroo76073 on 2009-05-19
@-geirha
Yes nm-manager is uninstalled, replaced by wicd, nm-manager was giving me fits with wifi so went to wicd, more stable connection.

---

### Post by geirha on 2009-05-19
Ah, ok. Is the gnome-panel package installed? ```
aptitude search gnome-panel
``` If it is, what's the output you get if you try to run it?
```
gnome-panel
```

---

### Post by randiroo76073 on 2009-05-19
Uhmm got a definite problem now, did a re-install now cannot get to terminal inside of GUI, sorry for impatients, good thing is I am learning alot from this experience tho. Seems as if some file in my /home/user is hanging me up, ideas??

Got terminal back

---

### Post by oOarthurOo on 2009-05-19
Try this:

Hit Alt+f1 to switch to another terminal. Log in with your borked user. Then do:
```
mv ~/.local ~/.backupoflocal
```
Now restart. Did it work? If not, just revert the above change by following the same steps, but reversing the order of the move command. I.e., 
```
mv ~/.backupoflocal ~/.local
```

---

### Post by geirha on 2009-05-19
> **randiroo76073 said:**
> Uhmm got a definite problem now, did a re-install now cannot get to terminal inside of GUI, sorry for impatients, good thing is I am learning alot from this experience tho. Seems as if some file in my /home/user is hanging me up, ideas??

Reinstall of Ubuntu, but you kept /home? And now you can't log in graphically? or you can log in graphically, but you can't open a terminal?

---

### Post by randiroo76073 on 2009-05-19
I've got terminal back(desktop launcher), Panel will come back thru "gnome-panel" but only stays running as long as I have terminal running. Yes, kept home

---

### Post by randiroo76073 on 2009-05-19
oOarthurOo thanks for chiming in :) will try as soon as get back from throne, desperate need

---

### Post by randiroo76073 on 2009-05-19
@ oOarthurOo
No joy there

---

### Post by geirha on 2009-05-19
Try moving away ~/.config/autostart
```
mv ~/.config/autostart{,backup}
```
Log out and back in again. Same deal?

.config/autostart contains the entries you've added/removed from System -> Preferences -> Sessions.

---

### Post by randiroo76073 on 2009-05-19
@ geirha
Nope, no joy there either

LOL, guess I could just leave a terminal running

---

### Post by soro2005 on 2009-05-19
```
gnome-panel &
```
Then you should be able to close the terminal with
```
exit
```

---

### Post by randiroo76073 on 2009-05-19
@ soro2005

Thats a rather novel way of doing it.....LOL, doesn't stick thru reboot tho.
This is getting to be quite a learning experience for me :)

---

### Post by oOarthurOo on 2009-05-19
If you've reinstalled, and the problem persists, I'd suggest deleting the customization folders. Your files will remain intact, but you'll have to reconfigure gnome to your liking. Start peeling them off one at a time, logging out or restarting, loggin in.

The folders I'm talking about are 
.local
.gnome2
.gnome2_private
.config
.gconf
.gconfd

a mv command might not be sufficient, you may need to mv -R as well. If you do this one at a time, you can at least narrow down the source of the problem should it reoccur, and also mv the non-problematic folders back so there is less work to do to get your desktop back up the way you like.

---

### Post by oOarthurOo on 2009-05-19
I'm a bit unclear what the current problem is... you seem to have resolved a lot of the issues in the original post. Can you summarize the current state of things?

---

### Post by randiroo76073 on 2009-05-19
@ oOarthurOo
Sounds like a plan to me, I can sudo into nautilus, create a backup folder at /media/Extras(nother partition) transfer back & forth from there :) Be back with results when I'm done.

---

### Post by randiroo76073 on 2009-05-19
@ oOarthurOo
Current state is: at startup/login I still have no Menu, no F2, no panels unless I open a terminal & code in " gnome-panel & " and then use " exit " to close terminal

---

### Post by randiroo76073 on 2009-05-19
Alrighty, by process of elimination, the winner is: /home/user/.local. I'm going to try to narrow it further & will post the results here.

Thank all of you who took the time to help me with this problem :D

---

### Post by oOarthurOo on 2009-05-19
If the culprit is .local, then the cause might be a bug I'm currently looking into. At the moment, the best advice I can give on how to avoid this re-occurring is to avoid deleting anything using alacarte. Just untick what you don't want to see, but don't delete.

If the problem turns out to not be .local, then feel free to ignore my warnings about alacarte.

---

### Post by randiroo76073 on 2009-05-19
I've rebooted 3 times now and everything seems OK. Till you mentioned it I had forgotten that I had deleted a item from alacarte just before trying the disk to 9.10 alpha. Hope this info helps.

PS: .local was the last folder I tried.

---

### Post by randiroo76073 on 2009-05-20
It's somewhere in /.local/share/applications, I strongly suspect the "alacarte.desktop..... given your post.

---

### Post by oOarthurOo on 2009-05-20
The bug has been confirmed, however, it is marked as invalid won't fix. So, until the developers remove the ability to delete entries from the menu using alacarte you should avoid doing so. 

[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/378422](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/378422)

---

### Post by randiroo76073 on 2009-05-21
Oh swell, now I've got a menu editor that can crash my desktop to unusability and it's "no big thing" ! What do I do with all the customizations of the menu since I can no longer access them & can't tell what they go to ??? Do I just keep adding to the file till it finally gets so big it starts to affect other apps, Oh, I forgot, dev's said that can't happen, it's no big thing. Ya!Right! and the moon is made of green cheese

---

### Post by Brandon Williams on 2009-05-21
OK ... here's what's going on ... 

If you delete an item from one of the menus using alacarte, an <appname>.desktop file is created in ~/.local/share/applications/ with a line that says 'Hidden=true'. For some reason, if a desktop file for an application in your local apps directory has this flag, the app won't be started when you log in, probably because it will be ignored when gnome searches for the application, and thus gnome doesn't know what command to run. If you delete Panel from the menu, the resulting 'Hidden=true' flag in gnome-panel.desktop will prevent gnome-panel from being found and started at login. Likewise for nautilus, and gnome-wm. If you delete any of these core components, each of which is specified in gconf as require components for the gnome desktop, you will lose functionality as a result.

When this problem occurs, simply delete the bad .desktop file. For example, if the panel doesn't start, then 'rm -f ~/.local/share/applications/gnome-panel.desktop'. If you're uncertain which deletion is causing trouble for you, then 'grep Hidden=true ~/.local/share/applications/*.desktop' to get a list of all the .desktop files that are candidates.

To avoid this in the future, simply avoid deleting items that represent important desktop elements from the menu. If you really just can't help yourself and that item *that only shows up in the menu editor* is too much to bear :-) ... try adding the associated application to your 'Startup Applications'. I don't know if that will work, but it's worth a try if it's important to you.

FWIW, I agree that this is a real bug. Deleting an item from the menu should not lead to gnome's refusal to start the app at login. If Hidden means "don't start at login", then there should be another way to indicate that the item shouldn't show up in the menu editor. Still, understand the developer's point, since deleting an item from the menu doesn't really buy you anything. In fact, you're better off not doing it, because deleting the item from the menu eats up a little bit of disk space, when simply unchecking the item will be perfectly adequate for 99.9% of users.

---

### Post by oOarthurOo on 2009-05-21
Brilliant reply Brandon, thanks for the information. =D>

---

### Post by randiroo76073 on 2009-05-21
Thanks for the clarification Brandon, so anything I created that wasn't on the menu originally should be safe to delete ? I usually only delete duplicate items but also add/customize my menu to my liking, unchecking things I won't/don't use :)

---

### Post by Brandon Williams on 2009-05-22
Generally speaking, you don't gain anything for your system by deleting the item using alacarte, since it cleans up the alacarte interface a little bit, but the item is still taking up disk space. What I recommend is this ... If you created the item, delete it by removing the .desktop file from your .local/share/applications/ directory. If you didn't create the item, then don't delete it. Just put up with the clutter in alacarte.

If you have duplicate items showing up in alacarte, you should be able to make the dupes go away by editing the .desktop file and removing entries from the Categories property. If the .desktop file in question is in /usr/share/applications/, then copy it into your .local/share/applications/ directory and edit your copy.

You might also consider using the Other category, which many people don't display in their menus anyway, as a holding ground for items that you would have deleted altogether, in which case you would simply remove the Categories property. It should now only show up in the Other category, and nowhere else.

---

### Post by randiroo76073 on 2009-05-25
Thanks for further clarification Brandon, sound advise :)

---

### Post by randiroo76073 on 2009-05-28
Ok, this is what I meant by affecting other app's: Any changes/customizations to Panel's whether made on desktop or thru the configuration editor do not stick, every time I reboot they go back to default settings and I have to do it all over again, so esentially I have a borked/crippled fresh install of Jaunty 9.04. While I may be the only one experiencing this problem(doubtful), I stil do not understand how it can just be shuffled off as "invalid" by dev's, I think this is going to come back and bite somebody right in the bum !!!

---

### Post by oOarthurOo on 2009-05-28
Have you tried deleting the panel, and recreating it?

---

### Post by randiroo76073 on 2009-05-28
Thanks for the thought arthur, deleted all 2 of my panels & had to sudo "gnome-panels" to get anything back. No joy there, still borked, no sense in even trying to customize, first reboot/shutdown-restart it's gone. Wish the "INVALID" dev's had this prob up their bum, maybe it'ud constipate them enough so they'd think about it for a while(GRRRR!)

PS: They'll probably carry this "INVALID" over into 9.10 and it'll be borked too!

---

### Post by oOarthurOo on 2009-05-28
Start a new thread with this issue. My hunch is that the panels not remembering customizations is unrelated to this bug, unless you mean, menu's not remembering customizations. In either case, a new forum post will cut down on the clutter and generate new interest. Link to it here so that I can follow along.

---

### Post by randiroo76073 on 2009-05-29
Neither one is remembering, panels or menu. I'm still working on it, trying to narrow it down to a specific file/files. I ain't whooped yet, tho your towel is starting to look like a good idea :)

PS: The only thing good so far is I now have "Alt-F2" working

---

### Post by soro2005 on 2009-05-29
If you do "sudo gnome-panel", then the customizations will be written by superuser (b/c of the sudo) and your normal user won't have the sufficient rights to change the relevant files. Either take ownership and change the relevant permissions, or remove the config files again and start over, without sudo.

---

### Post by randiroo76073 on 2009-05-29
Thanks soro2005 :), already triped myself(dumb & dumber) and went back and cleaned up.

---

### Post by soro2005 on 2009-05-29
> **randiroo76073 said:**
> Thanks soro2005 :), already triped myself(dumb & dumber) and went back and cleaned up.

Don't worry, it happens. My top two of things to check if random things fail: 1. ownership and permissions, 2. what's going on in your path (~/bin). Learned from painful experience. :popcorn:

---

### Post by randiroo76073 on 2009-06-04
Alright, I give up! I, as a user(not a dev) have done everything I can think of. I've gone into my backups from the day before to the week before this started, with no joy. I wish this problem with "[COLOR="Red"]alacarte[/COLOR]" had been made more public instead of just being tagged by the "[COLOR="Red"]DEV's[/COLOR]" as "[COLOR="Red"]invalid[/COLOR]" Either the "[COLOR="Red"]DEV's[/COLOR]" couldn't or wouldn't fix it, but it sure borked my system all to hell ! I'm gonna bite the bullet and do a fresh install after deleting the following folders from /home/user:
.local
.gnome2
.gnome2_private
.config
.gconf
.gconfd
as the problem seems to have it's roots there.
The good thing that has come from this is I now know alot more about my system than I ever did before(if my tired old brain can retain):)
Many thanks to all who chimed in with advise, your support was appreciated !

---

### Post by Brandon Williams on 2009-06-04
You should not need to do a fresh install, even if you can't fix your current user. Have you tried creating a new user? A completely new user should not display the same problems if this is related to the user config, and creating a new user is much less painful than a fresh install.

Of course, if the system is in a bad state because of global changes that you made while trying to fix the problem, then a fresh install might be the only option if you can't remember/find everything that needs to be reversed.

---

### Post by randiroo76073 on 2009-06-04
Thanks for reply Brandon, I think at this point a fresh install will be simplest, I have 5 other distros installed(writing from gOS, lvm rather than old style partitioning) & they're stable at present. Ubuntu is my main/core/swing distro that all the children are booted from, and yes I know I shouldn't play with it, LOL, but I can't resist the temptation, live & learn(hopefully). The good side is I've gotten a better understanding of Ubuntu(smiles wearily).
Thanks
Randy

---

### Post by mocha on 2009-06-09
I got bit by this one too.  Very disappointing.  I thought by now these issues with alacarte would be fixed.  This should be at the top of the list for Gnome to fix, or simply remove the delete button.

In case this might help anyone, after "resetting" my environment by renaming the dirs (.gnome, .gconf, .local, .config, etc etc...) I still couldn't get into Gnome, I had to rename my .profile file and now it lets me login.  This is very strange.  My .profile is as follows:

```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```

The only thing it does is add my home bin directory to the path.  What's so controversial about that that causes Gnome not to load?!?!

---

### Post by Brandon Williams on 2009-06-09
Post the content of your ~/.bashrc file and a listing of the contents of your ~/bin/.

---

### Post by mocha on 2009-06-10
> **Brandon Williams said:**
> Post the content of your ~/.bashrc file and a listing of the contents of your ~/bin/.

Here's my .bashrc.  I'm not going to post a list of my ~/bin, there's a ton of stuff in there.  Is there something I should be looking for?  Recall, everything with my configuration was fine until I started deleting menu items and had to "reset" the environment.

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups
# ... and ignore same sucessive entries.
export HISTCONTROL=ignoreboth

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_colored_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
	# We have color support; assume it's compliant with Ecma-48
	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
	# a case would tend to support setf rather than setaf.)
	color_prompt=yes
    else
	color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'

    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

shopt -s histappend
PROMPT_COMMAND="history -a; $PROMPT_COMMAND"
#PROMPT_COMMAND="history -a; history -n"

export VDPAU_NVIDIA_SYNC_DISPLAY_DEVICE="DFP-1"
export __VDPAU_NVIDIA_SYNC_DISPLAY_DEVICE="DFP-1"
export GL_SYNC_TO_VBLANK=1
export __GL_SYNC_TO_VBLANK=1
export GL_SYNC_DISPLAY_DEVICE="DFP-1"
export __GL_SYNC_DISPLAY_DEVICE="DFP-1"
```

The export lines at the bottom used to be in my .profile file, but since I can't use .profile anymore, I put them in .bashrc now.

---

### Post by randiroo76073 on 2009-06-10
> **mocha said:**
> I got bit by this one too.  Very disappointing.  I thought by now these issues with alacarte would be fixed.  This should be at the top of the list for Gnome to fix, or simply remove the delete button.


Ya mocha, I'm really po'd at the devs over this one. Cost me alot of time recustomising my setup + time tryin to find an answer to a glitch that never should have been there. This goes deeper than they want to admit. Wish I had an answer for you other than re-install.

---

### Post by Brandon Williams on 2009-06-10
> **mocha said:**
> I'm not going to post a list of my ~/bin, there's a ton of stuff in there. Is there something I should be looking for?  Recall, everything with my configuration was fine until I started deleting menu items and had to "reset" the environment.

Nothing looks out of the ordinary in your ~/.bashrc. The only thing that explains why moving your .profile out of the way would be causing trouble is the possibility that you have a program in your ~/bin directory that is over-riding a standard system program. By moving your ~/bin directory out of the way, you prevent that over-ride during session initialization, so the session starts up OK.

---

### Post by randiroo76073 on 2009-06-16
Ya, well here we are in alpha 2 of Karmic and Alacarte still has the same problem, [COLOR="Red"]**DO NOT DELETE ANYTHING FROM ALACARTE OR IT WILL MESSUP YOU"RE MENU'S & PANELS!!!**[/COLOR]

---

