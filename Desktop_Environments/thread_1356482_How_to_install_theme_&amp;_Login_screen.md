---
title: "How to install theme &amp; Login screen"
date: 2009-12-16
forum: Desktop Environments
---

### Post by T_1000 on 2009-12-16
Hi. I've just installed ubuntu 9.10. and this time i have new monitor. dell sx2210. you will see some of my old posts regarding some monitor problems. just ignore them because i've got this new beauty dell sx 2210. 

but with this new stuff, i couldn't install theme as well as login screen. 

with themes- i downloaded some themes from gnome art and when i tries to install them, it say, "not a valid theme package"

with login screen- when I select system->administration-> login screen, it just shows "Login screen settings". I also followed this procedure. 
CTR+ALT+f2 then 
export DISPLAY=:0.0 
sudo -u gdm gnome-control-center
using these commands i opened the gnome control panel
then when i select login screen, it shows same "login  screen setting".

could anyone please help me out with theme and login screen? from where can i select login screen? and why it is saying that the theme package is not valid

---

### Post by T_1000 on 2009-12-17
anyone??

---

### Post by nibirumarduk on 2009-12-17
T_1000 try gksudo -u gdm dbus-launch gnome-appearance-properties.

---

### Post by T_1000 on 2009-12-17
> **nibirumarduk said:**
> T_1000 try gksudo -u gdm dbus-launch gnome-appearance-properties.
hi. It gives error after typing your given command
> gksudo -u gdm dbus-launch gnome-appearance-properties.
Couldn't exec gnome-appearance-properties.: No such file or directoryroot@deepak

---

### Post by wojox on 2009-12-17
```
sudo su
```

Then run the command:

```
gksudo -u gdm dbus-launch gnome-appearance-properties
```

---

### Post by T_1000 on 2009-12-17
> **wojox said:**
> ```
sudo su
```

Then run the command:

```
gksudo -u gdm dbus-launch gnome-appearance-properties
```

tried but not working. it gives some error in terminal 

> root@deepak-desktop:~# sudo su
root@deepak-desktop:~# gksudo -u gdm dbus-launch gnome-appearance-properties

(gnome-appearance-properties:2064): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed


and then opens the appearance panel. but when I try to select any theme, it gives same error that "*anyselectedtheme* does not appear to be valid theme"

---

### Post by T_1000 on 2009-12-17
i have just come to know after reading several topics that Login Screen Preferences are not available in ubuntu 9.10. so sad!! so this has clear my one question but what about theme?
atleast I should be able change the theme. why it is keep saying that " ***** does not appear to be valid theme"
what should i do?

---

### Post by wojox on 2009-12-17
Use these commands again:

CTR+ALT+F2 then
export DISPLAY=:0.0
sudo -u gdm gnome-control-center
CTR+ALT+F7

but don't choose login screen, choose appearance. Then choose a theme and background. I see you were already root before. Try opening a normal terminal and sudo su 

As far as themes I just open Appearance > Theme and drag and drop my theme in. There are some pretty nice themes here:

[http://www.ubuntugeek.com/nice-themes-for-ubuntu-9-10-karmic-users.html](http://www.ubuntugeek.com/nice-themes-for-ubuntu-9-10-karmic-users.html)

---

### Post by T_1000 on 2009-12-18
> **wojox said:**
> Use these commands again:

CTR+ALT+F2 then
export DISPLAY=:0.0
sudo -u gdm gnome-control-center
CTR+ALT+F7

It gives same error, that ***** not a valid theme package
@wojox, 

> 
[http://www.ubuntugeek.com/nice-themes-for-ubuntu-9-10-karmic-users.html](http://www.ubuntugeek.com/nice-themes-for-ubuntu-9-10-karmic-users.html)

after running those command, it installed the given themes and are visible  in myapearance->theme. Theme is applied but the login screen is unchanged. Its not showing new login screen. Its using old login screen.

---

### Post by hariks0 on 2009-12-18
[http://forumubuntusoftware.info/viewtopic.php?f=65&t=4124](http://forumubuntusoftware.info/viewtopic.php?f=65&t=4124) has the right answer for you.

---

### Post by T_1000 on 2009-12-19
> **hariks0 said:**
> [http://forumubuntusoftware.info/viewtopic.php?f=65&t=4124](http://forumubuntusoftware.info/viewtopic.php?f=65&t=4124) has the right answer for you.

Ohh,thanks you very very much. Its working. It has changed the login screen and I can choose any login screen from Login window.
thank you hariks0
btw, since I have change login screen, I couldn't see Switch User Option on my desktop. how to get it manually?

---

### Post by hariks0 on 2009-12-19
> **T_1000 said:**
> Ohh,thanks you very very much. Its working. It has changed the login screen and I can choose any login screen from Login window.
thank you hariks0
btw, since I have change login screen, I couldn't see Switch User Option on my desktop. how to get it manually?

You are welcome. If you mean that the applet has disappeared from the panel, you can get it back by right clicking the panel and Selcting Add to panel. From the dialog box you can get the indicator applet session [Not indicator applet]

---

### Post by T_1000 on 2009-12-21
> **hariks0 said:**
> You are welcome. If you mean that the applet has disappeared from the panel, you can get it back by right clicking the panel and Selcting Add to panel. From the dialog box you can get the indicator applet session [Not indicator applet]

thanks. I can see switch user now.
but , there is one more problem. Since I've installed new gdm , I get an error before login screen appears. error comes in blue background,saying " another x server is running or something", may be another gdm is running. i couldn't get screenshot as it appears befor login screen. what is solution for this?

---

### Post by hariks0 on 2009-12-21
> After further debugging I found out that it's KDE starting up first on display :0 and then GDM starts on display :1
So disable the /etc/init.d/kdm daemon file or Try going to synaptic and remove kdm if kde is installed

This is what I found in this regard. Please try and post back.:popcorn:

---

### Post by T_1000 on 2009-12-21
> **hariks0 said:**
> This is what I found in this regard. Please try and post back.:popcorn:

how to disable it? what is the command?

---

### Post by hariks0 on 2009-12-21
```
sudo gedit /etc/init.d/kdm
```

---

### Post by T_1000 on 2009-12-21
> **hariks0 said:**
> ```
sudo gedit /etc/init.d/kdm
```

it shows a blank file. nothing inside it, no text. also in synaptic manager KDM is not checked.

---

### Post by hariks0 on 2009-12-21
> So disable the /etc/init.d/kdm daemon file or Try going to synaptic and remove kdm if kde is installed 

You obviously do not have kde [and hence kvm] installed. So it may be due to some other entry in the startup script. I will try to figure it out and revert if there is any result.:(

---

### Post by T_1000 on 2009-12-22
> **hariks0 said:**
> You obviously do not have kde [and hence kvm] installed. So it may be due to some other entry in the startup script. I will try to figure it out and revert if there is any result.:(
ok. i will wait for your answer.

---

### Post by hariks0 on 2009-12-23
Found in another forum

```

sudo mv /etc/init/failsafe-x.conf /etc/init/failsafe-x.conf-disable

```

Try this and post back.

---

### Post by hariks0 on 2009-12-23
> **T_1000 said:**
> ok. i will wait for your answer.

Been wresteling with this problem on multiple PCs for a few days now and I finally figured it out!

Looked at /etc/init and noticed both **kdm.conf** and **gdm.conf** are checking if they are the default display manager in **/etc/X11/default-display-manager** expecting different file content
Then I noticed that I don't have that file. 
So I reinstalled new gdm (apt-get install gdm) since that worked fine
Notice I do have the file
Reinstalled gdm-2.20 (apt-get install gdm-2.20) and created my own file
```
sudo echo "/usr/sbin/gdm" > /etc/X11/default-display-manager
```
Problem Solved!
Make sure your gdm is in /usr/bin with
```
which gdm
```


Side Notes:
Installing gdm while having gdm-2.20 will automatically remove gdm, no need to do it manually.
Same goes vice versus, installing gdm ontop of gdm-2.20 will remove older one 1st.

You can do all this from console with apt-get or from Gnome Synaptic application.

Enjoy!
:guitar::popcorn::):lolflag: Please mark as solved.

---

### Post by mechaxl on 2009-12-23
Thanks for the info. This: [http://ubuntuforums.org/showpost.php?p=8546528&postcount=20](http://ubuntuforums.org/showpost.php?p=8546528&postcount=20) fixed my problem that I was having with this as well.

---

### Post by T_1000 on 2009-12-24
> **hariks0 said:**
> Found in another forum

```

sudo mv /etc/init/failsafe-x.conf /etc/init/failsafe-x.conf-disable

```

Try this and post back.

ok, I will try tomorrow morning.. right now doing some imp work on windows.. 
There is one problem which I have not discussed yet. Since I have installed this latest version 9.10, Its running very slow. Its like its using the all the memory. very slow.I have installed earlier versions of linux but they were really fast. Is it happening due to same x server problem?

---

### Post by T_1000 on 2009-12-25
I think problem is sorted out now. Thanks.

still some issues are there. linux is running slow and also after updating linux from Update Manager, it is showing 2 entries for linux in bootloader.

---

### Post by arjunkn on 2010-01-10
it doesn't work showing an error while entering this command,"unable to connect to the running instances" this is the error... i cann't open gnome-control-center

---

### Post by eval- on 2010-01-21
I had to not just edit out the X11R6, and create /etc/X11/default-display-manager, but it was critical that I go into /etc/init/gdm.conf and change the last line from 'gdm-binary' to /usr/sbin/gdm

Otherwise I'd end up in the failsafe which would load a vesa driver that blanks all my consoles, joy.  What a waste of a day.

---

### Post by growlf on 2010-01-22
For those not able or willing to switch the GDM back to the older version, there is now another answer.  Check this topic out: [http://ubuntuforums.org/showpost.php?p=8707543&postcount=55](http://ubuntuforums.org/showpost.php?p=8707543&postcount=55)  The tool adds in much of the old functionality and we will be adding more as quickly as we are able.

---

### Post by freddyflo on 2010-01-23
to install the login screen
go to system > administration >  login window then click on the local tab on the dialogue box 
then click the add button to add your new login screen themes.

---

### Post by growlf on 2010-01-27
> **freddyflo said:**
> to install the login screen
go to system > administration >  login window then click on the local tab on the dialogue box 
then click the add button to add your new login screen themes.

@freddyflo - The problem is that in Karmic (the current release version of Ubuntu) that option is no longer there.

---

