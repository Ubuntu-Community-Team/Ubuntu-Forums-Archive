---
title: "gconf-editor  show_desktop -- Won't stay unchecked?"
date: 2011-04-01
forum: Desktop Environments
---

### Post by Buying_Some_Time on 2011-04-01
I have to use gconf-editor -> apps/nautilus/preferences/show_desktop  -> and uncheck it in order to get multiple wallpapers enabled, I have to do this every time I boot. Why  won't my change save?


Any help would be great thanks!

---

### Post by Krytarik on 2011-04-01
Check the permissions of "~/.gconf/apps/nautilus/preferences/%gconf.xml":
```
ls -al ~/.gconf/apps/nautilus/preferences/%gconf.xml
```They should be like this:
```
-rw------- 1 krytarik krytarik 7843 2011-04-02 00:37 /home/krytarik/.gconf/apps/nautilus/preferences/%gconf.xml

```Greetings.

---

### Post by Buying_Some_Time on 2011-04-01
Hey, thanks for the help!

When I enter in the command, I get this:

```
-rw------- 1 umightb umightb 0 2011-03-26 20:43 /home/umightb/.gconf/apps/nautilus/preferences/%gconf.xml
```

Is that right?

---

### Post by Krytarik on 2011-04-01
> **Buying_Some_Time said:**
> 
```
-rw------- 1 umightb umightb 0 2011-03-26 20:43 /home/umightb/.gconf/apps/nautilus/preferences/%gconf.xml
```Is that right?
I don't guess so, because its file size is "0". Thanks for posting it.

Run this command to reset the "preferences" and restart Nautilus, close all of its windows before:
```
gconftool-2 --recursive-unset /apps/nautilus/preferences && killall nautilus
```To disable those option again, run:
```
gconftool-2 /apps/nautilus/preferences/show_desktop --type bool --set false
```

---

### Post by Buying_Some_Time on 2011-04-01
Okay, I did everything you said, but it still it still didn't work. 

:confused::confused:

---

### Post by Krytarik on 2011-04-01
Has a new file been created now?

---

### Post by Buying_Some_Time on 2011-04-02
> **Krytarik said:**
> Has a new file been created now?

No, when I enter the command that you first gave me I now get this

```
/home/umightb/.gconf/apps/nautilus/preferences/%gconf.xml: No such file or directory
```

---

### Post by Krytarik on 2011-04-02
The cause may be wrong ownerships and/or permissions. Please make sure first, that all the contents of your home directory are owned by yourself, run this command:
```
sudo chown umightb.umightb -R /home/umightb
```Also, try to create a file in that directory, before and after running those command.

---

### Post by Buying_Some_Time on 2011-04-03
Okay. I did what you said and I know that I can add/edit/delete and create files in my home directory with and without that command you gave me, but I still can't get "show_desktop" to stay unchecked after I restart. :(

---

### Post by Krytarik on 2011-04-03
Are you running any custom startup apps then?

---

### Post by Buying_Some_Time on 2011-04-03
> **Krytarik said:**
> Are you running any custom startup apps then?
Sorry, but what's a custom start up app? :confused::confused::confused:

---

### Post by Krytarik on 2011-04-03
> **Buying_Some_Time said:**
> Sorry, but what's a custom start up app? :confused::confused::confused:
Basically, did you add any apps to "System -> Preferences -> Startup Applications", or did you put any commands somewhere to be run at startup?

---

### Post by Buying_Some_Time on 2011-04-04
> **Krytarik said:**
> Basically, did you add any apps to "System -> Preferences -> Startup Applications", or did you put any commands somewhere to be run at startup?

Nope, I haven't changed anything there.

---

### Post by Krytarik on 2011-04-04
You may try creating a fresh user and check if the issue occurs with those as well.

---

### Post by Buying_Some_Time on 2011-04-04
> **Krytarik said:**
> You may try creating a fresh user and check if the issue occurs with those as well.

Okay, I'm going to try that!

---

