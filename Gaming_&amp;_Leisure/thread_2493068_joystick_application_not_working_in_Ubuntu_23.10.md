---
title: "joystick application not working in Ubuntu 23.10"
date: 2023-12-02
forum: Gaming &amp; Leisure
---

### Post by rooman62 on 2023-12-02
the joystick app is broken.
The icon is visible in the applications window but said window just shuts when I click on the Joystick app icon, the app does not start.
reinstalled twice, apt updated etc, pc rebooted.

---

### Post by julian552 on 2023-12-09
Hi, have you checked the drivers?



 [RIGHT][SIZE=1][URL="https://tutuappx.com/"][COLOR=#a9a9a9]
Tutuapp[/COLOR][/URL][/SIZE][/RIGHT]

---

### Post by rooman62 on 2023-12-10
I assumed that deleting and reinstalling the application would do everything that's necessary concerning all needed libraries. What can I do and how?

---

### Post by maximge on 2024-05-21
sudo apt-get remove --purge joystick
sudo apt-get install joystick


If problems still persist, install Alternative Joystick Applications
sudo chmod +x /usr/bin/joystick


sudo apt-get install jtest-gtk
sudo apt-get update
sudo apt-get upgrade

---

