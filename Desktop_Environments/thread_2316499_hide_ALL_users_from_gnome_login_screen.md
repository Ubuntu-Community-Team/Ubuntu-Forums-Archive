---
title: "hide ALL users from gnome login screen"
date: 2016-03-08
forum: Desktop Environments
---

### Post by seabird22 on 2016-03-08
Hello to all,

  I don't want user names displayed by gnome (v.3.16.2p0). I would prefer to enter all credentials manually. I found a recent post, but it was outdated and did not apply to me. I am actually not running Ubuntu, I am on OpenBSD 5.8 -stable, however, since my question is in regards to a windows manager and not an OS, and many Ubuntu users use gnome, I thought it would be appropriate to post here. I believe the modification should be done in  /etc/gdm/custom.conf. In /etc/gdm there is also another file called locale.conf

this is what /etc/gdm/custom.conf looks like in its default state. 

```
# GDM configuration storage

[daemon]
# Uncoment the line below to force the login screen to use Xorg
#WaylandEnable=false

[security]

[xdmcp]

[greeter]

[chooser]

[debug]
# Uncomment the line below to turn on debugging
#Enable=true
```

Can someone guide me in the right direction? Please be advised that I am aware that I can change the UIDs to below 1000, however, I would prefer not to. 


thanks in advance.

---

### Post by goofprog on 2016-03-09
The login manager "Slim" does not usually display all the users on the log in prompt.  The user name has to be typed in.  I know it is beating around the bush but I do not know the technical knowledge to alter gdm to your needs and it is a solution that I know of.

---

### Post by v3.xx on 2016-03-09
I haven't tried it, but this looks doable.

[https://wiki.archlinux.org/index.php/GDM#Hide_user_from_login_list](https://wiki.archlinux.org/index.php/GDM#Hide_user_from_login_list)

---

### Post by seabird22 on 2016-03-10
Here is what worked:     I logged in as root. I then changed the uid of the user I wanted to hide from the login in screen to 999 using ```
 usermod -u 999 user 
``` I rebooted the system, and as expected, that user was no longer on the login screen. I logged in as that user by manually entering user name and pw, (you must login once with each user you set uid to below 1000) and of course gnome acknowledged the user name and password, however, since the user has a uid below 1000, gnome did not log user in. Instead, gnome will return you back to the login screen.  Then I logged in as root again, returned the uid of that user to the original (1000 or above) and rebooted. That user no longer shows up on the login screen, and it has an uid of 1000 or higher. I have done this with 2 users and confirmed their uid are 1000 or above with userinfo.   It appears that there is a static file somewhere that gnome keeps with uids below 1000. Once a user name gets a uid below 1000, it is put on that list, and for security reasons, it cannot be changed back. That is probably the reason the above solution works.

---

