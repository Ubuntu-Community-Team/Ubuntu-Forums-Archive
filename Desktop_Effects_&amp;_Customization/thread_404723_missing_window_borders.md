---
title: "missing window borders"
date: 2007-04-08
forum: Desktop Effects &amp; Customization
---

### Post by Donhu on 2007-04-08
i am using beryl and have lost my window borders, could someone please tell me the command to restore my window borders in emerald?

---

### Post by ComplexNumber on 2007-04-08
> **Donhu said:**
> i am using beryl and have lost my window borders, could someone please tell me the command to restore my window borders in emerald?
you mention that you've lost them, which means that you had them before, right? if so, what did you do thats significant inbetween when you had them and now?

---

### Post by Donhu on 2007-04-08
i had them, before i installed beryl, but someone told me this:

> **Happy_Man said:**
> Rember to add "emerald --replace" otherwise you won't have window borders! :D

but he didnt finish explaing to me how to do that

---

### Post by ComplexNumber on 2007-04-08
i imagine that it only happens when you first login in. if your right click on the ruby icon in the notification area, then revert back to metacity, then select beryl window manager again, your window borders will return, right?

btw both metacity and beryl are window managers. metacity is what controls your window borders by default in gnome. when you install and run beryl, you can switch between metacity and beryl.

---

### Post by Donhu on 2007-04-08
i dont even see any ruby icon anywhere, what notification area are u referring to?

---

### Post by Rab22 on 2007-04-08
I have been having a similar problem.  When I try using Beryl's window manager I lose the borders so I cannot move/resize the window.  However, Emerald works fine (desktop cube and such works). 

I can swtich back to Metacity just fine...

I have tried removing the beryl setting files under ~/.beryl to no avail. 

Anyone have any ideas?

Thanks

---

### Post by Donhu on 2007-04-08
> **Happy_Man said:**
> Rember to add "emerald --replace" otherwise you won't have window borders! :D

someone told me this...havent get to try it cuz i dont kno wat to add emerald --replace to...give it a shot and if it works for you...lemme kno how u did it

---

### Post by Eigenwert on 2007-04-09
Could you post your xorg.conf file? If I can get a look at that, maybe I might be able to help you out.

EW

---

### Post by lukew on 2007-04-09
I had this problem.

I used the instructions on the UDSF site. It turns out there are two sets of instructions; the one I used missed a small section which the following URL gave.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)

Basically I needed to do this bit:

 ```
   * Back up xorg.conf 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
gksudo gedit /etc/X11/xorg.conf

    * Add this to xorg.conf "Screen" section 

# Enable 32-bit ARGB GLX Visuals
    Option "AddARGBGLXVisuals" "True"

# If you are using an older version of compiz that
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
    Option "DisableGLXRootClipping" "True"

    * Add this to xorg.conf "Device" section 

Option          "TripleBuffer" "true"

```


Without this bit Beryl worked but I did not have window decorations (max/min etc) and I could not change theme and terminals would not display correctly.

---

### Post by lukew on 2007-04-09
> **Donhu said:**
> someone told me this...havent get to try it cuz i dont kno wat to add emerald --replace to...give it a shot and if it works for you...lemme kno how u did it

The reference was to add it as a startup procedure in the session.

System --> Preferences --> Sessions (Off the top of my head I think it is here?)

Luke

---

### Post by thedarkharlequin on 2007-04-17
I had this same problem, and followed what it said in this thread.  and for a second I thought I was saved, but no.  now if a window is already open and I start beryl I get my correct emerald borders and such.  but once emerald is started, any window opened after that does not have a menu bar.  just a VERY slight fading effect around the edges like it's trying.
Then when i return to metacity, all windows that did not have menu bars in beryl also do not have menu bars in metacity, I have to close and reopen them.

what am I missing.

running edgy 6.1 with an nvidia 6600 and dual monitors

when I run "emerald --replace"  emerald sort of restarts, but the terminal displays this

```


me@home:~S emerald --replace

(emerald:18184): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:18184): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:18184): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:18184): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:18184): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:18184): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:18184): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:18184): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:18184): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:18184): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:18184): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:18184): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:18184): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:18184): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:18184): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:18184): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

```

---

