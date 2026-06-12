---
title: "commands for knowing the chipset on my dell 1520"
date: 2009-06-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by abhinav.p on 2009-06-22
hello are their any commands for knowing which wireless chipset i am using.i use dell 1520 and run jaunty.thanks in advance

---

### Post by lisati on 2009-06-22
Included in a repetoire of commands to find out "what's under the hood?" are lspci, lsusb and dmidecode. You might have to use sudo with some of them.

---

### Post by abhinav.p on 2009-06-22
yeah i know these commands.but i dont know how to decipher the output.i was hoping a more direct command is available...

---

### Post by alancanniff on 2009-06-22
sudo lshw -html > hardwareprofile.html

This rather useful command from [http://www.tech-recipes.com/rx/2771/ubuntu_generate_hardware_profile_system/]("http://www.tech-recipes.com/rx/2771/ubuntu_generate_hardware_profile_system/")

generates a reasonably understandable html hardware profile.

---

