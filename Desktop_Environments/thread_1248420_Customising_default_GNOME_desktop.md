---
title: "Customising default GNOME desktop"
date: 2009-08-24
forum: Desktop Environments
---

### Post by .kkursor on 2009-08-24
Hello all!
I have a rather specific task. I am making an Ubuntu-based Linux distro which main task is accepting users from Active Directory and providing access to Offtopic Server 2003 terminal servers. AD logons are handled by LikeWise-Open 4. 
I have customized default user profile and want it to be spread over all new users who log on the computer. On first logon a folder /home/local/%username% is created, but it is filled with default Ubuntu files and folders. I have googled a lot and found that the folder /etc/skel is used to store default profiles, but it works only with useradd. In my case a user is not actually added to system, therefore useradd is not executed and the default profile is not copied to user's home directory.
Is there a correct way to replace default Ubuntu profile with customized one? I have it in /etc/skel and /home/user.
Thank you!

---

### Post by Copernicus1234 on 2009-08-24
In whatever script that creates the user directory you should be able to simply add a copy of the profile template files from /etc/skel, or even better, make a symbolic link to the one in /etc/skel so when you change it, the changes are in effect for all users.

Or am I misunderstanding the problem?

---

### Post by .kkursor on 2009-08-24
Thanks for your reply!
You describe the problem absolutely correctly, but I don't know which scripts create the profile. If I knew, I'd modified them easily. Symlink is not a good idea as each user in my system should have his own workspace.

---

### Post by .kkursor on 2009-08-24
Sabayon is probably the solution, but it fails to run properly with an segfault (Ubuntu Jaunty 9.04 with all updates applied).
The resulting system will be given to public, indeed :) we test it inside our enterprise now, we have no pirated offtopics on our computers remaining :) and users didn't notice difference, I think...

---

### Post by Copernicus1234 on 2009-08-24
Ok, so you need a global file that gets run for all user logins where you can put the copy command of the profile files?

Try /etc/profile, that will get run for all users if they use bash or sh as a command shell. You should be able to see what user it is from the /etc/profile script by checking the $USER shell variable. It will contain the username and you can use that to copy the profile files to the users home directory.

---

### Post by .kkursor on 2009-08-24
Ok, I see. You mean on every login I should check if the needed directory exists, and, if not, create it and fill it with data? That is a solution, but maybe there is a way to do it once on first login and to avoid it on latter logins?

---

### Post by Copernicus1234 on 2009-08-24
I wouldnt check if the home directory exist because it should exist already when /etc/profile is run. You have something creating the home directory already, right? You said it was being created and filled up with files. But you dont know which script is creating it.

I would check if the user specific profile file exists (/home/username/.profile) and if it already exists and is the same size as in the skeleton directory, just skip the copy.

Or you could copy it on every logon, its not like you will notice the performance difference. But all changes to individual profile files will then get lost.

In any case, you can implement whatever way of doing this you like by checking for file/directory existence in combination with the $USER variable in the /etc/profile script. :)

Perhaps you want the GNOME settings to be the same for all users? The above is if you want the Linux profile to be the same for all users, and thats not the same as Gnome settings.

---

### Post by .kkursor on 2009-08-24
> Perhaps you want the GNOME settings to be the same for all users? The above is if you want the Linux profile to be the same for all users, and thats not the same as Gnome settings.
No. I want the profile to be customized by default (i.e. company logo as a default wallpaper, default screensaver and taskbar parameters and so on), but physically they should be different for each user. I think that there is a script that creates default directory layout in GNOME upon first login.
Default directory layout of user profile (in Russian):
```
&#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052;@dil1:~$ ls -lah
&#1080;&#1090;&#1086;&#1075;&#1086; 160K
drwxr-xr-x 27 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 15:51 .
drwxr-xr-x  3 root        root                4,0K 2009-08-24 14:06 ..
drwx------  3 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:09 .adobe
-rw-------  1 root        root                 284 2009-08-24 15:51 .bash_history
drwxr-xr-x  3 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:55 .cache
drwxr-xr-x  5 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:55 .config
drwx------  3 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:07 .dbus
-rw-------  1 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072;   26 2009-08-24 14:07 .dmrc
-rw-------  1 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072;   16 2009-08-24 14:07 .esd_auth
drwx------  4 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:08 .gconf
drwx------  2 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 15:12 .gconfd
-rw-r--r--  1 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072;   76 2009-08-24 14:07 .gconf.path.defaults
-rw-r--r--  1 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072;   77 2009-08-24 14:07 .gconf.path.mandatory
drwx------  2 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:07 .gconf.xml.defaults
drwx------  2 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:07 .gconf.xml.mandatory
-rw-r-----  1 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072;    0 2009-08-24 14:07 .gksu.lock
drwx------  6 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:07 .gnome2
drwx------  2 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:07 .gnome2_private
drwxr-xr-x  2 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:07 .gstreamer-0.10
drwx------  2 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:07 .gvfs
-rw-------  1 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072;  155 2009-08-24 14:07 .ICEauthority
-rw-r--r--  1 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072;   68 2009-08-24 14:06 .k5login
drwx------  3 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:55 .local
drwx------  3 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:09 .macromedia
drwx------  4 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:09 .mozilla
drwxr-xr-x  3 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:07 .nautilus
drwx------  2 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:55 .pulse
-rw-------  1 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072;  256 2009-08-24 14:07 .pulse-cookie
-rw-------  1 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072;  870 2009-08-24 14:55 .recently-used.xbel
drwx------  2 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:17 .tsclient
-rw-------  1 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072;  115 2009-08-24 14:07 .Xauthority
-rw-r--r--  1 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072;  12K 2009-08-24 15:05 .xsession-errors
drwxr-xr-x  2 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:07 &#1042;&#1080;&#1076;&#1077;&#1086; (Video - my remark)
drwxr-xr-x  2 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:07 &#1044;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1099; (Documents)
drwxr-xr-x  2 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:07 &#1050;&#1072;&#1088;&#1090;&#1080;&#1085;&#1082;&#1080; (Images)
drwxr-xr-x  2 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:07 &#1052;&#1091;&#1079;&#1099;&#1082;&#1072; (Music)
drwxr-xr-x  2 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:07 &#1054;&#1073;&#1097;&#1077;&#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1085;&#1072;&#1103; (Shared)
drwxr-xr-x  2 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:07 &#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083; (Desktop)
drwxr-xr-x  2 &#1057;&#1072;&#1088;&#1082;&#1089;&#1103;&#1085;_&#1040;&#1044;&#1052; &#1055;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1080;^&#1076;&#1086;&#1084;&#1077;&#1085;&#1072; 4,0K 2009-08-24 14:07 &#1064;&#1072;&#1073;&#1083;&#1086;&#1085;&#1099; (Templates)
```

If only I knew where is this layout created...
If I don't find any other solution, I'll write scripts as you said... Thank you...

---

### Post by .kkursor on 2009-08-25
Up.
Who can help locate GNOME profile initialization scripts?

---

