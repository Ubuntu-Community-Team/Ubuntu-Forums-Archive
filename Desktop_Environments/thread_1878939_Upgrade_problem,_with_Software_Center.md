---
title: "Upgrade problem, with Software Center"
date: 2011-11-10
forum: Desktop Environments
---

### Post by alquimista on 2011-11-10
Hi,

I installed Ubuntu 10.04 and then upgraded to 10.10

When installing or uninistalling software, I get this error in the software center:


> installArchives() failed: /var/cache/apt/archives /
/
Id desconocido: 1000
No protocol specified

(zenity:4665): Gtk-WARNING **: cannot open display: :0.0
Id desconocido: 1000


I cheked other posts, and similar errors are related to installed fonts; I tryed those solutions, and didn't work. Any ideas on this one?

Thank you

---

### Post by agreimann on 2011-11-10
You could try to follow these steps to solve the problem:

- Press Alt+F2 (any desktop environment), type **gksudo gnome-terminal** and press enter. Alternatively, you may have lxterminal, xfce4-terminal, or xterm, for instance, installed as there are several.
- Type in your password when prompted.
- Type in **apt-get clean** and press enter. Type **apt-get purge** and press enter. Finally, type **apt-get update** to refresh the package list.
- Check if any dependency errors, for instance, spit out. If that is the case, you can do **apt-get install -f** to try and fix those.
- Try re-installing zenity. Do **apt-get remove zenity && apt-get install zenity** to do a quick version of that. While this isn't the most efficient method, it may help out in this case.

Software Center should work. If not, try to use a traditional program, like aptitude-gtk or the recently retired but reliable synaptic program. If you know how to use apt directly with the command line, doing a simple **apt-get install** should work.

---

### Post by alquimista on 2011-11-11
Hi agreimann,

I did what you suggested; I ran Synaptic, and now I get the error in the attached file. 

It is related to ocdc-lotus-upgradefix

When I was upgrading to 10.10, I recall receiving an error related to the  upgrade the Lotus Notes installation. Woud there be something there, preventing to install/uninstall the rest of the software?

---

### Post by agreimann on 2011-11-12
Using **apt-get install -f** should help fix dependencies or a software package that has failed to install in the past. A bad installation in the past can potentially clog the installation process in the future.

If apt-get does not get to the root of the problem, try using Synaptic. Press Alt+F2 (any desktop environment), type **gksudo synaptic** and press enter. In the sidebar, there will be a few buttons. I'm not sure what locale your system is using (my apologies), however, in English these read in the lower, left hand corner of the window's sidebar, from top to bottom "Sections", "Status", "Origin", "Custom Filters", and "Search Results". Click "Custom Filters". Click "Broken" in the list widget in the sidebar (it will also show "**All**" in bold, for instance. Resolve any packages that have been previously broken. They should be marked in red. Re-installing the packages listed here should be enough to fix the problem. The main issue, however, is that if not, then this may take more time, as linked packages to that package (dependencies) may themselves need to be reinstalled, which is a pain, but it has happened to me in the past. After that, the stopped up package should install, allowing new packages' installation processes to flow smoothly. 

I hope that this helps with your dilemma. Regards.

---

### Post by alquimista on 2011-12-05
Hi,

I solved the problem... well, was a fix yet not the ideal:

I found in /etc/apt/apt.conf.d the file "01oc-lotus-upgrade-fix" that had this as contents:
"#DPkg::Pre-Install-Pkgs {"/usr//bin/ocdc-lotus-upgrade-fix ";};"

The file "ocdc-lotus-upgrade-fix " did not exist anywhere ...so I just deleted the file 01oc-lotus-upgrade-fix, and now updates are working just fine. Maybe a bug in the Lotus Notes installer?

Regards,
Alquimista

---

