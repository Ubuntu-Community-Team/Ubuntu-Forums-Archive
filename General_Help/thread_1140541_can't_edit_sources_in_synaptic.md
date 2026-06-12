---
title: "can't edit sources in synaptic"
date: 2009-04-27
forum: General Help
---

### Post by rock4christ on 2009-04-27
when I try to edit my repositories in synaptic, It goes straight to the reload reminder.

---

### Post by miwaypet on 2009-04-27
I am not quite sure I follow you.

Are you talking about your repo list in software sources?

Why not try this in terminal;

> **sudo gedit /etc/apt/sources.list**

Edit your sources there. Then close out and update.

---

### Post by rock4christ on 2009-04-27
sorry. i mean I can't access the repository menu in synaptic. when i click it, It just brings up the reload warning w/o opening the repository menu.

---

### Post by rock4christ on 2009-04-27
meaning the menu never shows up.

---

### Post by rock4christ on 2009-04-27
also, before anyone says "sudo gedit /etc/apt/sources.list" that doesn't solve WHY the repos doesn't show up.

---

### Post by pirate_tux on 2009-04-27
sudo gedit /etc/apt/sources.list

edit your sources there and save the file

# aptitude update

also try:

$ aptitude search <package>

and:

$ apt-cache policy

Forget about Synaptic. Synaptic if for ignorant newbies.

---

### Post by rock4christ on 2009-04-27
> **pirate_tux said:**
> sudo gedit /etc/apt/sources.list

edit your sources there and save the file

# aptitude update

also try:

$ aptitude search <package>

and:

$ apt-cache policy

Forget about Synaptic. Synaptic if for ignorant newbies.

but synaptic is simple and easy. the search works well. also, the menu under repositories is the only one i know of that lets you change which mirror you dl updates from.

---

