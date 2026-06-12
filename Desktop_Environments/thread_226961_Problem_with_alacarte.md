---
title: "Problem with alacarte"
date: 2006-08-01
forum: Desktop Environments
---

### Post by aum11 on 2006-08-01
Whenever i try to start alacarte by applications/accessories/alacarte menu editor, it tries to start and then disappears.

Any suggestions?

---

### Post by Ziox on 2006-08-01
run alacarte from the terminal, i think this command will start it, but i'm not sure since i've never used alacarte b4:

alacarte

---

### Post by aum11 on 2006-08-01
Thanks Ziox but that did not work.  Have You given me the full command for this?

---

### Post by Ziox on 2006-08-01
> **aum11 said:**
> Thanks Ziox but that did not work.  Have You given me the full command for this?

yeah i did give you the full command. It works perfectly for me (the command I mean) :confused: 

maybe you need to reinstall alacarte

sudo aptitude reinstall alacarte

---

### Post by aum11 on 2006-08-01
Have reinstalled and rebooted...still the same propblem.

Just to be clear...all You entered into the command line was alacarte?

---

### Post by ardchoille on 2006-08-01
Open a term and run: /usr/bin/alacarte

Running an app from the terminal can sometimes show error output. Try running the above command and see if there is any error output.

---

### Post by Tomosaur on 2006-08-01
Are you sure you have sufficient permissions to run alacarte? If your account was set up by somebody else they may have disabled Alacarte but forgotten to remove it from your menu.

---

### Post by ardchoille on 2006-08-01
> **Tomosaur said:**
> Are you sure you have sufficient permissions to run alacarte? If your account was set up by somebody else they may have disabled Alacarte but forgotten to remove it from your menu.

Open a term and do this: ls -lha /usr/bin/alacarte

and post the output

---

### Post by aum11 on 2006-08-01
Sorry for the delay but got caught up in other issues.


@ubuntu:~$ ls -lha /usr/bin/alacarte
-rwxr-xr-x 1 root root 997 2006-05-13 11:17 /usr/bin/alacarte

---

### Post by Rondonjin on 2006-08-02
> **aum11 said:**
> Sorry for the delay but got caught up in other issues.


@ubuntu:~$ ls -lha /usr/bin/alacarte
-rwxr-xr-x 1 root root 997 2006-05-13 11:17 /usr/bin/alacarte

The best fix for Alacarte is calle Smeg. First you uninstall Alacarte then
install this file:

[http://dev.realistanew.com/smeg/latest/smeg.deb](http://dev.realistanew.com/smeg/latest/smeg.deb)

Future updates may want to replace Smeg with Alacarte again.

Wayne

---

### Post by ardchoille on 2006-08-02
Alacarte **is** smeg. It was called smeg and they changed the name to alacarte. If you uninstall alacarte and install that .deb, you may have problems later because you won't get updates to alacarte, and it's not a good idea to use debian .deb packages in Ubuntu anyway.

Open a term and do this: gksudo gedit /usr/share/applications/alacarte.desktop

Make sure the entries are ok, pay particular attention to the line in red below. Here is the default menu entry for alacarte in Ubuntu 6.06:

[Desktop Entry]
Encoding=UTF-8
Name=Alacarte Menu Editor
Name[de]=Alacarte Menü Editor
Name[es]=Editor de Menús Alacarte
Name[fr]=Editeur de Menu Alacarte
Name[nb]=Alacarte menybehandler
Name[nl]=Alacarte menu Editor
Name[no]=Alacarte menybehandler
Comment=Add, change, remove menu entries
[COLOR="Red"]Exec=alacarte[/COLOR]
Icon=gnome-main-menu
NotShowIn=KDE;
Terminal=false
StartupNotify=true
Type=Application
Categories=Application;Utility;
X-Ubuntu-Gettext-Domain=alacarte


If it's not correct, change the needed items and save the file. Then try right-clicking on the Applications menu, choose Edit Menus and see if alacarte launches successfully.

---

### Post by aum11 on 2006-08-08
The settings were exactly the same as above.

Where to from here?

---

### Post by aum11 on 2006-08-12
After many tries to fix alacarte 0.8, eventually I installed 0.9 from [http://members.shaw.ca/anduu/ubuntufiles/alacarte_0.9-0ubuntu1~amaranth_all.deb](http://members.shaw.ca/anduu/ubuntufiles/alacarte_0.9-0ubuntu1~amaranth_all.deb)
.  This solved all my problems.  Hope it helps You.

---

### Post by sblanzio on 2006-08-21
I had the same problem. Launching alacarte in console gave me this error:

```

UnicodeDecodeError: 'utf8' codec can't decode bytes in position 26-28: invalid data

```

I installed the file you indicated in the previous post and I solved the problem.

I write this reply for anybody else's convenience.

THank you!!!
bye
sblanzio

---

### Post by russelld on 2006-08-25
thanks for that, fixed my alacarte

---

### Post by cainmark on 2006-09-01
Thanks.  First time I had to look for a solution since I've been using Ubuntu since last month.  This was the anwer I was looking for.

---

