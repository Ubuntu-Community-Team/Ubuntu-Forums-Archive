---
title: "Xubuntu 18.04 Auto login not working - tried lots of things and no go!"
date: 2019-06-26
forum: Desktop Environments
---

### Post by md-au on 2019-06-26
Hi all,

Title says it all. Auto login on reboot is not working on my setup. The log in box wants me to click login when it should be auto login.

I have checked the box for not asking for password, and it hides the pw but it still requires me to click log in.

The following is what I have done:

/etc/lightdm/lightdm.conf 

[Seat*]
autologin-user=user
autologin-user-timeout=0
autologin-guest=false
autologin-session=lightdm-autologin

That did not work. So I tried this:

/etc/lightdm/lightdm.conf.d/12-autologin.conf      (created file that was not there)

[Seat*]
autologin-user=user
autologin-user-timeout=0

That did not work either so I tried the following:

groupadd -r autologin

 sudo gpasswd -a myuser autologin

This did not work either.

So expert people, what have I done wrong? Why does the login dialog box come up and make me click log in?

Any help to get this machine auto log in enabled would be amazing.

Thanks so much.
Matt.

---

### Post by again? on 2019-06-26
As a test, try setting autologin-user-timeout=5

---

### Post by md-au on 2019-06-26
Hi Guber2,

That did not work unfortunately. This is stubborn. Any other ideas?

---

### Post by again? on 2019-06-27
Autologin is not something I use but using the [Arch Wiki]("https://wiki.archlinux.org/index.php/LightDM#Enabling_autologin")
I can enable autologin straight through to the desktop in Xubuntu 18.04

Edited /etc/lightdm/lightdm.conf (I did not have this file)
```
sudo nano /etc/lightdm/lightdm.conf
```
Adding (check your current session name in ~/.dmrc)...
```
[Seat:*]
autologin-user=[COLOR="#FF0000"]glen[/COLOR]
autologin-session=xubuntu
```

Needs the package accountsservice which should be installed but check...
```
apt policy accountsservice
```

Create the system group autologin and add the user to the group...
```
sudo groupadd -r autologin
sudo gpasswd -a [COLOR="#FF0000"]glen[/COLOR] autologin
```
Use [COLOR="#FF0000"]your username[/COLOR] in above code.

May want to edit/delete other configs you created.
Cross your fingers and reboot. [-o<

---

### Post by md-au on 2019-06-27
Hey,
my username is actually 'user' lol. Pretty boring i know.

I tried all of the above and still the login box persists.

any other ideas? Driving me nuts.

matt.

---

### Post by again? on 2019-06-27
No idea.
This worked for me in 18.04 & 19.04 Xubuntu

```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] echo $DESKTOP_SESSION**
xubuntu

**[COLOR="#006400"]glen@Bionic:~$[/COLOR] inxi -S**
System:    Host: Bionic Kernel: 4.18.0-16-generic x86_64 bits: 64 Desktop: Xfce 4.12.3
           Distro: Ubuntu 18.04.2 LTS

```

---

### Post by md-au on 2019-06-27
echo $DESKTOP_SESSION returns nothing, and in inxi -S there is no DESKTOP line in the result....

weird because i definately have a desktop running.... any ideas?

---

### Post by md-au on 2019-06-27
Oh wait that was from ssh... doh. Back to square one.

---

### Post by again? on 2019-06-27
Check your lightdm settings.
```
cat /etc/X11/default-display-manager
```

```
lightdm --show-config
```

eg this is the results from an 18.04 Xubuntu live usb where by default
the live user "xubuntu" is auto logged in.
Shows current settings and the sources.
```
**[COLOR="#006400"]xubuntu@xubuntu:~$[/COLOR] lightdm --show-config**
   [Seat:*]
Q  allow-guest=false
K  greeter-wrapper=/usr/lib/lightdm/lightdm-greeter-session
L  guest-wrapper=/usr/lib/lightdm/lightdm-guest-session
M  xserver-command=X -core
N  greeter-setup-script=xubuntu-numlockx
O  greeter-session=lightdm-gtk-greeter
P  user-session=xubuntu
Q  autologin-guest=false
Q  autologin-user=xubuntu
Q  autologin-user-timeout=0

   [LightDM]
J  backup-logs=false

Sources:
I  /usr/share/lightdm/lightdm.conf.d/50-disable-guest.conf
J  /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
K  /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
L  /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
M  /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
N  /usr/share/lightdm/lightdm.conf.d/50-xubuntu-numlock.conf
O  /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
P  /usr/share/lightdm/lightdm.conf.d/60-xubuntu.conf
I  /usr/share/lightdm/lightdm.conf.d/50-disable-guest.conf
J  /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
K  /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
L  /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
M  /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
N  /usr/share/lightdm/lightdm.conf.d/50-xubuntu-numlock.conf
O  /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
P  /usr/share/lightdm/lightdm.conf.d/60-xubuntu.conf
Q  /etc/lightdm/lightdm.conf
```

---

### Post by yetimon_64 on 2019-06-27
> **guber2 said:**
> No idea.
This worked for me in 18.04 & 19.04 Xubuntu...
Your procedure when tested here on xubuntu 18.04 worked perfectly.

> **md-au said:**
> Oh wait that was from ssh... doh. Back to square one.You may have to undo any alterations you have made previously and try to get the setup back to as close to standard as possible  and retry guber2's procedure again, it works well here. Though I doubt you will be able to autologin with this IF you are trying to do so over ssh, I expect that would be quite a bit more complicated to set up.

---

### Post by md-au on 2019-06-28
I thought this was something i had done but today i reinstalled xubuntu 18.04 from the distro iso, and had autologin working perfectly.

THEN a sudo apt-get update then upgrade and autologin is broken immediately on reboot. So something in a new package or script or something. On reboot, the login box requesting password came up. Doh.

I have absolutely no idea where to start as all previous helps have been unsuccessful and all files read as they should as far as I can see. 

Cheers,
Matt.

---

### Post by again? on 2019-06-28
Did you change your gfx drivers?
Just an idea.

---

### Post by md-au on 2019-06-28
No change made on purpose anyway. The distro is on a HP T5740 thin client that runs intel GL40 graphics.

---

