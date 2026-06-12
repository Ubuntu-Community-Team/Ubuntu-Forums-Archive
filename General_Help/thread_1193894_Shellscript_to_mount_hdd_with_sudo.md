---
title: "Shellscript to mount hdd with sudo"
date: 2009-06-22
forum: General Help
---

### Post by newbmica on 2009-06-22
please move this thread if I put it at the wrong place :) couldn't find anything better.

I have a raid partition wich I cant mount without sudo becouse I lack previlages, so instead of making a backup and format it I thought I'd use this to "protect the files", but it's getting alittle tiresome to type the mount thingie in the terminal everytime I reboot the computer ^^;

So basicly what I am looking for is a shellscript that can mount the drive for me, when I want of course.

I am a total newb at shellscripts so I thought I'd explain alittle :)

I want to be able to type like "raid" or something in the box that comes up when u press alt+F2, then it would like to get the "enter password" thing in X that pops up when you are to add/remove programs or change settings in gnome.

Can you guys help me with this? or tell me an better alternative if you can :)

Ty! /Mica

---

### Post by kerry_s on 2009-06-22
i can think some ways. :)
1) just put what you type in the terminal, into **/etc/rc.local** without the sudo, it already runs as root. automatic mount with out you doing anything further.

2) alias your command in **~/.bashrc** then all you have to do is type raid in the terminal.
example:
**alias raid='your-command'**

3) create a **~/bin** folder in it put a script to do your thing. this lets you use alt+f2.

---

### Post by Arand on 2009-06-22
But the "proper" way to automount is to add an entry to fstab.
Alternatively you could use pythonSDM which is a graphical utility for configuring automounts.

- Arand

---

### Post by kerry_s on 2009-06-22
> **Arand said:**
> But the "proper" way to automount is to add an entry to fstab.
Alternatively you could use pythonSDM which is a graphical utility for configuring automounts.

- Arand

duh! if it was a snake it would have bit me. fstab should have been #1

---

### Post by newbmica on 2009-06-23
fstab didnt work, since the lack of previlages.. but I've tried the .bashrc, and /etc/rc.local ^^ dont have the time to reboot now though, but I'll say how it worked out :D

---

### Post by kerry_s on 2009-06-23
what did you put in fstab?

it would have to be something like:
/dev/hd?        /media/?   auto users     0       0

note, you also need to create the matching folder in /media/?

---

### Post by newbmica on 2009-06-23
Yes I used the same line as I used before I reinstalled and it didnt automount with fstab, plus when I tried to mount it normally with and without the fstab lines it said I lacked previlages, but it automounted now when I rebooted :)

---

