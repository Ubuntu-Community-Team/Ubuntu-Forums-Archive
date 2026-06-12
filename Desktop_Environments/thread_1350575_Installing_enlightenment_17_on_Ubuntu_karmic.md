---
title: "Installing enlightenment 17 on Ubuntu karmic"
date: 2009-12-09
forum: Desktop Environments
---

### Post by mack75 on 2009-12-09
Hi everybody:

Today I found the enlightenment 17 repository and I've installed it on my Ubuntu 9.10. Here's the mini howto to do it:

**Note:** as today does not exists a karmic 9.10 repository now, we will use the 9.04 repository.

[LIST=1]
[*]Enable the e17 repository: sudo echo "deb [http://packages.enlightenment.org/ubuntu](http://packages.enlightenment.org/ubuntu) jaunty main extras" >> /etc/apt/sources.list.d/enlightenment.list
[*]cd /tmp
[*]Download the repository key from: wget [http://packages.enlightenment.org/repo.key](http://packages.enlightenment.org/repo.key)
[*]Now, register the key: sudo apt-key add repo.key
[*]Update the apt: sudo apt-get update
[*]Download aditional package [libmpd0]("http://packages.ubuntu.com/jaunty/i386/libmpd0/download")
[*]Install libmpd0: sudo dpkg -i libmpd0_0.17.0-1_i386.deb
[*]And install the packages needed: 
sudo apt-get install e17 e17-data libefreet-svn-03 emodule-alarm emodule-bling emodule-calendar emodule-cpu emodule-deskshow emodule-diskio emodule-edgar emodule-efm-nav emodule-efm-path emodule-efm-pathbar emodule-emu emodule-execwatch emodule-extramenu emodule-flame emodule-forecasts emodule-iiirk emodule-language emodule-mail emodule-mem emodule-notification emodule-penguins emodule-places emodule-rain emodule-screenshot emodule-slideshow emodule-snow emodule-taskbar emodule-tiling emodule-trash emodule-uptime emodule-weather emodule-winselector emprint gxine xine-ui libxine1-ffmpeg thunar-archive-plugin thunar-media-tags-plugin emodule-mpdule emodule-net emodule-wlan gxineplugin
[*]Logout and login with the e17 now!
[/LIST]

**[COLOR="Blue"]NOTE2:[/COLOR]** Into the repository exists a dummy package called emodules-all, I've don't used it  because it include the emodule-exalt package that replace the network-manager network-manager-gnome packages and I don't want to do that and maybe you neither want, otherwise use: sudo apt-get install e17 e17-data libefreet-svn-03 emodules-all gxine xine-ui libxine1-ffmpeg thunar-archive-plugin thunar-media-tags-plugin gxineplugin

If you want the composite enabled then install:
sudo apt-get install libxcb-composite0 libxcomposite1 xcompmgr libgtkextra-x11-2.0-1 emodule-bling transset

And run from a terminal: xcompmgr -fF

If you wish integrate the gnome settings then run: gnome-settings-daemon

To execute this applications from the startup you need:
[LIST=1]
[*] Create a shell script with: "vi ~/startup-e17.sh" with the content:
#!/bin/bash
mplayer /usr/share/sounds/ubuntu/stereo/desktop-login.ogg &
xcompmgr -fF &
gnome-settings-daemon &
[*] Set the rights permissions: chmod 750 ~/startup-e17.sh
[*] now, create the .desktop file: "vi .local/share/applications/startup-e17.desktop" with the content:
[Desktop Entry]
Hidden=false
Exec=/bin/sh /home/[COLOR="Blue"][username][/COLOR]/startup-e17.sh
Name[es_AR]=startup-e17
Type=Application
NoDisplay=true
Version=1,
StartupNotify=false
Terminal=false
Name=startup-e17
**NOTE3:** replace the [COLOR="Blue"][username][/COLOR] with your user login name.
[*] finally, create the .order file: "vi ~/.e/e/applications/startup/.order" with the content:
startup-e17.desktop
[/LIST]

Enjoy! :popcorn:

---

### Post by joplass on 2009-12-09
Thank you for taking the time to write this fine "How To".  
Everything working good for me.

---

### Post by Leppie on 2009-12-10
Maybe a noob question, but when doing "sudo apt-get install e17" dependencies are not automatically installed? Or is this because the Jaunty repo is being used?

---

### Post by mack75 on 2009-12-10
Hi:

If you say this for the large package list, maybe you've not read my Note2:

"Into the repository exists a dummy package called emodules-all, I've don't used it because it include the emodule-exalt package that replace the network-manager network-manager-gnome packages..."

If you mean that the install command: sudo apt-get install e17 don't install automatically the reminding modules packages, it's fine, the modules packages depends of the e17 package but the e17 package don't depend of the modules packages.

Regards!

---

### Post by xguru84 on 2009-12-11
I used karmic instead of jaunty in the repo and everything worked fine!

---

### Post by kappa962 on 2009-12-13
Great howto. I've linked to it from my [minimal E17 install howto]("http://ubuntuforums.org/showthread.php?t=1280189"). I think some of the people who were trying to use my howto were really looking for something more like this.

---

### Post by joplass on 2009-12-14
Right cliking on my desktop does not give me a menu.  Is there a reason why?  Anything you guys can tell me?

---

### Post by mack75 on 2009-12-15
Hi joplass:

Probe with the left mouse button

Regards!

---

### Post by mack75 on 2009-12-15
> **kappa962 said:**
> Great howto. I've linked to it from my [minimal E17 install howto]("http://ubuntuforums.org/showthread.php?t=1280189"). I think some of the people who were trying to use my howto were really looking for something more like this.

Hi kappa962:

Thanks for the link.

Regards!

---

### Post by Leppie on 2009-12-17
> **mack75 said:**
> If you mean that the install command: sudo apt-get install e17 don't install automatically the reminding modules packages, it's fine, the modules packages depends of the e17 package but the e17 package don't depend of the modules packages.

wasn't really that interested in the modules part, but the command apt-get install **e17 e17-data** gave me the impression that dependencies may not be resolved properly for e17 installation.

---

### Post by kappa962 on 2009-12-20
> **Leppie said:**
> wasn't really that interested in the modules part, but the command apt-get install **e17 e17-data** gave me the impression that dependencies may not be resolved properly for e17 installation.

All you need to install for E17 to work is the E17 package. I assume the other E17 packages in this how-to are extras. I do not know of any dependency problems with the enlightenment repo.

---

### Post by mhbell on 2009-12-21
Unfortunetly I am running karmic amd 64 version and it won't work for me as the files are for i386 anyone got it working with amd 64 version of karmic?
Mel
:(

---

### Post by sandy8925 on 2009-12-23
@mhbell

You could probably get the source and compile it for your CPU. I have no idea how to do that though.

By the way this isn't working for me at all. I went upto step 7 but am not able to install that huge list of packages - I get messages about broken dependencies.

---

### Post by gonzakloperu on 2009-12-27
I also have a 64bit ubuntu karmic. Is there any option for us?

---

### Post by tomdkat on 2010-01-21
Today, I built a Dec 2 snapshot of E17 from source and it appears to be running ok (I haven't done much with it).

Here is a screenshot:

[[IMG]http://img63.imageshack.us/img63/1359/screenshote1764bit.th.png[/IMG]](http://img63.imageshack.us/i/screenshote1764bit.png/)

I downloaded the source from here:

[http://download.enlightenment.org/snapshots/LATEST/](http://download.enlightenment.org/snapshots/LATEST/)

and built them in the order listed here:

[http://trac.enlightenment.org/e/wiki](http://trac.enlightenment.org/e/wiki)

starting with the core elements.

For those wanting to live on "the edge" a bit, give it a try! :)  The screenshot shows E17 running in an Xnest window on my Ubuntu 9.10 64-bit system.

Peace...

---

### Post by stanca on 2010-01-22
My recent install of E17-Ecomorph in Ubuntu Karmic 9.10 Amd64:

---

### Post by Anubis on 2010-01-26
> **stanca said:**
> My recent install of E17-Ecomorph in Ubuntu Karmic 9.10 Amd64:

Great job! Best looking E17 desktop I've ever seen.

---

### Post by Eduardo André Viana on 2010-02-08
> **mhbell said:**
> Unfortunetly I am running karmic amd 64 version and it won't work for me as the files are for i386 anyone got it working with amd 64 version of karmic?
Mel
:(

I'm an amd 64 user and I didn't have any kind of problem using this howto. Everything worked perfectly and now I have a great E17 + Ubuntu Karmic desktop.

---

### Post by patg7590 on 2010-04-29
Has anyone got Compiz to work with this setup? Or some other way to make it dynamic and generally awesome? (scale/cube/etc.) Im trying to make my Ubuntu Lucid run E17 and be awesome and snazzy like OpenGEU.

EDIT: Just found something called Ecomorph? I think I have it installed already, I just dont know how to use/configure it...

---

### Post by jasonpeel on 2010-05-27
Could someone give me a little help with this.

Run as described but keep getting dependency problems please see output below.

is it just a case of finding the dependenies and installing them?


Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxine1-ffmpeg is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  e17: Depends: libecore-evas-svn-03 (>= 0.9.9.061) but it is not going to be installed
       Depends: libecore-imf-svn-03 (>= 0.9.9.061) but it is not going to be installed
       Depends: libecore-input-svn-03 (>= 0.9.9.061) but it is not going to be installed
       Depends: libecore-x-svn-03 (>= 0.9.9.061) but it is not going to be installed
       Depends: libedbus-svn-03 (>= 0.5.0.061) but it is not going to be installed
       Depends: libedje-svn-03 (>= 0.9.92.061) but it is not going to be installed
       Depends: libeet1 (>= 1.0.0) but it is not going to be installed
       Depends: libevas-svn-03 (>= 0.9.9.061) but it is not going to be installed
       Depends: libevas-svn-03-engine-software-x11
       Depends: libedje-bin but it is not going to be installed

---

