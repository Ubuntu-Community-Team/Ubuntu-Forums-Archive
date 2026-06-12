---
title: "Help Starting a script at boot time"
date: 2006-02-11
forum: Desktop Environments
---

### Post by hellerite on 2006-02-11
Hello, although not a complete newb, this is my first post. My problem: I have a wireless network card (D-Link, DWL-122) working. But in order to get it to communicate to the router I had to create a little script.
[INDENT]#!/bin/bash
# This litte script will bring wlan1 up and assign an IP Address
iwconfig wlan1 mode xxxxxxx
iwconfig wlan1 channel xxxxx
iwconfig wlan1 essid xxxxxx
iwconfig wlan1 key xxxxxxx
sleep3
dhclient3 wlan1
exit[/INDENT]
I would like to get this started at boot time so that I don't have to run it manually every time I boot the pc. I already tried to add it as a service but failed miserably. Any help will be greatly apreciated.

---

### Post by Aramil on 2006-02-11
How about adding it to /etc/init.d  folder?

---

### Post by uopjohnson on 2006-02-11
There is a README file in the init.d folder with a link to the debian policy manual where you can read all about properly adding scripts to this folder to start when you system starts.

---

