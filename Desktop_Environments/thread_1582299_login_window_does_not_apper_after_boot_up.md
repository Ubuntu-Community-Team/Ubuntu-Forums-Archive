---
title: "login window does not apper after boot up"
date: 2010-09-26
forum: Desktop Environments
---

### Post by Sharath on 2010-09-26
My laptop did a "shutdown" (not reboot) automatically over night when I was downloading few things. When I tried to boot it up, it boots up & it never displays the window which asks for password. I have tired to reboot it several times since then it still stays at the same place. Since it is not displaying username & password window & I am not able to login through gdm. Interesting thing is the normal sound which comes when the login window is display is heard but the window is not seen.

However when I press ctrl+alt+f5 I am able to login there which is only text based login.

I tried several things to get out of issue like

1) in the console run
   ps -eaf | grep -i gdm
   I see that the login process is running but is not displaying the 
   window.

2) sudo dpkg-reconfigure xserver-xorg ( it didnt ask me anything about the driver or anything like that & just returned with out any error message )
$? of the above command was 0.
==> reboot after this & still the login window would not come.

3) after login at the console ( ctrl_alt+f5 )
sudo service gdm stop ==> no error prints
sudo service sdm start ==> no error prints
==> no login window

4) apt-get remove ubuntu-desktop
   apt-get install ubuntu-desktop
==> no login window

5) export DISPLAY=:0.0
   sudo -u gdm gnome-control-center 2>gdm.txt ( this the attached error messages)
   ctrl+alt+f7
==> no login window

any clues.? I would hate to reinstall ubuntu again cause of the amount of software + data + personalization. Awaiting a quick solution/workaround for this.

---

### Post by sikander3786 on 2010-09-26
See these recent threads.

[http://www.ubuntuforums.org/showthread.php?p=8780648](http://www.ubuntuforums.org/showthread.php?p=8780648)

[http://www.ubuntuforums.org/showthread.php?t=1385455](http://www.ubuntuforums.org/showthread.php?t=1385455)

---

### Post by Sharath on 2010-10-11
this ticket can be closed. The issue got resolved.

I think the issue was "pidgin dev files which had replaced the existing X libraries.

---

### Post by samortan on 2010-10-11
This happened with me , when i did Window 7 in my system. The same happened with me as well. Then i reboot it and did window XP again in my pc.  It suits me well.

---

