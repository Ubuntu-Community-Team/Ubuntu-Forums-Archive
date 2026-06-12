---
title: "no desktop icons after upgrade from 18.10 to 19.04"
date: 2019-04-22
forum: Desktop Environments
---

### Post by Claus7 on 2019-04-22
Hello,

after upgrading from 18.10 to 19.04 no Desktop icons appear. Neither is possible to do right click on Desktop. This is under ubuntu flashback session. Is it because of any configuration or is it just that something went wrong during the upgrade? 

Entering to ubuntu session and enabling Desktop icons from there did not affect flashback. I'm thinking about a dconf reset, yet before doing so another idea can be welcome.

System comes from ubuntu 18.04 installation. No issue with 18.04 or 18.10.

edit: creating new user did not change things either, so dconf reset might not solve the issue...

Regards!

---

### Post by Claus7 on 2019-04-22
Hello,

in a new installation still desktop icons do not appear. I thought that this was not an issue for ubuntu sessions. It seems that this feature is not available for flashback yet.

Regards!

---

### Post by rbmorse on 2019-04-22
My desktop icons re-appeared after I installed ubuntu-gnome-desktop.  Vanilla-gnome-desktop would probably do the trick, too. 

These are meta-packages, so the real fix is in one of the actual packages they install.  If you were interested you could go spelunking through the dependencies and see if you could figure out which package you really need for desktop icons.

---

### Post by Claus7 on 2019-04-23
Hello,

thank you for both your suggestions, yet both did not do the trick for ubuntu flashback. Instead I followed this link:
[https://itsfoss.com/install-nemo-file-manager-ubuntu/](https://itsfoss.com/install-nemo-file-manager-ubuntu/)

and installed nemo instead of nautilus. 

Then I went in dconf editor, wrote "trash" and enabled the trash can on Desktop. 

Now things are better...

Regards!

---

### Post by Claus7 on 2019-04-23
Hello,

changing gdm3 with lightdm did not work either (nautilus). I have also to add that right click does not work as well, only when on Desktop.

The org.gnome.desktop.background.show-desktop-icons is set to true.

Regards!

---

### Post by Vincentlaborant on 2019-04-24
I assume you use Gnome shell.

If that is the case, check if the extension is installed and enabled: [URL="https://extensions.gnome.org/extension/1465/desktop-icons/"]https://extensions.gnome.org/extension/1465/desktop-icons/  

[/URL]

---

### Post by Claus7 on 2019-04-24
Hello,
> **Vincentlaborant said:**
> I assume you use Gnome shell.

If that is the case, check if the extension is installed and enabled: [URL="https://extensions.gnome.org/extension/1465/desktop-icons/"]https://extensions.gnome.org/extension/1465/desktop-icons/  

[/URL]

thank you for your answer, yet I do not use gnome shell and I have already enabled this option, which under gnome shell did not seem to make any difference since desktop icons were already there. It seems that the option from dconf:
 
/org/gnome/gnome-flashback/desktop-background/show-desktop-icons
which has as description:
If set to true, then GNOME Flashback application will be used to draw the desktop background.

it seems that does not the trick, which is the option that should work in that case...Now, its missing from my system though... I will check anew...
edit: It's there either gnome-session removed or not. It is enabled, yet it seems that it does not work. Restarting gave an error to xorg. I do not know if this is related...

Regards!

---

### Post by muktupavels on 2019-05-05
GNOME Flashback currently does not have support for desktop icons!:
[https://gitlab.gnome.org/GNOME/gnome-flashback/issues/7](https://gitlab.gnome.org/GNOME/gnome-flashback/issues/7)

Desktop background setting is only for background.

---

### Post by Claus7 on 2019-05-06
Hello,

thanks for your response *muktupavels*. The current version of nautilus in disco is 3.32 (under synaptic). Indeed there was a deprecation of desktop icons from gnome version 3.28 and above. The thing is that in cosmic the desktop icons were there and the version of Files (nautilus) was 3.26 as far as I can see. I thought that the version was higher than that, yet as it seems the version of gnome shell does not tally with that of Files.
[https://launchpad.net/ubuntu/+source/nautilus](https://launchpad.net/ubuntu/+source/nautilus)
[https://launchpad.net/gnome-shell/+packages](https://launchpad.net/gnome-shell/+packages)

Good to know. The new version of gnome-terminal is really a welcome upgrade, at least since its functionality returned, while in bionic and cosmic there was a some trouble with it.

As it seems nemo is proposed as an alternative to hold desktop icons, at least for the time being. 

Regards!

---

