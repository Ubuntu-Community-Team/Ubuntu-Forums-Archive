---
title: "How to disable antialising for qt4 apps"
date: 2009-04-26
forum: General Help
---

### Post by ra100 on 2009-04-26
Hi.
I need to disable antialising fo qt4 apps in 9.04. I have installed systemsettings and when i launch it, i can see only icons and emoticons in appearance. settings for fonts aren´t available.
It seems like a bug, or feature?
So, is any way how can i disable antialising/subpixelhinting?
Thanks

---

### Post by Tindytim on 2009-04-26
If you happen to be using a Nvidia card and installed Nvidia X Server Settings (system -> preferences) it allows you to override the anti-alising settings of all applications.

---

### Post by ra100 on 2009-04-26
> **Tindytim said:**
> If you happen to be using a Nvidia card and installed Nvidia X Server Settings (system -> preferences) it allows you to override the anti-alising settings of all applications.

I have Intel

---

### Post by hickop on 2009-06-17
I have the same problem. I'm trying to get rid of the anti-aliasing fonts in qt4 apps.
I have set Nvidia option to override anti-aliasing but it didn't work (doubt it has something to do with the fonts).

Made a screenshot to show difference between my system fonts (GTK) and Qt one.

thx.

---

### Post by Yellow Pasque on 2009-06-17
I'm guessing you could edit /etc/fonts/conf.avail/10-antialias.conf (change 'true' to 'false')

There's probably a cleaner way to do it that doesn't violate Debian policy, like  creating a custom .fonts.conf file in the user's home directory, but I'm not up on my XML, so I'm not exactly sure what would need to be in this file.

---

### Post by hickop on 2009-06-17
> **Temüjin said:**
> I'm guessing you could edit /etc/fonts/conf.avail/10-antialias.conf (change 'true' to 'false')

There's probably a cleaner way to do it that doesn't violate Debian policy, like  creating a custom .fonts.conf file in the user's home directory, but I'm not up on my XML, so I'm not exactly sure what would need to be in this file.

That's it !
just made .fonts.conf file in my /home with these lines:

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="antialias" mode="assign"><bool>false</bool></edit>
  </match>
</fontconfig>

```

And it works perfect , no more anti-aliasing.
Thanks.

---

