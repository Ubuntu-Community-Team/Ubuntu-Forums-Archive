---
title: "No titlebar on windows with Desktop Effects on Feisty with Nvidia"
date: 2007-04-23
forum: Desktop Effects &amp; Customization
---

### Post by patik on 2007-04-23
I've got a clean Feisty install and I installed the nvidia driver using envy. It's an AMD64 but I'm running Ubuntu in 32-bit. I haven't installed Beryl or anything related and I'm using the default Human theme in Gnome.

When I turn on the Desktop Effects they work -- the windows wobble and all that. However, the title bar (top of the window where the window title, close and minimize buttons are) disappears from all windows. It comes back when I turn off the effects. There's no crashing or instability, it just doesn't show the title bar.

How can I fix this?

---

### Post by umattu on 2007-04-23
There is some lines that you need to add into your xorg.conf file under the "devices" section I will post them ASAP let me find em.

Here are the lines you need to add.

append the following to your /etc/X11/xorg.conf in the &#8220;Device&#8221; section:

Option         "AddARGBGLXVisuals" "True"
Option         "RenderAccel" "True"
Option         "AllowGLXWithComposite" "True"
Option         "backingstore" "True"
Option         "TripleBuffer" "True"

I had this same issue. I found this info in a Beryl link but it worked for me.

---

### Post by Ozor Mox on 2007-04-23
Are these options specific to Nvidia cards? I have the no titlebar problem with an ATI card and adding these lines didn't help. Any ideas?

---

### Post by SL666 on 2007-04-23
This worked perfectly on my nvidia on AMD 64 (im running the 32bit install of ubuntu though) to fix the titlebar issue with desktop effects, it also works with beryl.

Cheers Steve.

---

### Post by Yuzem on 2007-04-23
You can try this:

```
metacity --replace&
sudo killall emerald
```

Then enable Desktop Effects
If it works go to Preferences > Sessions > Startup programs
Uncheck emerald

---

### Post by umattu on 2007-04-23
> **Ozor Mox said:**
> Are these options specific to Nvidia cards? I have the no titlebar problem with an ATI card and adding these lines didn't help. Any ideas?

Not sure on that one, you could always backup your xorg.conf and give it a try. If it doesnt work restore the original.

---

### Post by patik on 2007-04-24
> **umattu said:**
> append the following to your /etc/X11/xorg.conf in the “Device” section:

Option         "AddARGBGLXVisuals" "True"
Option         "RenderAccel" "True"
Option         "AllowGLXWithComposite" "True"
Option         "backingstore" "True"
Option         "TripleBuffer" "True"
That worked great, thanks a lot!

---

### Post by Ozor Mox on 2007-04-24
> **umattu said:**
> Not sure on that one, you could always backup your xorg.conf and give it a try. If it doesnt work restore the original.

I tried this and added all the required lines but it didn't fix the problem unfortunately. If anyone has a solution for ATI cards please post it :(

---

### Post by hyperair on 2007-04-24
You could manually run the window decorator. Press alt+f2 to bring up the run dialog, and type "gtk-window-decorator --replace" without the quotes.

---

### Post by cerberos on 2007-04-25
I have no title bars with working wobble/cube etc. It appears that emerald just doesn't want to run for me. When I run it from the console nothing happens, no output no nothing. I've attempted all the fixes I've found, but I can't get it working. Does anyone have any ideas? Is there somewhere I can see why emerald doesn't seem to be doing anything?

---

### Post by hyperair on 2007-04-25
Are you running Compiz or Beryl? Emerald only works with Beryl.

---

### Post by cerberos on 2007-04-25
I've tried to use both with the same error on both.

---

### Post by henriquemaia on 2007-04-25
> **umattu said:**
> There is some lines that you need to add into your xorg.conf file under the "devices" section I will post them ASAP let me find em.

Here are the lines you need to add.

append the following to your /etc/X11/xorg.conf in the “Device” section:

Option         "AddARGBGLXVisuals" "True"
Option         "RenderAccel" "True"
Option         "AllowGLXWithComposite" "True"
Option         "backingstore" "True"
Option         "TripleBuffer" "True"

I had this same issue. I found this info in a Beryl link but it worked for me.
  
Another happy user with your workaround. Thanks a lot for this help.

---

### Post by Yuzem on 2007-04-25
Try this:

```
gtk-window-decorator --replace&
compiz --replace&
```

---

### Post by cerberos on 2007-04-25
> **Yuzem said:**
> Try this:

```
gtk-window-decorator --replace
compiz --replace
```

switched to compiz (via beryl-manager)
attempted first command, waited some time with 0 output so killed it and ran it with & (does this indicate that something is broken?)
second command (also using &) gives this output:
 /usr/bin/compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
inotify_add_watch: No such file or directory


hrm, attempting to see if I need to add a 32bit option to xorg.conf

---

### Post by cerberos on 2007-04-25
found my fix, xorg.conf was set to default 16bit, changed to 24 bit and everything worked.

---

### Post by Yuzem on 2007-04-25
Sorry, it was wrong...
It is:
```
gtk-window-decorator --replace&
compiz --replace&
```

But it is better to do alt+F2 and insert:
gtk-window-decorator --replace
Alt+F2 again and:
compiz --replace

You can also set 24bit from the command line:
```
sudo nvidia-xconfig --add-argb-glx-visuals --depth=24
```

---

### Post by xchric on 2007-04-27
> **henriquemaia said:**
> Another happy user with your workaround. Thanks a lot for this help.

Yeah, I got the issue solved
thank you a lot!!

---

