---
title: "Hi everybody!I'm [BAD]Ravenio and I've got a big problem."
date: 2009-04-30
forum: General Help
---

### Post by [BAD]Ravenio on 2009-04-30
Hi everybody,this is my first post,and I already have to ask for help ;_;

Well,today I make trouble with nvidia drivers,i mean:I started with 180.44 drivers,then I wanted to put 180.51 drivers,so i did all the work without envy,and it asked me for some strange things,like updating kernel or something similar.Unluckly,180.51 didn't work,so I put 180.44 again as in-use-drivers.What's wrong are you saying?Well,games like Neverwinter Nights and Urban Terror don't work more,and I don't know why.Trying to run urban terror I received this error:

```
Sys_Error: GLimp_Init() - could not load OpenGL subsystem
```I use ubuntu 9.04,and I need help.Please,this is my first post,do not ignore me please,I'm desperated!;_;

---

### Post by Polygon on 2009-04-30
it seems that you borked something and now you do not get direct rendering

you can confirm this by running the command

glxinfo | grep direct

that will return yes , but most likely in your case it will say no (as in you do not have direct 3d rendering).

so, what you should do (first at least) is go to the restricted driver manager again, and then uninstall the nvidia drivers, usually by clicking the nvidia entry and click 'remove'

wait for it to finish and then restart your computer

then, go back to the restricted driver manager, and enable the nvidia drivers, wait for it to finish, then restart your computer again

if all goes well, then you should have 3d rendering again, if not, post here.

---

### Post by [BAD]Ravenio on 2009-04-30
Up!Please help me ;_;
At least teach me how to re-install the kernel.

---

### Post by [BAD]Ravenio on 2009-04-30
Man,you were right.
```
mattia@Raven:~$ glxinfo | grep direct
Error: couldn't find RGB GLX visual or fbconfig

```

Now I try on removing drivers,rebooting,reinstall drivers and reboot.I will ask you if it will not work ;)

---

### Post by [BAD]Ravenio on 2009-05-01
Hi!Yesterday I've tryied on doing what you said,but it still don't work ;_;.If I type glxgears,I get this error:

```
mattia@Raven:~$ glxgears
Error: couldn't get an RGB, Double-buffered visual

```

---

