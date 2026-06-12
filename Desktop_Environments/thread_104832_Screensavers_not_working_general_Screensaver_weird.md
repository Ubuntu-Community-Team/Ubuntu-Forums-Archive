---
title: "Screensavers not working/ general Screensaver weirdness"
date: 2005-12-17
forum: Desktop Environments
---

### Post by nrwilk on 2005-12-17
First Problem:
I've had a small problem with my screensavers for a while now, which is that the "test" button under the screensavers section of KControl will only work once each time the system boots up.  The first saver I "test" works, but then after that all I get is a blank, black screen when I press the "test" button.  This problem has been present on on my system through multiple installations, but other people seem not to have it.  I find that odd.  Should I download and burn a new installation disk?

Second (newer) Problem:
for the past several days My screensavers do not work at all.  I recently reinstalled my system, and they worked for a bit.  But, I have not made any changes or installed any software which (by my knowledge) would have affected screensavers in any way.  They do not come on automatically when they're supposed to, and when I click the "test" button nothing happens at all, I can still see my desktop.  The thing is, I can tell that it tries to go to screensaver, because in both the cases (using the "test" button and when the screen locks automatically) when I click afterwards, the screen flashes once as if the screensaver had been there, and the click is not registered on the desktop.  Is there some screensaver conf file that could be corrupted?  What could be causing this?

I've tried reinstalling all the screensaver packages, and KControl (as a last guess) but it hasn't cleared up any of the problems.

Can anyone please help me figure out what is causing my problems?

---

### Post by nrwilk on 2005-12-17
Also, I forgot to mention that none of the screensavers play a preview in the tiny preview window when they are highlighted.

---

### Post by nrwilk on 2006-01-10
Does anyone have an idea about this?

I'm still having these problems.

---

### Post by bulldogzerofive on 2006-01-11
For what this is worth, i would be willing to bet it has to do with your video card.

---

### Post by Thirsteh on 2006-01-11
I just noticed this yesterday as well. Was able to view the first screensaver without problems, then couldn't view any others until after about 30 seconds, then I could. It's all a matter of time before whatever process is hindering view of other screensavers shuts down, it seems.

---

### Post by patrick295767 on 2006-01-11
Me, it's energy saving of monitor not working...  in my login manager 
  
I dont know what to install.
I installed ubuntu from server:
```
#!/bin/bash
echo "I hope u didnt forget to start enter the name of the main user"
echo " If right, press space otherwise, quit with ctrl Z or ctrl c"
echo "wait functino ?"
echo " Processing ..."
##mkdir "/home/$1/.fvwm"
cp "/etc/apt/sources.list" "/etc/apt/sources.list-backup"
cp "/root/sources.list" /etc/apt/sources.list
##cp "/root/.fvwm2rc" "/home/$1/.fvwm/.fvwm2rc"
apt-get update
apt-get -y upgrade
apt-get -f -y install x-window-system-core
apt-get -f -y install xdm 
apt-get -f -y install openssh-server
apt-get -f -y install samba
apt-get -f -y install smbclient xloadimage

apt-get -f -y install dhcp3-server
apt-get -f -y install proftpd
echo " You can go now for a cup of coffee !"
echo " Enjoy & see you later !"
apt-get -f -y install numlockx
apt-get -f -y install xterm
apt-get -f -y install mc
apt-get -f -y install gnome-chess
apt-get -f -y install abiword gnome-gv
apt-get -f -y install xmms xlock
apt-get -f -y install fvwm
apt-get -f -y install xpdf 
apt-get -f -y install xpdf-reader
apt-get -f -y install rar
apt-get -f -y install tar
apt-get -f -y install zip

apt-get -f -y install 


apt-get -f -y install mozilla-firefox dillo
apt-get -f -y install sylpheed lynx gedit
apt-get -f -y install gnumeric
apt-get -f -y install gparted
apt-get -f -y install qtparted
apt-get -f -y install k3b mplayer-386
apt-get -f -y install cdrdao
apt-get -f -y install kadu gftp xpdf
apt-get -f -y install sylpheed
apt-get -f -y install idesk 
apt-get -f -y install gimp
apt-get -f -y install gnome-panel
apt-get -f -y install xloadimage
apt-get -f -y install nfs
apt-get -f -y install xfce
apt-get -f -y install samba
apt-get -f -y install amule alien
apt-get -f -y install rcconf kde
apt-get -f -y install xzgv
apt-get -f -y install nfs nfs-common
apt-get -f -y install 
apt-get -f -y install 

echo " the startup of Linux $(uname -r) "
echo "#!/bin/bash" > "/etc/init.d/patrickrcs70.sh"
echo "chmod 666 /dev/dsp" >> "/etc/init.d/patrickrcs70.sh"
chmod +x /etc/init.d/patrickrcs70.sh

cd /etc/init.d/
ln -s patrickrcs70.sh /etc/rc2.d/S70patrickrcs70.sh
echo "*** LINUX$(uname -r) startup file to be modified !"

cd ~
apt-get -f -y install rox-filer
apt-get -f -y install sun-j2re1.5
apt-get -f -y --force-yes sun-j2re1.5

echo "***"
echo "*** please go and get opera, skype and gaim, install them rox-filer***"
echo "** crossover is nice prg for windows apps**"
echo "fvwm" > "/home/$1/.Xsession"
echo "/home/$1/.Xsession"
echo "set up the fvwm as default"
apt-get -f -y install 
echo "Please choose gdm "
apt-get -f -y install 
apt-get -f -y install gdm 
apt-get -f -y install x-window-system-core
apt-get -f -y install xserver-xorg

apt-get -f -y install 
dpkg-reconfigure xserver-xorg
apt-get -f -y install 
apt-get clean
/etc/init.d/gdm restart
echo "*** dont forget to enable the XDMCP as true ":
echo "please do: gedit /etc/X11/gdm/gdm.conf &"
echo "gdmsetup should be done too !"
echo "Installation Done !!"

 
```

Thanks !

---

### Post by patrick295767 on 2006-01-11
[QUOTE=Fealos]First Problem:
I've had a small problem with my screensavers for a while now, which is that the "test" button under the screensavers section of KControl will only work once each time the system boots up.  The first saver I "test" works, but then after that all I get is a blank, black screen when I press the "test" button.  This problem has been present on on my system through multiple installations, but other people seem not to have it.  I find that odd.  Should I download and burn a new installation disk?

Second (newer) Problem:
for the past several days My screensavers do not work at all.  I recently reinstalled my system, and they worked for a bit.  But, I have not made any changes or installed any software which (by my knowledge) would have affected screensavers in any way.  They do not come on automatically when they're supposed to, and when I click the "test" button nothing happens at all, I can still see my desktop.  The thing is, I can tell that it tries to go to screensaver, because in both the cases (using the "test" button and when the screen locks automatically) when I click afterwards, the screen flashes once as if the screensaver had been there, and the click is not registered on the desktop.  Is there some screensaver conf file that could be corrupted?  What could be causing this?

I've tried reinstalling all the screensaver packages, and KControl (as a last guess) but it hasn't cleared up any of the problems.

Can anyone please help me figure out what is causing my problems?[/QUOTE]
  
I installed ubuntu pieces after pieces, and after my experience, the screensavers under ubuntu kde and gnome are not sthg very easy. It's kind of tricky. I mean when u installed my way, even after 
apt-get -f install kde (final step)
the screensaver / energy stuff are not working. 
I experienced that the installation of : 
apt-get -f -y install kdm 
makes ur screensaver / energy stuff working. 
  
It was then working, I installed apt-get -f -y gdm
and removed kdm, then screensaver / energy stuff not working, anymore.
  
This is also odd. 
  
Concerning the screensaver, u may use kicker bar; 
and drag and drop the icon from xlockmore 
this would / will work each time u click on it to start the screensaver when u leave ur pc. (gnome-panel too)... 
EVEN with XDMCP !!
  
Concenring the auto-screensaver, don't know very much, still some progress to make ;...
  
So maybe config file or maybe sthg missing in installation... 
  
Let's make progress together about it !

Greetings from belgium, 

Pat'

---

### Post by patrick295767 on 2006-01-11
Additionally to Linux, greetings to Colorado, I love this region of US !!
 Golden is very beautiful !!

Pat'

---

### Post by nrwilk on 2006-01-11
[QUOTE=Thirsteh]I just noticed this yesterday as well. Was able to view the first screensaver without problems, then couldn't view any others until after about 30 seconds, then I could. It's all a matter of time before whatever process is hindering view of other screensavers shuts down, it seems.[/QUOTE]

I'm not sure this is the same problem.  I can't "test" two in a row without first logging out and then back in to another KDM session.  I've tried waiting about 10 minutes now without touching the computer, and a second screensaver still will not play.

I've been out of town for two weeks, and I realized now that, for some reason, the previews work again, and so do the screensavers themselves automatically start, but this two-in-a-row problem still persists.

---

### Post by patrick295767 on 2006-01-11
[QUOTE=Fealos]I'm not sure this is the same problem.  I can't "test" two in a row without first logging out and then back in to another KDM session.  I've tried waiting about 10 minutes now without touching the computer, and a second screensaver still will not play.

I've been out of town for two weeks, and I realized now that, for some reason, the previews work again, and so do the screensavers themselves automatically start, but this two-in-a-row problem still persists.[/QUOTE]
  
Hi !!
  
I think we need help on that subject... 
Tricky screensaver stuffs

I go to bed (be), maybe tomorrow I'll find it.
  
Greetz'
 
Pat'

---

### Post by TransitMan on 2006-01-11
Along the same vien, I have a favorite screensaver I like - Matrix.
It works fine in GDM, but under KDM I must restart after either a session reboot or hard reboot/dual boot.
Under KDE screensaver, Matris shows, but will not run, test or preview.
If I use the Gnome screensavers under KDE, Matrix will test, preview, setup and run. But here again, it is only after restarting the app in KDE.

I'd like to see a little bit more of a solution to this issue as well, please.

---

### Post by patrick295767 on 2006-01-12
[QUOTE=TransitMan]Along the same vien, I have a favorite screensaver I like - Matrix.
It works fine in GDM, but under KDM I must restart after either a session reboot or hard reboot/dual boot.
Under KDE screensaver, Matris shows, but will not run, test or preview.
If I use the Gnome screensavers under KDE, Matrix will test, preview, setup and run. But here again, it is only after restarting the app in KDE.

I'd like to see a little bit more of a solution to this issue as well, please.[/QUOTE]
  
Thank you of your support TransitMan !!

---

### Post by Psimon on 2006-01-12
I gave up on KDE screensavers and installed Xscreensaver. Run the command xscreensaver-demo and click on the help button, and there are instructions on how to run it under KDE. It works much better and is much more configurable than the KDE Kcontrol screensaver.

---

### Post by patrick295767 on 2006-01-12
[QUOTE=Psimon]I gave up on KDE screensavers and installed Xscreensaver. Run the command xscreensaver-demo and click on the help button, and there are instructions on how to run it under KDE. It works much better and is much more configurable than the KDE Kcontrol screensaver.[/QUOTE]
  
And would you know about the login manager (gdm), how to make the energy saving (energy star) working ? (to turn off the monitor after some time)

 Thank you v. Much !
  
Pat'

---

### Post by nrwilk on 2006-01-12
[QUOTE=Psimon]I gave up on KDE screensavers and installed Xscreensaver. Run the command xscreensaver-demo and click on the help button, and there are instructions on how to run it under KDE. It works much better and is much more configurable than the KDE Kcontrol screensaver.[/QUOTE]

I've tried xscreensaver multiple times, and I can't stand how it doesn't divide the screensavers into catagories.  I also like to use the advanced features in KDE's native screensaver program to designate a hotcorner to lock the screen.

Plus, I'd prefer all my system preferences to be consolidated in kcontrol rather than having to delegate tasks between seperate programs, and having to remember which programs I'm using to do each task.  Also, why can't we get it to work, rather than abandoning it?  Shouldn't we get this issue heard by the people who can fix it instead of accepting the problem and inconveniencing ourselves?

---

### Post by alvonsius on 2006-01-12
I have some weirdness with my screensaver, particulary the default KDE OpenGL ones. It only shows half of my screen, and the other half is black. But when I'm using GL screensaver from Xscreensaver package or other screensaver (noon-GL) from default KDE package the problem doesn't exist. Is there any hint about this? I'm using i915GM for the graphic card. Thanks

---

### Post by nrwilk on 2006-01-12
It'd probably be helpful, I guess, if I was also to post info about my graphics card.

hehe

Nvidia 6600 TD 256MB

---

### Post by patrick295767 on 2006-01-13
For the gdm, I have found 2 internet links:
[http://www.linux.com/howtos/XFree-Local-multi-user-HOWTO/examples_dm.shtml](http://www.linux.com/howtos/XFree-Local-multi-user-HOWTO/examples_dm.shtml)
[http://www.nobell.org/~gjm/linux/x.html](http://www.nobell.org/~gjm/linux/x.html)
   
> Display Power Management System (DPMS)
If you have a monitor with DPMS, enable it by editing XF86Config-4 as below, and then restart the X server:

/etc/X11/XF86Config-4
Section "Monitor"
        ...
        Option "DPMS"
        ...
EndSection

K>Control Center>
    [+]Look & Feel>Screensaver
        x    Enable screensaver
            Screen Saver
                Random
             Settings
                Wait for 10 min (select time to screen saver startup)
    [+]Power Control>Energy>
        x    Enable Display Energy Saving
        Suspend after: 20 min (select time to screen blank)
        Power Off after: 30 min (select time to power saving mode)

For XDM (login screen):

/etc/X11/xdm/Xsetup_0
xset +dpms
xset dpms 0 0 300 # turns the display off after 300 seconds (5 minutes) 
  I dont think it'll work with Xorg... still dont know
No time to try yet....
  
Greetings !!
  
Pat'

---

### Post by Psimon on 2006-01-13
[QUOTE=Fealos]I've tried xscreensaver multiple times, and I can't stand how it doesn't divide the screensavers into catagories.  I also like to use the advanced features in KDE's native screensaver program to designate a hotcorner to lock the screen.

Plus, I'd prefer all my system preferences to be consolidated in kcontrol rather than having to delegate tasks between seperate programs, and having to remember which programs I'm using to do each task.  Also, why can't we get it to work, rather than abandoning it?  Shouldn't we get this issue heard by the people who can fix it instead of accepting the problem and inconveniencing ourselves?[/QUOTE]

I totally agree with you that it would be ideal to be able to run everything from within kcontrol, but having spent a lot of time failing to achieve that with the screensavers, I think xscreensaver is the best option. I quote from the xscreensaver FAQ :

The GNOME people used to have the same class of bugs as the KDE folks now have, but the GNOME crew finally came to their senses, and we worked together to come up with a solution that resulted in their being one and only one xscreensaver configurator, instead of two: mine and theirs. 
 Will the KDE people wise up and do the same? Only time will tell. I encourage you to encourage them.

---

### Post by TransitMan on 2006-01-13
I did some further digging and exploring in the synaptic menu.
What I did was install all available screen-savers, especially those that were not checked as install.
After doing this, logged out/logged in and went to the desktop controls for screensavers, and not only was the Matrixview (GL) there, so was The Matrix under <I>Banners and Pictures</i>.
The latter is the one I had used under Gnome, and it now works flawlessly under KDS.

I hope this little experiment helps others here.

---

### Post by mycroft on 2006-01-17
Well, for what it's worth, I experienced this screensaver weirdness constantly while running SUSE 10. I searched a number of forums, and the closest I got to an answer was that the KDE screensaver wrapper application is simply not very good at its job. The recommendation was to disable it (kscreensaver-xsavers), and to only use the xscreensaver...

I have an i915 too, by the way.

---

### Post by nrwilk on 2006-01-20
ok, so I've resorted to using xscreensaver.  :???: 

But, I have to start it's daemon every time I startup the machine.  Is there a way to get the daemon to start at login?

---

### Post by vayu on 2006-01-26
[QUOTE=Fealos]ok, so I've resorted to using xscreensaver.  :???: 

But, I have to start it's daemon every time I startup the machine.  Is there a way to get the daemon to start at login?[/QUOTE]

Put a link to it in your ~/.kde/Autostart directory.

---

### Post by JAwuku on 2006-02-09
I use a kcontrol module called Autostart, which starts programs up when you login to KDE.

The source code is found at [http://autostart.pwsp.net/]("http://autostart.pwsp.net/")

Just download it to your disk, then unzip it with ```
tar xvjf autostart-0.2.tar.bz2
cd autostart-0.2
./configure
make
make install
```

Make sure you have the Kde dev libraries installed, i.e. kde-devel

If you just want the binary, I've compiled a deb file of it below:

[http://www.drivehq.com/file/df.aspx/publish/jasonawuku/PublicFolder/autostart_0.2-1_i386.deb]("http://www.drivehq.com/file/df.aspx/publish/jasonawuku/PublicFolder/autostart_0.2-1_i386.deb")

---

