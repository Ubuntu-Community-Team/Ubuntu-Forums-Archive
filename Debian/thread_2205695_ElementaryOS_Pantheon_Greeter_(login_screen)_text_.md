---
title: "ElementaryOS Pantheon Greeter (login screen) text chars are square boxes, how to fix?"
date: 2014-02-15
forum: Debian
---

### Post by pr3fix2 on 2014-02-15
Hello,

This is actually a question concerning ElementaryOS ( elementaryos.org ), which is based off of the latest stable Ubuntu. [I posted this question on their forums]("http://elementaryos.org/answers/pantheon-greeter-login-screen-fonts-all-square-boxes-how-to-fix") but I have not received any response.


The login screen (Pantheon-Greeter) is not displaying text properly; all the text, including account names, password input, date (but not time), are displaying the generic white little boxes.


How can I fix this, or reinstall Pantheon Greeter, or reset it? I believe it got messed up after I followed this guide: [http://www.binarytides.com/gorgeous-looking-fonts-ubuntu-linux/](http://www.binarytides.com/gorgeous-looking-fonts-ubuntu-linux/)



none of the other system menus/apps are affected, just the login screen, so it's isolated to the Pantheon Greeter. How can I fix this? Thank you!

---

### Post by howefield on 2014-02-15
Thread moved to the "*Other OS/Distro Support*" forum.

---

### Post by pr3fix2 on 2014-02-15
> **howefield said:**
> Thread moved to the "*Other OS/Distro Support*" forum.

My apologies, howefield -- I am new to these forums and I must not have seen that forum when I was glancing through the index; sorry about that!


Any help on this issue is much appreciated. I've learned a lot from this great community as I've been learning the world of linux, many a google search has ended here :)

---

### Post by caffeinatedev on 2014-02-15
Do you have any other desktop environments installed?

---

### Post by pr3fix2 on 2014-02-15
> **caffeinatedev said:**
> Do you have any other desktop environments installed?

Thanks for the reply. I don't believe so, but what terminal command can I use to double check? Thanks!

---

### Post by vasa1 on 2014-02-15
> **pr3fix2 said:**
> Thanks for the reply. I don't believe so, but what terminal command can I use to double check? Thanks!Well, having more desktop environments than the default is not something that can happen without you initiating such a situation.

Anyway, please paste the results of */usr/share/xesssions/ls -al* here and enclose the contents within [CODE] tags for readability.

---

### Post by pr3fix2 on 2014-02-16
> **vasa1 said:**
> Well, having more desktop environments than the default is not something that can happen without you initiating such a situation.

Anyway, please paste the results of */usr/share/xesssions/ls -al* here and enclose the contents within ```
 tags for readability.

Pantheon.desktop is the only one listed.

This is what is inside Pantheon.desktop:

[code]
[Desktop Entry]Name=Pantheon
Comment=This session provides elementary experience
Exec=gnome-session --session=pantheon
TryExec=wingpanel
Icon=
Type=Application

```

---

### Post by pr3fix2 on 2014-02-17
Any insight? :)

---

