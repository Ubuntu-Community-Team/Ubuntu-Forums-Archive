---
title: "Application menu missing in gnome-Metacity"
date: 2015-02-25
forum: Desktop Environments
---

### Post by searchphoenix on 2015-02-25
Gnome2-Metacity is one of the windows manager that I am currently using in ubuntu 14.10.
Suddently the application bar at the top went missing and I am not able to get it back in metacity.
So I switched to gnome-3 and xfce for a while but want to resolve the issue with metacity.
Can you please advice the list of things that I can do to get this issue resolved. Thank you!

ubuntu - 14.10
gnome session manager version - 3.9.90
gnome shell - 3.12.2

---

### Post by dino99 on 2015-02-25
open a terminal (console) and run:
- sudo apt-get update
- sudo apt-get install -f
- sudo apt-get install --reinstall ubuntu-desktop
- sudo apt-get install --reinstall metacity

maybe you need to log out/in to get the change
):P

---

### Post by searchphoenix on 2015-02-25
as mentioned i have re-installed ubuntu-desktop and metacity and restarted the machine. still the problem persist. the re-installation breaks one more thing in my machine. Now, I am not able to  view different window manager in log-on prompt to login between, unity, gnome3 or xfce. i have only one option to login to metacity.

---

