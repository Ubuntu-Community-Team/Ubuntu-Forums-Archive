---
title: "Set workspaces with gconf-editor?"
date: 2009-11-01
forum: Desktop Environments
---

### Post by irishbreakfast on 2009-11-01
I know I can change the number of workspaces by right-cliking on a workspace in the panel.

But can I do it with gconf-editor? I found an occurance of 
num_workspaces with a value of 2, I changed it to 4. But no change occurred.

I'm using 9.10.
Thanx

---

### Post by pastalavista on 2009-11-01
When you make changes in gconf, usually you need to log off and back on before they take effect... or at least restart gdm.

---

### Post by irishbreakfast on 2009-11-01
Please, will you provide the command for restarting gdm
Cheers

---

### Post by mcduck on 2009-11-02
> **pastalavista said:**
> When you make changes in gconf, usually you need to log off and back on before they take effect... or at least restart gdm.

Actually gconf should make the changes immediately as soon as you change any setting. And that should work for most (or all?) apps, at least I've never seen one where gconf settings wouldn't have worked immediately.

For the original problem, where did you do the change, and are you using Compiz or not?

If you use Metacity, the setting is in *apps/metacity/general/num_workspaces*, for Compiz it's *apps/compiz/general/screen0/options/hsize*.

(and the command to restart GDM (in 9.10) is "sudo restart gdm". But you really shouldn't need it for any gconf changes. Even if the settings wouldn't work as soon as you change them, simply logging out and back again should be enough...)

---

### Post by irishbreakfast on 2009-11-02
mcduck, thanks for the wee lesson

I used gconf-editor and searched for num_workspaces, because that is what they are called when right clicking. 
Clearly I am using compiz and have more to learn about it.

---

