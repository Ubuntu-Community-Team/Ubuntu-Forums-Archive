---
title: "Problem to add login sound."
date: 2016-02-24
forum: Desktop Environments
---

### Post by satimis on 2016-02-24
Hi all,

Problem - adding login sound.

I followed
[https://ubuntu-mate.community/t/how-to-activate-ubuntu-login-sound/677](https://ubuntu-mate.community/t/how-to-activate-ubuntu-login-sound/677)

For Ubuntu (Mate) 14.04, use the following command:
1)
/usr/bin/canberra-gtk-play -f /usr/share/sounds/ubuntu/stereo/desktop-login.ogg
Restart Ubuntu

2)
/usr/bin/canberra-gtk-play -f /usr/share/sounds/ubuntu/stereo/desktop-login.ogg
Restart Ubuntu

3)
sudo apt-get install libsox-fmt-all sox paman

None of them can work.  

I heard the login melody but unable make it to work.  Please advise.  Thanks

Regards
satimis

---

### Post by satimis on 2016-02-24
Hi all,

Problem solved as follows:-

On Desktop
-> Search your computer and online sources -> Startup Applications

highlight "desktop login sound" -> Edit

Name:  Desktop Login Sound
Command:  /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
Comment:  Plays a sound when login
-> Save

Logout and relogin

Now it works playing login melody

satimis

---

