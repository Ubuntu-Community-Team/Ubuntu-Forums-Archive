---
title: "Mupen64Plus Segmentation Fault??"
date: 2009-06-11
forum: Gaming &amp; Leisure
---

### Post by Jcdlvsrbld on 2009-06-11
running jaunty 32-bit

:Dhi, having issues with mupen64plus. i wasnt able to install it using the documentation's guide. I did manage to install it via apprunner. it was running fine; however, it recently quit. it now only runs when i use the "gui app- as root" script with apprunner. when i try to run the program with the launcher, nothing happens and i get this when i try to run in the terminal i get this:

> 
(mupen64plus:3747): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
Config Dir:  /home/justin/.mupen64plus/
Install Dir: /usr/local/share/mupen64plus/
Plugin Dir:  /usr/local/share/mupen64plus/plugins/

Segmentation fault

im not sure what the segmentation fault is. any help is appreciated. 

also, this is what i get when using the "any app- as any user" app runner script

> (mupen64plus:4001): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
Config Dir:  /home/justin/.mupen64plus/
Install Dir: /usr/local/share/mupen64plus/
Plugin Dir:  /usr/local/share/mupen64plus/plugins/

/usr/bin/app-runner-launch: line 22:  4001 Segmentation fault      $run_mode ./"$file_name"


](*,)

---

### Post by Jcdlvsrbld on 2009-06-11
i figured out my installation issue, i just uninstalled it and reinstalled it normailly. but i still have no response from the launchers and still getting the segmentation output when i try to run via terminal

---

### Post by Jcdlvsrbld on 2009-06-11
thanks for all the help (lol), i uninstalled and noticed that the mupen64plus config files werent removed. i deleted these and reinstalled. everything works fine now!

---

