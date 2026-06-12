---
title: "[SOLVED] Compiz settings command line?"
date: 2007-12-13
forum: Desktop Effects &amp; Customization
---

### Post by mbeierl on 2007-12-13
What is this, Windows? :)

I am getting more and more confused by how hard it is to set things from the command line versus going through a UI.  For example, how can I change the number of desktops from a shell script, instead of having to point and click my way through ccsm?

Another one is (although this is probably nvidia's fault) how to change external monitor settings from a shell script?

---

### Post by mbeierl on 2007-12-19
Really?  No, for real?  You mean Linux progress has decided to do away command line interfaces?  We really are forced to use a mouse and a UI to configure compiz?

Forgive my astonishment, but ... this is practically unbelievable :)

---

### Post by ThaRabbit on 2007-12-19
Editing a graphical enhancement's options with a GUI is not logical? :D

Anyways, the xml configuration files are located here:
/home/<your username>.gconf/apps/compiz

For example:
/home/<your username>/.gconf/apps/compiz/plugins/wobbly/allscreens/options/%gconf.xml

```
<?xml version="1.0"?>
<gconf>
        <entry name="snap_button" mtime="1198082759" type="string">
                <stringvalue>Button0</stringvalue>
        </entry>
        <entry name="snap_edgebutton" mtime="1198082759" type="int" value="0">
        </entry>
        <entry name="snap_bell" mtime="1198082759" type="bool" value="false">
        </entry>
        <entry name="snap_edge" mtime="1198082759" type="list" ltype="string">
        </entry>
</gconf>
```

Should be able to edit those with VI, nano or your tool of choise... 

Have fun :)

*edit*

Actually, thinking about my reply... I think you may be looking for an actual command line script or tool to edit the settings.

You can start compiz from the command line with several options, have a looksy here:
[http://gentoo-wiki.com/Compiz#Using_Command-Line](http://gentoo-wiki.com/Compiz#Using_Command-Line)

```
Example:
compiz --replace miniwin decoration transset wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water &
```

---

### Post by mbeierl on 2007-12-19
Say, for example, I want to write a script that changes my desktop from dual monitor to single, while at the same time changing my cube from 4 desktops to 8, so my window placement does not get all messed up.

I can then bind that to, say a function key and rapidly toggle between docked and undocked settings, or even have it run that script for me on dock action.  That's why I don't want to use the gui.

So, if the gui ccsm can do it without restarting compiz, how can we also do that?

---

### Post by Arcnsparc on 2008-01-04
I am looking for similar things, [http://ubuntuforums.org/showthread.php?p=4074918#post4074918](http://ubuntuforums.org/showthread.php?p=4074918#post4074918)

i think what we need to do is write a script that changes all of the options, and then assign a hotkey to that script.  I got the hotkey part: [http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)

now all I need to do is figure out how to do the scripts themselves...
I think I know what you are looking for, I want to quick switch between different setups because compiz doesn't get along with everything very well.   But when I switch off compiz my theme no longer looks good so i wanted to change colors and other desktop effects to match it, including background.  I will be watching this post too, I hope somebody can help us!

---

### Post by psyopper on 2008-01-04
Ummm... through [DBus]("http://wiki.compiz-fusion.org/Plugins/Dbus")?

---

### Post by mbeierl on 2008-01-07
YES!!! That's what I was finally wanting.  I never looked much into dbus - I'm an old "everything's a file" type of person...

I suppose I should put my "solution" here:

To go to "single monitor":
```
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/core/screen0/hsize org.freedesktop.compiz.set int32:8
xrandr -s 1
```

"Dual monitor"

```
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/core/screen0/hsize org.freedesktop.compiz.set int32:4
xrandr -s 0
```

In this case my xrandr shows:
```
   2720x1024      50.0  
   1440x900       52.0
```

---

