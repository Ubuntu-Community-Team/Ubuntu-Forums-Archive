---
title: "Unable to launch &quot;/usr/bin/startxgl.sh"
date: 2007-05-02
forum: Desktop Effects &amp; Customization
---

### Post by Sokar on 2007-05-02
Hi, yesterday beryl was running perfectly on my laptop. I wanted to add the shutdown and restart buttons to the poweoff button, since they don't appear due to a bug with beryl...

So i went to beryl forums, and found that startxgl.sh must be like this for an ATi in Gnome:

```

#!/bin/sh
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
# Iniciar Gnome
exec gnome-session
```

Before, i had it like this:

```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer & DISPLAY=:1
exec gnome-session
```
startxgl.sh is in  /usr/bin/

And this script is called from xgl.desktop, which is in /usr/share/xsessions :

```

[Desktop Entry]
Encoding=UTF-8
Name=xgl
Comment=Start an xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application

```

Well, my problem. Now, no matter what the content of startxgl.sh is, the xgl session doen't start, i get this error (written word by word):

```

Xsession: unable to launch "/usr/bin/startxgl.sh
"X session --- "/usr/bin/startxgl.sh
"not found; falling back to default session.

```

But startxgl.sh does exist!! And has execution rights (chmod +x).. i've tried changing the name,moving it to /usr/local/bin, creating it from the begining many times ( and updating it's name and location in xgl.desktop).. but nothing...

And the file does exist!!

What could it be? Is it a very rare bug! Am i forgeting something???

Thanks in advance :P

---

### Post by mdwuznik on 2007-05-02
Is startgl.sh executable ?

Michal

---

### Post by Sokar on 2007-05-02
Yeah, sure it is. I 've checked it many times. sudo chmod +x /usr/bin/startxgl.sh should do it.

Could it be some of group permissions to the file, or to the whole directory??

I'm completely lost

Thanks 4 your replies ^^

---

### Post by rolf-c on 2007-05-02
What is the " ?

> Xsession: unable to launch "/usr/bin/startxgl.sh
"X session --- "/usr/bin/startxgl.sh
"not found; falling back to default session.

Just looks odd, but I think it's the way X is reporting it.  May not be related to this issue, if not sorry to derail.

---

### Post by Sokar on 2007-05-03
> **rolf-c said:**
> What is the " ?



Just looks odd, but I think it's the way X is reporting it.  May not be related to this issue, if not sorry to derail.
No idea. I also think is the way X reports the error...

I'll try to put the sh in home...to see if it's something related to group pemissions...

Thanks

---

### Post by Sokar on 2007-05-04
I solved it. It was a text codification problem. I was copying the script content from a txt file created under windows. I created it from linux from the beginning and worked.

Bye

---

### Post by rolf-c on 2007-05-04
Ah yes, the ^M.  Good find!!  Glad it's working now!

---

