---
title: "Modifying keymap"
date: 2008-08-06
forum: Desktop Environments
---

### Post by robz0rz on 2008-08-06
Hello all

I recently got my laptop, and I'm trying to get everything to work as it should. The laptop is a Lenovo Thinkpad T61. Most of the keys on the keyboard work as they should, but I'd like to modify a few keys.

The laptop has a blue "ThinkVantage" key. I believe this gives access to some sort of option menu under Windows, and it can be used during boot-time to get a restore-menu. In Linux, I'd like to use that button as a hotkey to open a terminal.

Also, by pressing Fn+F5, you can toggle bluetooth and wlan. Seeing there is already a switch somewhere else on the laptop just for the wlan adapter, I'd like to set it so it just switches bluetooth. I was following [this guide]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_Release_Candidate_on_a_ThinkPad_T61#Bluetooth"), but I'd like to set Fn+F5 to use the script created in the guide.

The problem is that I don't know how to change the actions mapped to keys. Also, the script "bluetooth-toggle" needs superuser rights, and I don't know how to allow normal users to use it.

I hope someone can help me. I use Ubuntu 8.04 Hardy Heron. Thank you very much in forward.

--Rob Spoel

---

### Post by robz0rz on 2008-08-18
Alright, I've learned a lot about keymapping since I made the post, but I could still use some help because I lack the knowledge of what exactly to do.


I really want Fn+F8 (this generates an acpi event I believe) to toggle the touchpad. I can't seem to get it to work.

I also really want Fn+F5 (I'm sure this generates some sort of event) to toggle just bluetooth instead of bluetooth and wifi.

Also, I've managed to set two keys next to my arrow keys to Back and Forward using xmodmap and some XF86* keysyms. I'd rather use those keys to switch desktop-viewport though, but I can't seem to figure out which keysym to type into my xmodmap file.


Thanks in forward

---

