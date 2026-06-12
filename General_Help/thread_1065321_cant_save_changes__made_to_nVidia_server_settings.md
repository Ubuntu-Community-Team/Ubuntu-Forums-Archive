---
title: "cant save changes  made to nVidia server settings"
date: 2009-02-09
forum: General Help
---

### Post by eival on 2009-02-09
im trying to save the changes i make but it gives me this error


Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

---

### Post by jimmy the saint on 2009-02-09
make sure you preface the nvidia-settings command with "Sudo" in order to give it root privilages.  Otherwise it cannot write the new file.

---

### Post by C.S.Cameron on 2009-02-09
Try opening nvidia-settings as superuser ie in terminal type ```
sudo nvidia-settings
```

---

### Post by eival on 2009-02-09
> **C.S.Cameron said:**
> Try opening nvidia-settings as superuser ie in terminal type ```
sudo nvidia-settings
```

thanks this worked, i made changes an rebooted an the changes are still there.

i also seen the nvidia logo after the bios startup which i never seen prior :popcorn:

---

### Post by eival on 2009-02-20
new issue, my changes arent loading automatically when i start ubuntu.

its not till i open the nvidia server settings menu that i see the changes occur an they will stay that way till i shutdown.

but is there a way to have my settings load automatically?

---

### Post by trlkly on 2009-02-20
Yes. I don't know why Nvidia didn't make this automatic.

[LIST=#][*]Open System > Preferences > Sessions.
[*]Type in your password (if necessary).
[*]Click Add
[*]Type "nvidia-settings -l" in the Command field.
[*]Customize any of the other fields to your liking
[*]Click OK, and close Session Preferences.[/LIST]

That should do it. "nvidia-settings -l" loads your Nvidia settings without pulling up the configuration window.

Note: -l is an L.

---

### Post by eival on 2009-06-08
*bump*

new problem, im now trying to make changes to the the digital vibrance settings and i save like i did with the x server settings but when i restart ubuntu the color vibrance stays at default zero.


heres a screen cap of the exact setting im trying to change

[http://i43.tinypic.com/315hjxv.png](http://i43.tinypic.com/315hjxv.png)


is there a different code i need?

---

### Post by surfed on 2009-06-11
> **eival said:**
> *bump*

new problem, im now trying to make changes to the the digital vibrance settings and i save like i did with the x server settings but when i restart ubuntu the color vibrance stays at default zero.


heres a screen cap of the exact setting im trying to change

[http://i43.tinypic.com/315hjxv.png](http://i43.tinypic.com/315hjxv.png)


is there a different code i need?

add this to your start up programs:

nvidia-settings --load-config-only

this command will restore digital vibrance and anti aliasing settings from nvidia-settings

---

