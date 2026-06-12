---
title: "Panels Dissapeared!"
date: 2009-03-03
forum: General Help
---

### Post by mulluysavage on 2009-03-03
Hi, 

My panels have dissapeared and I'm wondering what to do! I had to force quit Banshee after it froze and pegged one of my cores at 100% for quite a while. Then when I restarted, my panels were gone. It's tough for me to get at anything now like software or open windows. Please help! Thanks.

Mythbuntu 8.04 LTS

---

### Post by onero on 2009-03-03
Have you tried manually running gnome-panel from the terminal? If it still doesn't appear, is there any error output? I haven't used Mythbuntu, but on stock Ubuntu Alt+F1 will popup the Applications Menu and Alt+F2 will show the Run window, so you can launch programs from there.

---

### Post by mulluysavage on 2009-03-03
I found that gnome-panels was not installed so I installed it. It did not help.

Then I realized that I was on xfce so I did xfce4-panels as instructed in [this thread.]("http://ubuntuforums.org/showthread.php?t=707979&highlight=panels+dissapeared") 

Alt-F1 shows help, not apps - does anyone know the keystroke for apps on xfce?

Should I uninstall gnome-panels? Is that going to screw me up? How would I do that?

I added xfce4-panels to my startup program which brings up my panels now on startup.

---

### Post by nzadLithium on 2009-03-04
It shouldn't screw anything up to leave gnome-panels installed, just a bit of waste of hard disk space if you aren't using them. If your concerned about that you can remove via synaptic:
find gnome-panel in list, right click select mark for removal.

via terminal:
sudo apt-get remove gnome-panel

---

