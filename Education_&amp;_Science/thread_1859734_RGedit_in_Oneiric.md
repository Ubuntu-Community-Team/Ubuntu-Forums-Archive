---
title: "RGedit in Oneiric"
date: 2011-10-14
forum: Education &amp; Science
---

### Post by AntoineT on 2011-10-14
Hi,

I'm having trouble making RGedit work in Oneiric. I have installed gedit-r-plugin from the software center. It installs gedit-r-plugin 0.7.0.2-1 (which is old) ; but the plugin would not show up in Gedit3.

After removing the package, I have downloaded rgedit v0.7.1.0-Gtk3 from the website and installed by following the instructions. The pluging now shows up and I can activate it. The icons appear in Gedit, but won't work. [COLOR=Black][]("http://sourceforge.net/projects/rgedit/files/rgedit-0.7.1.0-Gtk3.tar.bz2/download") [/COLOR]The traceback shows the following error when trying to open an R tab:
Traceback (most recent call last):
  File "/home/antoine/.local/share/gedit/plugins/RCtrl.py", line 2073, in on_create_new_R_tab
    self.createRGeditTerminal()
  File "/home/antoine/.local/share/gedit/plugins/RCtrl.py", line 2448, in createRGeditTerminal
    self.R_widget = RGeditTerminal(self._plugin)
  File "/home/antoine/.local/share/gedit/plugins/RCtrl.py", line 221, in __init__
    self.reconfigure_vte(self._vte,1)
  File "/home/antoine/.local/share/gedit/plugins/RCtrl.py", line 301, in reconfigure_vte
    _vteN.set_colors(fg[1], bg[1], palette)
TypeError: 'Color' object does not support indexing

Has anyone managed to make it work?

---

### Post by arnehe on 2011-10-17
The same problem occurs with the lastest version of RGedit:

[https://sourceforge.net/projects/rgedit/forums/forum/993860/topic/4759138](https://sourceforge.net/projects/rgedit/forums/forum/993860/topic/4759138)

---

### Post by vincegata on 2011-10-17
Same is here. I used these instructions so the plugin will show up on the plugins list in GEdit:

[http://askubuntu.com/questions/61785/how-do-i-install-a-plugin-for-gedit-v3](http://askubuntu.com/questions/61785/how-do-i-install-a-plugin-for-gedit-v3)

however, once I select the checkbox to activate plugin GEdit shuts down.

Any help please!

---

### Post by mhane on 2011-10-19
Hello,

Thanks to Dan Dediu, there is a new version of rgedit ([http://sourceforge.net/projects/rgedit/forums/forum/993860/topic/4759138](http://sourceforge.net/projects/rgedit/forums/forum/993860/topic/4759138)) running in Ubuntu 11.10. Be aware of a new plugin folder in gedit 3 ([http://askubuntu.com/questions/61785/how-do-i-install-a-plugin-for-gedit-v3](http://askubuntu.com/questions/61785/how-do-i-install-a-plugin-for-gedit-v3)).

martin

---

### Post by AntoineT on 2011-10-20
> **mhane said:**
> Hello,

Thanks to Dan Dediu, there is a new version of rgedit ([http://sourceforge.net/projects/rgedit/forums/forum/993860/topic/4759138](http://sourceforge.net/projects/rgedit/forums/forum/993860/topic/4759138)) running in Ubuntu 11.10. Be aware of a new plugin folder in gedit 3 ([http://askubuntu.com/questions/61785/how-do-i-install-a-plugin-for-gedit-v3](http://askubuntu.com/questions/61785/how-do-i-install-a-plugin-for-gedit-v3)).

martin

Yes, I had followed the discussion in the rgedit forum. Everything now works fine. I have added a comment to the bug I filed in launchpad ([https://bugs.launchpad.net/ubuntu/+source/gedit-r-plugin/+bug/874064](https://bugs.launchpad.net/ubuntu/+source/gedit-r-plugin/+bug/874064) )

---

### Post by jrkrideau on 2012-04-30
Any news on what's happening  here?  I am a complete newbie as far as Linux goes and while I was able to get Rgedit to work on a WUBI installation as of last year I cannot seem to install it correctly now although the command
 apt-get install gedit-r-plugin
returns a message that it is already installed and is up to date!

The gedit-plugin folder in usr/lib is not showing the files and my clumsy attempt to copy the files to it using a gui approach just give me a message about not having permission to copy into it.

Is the any way to do this by terminal?  I should point out I have not used a command line interface for an OS since DOS 3.x or an early Unix.

Any advice is welcome.

---

