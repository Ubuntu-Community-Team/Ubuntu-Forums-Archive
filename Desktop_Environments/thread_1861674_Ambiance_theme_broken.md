---
title: "Ambiance theme broken"
date: 2011-10-15
forum: Desktop Environments
---

### Post by ShinIori319 on 2011-10-15
I have just upgraded to version 11.10, but I'm having quite a bit of problems with the "Ambiance" theme. It won't just show properly. I have tried with the other themes, and all, including Radiance work properly. Unlike others I've seen, it doesn't show all grey and old-styled. The buttons and icons show properly. Most of the problem is the title bars. They're orange colored, unlike the elegant black ones from Ambiance itself. It happens in both the Unity and classic GNOME fallback sessions. Here are two screenshots of each session.

---

### Post by ShinIori319 on 2011-10-17
Bump.

---

### Post by herophuong on 2011-10-24
I have the same prob too. Hope they will fix it soon.

---

### Post by ShinIori319 on 2011-11-02
Okay, I'm bumping again. This issue is already annoying me. But I have now something that would help find the PROBLEM.

I tried running the command [COLOR=Red]unity --reset[COLOR=Black] and found an error that caught my eye. It reads the following:

[/COLOR][/COLOR]> Window manager warning: Failed to load theme "Ambiance": Line 308 character 106: Couldn't recognize the image file format for file '/usr/share/themes/Ambiance/metacity-1/minimize_focused_normal.png'Hope someone can provide any suggestion now. I am not an expert with Linux.

I have uploaded a bug report as well: [https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/878073](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/878073)

**[COLOR=Red]EDIT:[/COLOR]**[COLOR=Red][COLOR=Black] I have found a temporary workaround for the problem until Ubuntu devs decide to release a fix for this.

1. Run Nautilus as root [B](gksudo nautilus)
[/B]2. Locate the folder **/usr/share/themes/Ambiance**. We will work on two folders: **metacity-1** and **unity**. Browse **metacity-1**. The files that are likely causing the problem will show their thumbnail as a black square with the letters "PNG".
3. Now go to the **unity** folder. Press **F3** to split the screen so you can see both folders.
4. Copy the files from **unity** to **metacity-1**.
5. Either you can switch to another theme and back to Ambiance from the settings manager, or re-log/reboot/whatever.
[/COLOR][/COLOR]

---

### Post by pbhedlund on 2011-11-20
> **ShinIori319 said:**
> **[COLOR=Red]EDIT:[/COLOR]**[COLOR=Red][COLOR=Black] I have found a temporary workaround for the problem until Ubuntu devs decide to release a fix for this.[/COLOR][/COLOR]

Thank you!

---

