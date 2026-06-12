---
title: "plugins for beryl???"
date: 2007-06-18
forum: Desktop Effects &amp; Customization
---

### Post by Irti on 2007-06-18
are there any more plugins for beryl apart from the emerald theme manager???? where ca n i download those plugins from..........

---

### Post by insert_name_here on 2007-06-18
The plugins come with the main beryl package.  They are accessible from beryl manager - they are things like cube effect, water effect, etc.  SVN versions of Beryl will have difference plugins (for example, this past winter, there was a snow plugin that never made it into the stable versions)

---

### Post by madcow72 on 2007-06-18
Do:  ```
sudo aptitude search beryl-plugins
``` and then install whatever looks good.  You'll find something like:
```
i A beryl-plugins                   - Collection of plugins for Beryl           
i A beryl-plugins-data              - Plugins data - Beryl Project              
p   beryl-plugins-dbg               - Collection of plugins for Beryl, debug ver
p   beryl-plugins-unsupported       - Collection of extra plugins for Beryl     
p   beryl-plugins-unsupported-data  - Unsupported Plugins Data                  
p   beryl-plugins-unsupported-dbg   - Collection of plugins for Beryl, debug ver
```
The "i" says that a package is already installed, the "p" means it is not.

---

