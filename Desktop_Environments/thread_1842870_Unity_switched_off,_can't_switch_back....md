---
title: "Unity switched off, can't switch back..."
date: 2011-09-12
forum: Desktop Environments
---

### Post by muddi900 on 2011-09-12
Hello,

On my latest log-in, ubuntu threw "Your machine is not capable of handling Unity..." and switched to gnome2. How do I switch back? I tried switching to classic and back again in the login settings but it didn't work. What should I do?

Thanks.

---

### Post by 2F4U on 2011-09-12
I guess you had Unity running before, so the question is, what changed since or in the last successful Unity session. Did you, for example, install graphics drivers or software updates?

---

### Post by muddi900 on 2011-09-12
Nothing. I didn't even do any other application updates. I did install a bunch of NES emulators.

---

### Post by JM68 on 2011-09-12
Unity is like Microsoft's Vista! I really hate it! never ever seen that unusable UI than Unity.

Unity lovers should have their own distro UbuntuFlop and leave Gnome as Ubuntu.

---

### Post by muddi900 on 2011-09-12
> **JM68 said:**
> Unity is like Microsoft's Vista! I really hate it! never ever seen that unusable UI than Unity.

Unity lovers should have their own distro UbuntuFlop and leave Gnome as Ubuntu.
NOOO ur mom!:p

Seriously dude, no need for this!

---

### Post by raja.genupula on 2011-09-12
hmm ok login with ubuntu(not classic )
do this 

```
unity --reset
```
please let me know what  you got .

---

### Post by muddi900 on 2011-09-12
> **raja.genupula said:**
> hmm ok login with ubuntu(not classic )
do this 

```
unity --reset
```
please let me know what  you got .
this.

```
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXCreateContext failed
Compiz (bailer) - Info: Ensuring a shell for your session
mudassir@mudassir-laptop:~$ Cannot register the panel shell: there is already one running.

```

That is where it stops

---

### Post by raja.genupula on 2011-09-12
type ```
ccsm
``` in terminal and look that ubuntu unity plugin enabled or not .

---

### Post by muddi900 on 2011-09-12
unity plugin is enabled.

---

### Post by raja.genupula on 2011-09-12
re-install the unity from synaptic

---

### Post by muddi900 on 2011-09-15
Sorry for the late reply, but I disabled and enabled it and then reinstalled it and it didn't work.

---

### Post by raja.genupula on 2011-09-15
sorry man,  then only one solution i have with me , install ubuntu-desktop```

sudo apt-get install ubuntu-desktop
```

or wait for experts , i hope they gonna help you  with your issue .

---

