---
title: "Devilspie workstations don't work"
date: 2014-03-02
forum: Desktop Environments
---

### Post by nibal on 2014-03-02
I use ubuntu 12.04 LTS. Creating some startup windows and application. Read that devilspie can position them in the workspaces that I choose.
I use the following configuration file, devil.ds:

```
(if
 (is (application_name) "opera")
 (begin
 (set_workspace 2)
 (maximize)
 )
 )

(if
 (is (application_name) "qbittorrent")
 (begin
 (set_workspace 3)
 )
 )

(if
 (is (application_name) "clementine")
 (begin
 (set_workspace 4)
 )
 )

```

No matter what I do all windows appear on top of each other, in the first workspace :-(
There are not any useful logs or warnings and running it in debug mode just tells me that it has loaded 3 s-expressions.
Is there a problem with 12.04, or am I doing smt wrong?

TIA,
Nikos
I cannot find any usefule logs or warnings. Running it in debug mode, just tells me it reads 3 configurations.

---

### Post by Frogs Hair on 2014-03-02
You may have seen this . [https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)

---

### Post by nibal on 2014-03-03
> **Frogs Hair said:**
> You may have seen this . [https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)

No , I hadn't. Looking at it has an interesting example of a 3-window setup. Unfortunately, no workspaces or an indication if they work in 12.04 :-(

---

### Post by nibal on 2014-03-03
Forgot to mention that I use unity w/ compiz. Maybe devilspie has a problem with compiz.

---

### Post by Frogs Hair on 2014-03-03
If you have installed the CCSM and are using plugins it could possibly be a problem , but I have never used devilspie.

---

### Post by Toz on 2014-03-03
Make sure you have the application names correct. Alot of them are case-sensitive (usually the first letter capitalized). I unfortunately don't have any of those apps installed to check for you, but you can find the application's name by running:
```
xprop | grep ^WM_NAME
```
...then clicking on the application.

---

### Post by nibal on 2014-03-04
> **Toz said:**
> Make sure you have the application names correct. Alot of them are case-sensitive (usually the first letter capitalized). I unfortunately don't have any of those apps installed to check for you, but you can find the application's name by running:
```
xprop | grep ^WM_NAME
```
...then clicking on the application.

Thank you. That didn't solve the problem, but getting the application names correct at least gave me some progress:

Opera:

```

 $ xprop | grep ^WM_NAME
WM_NAME(STRING) = "[ubuntu] Devilspie workstations don't work - Opera"

```

Problem solved :-(
As for the rest putting in the correct names and running devilspie from the shell got me:

```

** (devilspie:11306): WARNING **: Workspace number 3 does not exist
(devilspie:11306): Wnck-CRITICAL **: wnck_window_move_to_workspace: assertion `WNCK_IS_WORKSPACE (space)' failed

** (devilspie:11306): WARNING **: Workspace number 4 does not exist

(devilspie:11306): Wnck-CRITICAL **: wnck_window_move_to_workspace: assertion `WNCK_IS_WORKSPACE (space)' failed

```

Seems like there is a problem with compiz workstations. I will take it up with devilspie forums and report results back here ;-)

---

### Post by nibal on 2014-03-04
Couldn't find devilspie forums, but a quick search in the Internet gave me the solution:

With Compiz, i have to use set_viewports instead of set_workspaces. Even Opera works ;-)

---

### Post by nibal on 2014-03-04
> **nibal said:**
> Couldn't find devilspie forums, but a quick search in the Internet gave me the solution:

With Compiz, i have to use set_viewports instead of set_workspaces. Even Opera works ;-)


devilspie rocks ;-)

---

