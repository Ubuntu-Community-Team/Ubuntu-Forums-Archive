---
title: "Fedora 10 tips and tricks"
date: 2008-11-29
forum: Fedora/RedHat and derivatives
---

### Post by pelle.k on 2008-11-29
I thought i'd put this together for som of you hard core ubuntu heads out there. It took me quite some time to be comfortable with fedora, but with some work i've got it setup much like i run my ubuntu.
These tips deal with some common problems, going from ubuntu to fedora.
[B]
[COLOR="Red"]1.[/COLOR][/B] Disable automounting of local drives at login (gnome). This is prevented by means of HAL in ubuntu. Just put this in **/etc/hal/fdi/policy/preferences.fdi**
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
<!-- 
  The following shows how to hint gnome-volume-manager and other programs 
  that honor the storage.automount_enabled_hint to not mount non-removable
  media.
-->

  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
  </device>

</deviceinfo>
```
[B]
[COLOR="Red"]2.[/COLOR][/B] SHMconfig without touching xorg.conf (synaptics touchpads). This is also done with HAL in ubuntu. Put this in **/etc/hal/fdi/policy/shmconfig.fdi**
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>
  </match>
 </device>
</deviceinfo>
```
You've got options to turn touchpad on/off by installing gsynaptics
```
yum install gsynaptics
```

**[COLOR="Red"]3.[/COLOR]** apt-get/aptitude is as good as it gets, no doubt about that. yum is, however, a very nice package manager as well. Lets add some speed, and auto-removal of "leaves" (i.e. unused dependencies that got pulled when you installed a piece of software)
```
yum install yum-fastestmirror yum-remove-with-leaves
```
These two are plugins, meaning you can temporarily disable them, and they work by default without you doin anything.

**[COLOR="Red"]4.[/COLOR]** tab auto-complete commands in the terminal. very easy.
```
yum install bash-completion
```
restart (terminal).
[B]
[COLOR="Red"]5.[/COLOR][/B] fedoras eqvivalent to medibuntu is rpmfusion, allthough it contains more than just media extras. It adds quite a bit of other software as well. Antman already covered that here :)
[http://ubuntuforums.org/showthread.php?t=989530](http://ubuntuforums.org/showthread.php?t=989530)

**[COLOR="Red"]6.[/COLOR]** For exmaple, to install nvidia driver (**rpmfusion**!)
```
yum install akmod-nvidia
```
Then run the livna display configuration in system>administration meny. Then reboot.

**[COLOR="Red"]7.[/COLOR]** To play basic media files (.mp3/.xvid etc) (**rpmfusion** not needed, but recommended!)
```
yum install gstreamer-plugins-ugly gstreamer-ffmpeg
```

**[COLOR="Red"]8.[/COLOR]** dvd playback
```
yum install libdvdread libdvdnav
```
and get libdvdcss here [http://atrpms.net/dist/f10/libdvdcss/](http://atrpms.net/dist/f10/libdvdcss/)
you need both libdvdcss and libdvdcss2

[COLOR="Red"]**9.**[/COLOR] A few common extras
**flash** [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
**skype** (the fedora 7 one) [http://www.skype.com/intl/sv/download/skype/linux/choose/](http://www.skype.com/intl/sv/download/skype/linux/choose/)

[COLOR="Red"]**10.**[/COLOR] If you want a "human" theme, install this
[http://www.gnome-look.org/content/show.php/Clearlooks-Colors?content=75417](http://www.gnome-look.org/content/show.php/Clearlooks-Colors?content=75417)
Should you miss the human-icon-theme, download it here
[http://packages.ubuntu.com/intrepid/all/human-icon-theme/download](http://packages.ubuntu.com/intrepid/all/human-icon-theme/download)
extract the .deb (it's an archive), then extract the "data" dir.
It's in **usr/share/icons**, so just right click and create a tar.gz of the "Human" dir, and you've got your human icon theme, ready to drop in System>prefernces>look and feeel>appearance.
I'm more of a tango guy, so i recommend
```
yum install tango-icon-theme tango-icon-theme-extras
```
of course ;)

[COLOR="Red"]**11.**[/COLOR] EDIT: Almost forgot! Sudo :)
```
su
cp /etc/sudoers /etc/sudoers.backup
echo "%wheel        ALL=(ALL)       ALL" >> /etc/sudoers
usermod -aG wheel USERNAME
```
Obvisouly, replace USERNAME with the user that should join the wheel group, and thereby gain sudo rights for ALL commands. I'm not recommending this (you should always be careful with these things), but this is how it is done in ubuntu.

Good luck!

---

### Post by SamSlater on 2008-12-01
Thanks for that info. I'm a noob to Fedora 10 and was having trouble with a few things.

Do you know the gpg key for the libdvdcss rpms? Can't install without the key, either from root or clicking the .rpms.

Thanks.

---

### Post by igknighted on 2008-12-01
> **SamSlater said:**
> Thanks for that info. I'm a noob to Fedora 10 and was having trouble with a few things.

Do you know the gpg key for the libdvdcss rpms? Can't install without the key, either from root or clicking the .rpms.

Thanks.

'yum localinstall --nogpgcheck package.rpm'

or

'rpm -ivh package.rpm'

The first method is preferable.

---

### Post by zman0900 on 2008-12-17
> **pelle.k said:**
> [COLOR="Red"]**11.**[/COLOR] EDIT: Almost forgot! Sudo :)
```
su
cp /etc/sudoers /etc/sudoers.backup
echo "%wheel        ALL=(ALL)       ALL" >> /etc/sudoers
usermod -aG wheel USERNAME
```


The sudoers file should always be edited using the command "visudo".  I'm not even sure that it will work if you edit it any other way.  If you don't like vi, use "env EDITOR=nano visudo".  Replace nano with whatever you want.

---

### Post by uncholowapo on 2008-12-17
> **zman0900 said:**
> The sudoers file should always be edited using the command "visudo".  I'm not even sure that it will work if you edit it any other way.  If you don't like vi, use "env EDITOR=nano visudo".  Replace nano with whatever you want.

From my experience it does work. But I also do recommend visudo as it is the safest way to edit the file.

---

### Post by pelle.k on 2008-12-18
> From my experience it does work. But I also do recommend visudo as it is the safest way to edit the file.
Yes, and yes.
I did make sure the layout of the default /etc/sudoers would allow this "hack" before i put it the "guide". But you are correct, you should normally use the visudo mechanism to edit /etc/sudoers because it's got syntax and error checking.
Unlike ubuntu, you are not locked out if you make a mistake though, since the root account isn't locked by default.

---

### Post by ingvildr on 2008-12-18
> **pelle.k said:**
> **[COLOR="Red"]3.[/COLOR]** apt-get/aptitude is as good as it gets, no doubt about that. yum is, however, a very nice package manager as well. Lets add some speed, and auto-removal of "leaves" (i.e. unused dependencies that got pulled when you installed a piece of software)
```
yum install yum-fastestmirror yum-remove-with-leaves
```


In my experience yum doesn't need the fastestmirror plugin anymore because when i used it, it actually took more time then without it, so milage may vary with that one.

---

