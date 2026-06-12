---
title: "Desktop environment choice can or not influence app compatibility"
date: 2018-12-25
forum: Desktop Environments
---

### Post by davide445 on 2018-12-25
New to Ubuntu and Linux, will install my first distro in a few days on my new PC.
Wondering if choosing a DE or another (i.e. GNOME or Budgie) can result in any compatibility issue with prototyping framework such as Python or Machine Learning libraries or as GUI didn't have anything to do with installing / maintaining applications.

---

### Post by SeijiSensei on 2018-12-25
Software like Python works the same on any Ubuntu flavor.  Most of what differentiates among the flavors is the desktop GUI.  

I don't know anything about "machine learning libraries," but if they're in the Ubuntu repositories they should work on all Ubuntu versions.  If you have more idiosyncratic needs, and the software is open-source, you can compile the source code.

---

### Post by davide445 on 2018-12-25
Thanks for sharing your experience.
To avoid installation troubles I'll probably install all the libraries as Docker images,that is asking for Ubuntu 18.04 for installation. I can suppose will work on any Ubuntu flavour of this version?
Another sw I want to install natively is Knime, I didn't find specific Linux requirements ([https://docs.knime.com/2018-12/analytics_platform_installation_guide/index.html](https://docs.knime.com/2018-12/analytics_platform_installation_guide/index.html)), and Orange3 where I also didn't find any specific installation on Ubuntu ([https://orange.biolab.si/download/linux/](https://orange.biolab.si/download/linux/)), also in these cases I can suppose any Ubuntu flavor will behave the same? There might be Gnome dependencies in packages or any application is GUI neutral.
Pardon my ignorance I really didn't know Linux (yet).

---

### Post by Tadaen_Sylvermane on 2018-12-25
Is one of the biggest strengths of Linux and open source. If it can compile, it can most likely run properly. We aren't tied into a specific environment to get things to work. The only thing that may not be perfect is the look of the gui window. GTK vs QT vs w/e else there is. Personally I wish there was a standard they all had to follow instead of having multiples types. They don't always match themes. Aside from that though, it will work. It wouldn't be in the repositories if it wouldn't.

---

### Post by davide445 on 2018-12-25
Compiling from source is the kind of activity I'm absolutely not skilled in doing. I hope is not required for this applications. 
Returning to the compatibility topic I find references is Knime to change Gnome configuration for working, and for Orange3 to install Pyqt5 package.
My interest lie with Budgie that is currently Gnome based, might I have problems with a package requiring Qt? And if as I read they will in the future migrate Budgie Desktop to Qt will I have problems with app requiring Gnome?

---

### Post by PerfMonk on 2018-12-25
Both WM are based on gnome.   Gnome has more fonctions and is more complex than budgie.  But both desktop are great desktops.  I have used both and didn't had any problems.  
If you want a lighter desktop budgie is a good choice.  I you want everything to works in a more integrated desktop gnome is a good choice.

That's  one great problem with linux : You have choice!

---

### Post by davide445 on 2018-12-26
Started also evaluating Kubuntu since appear to be a bit more used on the Machine Learning sector than Budgie.
Using KDE instead of Gnome will have any influence on the applications such as Knime or Orange3?
They need to be created with one or another DE as a target, or any DE will work?
Thanks for your patience.

---

### Post by liaata on 2018-12-28
Usually you can check it out at the developers website or ask the support if any compatibility problems may occur

---

