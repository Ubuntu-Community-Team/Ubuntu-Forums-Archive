---
title: "Compiz and dapper?"
date: 2007-07-01
forum: Desktop Effects &amp; Customization
---

### Post by phizikal on 2007-07-01
Ok, I have direct rendering. I haven't tried installing it, because I don't know what will happen. If it is available, can anyone pleas give me instructions. Please and thank yous.

---

### Post by phizikal on 2007-07-05
*cough*

---

### Post by phizikal on 2007-07-06
*cough*

Ok I have downloaded and installed compiz. but when i try to run it in terminal i ge, "no compostite extensions" or something like that.

---

### Post by NeoLithium on 2007-07-06
For dapper, take a look here:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#Eye_Candy](http://ubuntuguide.org/wiki/Ubuntu_dapper#Eye_Candy)

---

### Post by phizikal on 2007-07-06
Ok all that went succesful, but i am getting this error.

```

compiz.real: No composite extension
/usr/bin/thefuture: line 2: gnome-window-decorator: command not found

```

---

### Post by NeoLithium on 2007-07-06
You have to add something to your xorg.conf file.  First:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
``` That backs up your configuration file for easy fixes.  Then, open up your xorg.conf and add a line:
```
gksu gedit /etc/X11/xorg.conf
```
Then add the following into the file:
```

Section "Extensions"
    Option "Composite" "true"
EndSection

```

Save and then log out and restart your x-server (CTRL+ALT+BACKSPACE)

---

### Post by phizikal on 2007-07-06
Okay, i did all that. I am wonder when i reboot what should I do if I get a HDD error?

---

### Post by phizikal on 2007-07-06
Ok I cant see my window borders at all! Can you please help.

---

### Post by avik on 2007-07-06
Try:

```
metacity --replace&
```

If you have emerald installed, try

```
emerald --replace&
```

---

### Post by phizikal on 2007-07-06
Ok, i did the metacity replace, and my borders showed back up and then switched back.

I tried the emerald but i got something like [1] 55325  but not exact numbers.

---

### Post by phizikal on 2007-07-06
Ok, can anyone help.

I found out when using metacity --replace& it fix the borders and such but when i exit the terminal it takes them off.

And I don't even think compiz is working, please help.

---

### Post by NeoLithium on 2007-07-06
Run the command ```
metacity --replace
``` with ALT+F2.  You can also add it to your startup if you have compiz in the startup System -> Preferences -> Sessions

---

### Post by phizikal on 2007-07-06
Okay that totally solves it, now that its fixed.

Where is the compiz settings and how do i get it running?

---

### Post by phizikal on 2007-07-06
I am not getting none of the effects, where is the settings? I cant find them no where. =/

---

### Post by NeoLithium on 2007-07-06
You may need to install the settings manager. It's been a while since I've been on dapper. Just take a look through synaptic by searching for: compiz

It's not much to go on, but hopefully it may help a bit.

---

### Post by avik on 2007-07-06
> **phizikal said:**
> I am not getting none of the effects, where is the settings? I cant find them no where. =/

Considering you used the Dapper Eye Candy guide, I don't think there's a specific settings manager.

Run gconf-editor using Alt-F2, then navigate to apps->compiz.  The settings are there.

---

### Post by phizikal on 2007-07-06
It's not in my configuration editor. =/

I still cant find it.

---

