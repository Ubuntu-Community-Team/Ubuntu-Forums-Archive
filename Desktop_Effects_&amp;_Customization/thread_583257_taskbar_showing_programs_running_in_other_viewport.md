---
title: "taskbar showing programs running in other viewports in gutsy"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by edsadr on 2007-10-20
Hello

some updates ago my taskbar is showing programs running in other viewports, I am using gutsy with all updates and compiz with windows preview plugin with the option "Taskbar shows only windows of current viewport" enabled, but I still see programs running in the other views.

I already tried to disable the plugin and configure the window list option to show only windows in the current workspace and the problem persist.

Thank you

---

### Post by sarutv on 2007-10-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/151343/](https://bugs.launchpad.net/ubuntu/+bug/151343/) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I had the same problem, this is not a bug per se, more like a misconfiguration. To fix this install 'compizconfig-settings-manager', then choose **System -> Preferences -> Advanced Desktop Effects Settings**. In the Compiz Settings Manager, select "**General Options**" and goto "**Desktop Size**". Set the "*Horizontal Virtual Size*" to 4 (or how many ever desktops you want) and set the "*Number of Desktops*" to 1.

Now the taskbar functions as expected and shows only the windows that are visible in the current workspace.

---

### Post by edsadr on 2007-10-21
Man you are right, thank you very much for your answer, this problem was a head ache for me and your answer solve it

thank you again

---

