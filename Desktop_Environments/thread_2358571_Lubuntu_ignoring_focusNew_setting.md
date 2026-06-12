---
title: "Lubuntu ignoring focusNew setting"
date: 2017-04-14
forum: Desktop Environments
---

### Post by clepsdyrae on 2017-04-14
Thought I'd share this in case anyone else came across it:

In Lubuntu 16.10 I was attempting to use the focusNew configuration option in ~/.config/openbox/lubuntu-rc.xml to prevent focus stealing when new windows were opening, followed by an "openbox --reconfigure".

It worked in past versions of Lubuntu, but in 16.10 it was having no effect. Opening the GUI configuration manager showed that the setting was taking hold properly, but it still was being ignored: new windows took focus.

Then I found, wayyyyy at the end of the .xml file, the following:

<application class="*">
  <focus>yes</focus>
</application>

...which effectively overrides the focusNew setting, AFAICT. Setting that to "no" in addition to focusNew finally worked.

Is this a bug? Where to report, if so? EDIT: right above it is a comment that says "Lubuntu specific: focus all applications launched" so I suppose that's the place to report...

---

### Post by Paddy Landau on 2017-04-14
Thanks for sharing this.

---

### Post by clepsdyrae on 2017-04-14
You bet. Bug reported here: [https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/1682927](https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/1682927)

---

### Post by Paddy Landau on 2017-04-15
This must be new. I have 16.04, and there is no <application class> entry.

---

### Post by vasa1 on 2017-04-15
> **Paddy Landau said:**
> This must be new. I have 16.04, and there is no <application class> entry.

OP wrote:> It worked in past versions of Lubuntu, but in 16.10 it was having no effectSo it seems to have started in 16.10.

I never really looked at this in 16.04 or 14.04 because I don't mind the new application gaining focus.

Re. *there is no <application class> entry*, the last section of lubuntu-rc.xml _in Lubuntu 16.04_ has this```
  <applications>
    <!--
  # this is an example with comments through out. use these to make your
  # own rules, but without the comments of course.
  # you may use one or more of the name/class/role/title/type rules to specify
  # windows to match

  <application name="the window's _OB_APP_NAME property (see obxprop)"
              class="the window's _OB_APP_CLASS property (see obxprop)"
               role="the window's _OB_APP_ROLE property (see obxprop)"
              title="the window's _OB_APP_TITLE property (see obxprop)"
               type="the window's _OB_APP_TYPE property (see obxprop)..
                      (if unspecified, then it is 'dialog' for child windows)">
  # you may set only one of name/class/role/title/type, or you may use more
  # than one together to restrict your matches.

  # the name, class, role, and title use simple wildcard matching such as those
  # used by a shell. you can use * to match any characters and ? to match
  # any single character.

  # the type is one of: normal, dialog, splash, utility, menu, toolbar, dock,
  #    or desktop

  # when multiple rules match a window, they will all be applied, in the
  # order that they appear in this list


    # each rule element can be left out or set to 'default' to specify to not 
    # change that attribute of the window

    <decor>yes</decor>
    # enable or disable window decorations

    <shade>no</shade>
    # make the window shaded when it appears, or not

    <position force="no">
      # the position is only used if both an x and y coordinate are provided
      # (and not set to 'default')
      # when force is "yes", then the window will be placed here even if it
      # says you want it placed elsewhere.  this is to override buggy
      # applications who refuse to behave
      <x>center</x>
      # a number like 50, or 'center' to center on screen. use a negative number
      # to start from the right (or bottom for <y>), ie -50 is 50 pixels from the
      # right edge (or bottom).
      <y>200</y>
      <monitor>1</monitor>
      # specifies the monitor in a xinerama setup.
      # 1 is the first head, or 'mouse' for wherever the mouse is
    </position>

    <focus>yes</focus>
    # if the window should try be given focus when it appears. if this is set
    # to yes it doesn't guarantee the window will be given focus. some
    # restrictions may apply, but Openbox will try to

    <desktop>1</desktop>
    # 1 is the first desktop, 'all' for all desktops

    <layer>normal</layer>
    # 'above', 'normal', or 'below'

    <iconic>no</iconic>
    # make the window iconified when it appears, or not

    <skip_pager>no</skip_pager>
    # asks to not be shown in pagers

    <skip_taskbar>no</skip_taskbar>
    # asks to not be shown in taskbars. window cycling actions will also
    # skip past such windows

    <fullscreen>yes</fullscreen>
    # make the window in fullscreen mode when it appears

    <maximized>true</maximized>
    # 'Horizontal', 'Vertical' or boolean (yes/no)
  </application>

  # end of the example
-->
    <!-- Option to maximize all normal window when launched-->
    <!--
    <application type="normal">
      <maximized>true</maximized>
    </application>
    -->

  </applications>
```So it's basically all commented out and then it's for the user to add stuff. For example, I have```
    <application class="Lxterminal" name="lxterminal">
      <position force="yes">
        <x>-0</x>
        <y>0</y>
      </position>
      <decor>no</decor>
    </application>

```and```
    <application class="Galculator">
      <position force="yes">
        <x>500</x>
        <y>300</y>
      </position>
    </application>

```

---

### Post by clepsdyrae on 2017-04-15
> **vasa1 said:**
> I never really looked at this in 16.04 or 14.04 because I don't mind the new application gaining focus.

Yeah, it's certainly not useful in most circumstances to disable focusing new windows, which is why I never noticed it myself until recently. I need it for a particular application and so I stumbled upon the issue when I was setting things up.

---

### Post by vasa1 on 2017-04-15
> **clepsdyrae said:**
> Yeah, it's certainly not useful in most circumstances to disable focusing new windows, which is why I never noticed it myself until recently. I need it for a particular application and so I stumbled upon the issue when I was setting things up.
This is what I did for a zenity window I wanted on top but not in focus:```
    <application title="Alarm" class="Zenity" name="zenity">
      <focus>no</focus>
      <decor>no</decor>
      <layer>above</layer>
    </application>

```

---

### Post by mörgæs on 2017-04-16
Thanks for marking the thread solved but better to use Thread Tools for that.

16.04, 16.10 and 17.04 are all old news and none of them are likely to receive non-security bugfixes. If you believe it's a bug the best you can do is to see if it's still there in the new development version (17.10) when the new cycle begins.

---

