---
title: "Password"
date: 2024-10-02
forum: Desktop Environments
---

### Post by angel mike on 2024-10-02
Is there a way to login without requiring a password. I am aware of the security issues but only my laptop for keeping notes. Tried PAM and that does not work. I am the sole user.

---

### Post by angel mike on 2024-10-02
Opening the 'Activities' and clicking on 'Automatic Login' does not work

---

### Post by 1fallen on 2024-10-02
The DE your using would have been nice to add, please show this:
```
systemctl status display-manager
```

---

### Post by deadflowr on 2024-10-02
Which version of Ubuntu as they change the name sometimes.
But in General, as an example on 24.04, 
goto Settings > System > Users.
Find your user click on it, then click on the lock/unlock up in top area of the window.
Then select the option that says Automatic Login and toggle it to on.

---

### Post by yancek on 2024-10-02
> Opening the 'Activities' and clicking on 'Automatic Login' does not work 				 

Typing in login in the Activities menu gets the same window referred to in post 4, Settings/Users which is the same on 22.04 and I believe has been used for a number of years.

---

### Post by angel mike on 2024-10-04
Apologise for the slow response.
Request by 1Fallen2 gives on putting '[COLOR=#000000][FONT=&quot]systemctl status display-manager' into the Terminal[/FONT][/COLOR]

mgstevens@mgstevens-XPS-13-9310:~$ systemctl status display-manager
&#9679; gdm.service - GNOME Display Manager
     Loaded: loaded (/lib/systemd/system/gdm.service; static)
     Active: active (running) since Fri 2024-10-04 08:00:38 BST; 2min 19s ago
    Process: 775 ExecStartPre=/usr/share/gdm/generate-config (code=exited, stat>
   Main PID: 803 (gdm3)
      Tasks: 3 (limit: 18755)
     Memory: 7.1M
        CPU: 113ms
     CGroup: /system.slice/gdm.service
             &#9492;&#9472;803 /usr/sbin/gdm3


Oct 04 08:00:38 mgstevens-XPS-13-9310 systemd[1]: Starting GNOME Display Manage>
Oct 04 08:00:38 mgstevens-XPS-13-9310 systemd[1]: Started GNOME Display Manager.
lines 1-13/13 (END)

---

### Post by angel mike on 2024-10-04
For deadflower I am using Ubuntu 22.04.. Yes I did that and it does open up the desktop automatically but when I try to use 'Brave' my search engine it requests my password in the usual separate window.

---

### Post by Shibblet on 2024-10-04
I made my password "Hercules," but then Ubuntu said it wasn't strong enough...

---

### Post by mmuzar on 2024-10-18
The prompt you are seeing once you open your browser is to unlock your keyring.
You can open "Passwords and Keys" manager and change the passphrase of the default keyring to something simple or entirely blank.

---

