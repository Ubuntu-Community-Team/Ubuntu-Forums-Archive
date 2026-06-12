---
title: "Announce Battery State Script"
date: 2009-06-01
forum: General Help
---

### Post by chrisss404 on 2009-06-01
Hey all!
I sometimes have the probleme that I don't notice that my battery is nearly empty. So I decided to write a little script that tells me from time to time how much power is left. It's a quick and dirty script written in python only tested with Ubuntu 9.04, so don't expect too much.
It uses the new notifying system (notify-osd) that came with ubuntu 9.04 to notify the actual battery state and plays a sound in the same time.

So here comes [the script]("http://mytug.net/HOWTOs/check_battery_state/check_battery_state.py"). Just make it executeable [INDENT]chmod +x check_battery_state.py[/INDENT] , add it to your startup applications and don't forget to install python-pyxine otherwise the sound wont work [INDENT]sudo apt-get install python-pyxine[/INDENT]Thats it, I hope it's usefull to someone out there.

---

