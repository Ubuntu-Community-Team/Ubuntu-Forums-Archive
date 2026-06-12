---
title: "EDR17 compiled from cvs doesn't start!"
date: 2006-11-16
forum: Desktop Environments
---

### Post by Erzei on 2006-11-16
i. I have a problem installing Enlightenment DR17 from the cvs sourceforge repo.

First, i followed all the steps of the following page:
[https://vogelweith.homeftp.net/Linux/e17_en.php]("https://vogelweith.homeftp.net/Linux/e17_en.php")

The process of compilation and instalation was clean, without any problem. :-D 

BUT, after the part 3.1.2, when i try to start Enlightenment, the environment doesn't start.

I made a enlightenment.desktop file for running E17 from GDM.

If i put this, i got the first image... i got a empty environment...
```

[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=This session logs you into EDR17
Exec=/usr/local/bin/enlightenment_start
# no icon yet, only the top three are currently used
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=Enlightenment DR17

```

So, if i change *enlightenment_start* for *enlightenment*, i got the second screen...
```

[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=This session logs you into EDR17
Exec=/usr/local/bin/enlightenment_start
# no icon yet, only the top three are currently used
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=Enlightenment DR17

```

I've done too the next step:
-Added to ~/.xinitrc the following line:
```
/usr/local/bin/enlightenment
```

So... can someone help me??? I really want to run DR17, and with only one step away, i'm desesperating... ](*,) 

Thanks

---

### Post by Erzei on 2006-11-18
Can anyone help me? Plz, i really want to run DR17..

Thanks

---

### Post by Erzei on 2006-11-18
I got a little clue...

I made a file called .xsession in Home Directory...
And i've wrote a line:
```
exec /usr/local/bin/enlightenment
```

Now, i wrote the following command:
```
enlightenment
``` and ```
enlightenment_start
```

And a message appear...
```

Enlightenment cannot initialize its X connection

Have you set your DISPLAY variable?
```

So...
```

# echo DISPLAY
/usr/lib

```

What should i do?

:-k

---

### Post by Erzei on 2006-11-19
Error...

Is
```

# echo $DISPLAY 
:0.0
#

```

Anyone can't help me??? :(

---

### Post by josir on 2008-06-08
Hi Erzei, did you find how to solve this problem?
Josir.

---

