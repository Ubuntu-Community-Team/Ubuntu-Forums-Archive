---
title: "Trying to use Remastersys to create iso"
date: 2014-05-23
forum: Desktop Environments
---

### Post by SurfaceUnits on 2014-05-23
I get the following message when trying to create the iso. How to set the Lightdm derfault desktop?
"Lightdm not setup properly. You must set your default desktop with lightdm prior to remastering"

---

### Post by sudodus on 2014-05-23
I have read that Remastersys works in 12.04 LTS. I don't know if and how it works in newer versions. Which version are you trying to remaster?

---

### Post by SurfaceUnits on 2014-05-23
Lubuntu is the only distro I've had trouble with. 14.04 .Remastersys works great in other Buntu distros including 14.04

---

### Post by sudodus on 2014-05-24
Great news that Remastersys works in other Buntu distros including 14.04:-)

Too bad about Lubuntu. Lightdm has been around for years (also during 12.04), I don't understand why its settings are not accepted in Lubuntu.

- Could the problem be that there is an embryo to a LXQt session? This might be the case, even if it is not shown in the session menu. If I remember correctly, there was an LXQt entry in the session menu some time during Trusty alpha or beta.

- Or could it be something that *you* have tweaked (changed, added or removed)? I mean, there is no reason to use Remastersys (except for testing), if you have not tweaked anything.

-o-

Anyway, if you want to create a portable system, you can also make a tarball of your installed system with the One Button Installer, and install into other computers. This works as long as you avoid proprietary drivers. When necessary you install such drivers after installation. See this link

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

---

### Post by SurfaceUnits on 2014-05-24
Just a virgin 14.04 install. Was testing to see if I could build out my common installs and remaster it.  I tried a 14.04 with the LXQT PPA installed, same error. May try an earlier Lubuntu to see if any different. Thanks. Have been using Xubuntu for XP replacements. Was going to look at Lubuntu.

---

### Post by Portaro on 2014-05-25
sudo /usr/lib/lightdm/lightdm-set-defaults -s lubuntu

see here - [http://www.remastersys.com/forums/index.php?topic=1959.0](http://www.remastersys.com/forums/index.php?topic=1959.0)

---

### Post by SurfaceUnits on 2014-05-26
> **Portaro said:**
> sudo /usr/lib/lightdm/lightdm-set-defaults -s lubuntu

see here - [http://www.remastersys.com/forums/index.php?topic=1959.0](http://www.remastersys.com/forums/index.php?topic=1959.0)

Ok thanks. That link led to sudo /usr/lib/lightdm/lightdm-set-defaults  which led to lightdm-set-defaults: command not found

which led to [http://askubuntu.com/questions/251041/how-to-install-lightdm-set-defaults](http://askubuntu.com/questions/251041/how-to-install-lightdm-set-defaults)
[TABLE]
[TR]
[TD="class: votecell"]          

              [/TD]
                [TD="class: answercell"]                  As of Ubuntu Trusy 14.04, lightdm-set-defaults is [no longer available]("http://packages.ubuntu.com/search?suite=trusty&arch=any&mode=exactfilename&searchon=contents&keywords=lightdm-set-defaults").  This is because lightdm now using a configuration directory /etc/lightdm/lightdm.conf.d/  rather than a single configuration file.  The files in this directory  can be edited by hand, new files can be added, or files can be removed.   There is no longer any need for a command that edits the single  configuration file.
      
[/TD]
[/TR]
[/TABLE]
Which in the .conf file in that directory looks like it is set properly. More work later.

---

### Post by travis-falkenberg on 2014-05-29
Remastersys does work on a standard Ubuntu 14.04 install. It does not work on Xubuntu or Lubuntu (I didn't try Kubuntu).

You only need to add an empty lightdm.conf in /etc/lightdm for Remastersys to work in Xubuntu and Lubuntu. I succesfully made distribution iso's and started them in Virtualbox. I also made a custom Xubuntu distribution with some deleted packages and lots of extra packages. which came out at 2.2gb. and installed it on a real hard drive.

---

### Post by SurfaceUnits on 2014-05-30
> **travis-falkenberg said:**
> Remastersys does work on a standard Ubuntu 14.04 install. It does not work on Xubuntu or Lubuntu (I didn't try Kubuntu).

You only need to add an empty lightdm.conf in /etc/lightdm for Remastersys to work in Xubuntu and Lubuntu. I succesfully made distribution iso's and started them in Virtualbox. I also made a custom Xubuntu distribution with some deleted packages and lots of extra packages. which came out at 2.2gb. and installed it on a real hard drive.

Haven't had any problems with Xubuntu 13.10 or 14.04. Thanks for the tip.

---

