---
title: "Hot corners for Ubuntu Budgie"
date: 2017-04-08
forum: Desktop Environments
---

### Post by geovino on 2017-04-08
I've installed Ubuntu Budgie 16.04 and I really like the budgie desktop. Is there a way to add hot corners like you can in unity tweaks? or not?

---

### Post by davidmohammed on 2017-04-08
yes  - just install brightside - you can then configure what you want to-do for each corner of the desktop

---

### Post by RobGoss on 2017-04-08
Hello and welcome to the forum, Try installing **Unity tweak tool**, from the Ubuntu repository you can enable **Hot corners **using this tool, just follow the link [https://apps.ubuntu.com/cat/applications/unity-tweak-tool/](https://apps.ubuntu.com/cat/applications/unity-tweak-tool/)

Best of luck

---

### Post by geovino on 2017-04-08
> **RobGoss said:**
> Hello and welcome to the forum, Try installing **Unity tweak tool**, from the Ubuntu repository you can enable **Hot corners **using this tool, just follow the link [https://apps.ubuntu.com/cat/applications/unity-tweak-tool/](https://apps.ubuntu.com/cat/applications/unity-tweak-tool/)

Best of luck

Don't think that Unity Tweak tool will work with Budgie

---

### Post by geovino on 2017-04-08
Installed Brightside but it doesn't show up in the program list. 

So far nothing is working. Any other ideas?

---

### Post by vasa1 on 2017-04-09
> **geovino said:**
> Installed Brightside but it doesn't show up in the program list. 

So far nothing is working. Any other ideas?

Have you tried```
brightside
```in a terminal?

According to [http://ubuntuhandbook.org/index.php/2015/03/enable-hot-corners-xfce-desktop/](http://ubuntuhandbook.org/index.php/2015/03/enable-hot-corners-xfce-desktop/), you may first have to run```
brightside-properties
```

Also, read [http://www.webupd8.org/2011/04/set-up-hot-corners-edge-flipping-in.html](http://www.webupd8.org/2011/04/set-up-hot-corners-edge-flipping-in.html). From there:> Once installed, you won't find a menu entry to launch Brightside so either press ALT + F2 or open a terminal and type: "brightside-properties" to launch the Brightside configuration. If you plan on using it, add "brightside" (not "brightside-properties") to your Startup Applications - in Ubuntu 10.10 and older, go to System > Preferences > Startup Applications, click "Add" and under "Command", enter "brightside".

---

### Post by geovino on 2017-04-09
I get this...

```
[CODE]davek@HP6200:~$ brightside-properties
Gtk-Message: Failed to load module "canberra-gtk-module"
```[/CODE]

program does open but there's no option to show all windows. 

What's DPMS?

---

### Post by vasa1 on 2017-04-09
When I Googled for DPMS I found that it stands for "Display Power Management Signaling". As for your other queries, not a clue. I don't use bright-side but, again, Googling for "Failed to load module "canberra-gtk-module"" gave several hits. Maybe you can do the same and find something appropriate for your situation.

---

### Post by geovino on 2017-04-09
Thanks for the help. Brightside doesn't do the job, I'll skip trying to get hot corners in Budgie, maybe one day someone will add it to settings.

---

### Post by davidmohammed on 2017-04-09
> **geovino said:**
> I get this...

```
[CODE]davek@HP6200:~$ brightside-properties
Gtk-Message: Failed to load module "canberra-gtk-module"
```[/CODE]

program does open but there's no option to show all windows. 

What's DPMS?

ok - you want to show all windows in a spread when navigating to a corner?

simple - install skippy-xd (via budgie-welcome recommendations).

Then for the hotcorner that you want the command is simply skippy-xd-toggle

---

### Post by geovino on 2017-04-09
It's installed but its not opening to configure...

```
davek@HP6200:~$ skippy-xd
wm_check(): Your WM looks EWMH compliant.
main(): running once then quitting...
wm_get_stack_sub(): Retrieved window stack from _NET_CLIENT_LIST.
[     0.02 ] error 8 (BadMatch) request 42 minor 0 serial 290 ("BadMatch (invalid parameter attributes)")
clientwin_handle(): KeyRelease 36 (Return) ignored.
davek@HP6200:~$ 


```

skippy needs work ;)

---

