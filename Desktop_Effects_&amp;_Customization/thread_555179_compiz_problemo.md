---
title: "compiz problemo"
date: 2007-09-19
forum: Desktop Effects &amp; Customization
---

### Post by mpgarate on 2007-09-19
ive had plenty of problems with compiz and beryl in the past, but never

> mike@mike-desktop:~$ compiz --replace && kde-window-decorator
Checking for Xgl: not present.
Detected PCI ID for VGA: 00:05.0 0300: 10de:0241 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x1024) to maximum 3D texture size (512): Failed.
aborting and using fallback: /usr/bin/metacity
Not initializing the Gtk-Qt theme engine
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x186 specified for 0x3200007 (Configure ).

anyone know whats going on? google didn't :(

---

### Post by Happy_Man on 2007-09-19
Try just ```
compiz --replace
```

---

### Post by mpgarate on 2007-09-19
when I do that (before this error) It gives me no window borders, but yes compiz effects

---

### Post by kroenecker on 2007-09-19
You might try installing xserver-glx (if you are running Gutsy.  It works for me.)

Do so at your own risk :P

---

### Post by ricardoec on 2007-09-19
I solved the no border issue installing emerald

---

### Post by mpgarate on 2007-09-20
im assuming you mean install "xserver-xgl"

and no it didnt work. I will try restarting..

the error that came that I really didnt understand was (also above)

> Comparing resolution (1280x1024) to maximum 3D texture size (512): Failed.

anyone even heard this one?

---

### Post by praet on 2007-09-20
According to this:
[http://ubuntuforums.org/showthread.php?p=3394690](http://ubuntuforums.org/showthread.php?p=3394690)

Its a problem with the check script in the compiz wrapper.

```
sudo gedit /usr/bin/compiz
```

In the script change GL_MAX_3D_TEXTURE_SIZE to GL_MAX_TEXTURE_SIZE 
```
# Check if the max texture size is large enough compared to the resolution
check_texture_size()
{
	TEXTURE_LIMIT=$(glxinfo -l | grep GL_MAX_TEXTURE_SIZE | sed 's/.*=[^0-9]//g')
	RESOLUTION=$(xdpyinfo  | grep -i dimensions: | sed 's/[^0-9]*pixels.*(.*).*//' | sed 's/[^0-9x]*//')
	VRES=$(echo $RESOLUTION | sed 's/.*x//')
	HRES=$(echo $RESOLUTION | sed 's/x.*//')
	verbose "Comparing resolution ($RESOLUTION) to maximum 3D texture size ($TEXTURE_LIMIT): ";
	if [ $VRES -gt $TEXTURE_LIMIT ] || [ $HRES -gt $TEXTURE_LIMIT ]; then
		verbose "Failed.\n"
		return 1;
	fi
	verbose "Passed.\n"
	return 0
}
```

---

### Post by dmolinap on 2007-09-20
thanks man, it worked for me

---

### Post by mpgarate on 2007-09-20
hey! me too!!

thanks!

---

### Post by Epimetheus on 2007-09-20
Worked for me too! Yey!

---

### Post by _newbie on 2007-09-21
thanks man! now compiz works

---

### Post by Dianoga on 2007-09-21
Worked for me as well...

Thanks

---

