---
title: "Compiz Help!"
date: 2007-01-04
forum: Desktop Environments
---

### Post by Lucas0607 on 2007-01-04
I get this error when I start compiz... when I type compiz-tray-icon in terminal.

(compiz-tray-icon:9414): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:9414): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(compiz-tray-icon:9414): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:9414): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed


And when I close this particular terminal window, the borders dissapear.
Could this be related to the failed sudo apt-get install with a package from gandalfn I think it's the compiz-freedesktop gnome saying

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
****
Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-freedesktop-gnome: Depends: compiz-freedesktop (= 0.2.2-0gandalfn1) but 1:0.3.6-0gandalfn3 is to be installed
E: Broken packages

***************

I have loads of questions here as I am new to linux and this is my first day using ubuntu (thank god I got compiz working without anything bad happening)
So I'm using a Nvidia 5500 videocard , I got drivers installed and all, but is it really like this with linux? Like screen resolution isn't optimum. Unlike in windows I get to 1440x900 but here it get to 1280x960 wich is just bad. It isn't clear at all and refresh rate is only up to 51 hz.
How do I get this running to its optimum performance?

Help Please... Thank you guys!

---

### Post by Lem on 2007-01-04
The gandalfn repo is shot at the moment - it's got part 0.22 and part 0.36 debs in it. It's blown my compiz too - Hopefully it will be fixed soon!

---

### Post by Lem on 2007-01-05
Fixed - Gandalfn repo and Compiz install information - [http://forum.go-compiz.org/viewtopic.php?t=360&highlight=gandalfn](http://forum.go-compiz.org/viewtopic.php?t=360&highlight=gandalfn)

---

