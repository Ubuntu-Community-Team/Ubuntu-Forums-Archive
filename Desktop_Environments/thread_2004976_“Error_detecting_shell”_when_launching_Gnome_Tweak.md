---
title: "“Error detecting shell” when launching Gnome Tweak Tool"
date: 2012-06-16
forum: Desktop Environments
---

### Post by greenbeaver on 2012-06-16
Hi there.

I have a bit of a problem when opening Gnome Tweak Tool. I am logged into Gnome Classic now, but it doesn't load when logged into Ubuntu or Gnome 3 either.

When logged into Gnome 3 my resolution is huge and I can't change it in System Settings - hoping the fix might've been in Tweak Tools.

This is the code I get when I try to launch from terminal:

```
__
WARNING : Error detecting shell
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell_extensions.py", line 149, in __init__
    shell = GnomeShellFactory().get_shell()
  File "/usr/lib/python2.7/dist-packages/gtweak/utils.py", line 38, in getinstance
    instances[cls] = cls()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 143, in __init__
    proxy = _ShellProxy()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 44, in __init__
    result, output = self.proxy.Eval('(s)', js)
  File "/usr/lib/python2.7/dist-packages/gi/overrides/Gio.py", line 148, in __call__
    kwargs.get('flags', 0), kwargs.get('timeout', -1), None)
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
GError: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.Shell was not provided by any .service files
WARNING : Shell not running
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell.py", line 59, in __init__
    self._shell = GnomeShellFactory().get_shell()
  File "/usr/lib/python2.7/dist-packages/gtweak/utils.py", line 38, in getinstance
    instances[cls] = cls()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 143, in __init__
    proxy = _ShellProxy()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 44, in __init__
    result, output = self.proxy.Eval('(s)', js)
  File "/usr/lib/python2.7/dist-packages/gi/overrides/Gio.py", line 148, in __call__
    kwargs.get('flags', 0), kwargs.get('timeout', -1), None)
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
GError: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.Shell was not provided by any .service files
WARNING : Could not list shell extensions
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell.py", line 64, in __init__
    extensions = self._shell.list_extensions()
AttributeError: ShellThemeTweak instance has no attribute '_shell'
Traceback (most recent call last):
  File "/usr/bin/gnome-tweak-tool", line 76, in <module>
    MainWindow()
  File "/usr/lib/python2.7/dist-packages/gtweak/mainwindow.py", line 44, in __init__
    model)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakview.py", line 40, in __init__
    self._model.load_tweaks()
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakmodel.py", line 135, in load_tweaks
    mods = __import__("gtweak.tweaks", globals(), locals(), tweak_files, 0)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell.py", line 236, in <module>
    GSettingsSwitchTweak("org.gnome.settings-daemon.plugins.power", "lid-close-suspend-with-external-monitor"),
  File "/usr/lib/python2.7/dist-packages/gtweak/widgets.py", line 116, in __init__
    _GSettingsTweak.__init__(self, schema_name, key_name, **options)
  File "/usr/lib/python2.7/dist-packages/gtweak/widgets.py", line 105, in __init__
    options.get("summary",self.settings.schema_get_summary(key_name)),
  File "/usr/lib/python2.7/dist-packages/gtweak/gsettings.py", line 122, in schema_get_summary
    return self._schema._schema[key]["summary"]
KeyError: 'lid-close-suspend-with-external-monitor'

```

Let me know if there is any more information I can provide.

Thanks for your help...

greenbeaver.

---

### Post by greenbeaver on 2012-06-17
Hey guys - have read a few others are having coniptions w/ Advanced Settings.

Received an answer [here,]("http://askubuntu.com/questions/151671/error-detecting-shell-when-launching-gnome-tweak-tool"). I'm trying it out now and will see what happens.

---

