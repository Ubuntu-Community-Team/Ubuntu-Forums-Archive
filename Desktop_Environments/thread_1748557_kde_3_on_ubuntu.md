---
title: "kde 3 on ubuntu"
date: 2011-05-03
forum: Desktop Environments
---

### Post by Raevyn on 2011-05-03
Hi

Okay THIS is why Linux annoys me.. installing things can end up being a real PITA.

I just installed KDE 3, but it wont show up in the GDM list. I dont even know where the executable for KDE is.. a search online shows it could be in a few places.. and I tried adding an entry into GDM but that apparently didnt work. Does anyone have any ideas? Or should I destroy the installation and try again?

---

### Post by Raevyn on 2011-05-22
I still cant seem to get KDE working :(

---

### Post by novafluxx on 2011-05-22
When you said you installed KDE 3, what exactly did you do?

---

### Post by SeijiSensei on 2011-05-22
And why are you installing KDE3 which isn't supported any more?

---

### Post by Raevyn on 2011-05-23
Well it was called Trinity, which is KDE3. They are here:

[http://www.trinitydesktop.org/wiki/bin/view/Main/WebHome](http://www.trinitydesktop.org/wiki/bin/view/Main/WebHome)

I downloaded it and installed using the apt-get system.. the instructions they gave on their site. My problem is, I cant seem to update GDM. I have read I need to go to usr/share/xsesions and make an entry for KDE and then GDM is updated but, I cant seem to get it updated. 

I created a desktop file with the following entry

[Desktop Entry]
Name=KDE 3.5
Comment=This session logs you into KDE
Encoding=UTF-8
Type=XSession
Exec=/usr/bin/startkde
TryExec=/usr/bin/startkde
Icon=
Type=Application

but gdm wont see it even after a restart. I did notice the other files that gdm does see seem to be executable and mine is not, but I have no idea how to make it executable

---

### Post by Raevyn on 2011-05-23
Okay.. I just figured out that, startkde is not anywhere to be found. Thats probably why it doesnt work :(

I am going to reinstall ubuntu and try the apt get package again. maybe something happened during installation. But does my desktop file look right?

---

### Post by debd on 2011-05-23
this might help:
> The best way to execute xsession is to include it in your ~/.xinitrc (or
  ~/.xsession) file, as the last client.  The xinit(1) manual page says that
  "the last long-lived program started [...] should be left in the foreground
  so that the script won't exit".  You will find a similar statement in the
  xdm(1) manual page.  This last program should be xsession.  As a matter of
  fact, this may even be the only program executed in your startup file,
  because xsession itself provides a way to launch other applications.  When
  started, xsession will look in your home directory and execute a file named
  .X11Startup, if found.  This shell script is used to start your client
  programs.

here's the site : [http://ftp.x.org/contrib/applications/xsession-1.1.README](http://ftp.x.org/contrib/applications/xsession-1.1.README)

---

### Post by Raevyn on 2011-05-29
Im sorry I meant to get back to this earlier..

I did finally get KDE3 installed via Trinity! Thank you! I ended up NOT switching from GDM and I had to install Trinity from the root account itself.. NOT using sudo, and everything worked fine!

---

### Post by wildmanne39 on 2011-05-29
> **Raevyn said:**
> Im sorry I meant to get back to this earlier..

I did finally get KDE3 installed via Trinity! Thank you! I ended up NOT switching from GDM and I had to install Trinity from the root account itself.. NOT using sudo, and everything worked fine!
Hi, if you looked in synaptic you could have installed kde4 and it would have done all the work for you then you log out click on user name go to the bottom of the screen and choose kde.

---

