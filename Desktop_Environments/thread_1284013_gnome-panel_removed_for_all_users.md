---
title: "gnome-panel removed for all users"
date: 2009-10-06
forum: Desktop Environments
---

### Post by rozbuntu on 2009-10-06
Hello Ubuntu users,

I'm a system operator of a healthcare organization and we are supporting ubuntu big time! We currently have ubuntu running on all our workstations. And also on the servers we are running ubuntu.

Now for the problem...

I'm currently working on a customized desktop for all users. So that's means that i replaced the standard wallpaper with my own in /usr/share/background and replaced the standard theme and icons. Now i want the bottom panel to be removed when a newly created users logs on for the first he doesn't see the bottom panel. It's just because we use Avant Window Navigator.

So how do i remove the bottom-panel (GNOME) for all users (and for all users that are going to be created in the future, they should have a desktop without the bottom-panel).

Thanx in advance.
-- rozbuntu

---

### Post by zeroseven0183 on 2009-10-06
Hi!

Try this 
1. press Alt + F2
2. type **gconf-editor**
3. click **Run**
4. in the **Configuration Editor** look for **panel** under **desktop **>** gnome **>** session **>** required_components**
5. right-click **panel **and select **Edit Key..**
6. delete [B]gnome-panel
[/B]7. click [B]OK

[/B]and log-off from your current session and login again.

Of course, be sure you have **AWN** included in the **Startup Applications** first before logging off.

Reference: [http://ubuntuforums.org/showpost.php?p=7987602&postcount=4](http://ubuntuforums.org/showpost.php?p=7987602&postcount=4)

---

### Post by rozbuntu on 2009-10-06
Hi,

Thanx for the quick reply! But if i understand it correctly this deletes all the panels and i only need the bottom-panel removed.

Thanx.
-- rozbuntu

---

### Post by ajgreeny on 2009-10-06
Have a look at running ```
gksudo gconf-editor
``` and in apps>panel> you may find something to do it, though I admit I can't a way to remove it in all users by default.  However, being linux, I'm sure there must be a way, it's just not easy to find.

---

