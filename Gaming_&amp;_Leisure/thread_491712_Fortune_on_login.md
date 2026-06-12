---
title: "Fortune on login"
date: 2007-07-03
forum: Gaming &amp; Leisure
---

### Post by shew on 2007-07-03
Is there a way to get Fortune to run when I login to Gnome?

---

### Post by FoolsGold_MKII on 2007-07-04
Depends on what you're after.

I like starting a fortune whenever I open a terminal. If that sounds interesting, do what I did:

cd ~
gedit .bashrc

At the very end, add the following line:

echo; fortune; echo

Save, and the next terminal you open, you get your fortune. If you're looking for a way to show a fortune in a window after you log into Gnome though, dunno, but I've seen it happen.

---

### Post by hikaricore on 2007-07-04
This might work for ya.

Put this in your startup sessions (System/Preferences/Sessions): 

```
echo "$(fortune);" | zenity --text-info
```

This assumes you have both zenity and fortune installed.  ^_^

---

### Post by shew on 2007-07-04
> **FoolsGold_MKII said:**
> Depends on what you're after.

I like starting a fortune whenever I open a terminal. If that sounds interesting, do what I did:

cd ~
gedit .bashrc

At the very end, add the following line:

echo; fortune; echo

Save, and the next terminal you open, you get your fortune. If you're looking for a way to show a fortune in a window after you log into Gnome though, dunno, but I've seen it happen.

Thanks for the quick reply.  I found lots of resources on how to get a starting message in a terminal.  What I'm after doesn't isn't in the terminal, but rather the Gnome gui.  I'd like to login to Gnome and get a fortune message (not in a terminal) somewhere on the desktop.

---

### Post by shew on 2007-07-04
> **hikaricore said:**
> This might work for ya.

Put this in your startup sessions (System/Preferences/Sessions): 

```
echo "$(fortune);" | zenity --text-info
```

This assumes you have both zenity and fortune installed.  ^_^

From a quick look at the project page for zenity, this may do exactly what I want.  Thanks.  I'll post a follow up.

---

### Post by shew on 2007-07-05
> **hikaricore said:**
> This might work for ya.

Put this in your startup sessions (System/Preferences/Sessions): 

```
echo "$(fortune);" | zenity --text-info
```

This assumes you have both zenity and fortune installed.  ^_^

This works when run from a terminal.  However, it does not run when put the code into Startup Programs in Sessions.  I do not get an error message.  Simply nothing happens.

---

### Post by hikaricore on 2007-07-05
Make a script in your homefolder then.

```

gedit ~/fortune.sh
```

Paste this in gedit:

```
#! /bin/bash
echo "$(fortune);" | zenity --text-info
```

Save the file and then from a terminal:

```
chmod +x ~/fortune.sh
```

You should be able to put *~/fortune.sh* in your startup sessions and have it work.  ^_^

---

### Post by hikaricore on 2007-07-05
Also if you want something a little less generic and less oddly sized:

```
#! /bin/bash
echo "$(fortune)" | zenity --title=Fortune --text-info= --height=225 --width=325
```

I got bored and played around with the zenity options some more. ^_^

---

### Post by shew on 2007-07-05
> **hikaricore said:**
> Also if you want something a little less generic and less oddly sized:

```
#! /bin/bash
echo "$(fortune)" | zenity --title=Fortune --text-info= --height=225 --width=325
```

I got bored and played around with the zenity options some more. ^_^

lol Thanks

---

### Post by shew on 2007-07-05
Oddly, using ~/fortune.sh did not work, but /home/<username>/fortune.sh did.  Anyway that's exactly what I wanted.  Thanks again

---

### Post by go_beep_yourself on 2008-09-17
or you could put this in your session list instead of creating the script

bash -c 'echo "$(fortune)" | zenity --title=Fortune --text-info= --height=225 --width=325'

---

