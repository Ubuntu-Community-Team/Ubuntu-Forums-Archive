---
title: "Changing screen resolution in KDE"
date: 2006-04-04
forum: Desktop Environments
---

### Post by SteveRwanda on 2006-04-04
I'm wondering how an individual user can change his/her screen resolution and refresh rates under KDE? In Gnome there's a little package in the main menu systems for doing that but I can't find it in KDE...

Cheers,
Steve

---

### Post by Monster_user on 2006-04-04
2 ways.

Open the Control Center (Alt-F2 -> kcontrol), and then browse to the Display -> Settings area.

Open the Krandrtray utility.

Alt-F2-> krandrtray

---

### Post by dr.drake on 2006-04-28
I installed KDE over Ubuntu Dapper Beta, and I can't change my screen resolution either..

in kcontrol (control center) there is no option "display". 

I used to run Kubuntu, and I had it there, but somehow the Kubuntu Dapper install gave me some problems, so I installed Ubuntu + KDE instead... and now I'm stuck with the default resolution.

I also tried Krandrtray, but I can't open it nor can I find a program with this name in synaptic.

help, please?

---

### Post by Monster_user on 2006-04-30
[QUOTE=dr.drake]I installed KDE over Ubuntu Dapper Beta, and I can't change my screen resolution either..[/QUOTE]
Sorry, I have not gotten around to install KDE on Dapper, and right now I'm stuck on DSL lite, and it keeps dropping the connection (might as well be dialup).

I'm still using KDE 3.3 on my other distros. I have never used KDE 3.5. They have probably moved things around, or renamed Krandrtray.

Or you may need to add the Universe repository to get Krandrtray. Also, make sure that 'krandrtray' is in all lowercase letters. 

Try typing 'kra' in a terminal, and then pressing tab. It should show a list of programs that start with 'kra'.

---

### Post by [S|G] on 2006-05-01
[QUOTE=dr.drake]I installed KDE over Ubuntu Dapper Beta, and I can't change my screen resolution either..

in kcontrol (control center) there is no option "display". 

I used to run Kubuntu, and I had it there, but somehow the Kubuntu Dapper install gave me some problems, so I installed Ubuntu + KDE instead... and now I'm stuck with the default resolution.

I also tried Krandrtray, but I can't open it nor can I find a program with this name in synaptic.

help, please?[/QUOTE]
I'm also using Dapper, and I can start Krandrtray (just make sure you type krandrtray, no capitals). However I've been unable to change my screen resolution since I upgraded too... Maybe a bug? 

Anyway, I can change my screen res using a not-so-elegant workaround: I open VMware, change windows screen res, full screen it then revert to windowed mode. VMware doesn't restore my original resolution when I do this :P Then whenever I want to go back I do the process again, choosing the resolution I want. There should be other applications that do this (Doom3 also does this for me).

Also screen resolution on K control panel has no effect for me. On a side note, I've been using KDE 3.5 with breezy (installed from kde repos) but never had this problem.

---

### Post by njf on 2006-05-01
Try [http://kubuntuforums.net/forums/index.php?topic=4373.msg17167#msg17167](http://kubuntuforums.net/forums/index.php?topic=4373.msg17167#msg17167)

---

