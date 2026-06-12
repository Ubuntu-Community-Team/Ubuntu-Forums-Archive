---
title: "installing compizconfig-settings-manager on ubuntu"
date: 2009-09-14
forum: Desktop Environments
---

### Post by jkozain on 2009-09-14
Hello, I recently tried to install the[B] compizconfig-settings-manager and all its dependecies. Everytime I try to tho, it says Im missing the depedency python-compizconfig. I installed this dependency, however, it still says this dependency is missing. How can I fix this. Hook a nub up yo.
[/B]

---

### Post by drs305 on 2009-09-14
jkozain, welcome to the Ubuntu forums.

Try running it from the command line (Applications, Accessories, Terminal), and reinstalling compiz-config. 

If you are unfamiliar with sudo and the command line, you will be asked for your password. You won't see it as you type but hit ENTER once you have typed it out. Report the specific error messages. Both compiz-config... and the python dependency should be in the *universe* repository.

```
sudo apt-get install --reinstall compizconfig-settings-manager
```

---

### Post by jkozain on 2009-09-14
Thanks, now where can i find the command prompt on ubuntu, and what would be the code I would need to intall the python-comizconfig because I believe I might be installing that dependency wrong, thus not letting me install the compizconfig-setttings-manager.

---

### Post by jkozain on 2009-09-14
Ok, cancel that lost post. I typed that into the terminal. However, what would be the code to install the python-comizconfig dependency which I believe is missing.

Also, the reason Im installing this is because I am trying to get the visual effects on ubuntu to work. Everytime I try to use them, I get the error that they can't be applied or w/e.

---

### Post by drs305 on 2009-09-14
> **jkozain said:**
> Thanks, now where can i find the command prompt on ubuntu, and what would be the code I would need to intall the python-comizconfig because I believe I might be installing that dependency wrong, thus not letting me install the compizconfig-setttings-manager.

The command prompt would be from "the terminal". That's what the Applications, Accessories, Terminal part was about. You can also ALT-F2, tick 'run in terminal' and run the first command in the window.

Reinstalling compiz-config with the command given previously should recheck the dependencies. If you need to try to install the dependency separately, it would be:
```

sudo apt-get install --reinstall python-compizconfig

``` 
If it says it is not installed, remove the "--reinstall" and run again.

---

### Post by jkozain on 2009-09-14
Ok, I typed both in, and as far as Im concerned, they are both installed. However, my visual effects still fail to work.

---

### Post by gismo93 on 2009-09-14
usually when it won't let you use desktop effects its because your graphics card is too old and doesn't support 3-d graphics i tink.

this is just the most common problem but it may be something else that you can fix

---

### Post by oldos2er on 2009-09-14
To enable compiz, go to menus System, Preferences, Appearance, Visual Effects, choose normal or extra. After doing that, run Compiz config settings manager to further tweak effects.

---

### Post by steveneddy on 2009-09-14
> **oldos2er said:**
> To enable compiz, go to menus System, Preferences, Appearance, Visual Effects, choose normal or extra. After doing that, run Compiz config settings manager to further tweak effects.

Took the words out of my mouth.

(Typed the text out of my fingers?)

---

