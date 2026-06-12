---
title: "Shortcut Hijack"
date: 2009-11-16
forum: Desktop Environments
---

### Post by mbn18 on 2009-11-16
Hi,

I have a problem where some application catch the shortcut combination I activate in other applications.

For example:
When configuring through console the startup services in RedHat ( the setup command ) I can press F1 for more info.

The problem is that upon pressing F1 the 'Ubunto help' pop up and not the function which is associated with the application I am working at.

Any idea how to workaround?

Thanks

---

### Post by bernardfrancois on 2009-11-16
Are you sure the program in which you want to use the F1 shortcut has the focus? To give the focus to a program, you can click it so it's title bar becomes colored instead of gray.

I don't have any command called 'redhat' here. Could you provide some steps to reproduce this?

---

### Post by mbn18 on 2009-11-16
> **bernardfrancois said:**
> Are you sure the program in which you want to use the F1 shortcut has the focus? To give the focus to a program, you can click it so it's title bar becomes colored instead of gray.

I don't have any command called 'redhat' here. Could you provide some steps to reproduce this?

Have easier way to reproduce it ( Without the need for RedHat access ).
[LIST=1]
[*]Open Terminal
[*]Run the application 'mc'
[*]Click <F1> for Help
[/LIST]

Notice that F1 open the Ubuntu help.
F2 work as expected opening the menu in the terminal.

---

### Post by bernardfrancois on 2009-11-19
I just installed mc to see if I can reproduce this.

If I run mc from an **xterm** window, I do get the midnight commander help when I press F1.

If I run it from **gnome-terminal**, I get the help of gnome-terminal when I press F1.
Since gnome-terminal is the application that has the focus for the window manager, I would indeed expect the gnome-terminal help (regardless the fact that there is another application running inside gnome-terminal).

xterm simply doesn't have a help function, so pressing F1 doesn't trigger any xterm help window.

Maybe you could see this behaviour as a bug indeed. I think the gnome-terminal should still show its help window when F1 is pressed, but it should also send the F1 key event to the application it is displaying, so midnight commander would also get a chance to show its help functionality.

You can report this bug by executing the following command, and by following the subsequent instructions:
```
sudo ubuntu-bug gnome-terminal
```

---

### Post by mbn18 on 2009-11-20
There is already a reported bug.
They suggest to go to Edit->Keyboard shortcut... to disable F1.

Not optimal but works.

---

### Post by bernardfrancois on 2009-11-20
Not really a good solution. But I use xterm, so it doesn't affect me :)

---

