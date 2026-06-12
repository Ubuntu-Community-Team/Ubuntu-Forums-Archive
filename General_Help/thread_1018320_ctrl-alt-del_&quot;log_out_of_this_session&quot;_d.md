---
title: "ctrl-alt-del &quot;log out of this session&quot; doesn't include &quot;shut down&quot; on 8.10"
date: 2008-12-22
forum: General Help
---

### Post by inanutshellus on 2008-12-22
On my laptop it's much easier to use keyboard shortcuts than use the mouse, so my standard way of shutting off my laptop is "ctrl-alt-del + alt-s" which in previous versions of Ubuntu means "bring up the 'shut down or log out' dialog", then alt-s chooses the "shut down" menu option.

But in Ubuntu 8.10 the menu has changed. It's called "Log out of this session" now, and only includes two options: "Log out" or "Switch User". So instead I have to cancel the dialog, then start using this crappy laptop mouse and navigate to the shut down icon so I can click it and select the "shut down" dropdown item. 

How do I get "shut down" back in the dialog, or alternately, what's the keyboard combination to get to that dropdown?

---

### Post by inanutshellus on 2008-12-27
no ideas on this, eh? :-(

---

### Post by tony_clifton on 2008-12-27
I'd also like to get a full shutdown menu when entering ctrl-alt-del.

All I've been able to find is the contents of /etc/event.d/control-alt-delete:

```
# control-alt-delete - emergency keypress handling
#
# This task is run whenever the Control-Alt-Delete key combination is
# pressed.  Usually used to shut down the machine.

start on control-alt-delete

exec /sbin/shutdown -r now "Control-Alt-Delete pressed"
```

However, this doesn't make sense to me.   If Ctrl-alt-del is the same as shutdown -r now then you wouldn't get a menu at all, just direct to reboot, right?

---

### Post by tony_clifton on 2008-12-28
I found the article [Computing Tech: Ubuntu Ctrl+Alt+Delete (CAD) Key Sequence]("http://computingtech.blogspot.com/2008/10/ubuntu-ctrlaltdelete-cad-key-sequence.html") which talks about ways to modify the Ctrl-Alt-Delete command in Ubuntu.  

It includes the interesting quote > However, the Gnome desktop intercepts CAD. To reboot, you need to switch to a text window (Ctrl+Alt+F1) and then press CAD.

Since the Gnome desktop intercepts CAD, you can remap this key sequence to run a different command. For example, to bring up the Gnome System Monitor, you can use:

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_10 \
'<Control><Alt>Delete'
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_10 \
"gnome-system-monitor"

Unfortunately there is no folder named /apps on my system so it appears these instructions are outdated for 8.10.

---

### Post by tony_clifton on 2008-12-28
There's System->Preferences->Keyboard shortcuts, however I'm not seeing how to edit the shortcuts via this interface in a way that would bring up the shutdown menu.

Going back to what is in previous posts, if you edit /etc/event.d/control-alt-delete to read ```
# control-alt-delete - emergency keypress handling
#
# This task is run whenever the Control-Alt-Delete key combination is
# pressed.  Usually used to shut down the machine.

start on control-alt-delete

exec /sbin/shutdown -h now "Control-Alt-Delete pressed"
```

then you would be able to use Ctrl-Alt-F1 to open the text window, next hitting Ctrl-Alt-Del would shutdown.

---

### Post by vyco10 on 2009-03-08
Anyone ever figure out the easy way to fix this problem?

---

