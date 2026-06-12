---
title: "xfdesktop does not start on boot up"
date: 2008-01-23
forum: Desktop Environments
---

### Post by nutts4life on 2008-01-23
OK,

I installed the minimal ubuntu server and added xfce4 and all the apps.

Now i've got it all configured OK, but i have one really annoying problem.

I can't get the 'allow xfce to manage the deskop' checkbox to stayed checked on startup.

Ok, i know what you are going to say:
Just check the box then save the session when you exit.

I really don't want to do that, i've configured everything else using the files in the .config directory and the /etc/xdg/xfce4 directory and everything is now set for all users.

BUT, it seems that there is no configuration file that forces xfce4 to manage the desktop.

I know what you are going to say now. Edit your xinitrc. 
I checked that and it has xfdesktop & there. No probs. (I edited one in /etc/xdg/xfce4/ and one in /home/user/.config)

So if i run xfdesktop & in a terminal it starts fine and my background appears fine. But it i can't get it started on boot up.

Any ideas? I really don't want to rely apon saving the session, i want this to be coded somewhere.

Thanks!

---

### Post by nutts4life on 2008-01-28
Anybody? This is really annoying and i'm sure it isn't that difficult to fix. 

I'm just a lonely linux sole learning his way to a beautiful place.

---

### Post by mali2297 on 2008-01-28
I haven't had this problem. :-k 

How do you start Xfce? Try using
```

startxfce4

```

If xfdesktop still doesn't start, there is also the option to add it to autostart. Go to Xfce4 menu > Settings > Xfce 4 Autostarted Applications, or create a .desktop file in the ~/.config/autostart/ directory.

---

### Post by nutts4life on 2008-01-30
Thanks for your reply.

I run xfce from a autologin script which runs xfce4start.

I will try putting it in autostart. thanks.

O

---

### Post by nutts4life on 2008-02-01
I'm not on my linux PC so bear with me here.

I managed to fix the problem and it's worthing noting what i did for future reference.

The idea behind my project was to remove the idea of the xfce4-session completely. I don't want to have to worry about saving a session to save my settings as i want to just hard code my settings from the off.

The problem is xfce4-session is started by default by xfce4 on startup.

The startup of xfce4 is found in the file XDG_CONFIGHOME/xinitrc . This is usually /etc/xdg/xfce4/xinitrc for most installs. 

What i didn't notice in this script is that if the xfce4-session is found then the script is exited: 
exit 0;

This then means the rest of the boot process is handled from your last login. Therefore xfdesktop is started, as is orage and of course your autostart apps. One last important this that is started with xfce4-session is gnome/kde services. I will come to those later.

So basicaly i commented the line:
'which xfce4-session' so that xfce4-session is not started and the rest of the script is run.

The rest of the script runs xfdestop & and orage manually and of course your startup apps.

One problem you will find is that gnome services will not start, so you will need to add this to the file.
This example, my gnome file is gnome-keyring-daemon.

so i ran:
eval " 'gnome-keyring-daemon'"

and passed the data to my nm-applet. This gnome service has then been started manually.

This makes the system very quick as there is no gnome bloat, but of course you have to be careful which apps you install.

I hope this helps someone.

O

---

