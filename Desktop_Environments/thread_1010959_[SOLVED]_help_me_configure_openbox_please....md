---
title: "[SOLVED] help me configure openbox please...?"
date: 2008-12-14
forum: Desktop Environments
---

### Post by bryncoles on 2008-12-14
hallo! 

now, i dont exactly have a slow system, but im getting to be a speed freak too. i discovered openbox, and found that on a pure openbox configuration my laptop (dell inspiron 1525n) runs hellova-fast!

in installed the scale plugin (skippy) from 

[http://ubuntuforums.org/showthread.php?t=846643](http://ubuntuforums.org/showthread.php?t=846643)

but cant manage to change the keybinding for it. why not i wonder?

id like help changing the skippy-xd command form f11 (the default), to control up as this is more comfortable for me.

also, i only seem to have one desktop with openbox... id quite like to find my others please!

when i run skippy-xd in the terminal, it tells me that:

```
WARNING: Couldn't load config file '/home/bryn/.skippy-xd.rc'.
```

perhaps ive put the file in the wrong place?

---

### Post by bryncoles on 2008-12-14
ok, solved that first problem. but now as things are, i have to type 'skippy-xd when i want it to start. it gives me the warning

> Ignoring invalid line: ctiv

and i still cant change the keybinding. 

ideas?

---

### Post by urukrama on 2008-12-14
I have never used skippy-xd, but use skippy on some of my computers. If you are a speed freak as you claim, you might like that better. It doesn't require compositing and is a lot faster, especially on computers with low resources.

You'll first need to copy the skippy-xd.rc-default file in the source code to ~/.skippy-xd.rc. To change the keybinding, change the line that reads "keysym = F11" to whatever key you'ld like to use instead. Note that you can only specify one key, so Ctrl or Alt with another key is impossible. 

You also need to give the correct keyname. To find the name of a key, use xev (which comes with a default or minimal Ubuntu install). Type xev in a terminal and press the key you want to use. A lot of information will appear. You'll need what comes after the code after "keysym". For the PrintScreen key this will be "Print".

You might also be interested in [this post]("http://urukrama.wordpress.com/2008/05/23/expose-type-behaviour-in-openbox/") on my blog.

---

### Post by bryncoles on 2008-12-15
cheers for that - ive actually found your blog already! thats how i managed to figure out keyboard shortcuts ;) and so far, im only an aspiring speed freak... depends if i can get open box fixed or not!

thought i had figured out the keychange thing - i have to reload skippy, not just the windows manager when i make the amendment. 

thing is, now i have F11 and F12 launching skippy! and i have little to no idea how to auto start skippy with openbox...

---

### Post by urukrama on 2008-12-15
> **bryncoles said:**
> thing is, now i have F11 and F12 launching skippy! and i have little to no idea how to auto start skippy with openbox...

You can only autostart skippy with Openbox if you add *skippy &* to your autostart.sh file (in ~/.config/openbox/). If you don't tell Openbox to launch skippy (or any other program) it won't launch it.

Yes, you will have to restart skippy if you made changes in the configuration file. To do so, just type *killall skippy* in a terminal to terminate the running skippy, and relaunch skippy. You could create menu entries for this. I have an entry called "Skippy Off" with the command *killall skippy* and one called "Skippy On" with the command "skippy".

If two keys trigger skippy, it means you have two instances of skippy running. You can only specify one key in skippy's configuration file.

---

### Post by bryncoles on 2008-12-15
cool... thanks for that. now i have only one instance of skippy running, and its activated by F12! i also added 'skippy-xd &' to the autostart file, just by putting it at the bottom of the file. seems not to have worked though, what could be wrong?

when i run skippy form a terminal though, its tells me 

>  WARNING: Ignoring invalid line: ctiv&#65533;

my google-fu is weak, and i am not sure what this means. do you have an idea?

is there a way i can set up a run dialogue like gnome has with alt-f2?

[edit]

[https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox) tells me something about a run dialogue... ill have a deeper look into that i think...

[/edit]

im really appreciating all this help by the way!

finally, i installed something which would use the gnome desktop settings. big mistake! and i forget what i installed to be able to uninstall it! i get this error message when i start openbox though:

> GTK+ icon theme is not properly set

This usually means you don't have an XSETTINGS manager running.  Desktop environment like GNOME or XFCE automatically execute their XSETTING managers like gnome-settings-daemon or xfce-mcs-manager.

If you don't use these desktop environments, you have two choices:
1. run an XSETTINGS manager, or
2. simply specify an icon theme in ~/.gtkrc-2.0.
For example to use the Tango icon theme add a line:
gtk-icon-theme-name="Tango" in your ~/.gtkrc-2.0. (create it if no such file)

NOTICE: The icon theme you choose should be compatible with GNOME, or the file icons cannot be displayed correctly.  Due to the differences in icon naming of GNOME and KDE, KDE themes cannot be used.  Currently there is no standard for this, but it will be solved by freedesktop.org in the future.

rather than specifying an icon theme, or a xsettings manager, do you know how i can get openbox to not look for either again (its default behaviour?)

---

### Post by urukrama on 2008-12-16
[LIST]For a run dialog, try gmrun, or dmenu. You can bind it to Alt+F2 in the rc.xml of Openbox. For dmenu, have a look [here]("http://urukrama.wordpress.com/2008/02/07/using-dmenu-in-pekwm-and-openbox/"). To bind gmrun to Alt+F2, add the following to the <keyboard> section of your rc.xml:

```
<keybind key="A-F2">
      <action name="execute">
        <execute>gmrun</execute>
      </action>
    </keybind>
```

[/LIST]

[LIST]If you want to disable to use a Gtk theme or Gtk icon theme, just don't load gnome-settings-daemon or xfce-mcs-manager, and make sure you haven't specified the Gtk theme in your ~/.gtkrc-2.0 (either manually or with an application like LXAppearance or gtk-theme-switch2). For more info on Gtk themes, see my Openbox guide. 
[/LIST]

[LIST]If you don't remember what application you installed, check the history of Synaptic (if you used that -- under File > History), or check the log in /var/log/apt/term.log (you'll need administrative privileges for this).
[/LIST]

[LIST]I don't know why you get that error from skippy-xd. Does it not load at all? Or does it give this error message before it launches?
[/LIST]

[LIST]Skippy is hard to start when Openbox starts. You need to allow Openbox to start first before you launch skippy. You can do so with the sleep command: to wait ten seconds before launching skippy, you'd add the following command to the bottom of your autostart.sh file: *sleep 10 && skippy &*[/LIST]

---

### Post by bryncoles on 2008-12-17
cool stuff! i figured out keyboard shortcuts, and ive just tried setting the 'sleep 10 &&' thing. ill play about with that and see what else i can achieve, what other tweeks it'll accept.

as for the warning - it gives it in the terminal but skippy-xd loads anyway, and seems to work fine. maybe ill just not worry about that too much... ill explore and see if it causes me any troubles. 

once again, i appreciate your help, and your very useful blog!

*** edit ***

winner! thanks to your help, ive not got the error message when i open up openbox anymore, and skippy begins working on boot! this makes me a very happy man! 

now ill start thinking about putting an info panel up on there, but i can probably muddle through with your blog. cheers!

---

