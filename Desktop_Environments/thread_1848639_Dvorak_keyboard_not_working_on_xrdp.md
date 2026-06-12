---
title: "Dvorak keyboard not working on xrdp"
date: 2011-09-22
forum: Desktop Environments
---

### Post by Daniel Garcia on 2011-09-22
I'm running 11.04 on hyper-v. 

When I connect to the console using  hyperv manager (equivalent to sitting in front on an actual console) my dvorak keyboard works fine.

When I connect via xrdp I get a different logon page (see screenshot1.jpg) and I logon using qwerty. Once I have logged on everything is still set to qwerty.

On the console when I go into system->preferences->keyboard I see 1 layout: dvorak. (see screenshot2.jpg)

In my xrdp session, the same dialog looks different. (see screenshot3.jpg). When I go to add a new keyboard layout in the xrdp session, dvorak is not listed and "US 105-key keyboard (with windows key)" is the only select-able option. (see screenshot4.jpg).

my /etc/default/keyboard file has
```

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT="dvorak"
XKBOPTIONS=""

```

What am I doing wrong?

---

### Post by Daniel Garcia on 2011-09-23
When I execute the command "setxkbmap dvorak" I get

XKB extension not present on :11.0

---

### Post by Daniel Garcia on 2011-09-28
OK, I've figured out the solution.
[LIST]
[*]xrdp uses it's own keymap files in /etc/xrdp
[*]It uses 1 keymap per rfc1766 language
[*]I'm not sure how it determines your current language, but mine seemed to match to km-0409.ini even though my LANGUAGE setting is en_AU:en, which should match to km-0C09.ini.
[*]To create a new keymap file
[LIST]
[*]Log onto the console
[*]Run setxkbmap with the parameters that correspond to your layout
[*]Run xrdp-genkeymap 
[/LIST]
[/LIST]

So in my case I did:
```

setxkbmap –model pc104 –layout us –variant dvorak
xrdp-genkeymap km-0409.ini
```

This overrides the existing keymap, so good to make a backup first.

Daniel.

---

### Post by coffee_fan on 2012-09-19
This was exactly what I needed, thank you very much for the info. 

Note: I used your solution in Centos 5.7, where xrdp needs to be installed from sources. The only caveat was finding the xrdp-genkeymap file which is in /usr/local/bin. I figure in Ubuntu it may be readily accessible. I will find out soon enough :-).

---

