---
title: "kcontrol: Administrator mode (crash)"
date: 2005-06-25
forum: Desktop Environments
---

### Post by wdso on 2005-06-25
I can no longer switch to Administrator mode in kcontrol. After entering the password, the module crashes and I see the default kcontrol page.
Running sudo kcmshell (... using the commando from the password popup) from konsole works fine.

I've updated to KDE 3.4.1. Has anyone experienced this?

---

### Post by tlaloczint on 2005-06-26
[QUOTE=wdso]I can no longer switch to Administrator mode in kcontrol. After entering the password, the module crashes and I see the default kcontrol page.
Running sudo kcmshell (... using the commando from the password popup) from konsole works fine.

I've updated to KDE 3.4.1. Has anyone experienced this?[/QUOTE]

I do, I just figure it out today when I was tring to auto login it din`dt take me to the administrator just keep keep taking me to control page as you describe I am still looking for anwers in the forum if I find some I `ll let you know

---

### Post by Xian on 2005-06-26
I am not aware of a fix for this. 
The workaround is to open kcontrol as admin.

```
$ kdesu kcontrol
```

---

### Post by wdso on 2005-06-26
Has someone already filed a bug report for this? If not, whats the address of ubuntus bugreport site? This is a showstopper bug!

---

### Post by Xian on 2005-06-26
[QUOTE=wdso]Has someone already filed a bug report for this? If not, whats the address of ubuntus bugreport site? This is a showstopper bug![/QUOTE]
It's been well documented. 
Here's the Ubuntu bug site: [Bugzilla Main Page](https://bugzilla.ubuntu.com/)

---

### Post by Feanor on 2005-06-29
[QUOTE=wdso]I can no longer switch to Administrator mode in kcontrol. After entering the password, the module crashes and I see the default kcontrol page.
Running sudo kcmshell (... using the commando from the password popup) from konsole works fine.

I've updated to KDE 3.4.1. Has anyone experienced this?[/QUOTE]

I've the same problem, but if you reinstall kcontrol from synaptic (or kynaptic) and then you open kcontrol, it works fine. But if you reboot the system after reinstall, it will no longer works. It's a boring bug...  ](*,)

---

