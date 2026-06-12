---
title: "openbox : run a program without window decorator &amp; stickify on all desktop?"
date: 2011-01-26
forum: Desktop Environments
---

### Post by garfonkee on 2011-01-26
Is it possible? I have a tool I want to keep open and without decorator (the window decorations etc) to start everytime I log in, and available in all workspaces. Is this doable?

---

### Post by urukrama on 2011-01-26
Yes, that is possible. You have to specify this in the <applications> section of your rc.xml (at the very bottom of that file). This will set Firefox maximized, without window decorations on all desktops:

```
application class="Firefox-bin">
      <desktop>all</desktop>
      <maximized>yes</maximized>
      <decor>no</decor>
    </application>
```

The trick is getting the class name right. You can do that by running the following in a terminal and then clicking on the application window you want to configure:

```
obxprop | grep "^_OB_APP"
```

You will need the value that is given in quotation marks after _OB_APP_CLASS in the terminal output.

For more info, have a look at the Openbox documentation: [http://openbox.org/wiki/Help:Applications](http://openbox.org/wiki/Help:Applications)

---

### Post by garfonkee on 2011-01-26
Worked like a charm! Thanks a lot!

edit: additional question : can those attributes be changed during run-time, (in particular, changing whether a window's on "above" layer, or "bottom" layer) outside of the rc.xml script?

---

### Post by urukrama on 2011-01-26
I'm not sure what exactly you are asking, but you can change the settings in your rc.xml after Openbox has started; they will take effect when you reconfigure Openbox (by running *openbox --reconfigure*, or by using the Reconfigure menu item). If you change the application settings in your rc.xml they will not affect your already running applications, until you reload them.

You can also bind the actions you specify (always on top or always on bottom) to a keybinding (or even a mousebinding if you prefer that). Have a look at the [documentation on Openbox actions ]("http://openbox.org/wiki/Help:Actions") and [keybindings]("http://openbox.org/wiki/Help:Bindings"). For example if you want to raise an application to the top layer with the keypress Windows key+t or make it normal when it is already on top, you would add the following to your rc.xml (in the <keybindings> section):

```
 <keybind key="W-t">
<action name="ToggleAlwaysOnTop"/>
</keybind>
```

To bind Windows key+l to lower the application, add the following:

```
<keybind key="W-l">
  <action name="ToggleAlwaysOnBottom"/>
</keybind>
```

Once you start using keybindings extensively, you'll realise the power of Openbox. I have my Openbox configured in such a way that I can manipulate (raise, lower, maximise, iconify, close, move around on the screen, move to another desktop, resize, etc.) my windows without having to use a mouse. I talk more elaborately about this here: [http://urukrama.wordpress.com/2008/07/22/my-openbox-keybindings/](http://urukrama.wordpress.com/2008/07/22/my-openbox-keybindings/)

---

