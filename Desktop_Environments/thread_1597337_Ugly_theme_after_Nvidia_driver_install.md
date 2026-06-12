---
title: "Ugly theme after Nvidia driver install"
date: 2010-10-15
forum: Desktop Environments
---

### Post by Jungleboss on 2010-10-15
I've tried the 'current' proprietary Nvidia drivers in the repository and also the newest from Nvidias home page. Both of them gives me, regardless of what theme I choose, ugly windows. The only things that are shown correct according to the theme is the minimise, maximise, close buttons (correct colour and form). Everything else is grey and ugly. I have successfully activated 'Normal' visual effects, so composite/opengl seems to work.

The only window that is according to the theme is System/Preferences/Appearance!?

Any ideas?

---

### Post by gg234 on 2010-10-15
Try this [http://www.mydailytechtips.com/2010/10/how-to-fix-plymouth-ugly-resolution-for.html](http://www.mydailytechtips.com/2010/10/how-to-fix-plymouth-ugly-resolution-for.html)

---

### Post by xircon on 2010-10-15
> **gg234 said:**
> Try this [http://www.mydailytechtips.com/2010/10/how-to-fix-plymouth-ugly-resolution-for.html](http://www.mydailytechtips.com/2010/10/how-to-fix-plymouth-ugly-resolution-for.html)

That is for Plymouth!  Select appearance from the menu and select a new theme.

---

### Post by ankspo71 on 2010-10-15
Hi,
I think it could be gnome-settings-daemon crashing. Does the theme get reapplied if you press Alt+F2 then type in: gnome-settings-daemon ? 

If running gnome-settings-daemon does help, then...
Try doing what this post says to do then log out then log back in:
[http://ubuntuforums.org/showthread.php?t=885038](http://ubuntuforums.org/showthread.php?t=885038)

If that doesn't help, see the post made by "serfcx" here:
[http://ubuntuforums.org/archive/index.php/t-688522.html](http://ubuntuforums.org/archive/index.php/t-688522.html)

If neither of them help, then try what I said in this post:
[http://ubuntuforums.org/showpost.php?p=9958138&postcount=3](http://ubuntuforums.org/showpost.php?p=9958138&postcount=3)

Hope this helps.

---

### Post by Jungleboss on 2010-10-15
> **xircon said:**
> That is for Plymouth!  Select appearance from the menu and select a new theme.

Only the minimise/maximise/close buttons are changed when selecting a new theme. Nothing else.

---

### Post by Jungleboss on 2010-10-15
> **ankspo71 said:**
> Hi,
I think it could be gnome-settings-daemon crashing. Does the theme get reapplied if you press Alt+F2 then type in: gnome-settings-daemon ? 

If running gnome-settings-daemon does help, then...
Try doing what this post says to do then log out then log back in:
[http://ubuntuforums.org/showthread.php?t=885038](http://ubuntuforums.org/showthread.php?t=885038)

If that doesn't help, see the post made by "serfcx" here:
[http://ubuntuforums.org/archive/index.php/t-688522.html](http://ubuntuforums.org/archive/index.php/t-688522.html)

If neither of them help, then try what I said in this post:
[http://ubuntuforums.org/showpost.php?p=9958138&postcount=3](http://ubuntuforums.org/showpost.php?p=9958138&postcount=3)

Hope this helps.

Killing gnome-settings-daemon and running it again works!

But running the script:

#!/bin/sh
sleep 2 && gnome-settings-daemon ;

(I've tried sleep 10 aswell)

At startup doesn't work. Gnome-settings-daemon seems to be started every time (even without the script). It never crashes (as far as I can see). But to get correct theme I have to kill it and restart it manually.

I'm booting from a fast SSD, if that can be the cause. That the processes aren't starting in the correct order because of the high performance disk.

---

### Post by xircon on 2010-10-15
```
#!/bin/sh
killall gnome-settings-daemon
sleep 2 && gnome-settings-daemon ;

```

---

### Post by Jungleboss on 2010-10-15
> **xircon said:**
> ```
#!/bin/sh
killall gnome-settings-daemon
sleep 2 && gnome-settings-daemon ;

```

Actually I made this script and it seems to work :)
Thanks anyway.

```
#!/bin/sh
sleep 3
killall -9 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
gnome-settings-daemon
```


Btw, is:
sleep 2 && gnome-settings-daemon ;

identical with:
sleep 2
gnome-settings-daemon

?

And what does the ending ';' mean?

---

### Post by Jungleboss on 2010-10-16
To get correct theme in Nautilus I had to do the following:

[http://wwww.ubuntuforums.org/showpos...80&postcount=4](http://wwww.ubuntuforums.org/showpos...80&postcount=4)

---

### Post by ankspo71 on 2010-10-16
Hi Jungleboss

"&" =  means run this following command at the same time.

"&&" = means run this following command next, but only after the previous command is successfully completed. 

If you only make a list of applications in a script and not use "&" or "&&" it will only launch one application at a time. Each command (application) might need to exit first before the next one is launched. 
```

#!/bin/sh 

gbrainy
sol
gnomine

```

You are probably better off with something like this (in most cases):

```

#!/bin/sh 

gbrainy &
sol &
gnomine &

```

";" = I don't know what that is used for to be honest. I have seen other people using that at the end of scripts (especially in start up scripts) so I use it since it has always worked in my commands. It might just mean 'the end of this string of commands'.

Hope this helps.

---

### Post by Spade12 on 2010-10-17
hey guys, im dealing with this same issue, running the aforementioned script : 

```
#!/bin/sh sleep 3 killall -9 /usr/lib/gnome-settings-daemon/gnome-settings-daemon gnome-settings-daemon
```

works for everything but nautilus

will there be a patch for this?  should i try updating my nvidia driver to a newer release?

---

### Post by ankspo71 on 2010-10-18
Hi Spade12

Here is a link talking about how to get nautilus re-themed:
[http://wwww.ubuntuforums.org/showpost.php?p=9307380&postcount=4](http://wwww.ubuntuforums.org/showpost.php?p=9307380&postcount=4)

Also, here is a similar thread to keep an eye on:
[http://ubuntuforums.org/showthread.php?t=1594010](http://ubuntuforums.org/showthread.php?t=1594010)

---

### Post by Spice Weasel on 2010-10-18
A permanent fix for this is installing LXAppearance and making sure it saves to your ~/.gtkrc2.0.

---

