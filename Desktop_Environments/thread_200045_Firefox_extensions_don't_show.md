---
title: "Firefox extensions don't show"
date: 2006-06-19
forum: Desktop Environments
---

### Post by 3dsoft on 2006-06-19
When logged in as "sudo" I am having no problems installing extensions. But when logged in as a normal user I am not able to use them. It is possible to install extensions as a normal user but again the are not active.

How do I install firefox extensions **within a normal user account?**

---

### Post by johnc4510 on 2006-06-19
Click on Tools, Click on Extensions, Click on Get More Extensions
It will open a new browser window to the extensions page, navigate to the one you want to install, and click on install.
It will ask you if you want to install the extension, click on yes.
The extension will be installed when you restart Firefox

---

### Post by 3dsoft on 2006-06-19
The extension seems to be installed but it is NOT usable. 
How do I properly install an extension as an normal user. Do I have to change permissions?

---

### Post by aysiu on 2006-06-19
```
sudo chown -R 3dsoft:3dsoft /home/3dsoft/.mozilla
``` And then the next time you need to launch Firefox as sudo, launch it with this command ```
gksudo firefox
``` instead of this command ```
sudo firefox
```

---

### Post by johnc4510 on 2006-06-19
aysiu, why would you have to launch firefox with sudo or gksudo?

---

### Post by aysiu on 2006-06-19
Well, depending on how you installed it (i.e., if it's not the Ubuntu version of Firefox), you may need to occasionally run it as root in order to install updates. Otherwise, the option is greyed out.

From [https://wiki.ubuntu.com/FirefoxNewVersion:](https://wiki.ubuntu.com/FirefoxNewVersion:) > There are two ways you can update firefox to the newest version.

The first way is to close Firefox and give your user (yourself) file ownership: sudo chown -R ${USER}:${USER} /opt/firefox Start Firefox normally and update (Help -> Check for updates...) Once the update is completed, close Firefox and then restore ownership to root: sudo chown -R root:root /opt/firefox Do NOT browse other sites while firefox has these elevated permissions, that is without changing back the ownership of /opt/firefox over to root. Such a practice is not safe.

Note that the following alternative method may give some files in your home directory root ownership and cause problems. The first method above is safer. To update firefox you can run Firefox from the terminal with  gksudo firefox . Be sure to close any running version of Firefox first. Enter your password where prompted. Then check update (Help -> Check for updates...). It may prompt you to restart Firefox. When Firefox restarts you should see a Mozilla page confirming that you're using the latest version. Close Firefox and open it as a normal user (the way you usually open it). Firefox should now be updated to the newest version for all users. This way you don't have to change any file permissions and you wont forget to not change them back. 

---

### Post by 3dsoft on 2006-06-19
Strange but it didn't help.

---

### Post by johnc4510 on 2006-06-19
Thanks, that makes sense.

---

### Post by aysiu on 2006-06-19
Can you run these commands and post the output back here? ```
cd ~/
ls -al
cd ~/.mozilla/firefox
ls -al
```

---

### Post by 3dsoft on 2006-06-19
[B]
cd ~/[/B]

> drwxr-xr-x 33 mstar mstar 4096 2006-06-19 17:50 .
drwxr-xr-x  3 root  root  4096 2006-06-17 15:14 ..
-rw-r--r--  1 mstar mstar  144 2006-06-17 12:50 .audacity
-rw-------  1 mstar mstar 5317 2006-06-20 00:08 .bash_history
-rw-r--r--  1 mstar mstar  220 2006-06-13 19:30 .bash_logout
-rw-r--r--  1 mstar mstar  414 2006-06-13 19:30 .bash_profile
-rw-r--r--  1 mstar mstar 2227 2006-06-13 19:30 .bashrc
drwxr-xr-x  3 mstar mstar 4096 2006-06-14 00:25 .config
drwxr-xr-x  3 mstar mstar 4096 2006-06-19 18:45 Desktop
-rw-------  1 mstar mstar   26 2006-06-13 19:40 .dmrc
drwxr-xr-x  5 mstar mstar 4096 2006-06-19 18:07 Downloads
-rw-------  1 mstar mstar   16 2006-06-13 19:40 .esd_auth
drwxr-xr-x  7 mstar mstar 4096 2006-06-17 15:13 .evolution
lrwxrwxrwx  1 mstar mstar   26 2006-06-13 19:30 Examples -> /usr/share/example-c ontent
-rw-r--r--  1 mstar mstar 4534 2006-06-19 11:03 .fonts.cache-1
drwx------  4 mstar mstar 4096 2006-06-19 17:02 .gconf
drwx------  2 mstar mstar 4096 2006-06-20 00:14 .gconfd
drwx------  3 mstar mstar 4096 2006-06-19 17:03 .gftp
drwxr-xr-x 21 mstar mstar 4096 2006-06-19 18:39 .gimp-2.2
-rw-r-----  1 mstar mstar    0 2006-06-20 00:07 .gksu.lock
drwxr-xr-x  4 mstar mstar 4096 2006-06-17 15:25 .gnome
drwx------  9 mstar mstar 4096 2006-06-19 18:35 .gnome2
drwx------  2 mstar mstar 4096 2006-06-13 19:40 .gnome2_private
drwx------  2 mstar mstar 4096 2006-06-16 23:43 .gnupg
drwx------  4 root  root  4096 2006-06-17 15:27 .googleearth
drwxr-xr-x  2 mstar mstar 4096 2006-06-13 22:25 .gstreamer-0.10
-rw-------  1 mstar mstar    0 2006-06-17 13:05 .gtk-bookmarks
-rw-r--r--  1 mstar mstar   87 2006-06-13 19:40 .gtkrc-1.2-gnome2
-rw-------  1 mstar mstar 2642 2006-06-19 17:02 .ICEauthority
drwx------  3 root  root  4096 2006-06-17 15:25 .kde
drwxr-xr-x  3 mstar mstar 4096 2006-06-14 00:26 .local
drwx------  3 mstar mstar 4096 2006-06-17 14:58 .macromedia
drwx------  3 mstar mstar 4096 2006-06-13 19:40 .metacity
drwx------  3 mstar mstar 4096 2006-06-19 11:52 .mozilla
drwx------  3 mstar mstar 4096 2006-06-19 11:52 .mozilla-thunderbird
drwxr-xr-x  2 mstar mstar 4096 2006-06-17 15:37 .mplayer
drwxr-xr-x  3 mstar mstar 4096 2006-06-13 19:40 .nautilus
drwx------  3 mstar mstar 4096 2006-06-19 21:37 .openoffice.org2
drwxrwxrwx 13 mstar root  4096 2006-06-19 19:19 .opera
drwxr-xr-x  2 mstar mstar 4096 2006-06-17 13:31 .qt
-rw-------  1 mstar mstar 8448 2006-06-19 21:37 .recently-used
-rw-------  1 mstar mstar  108 2006-06-19 11:45 .serverauth.7307
drwx------  3 mstar mstar 4096 2006-06-17 13:33 .Skype
-rw-r--r--  1 mstar mstar    0 2006-06-13 20:22 .sudo_as_admin_successful
drwx------  4 mstar mstar 4096 2006-06-13 20:01 .thumbnails
drwx------  2 mstar mstar 4096 2006-06-19 18:45 .Trash
drwx------  2 mstar mstar 4096 2006-06-13 19:40 .update-notifier
-rw-------  1 mstar mstar 1060 2006-06-17 10:03 .viminfo
drwxr-xr-x  9 mstar mstar 4096 2006-01-17 21:18 VRT
-rw-------  1 mstar mstar  169 2006-06-19 17:02 .Xauthority
drwxr-xr-x  2 mstar mstar 4096 2006-06-17 13:35 .xine
-rw-r--r--  1 mstar mstar 5801 2006-06-19 23:30 .xsession-errors


[B]
cd ~/.mozilla/firefox[/B]

> drwx------ 6 mstar mstar  4096 2006-06-20 00:13 bamskjjp.default
-rw------- 1 mstar mstar 11574 2006-06-19 21:20 pluginreg.dat
-rw-r--r-- 1 mstar mstar    94 2006-06-13 19:42 profiles.ini



-----
thanks for your help

---

### Post by aysiu on 2006-06-19
And when you do ```
cd banskjjp.default
ls -al
``` Do you get a line that looks something like this? ```
**drwxr-xr-x** 10 mstart mstar    4096 2006-06-19 08:42 extensions

```

---

### Post by 3dsoft on 2006-06-20
Yes, I get this line:

> drwxrwxrwx 2 mstar mstar   4096 2006-06-20 08:30 extensions


---

### Post by aysiu on 2006-06-20
Looks as if you have a bit too many *w*'s in there.

Can you try [this](http://www.ubuntuforums.org/showthread.php?t=103930) and see if you can then install extensions?

If that still doesn't work, and you want your old profile back: ```
rm -rf ~/.mozilla
mv ~/.mozilla_backup ~/.mozilla
```

---

### Post by 3dsoft on 2006-06-20
Guess what?
It really works now. Finally I am able to install some firefox extensions.
Thank you very much for your time and your help!

---

