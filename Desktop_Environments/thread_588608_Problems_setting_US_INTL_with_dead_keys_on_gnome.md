---
title: "Problems setting US INTL with dead keys on gnome"
date: 2007-10-23
forum: Desktop Environments
---

### Post by aylons on 2007-10-23
I´ve just installed Gutsy Gibbon in my Dell E1505 laptop and I`m struggling with gnome to make dead keys work as they should, ie, ´+e making an é and ´+c making a ç.

Naturally, I first tried to change the layout in keyboard preferences, and it is set to US Internationak (with dead keys). It didn´t worked, so I googled for further help and edited xorg.conf, changing the input device section to this:

```
Section "InputDevice"
	Identifier "Generic Keyboard"
	Driver "kbd"
	Option "CoreKeyboard"
	Option "XkbRules" "xorg"
	Option "XkbModel" "pc104"
	Option "XkbLayout" "us"
	Option "XkbVariant" "intl"
EndSection

```

Unfortanely, dead keys are not working yet... Interestingly, in the login screen, dead keys works fine, and I can insert an á in the username by typing ´+a, for example.

And more, trying to solve my problem,  I found something about an app called SCIM. Following the manual, when I type:

```

GTK_IM_MODULE="scim"
export GTK_IM_MODULE

```

The applications I launch in this shell window works fine (naturally, I`ve configured SCIM accordingly before), but I want every application to work right, naturally.

And last, to my surprise, while running the live CD, changing the keyboard layout works fine and dead keys act as they should (except for the ´+c, which returns a c acute).

What am I missing? I really can´t understand the erratic behaviour, working fine in the login screen, working poorly in live CD, and not working at all everywhere else.

Oh, and no, using compose keys is not an option.

---

### Post by miestrâ on 2007-11-20
I haven't got a live CD so I can't confirm that part of what you're saying, but I can confirm everything else about this problem using dead keys in Gutsy. I'm sorry I can't be of more help, but perhaps it's good to know it's not just you.

---

### Post by miestrâ on 2007-11-20
Ãh, próblêm sòlvëd for me! :) For dead keys to work does require, as you seem to have guessed, a package called "scim" - and there have been problems migrating scim to work properly on Gutsy. The following solution solved everything for me:

[http://ubuntuforums.org/showpost.php?p=3676161&postcount=6](http://ubuntuforums.org/showpost.php?p=3676161&postcount=6)

Hope this helps!

---

### Post by aylons on 2007-11-20
Not really worked for me... ç was not working with dead acute + c. But I managed to solve this problem changing keymaps, Gnome and QT configuration. Annoying, ideed, but worked.

---

