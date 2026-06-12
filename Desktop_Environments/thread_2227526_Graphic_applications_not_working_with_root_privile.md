---
title: "Graphic applications not working with root privileges (sudo)"
date: 2014-06-02
forum: Desktop Environments
---

### Post by sherlock2 on 2014-06-02
After upgrading from Ubuntu **11.10 **to **12.04 LTS**, I keep getting the following error when trying to open graphic applications with root privileges (sudo).
eg.: executing "sudo gedit" I get "**cannot open display**" after "Autolaunch error: X11 initialization failed"

The following happens under Gnome classic (no effects)
[FONT=system]
**$ sudo gedit**
** (gedit:18400): WARNING **: Riga di comando "dbus-launch --autolaunch=687c94355e5f99d1f9b772630000000c --binary-syntax --close-stderr" uscita con stato di uscita 1 non-zero: Autolaunch error: X11 initialization failed.\n
Impossibile aprire il display: 
Eseguire "gedit --help" per visualizzare un elenco completo delle opzioni disponibili a riga di comando.
[/FONT]
echo $DISPLAY prints :0.0

**if I give sudo -i and then echo $DISPLAY, nothing is returned.**
What should I check?

---

### Post by Frogs Hair on 2014-06-02
Try the following , ```
sudo apt get install gksu 
``` Preferred commands for graphical applications are as follows . ```
gksu gedit  
```or ```
gksudo gedit
```

---

### Post by sherlock2 on 2014-06-02
I forgot to mention that I already tried using gksu or gksudo, and the result is that I get the "Cannot open display"  error the same

```

$ gksu gedit
Cannot open display: 
Run 'gedit --help' to see a full list of available command line options.

```

---

### Post by Frogs Hair on 2014-06-02
Please wait for a user experienced with permissions . I have not tried an end of life upgrade before and 11.10 certainly was . You may also want to translate the error messages.

---

### Post by sherlock2 on 2014-06-10
solved adding the line Defaults env_keep+="DISPLAY XAUTHORITY" at the end of /etc/sudoers

---

