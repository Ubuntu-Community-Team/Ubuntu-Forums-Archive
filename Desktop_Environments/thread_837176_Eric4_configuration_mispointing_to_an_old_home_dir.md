---
title: "Eric4 configuration mispointing to an old home directory"
date: 2008-06-22
forum: Desktop Environments
---

### Post by bogdanbiv on 2008-06-22
I think I've got a bug with eric4.
Here's my scenario: I had Kubuntu 8.04 (upgraded from 7.10), on which I had installed eric4; I was using eric4 as user zbog. 

Then I did a clean install of Kubuntu 8.04 (keeping  the home directory). The new user is now bog (/home/bog). I had moved the files from the old home directory (/home/zbog) to the new home (/home/bog), including .eric4 configuration folder. Now Eric just shows the splash screen and disappears.Upon running it from the terminal, I got the 
output listed below.


Whenever I delete the /home/zbog/.eric4 directory I receive the following error:

bog@bog-desktop:~$ eric
Warning: translation file 'qt_en_US'could not be loaded.
Using default.
Warning: translation file 'eric4_en_US'could not be loaded.
Using default.
Warning: translation file 'qscintilla_en_US'could not be loaded.
Using default.
An unhandled exception occurred. Please report the problem using the error reporting dialog or via email to <eric4-bugs@die-offenbachs.de>. A log has been written to "/home/bog/.eric4/eric4_error.log".

Error information:
--------------------------------------------------------------------------------
2008-06-22, 12:27:41
--------------------------------------------------------------------------------
<type 'exceptions.OSError'>:
[Errno 2] No such file or directory: '/home/zbog/.eric4/Downloads'
--------------------------------------------------------------------------------
  File "/usr/share/eric/modules/eric4.py", line 248, in <module>
    main()
  File "/usr/share/eric/modules/eric4.py", line 233, in main
    mainWindow = UserInterface(loc, splash, pluginFile)
  File "/usr/share/eric/modules/UI/UserInterface.py", line 219, in __init__
    self.pluginManager = PluginManager(self, develPlugin = plugin)
  File "/usr/share/eric/modules/PluginManager/PluginManager.py", line 101, in __init__
    self.__checkPluginsDownloadDirectory()
  File "/usr/share/eric/modules/PluginManager/PluginManager.py", line 845, in __checkPluginsDownloadDirectory
    os.mkdir(downloadDir, 0755)

--------------------------------------------------------------------------------
Version Numbers:
  Python 2.5.2
  Qt 4.4.0
  PyQt4 4.3.3
  sip 4.7.3 /home/zbog/.eric4
  QScintilla 2-snapshot-20070923
  eric4 4.1.1 (r1972)

Platform: linux2
2.5.2 (r252:60911, Apr 21 2008, 11:12:42)
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)]

Although I removed /home/bog/.eric4 several times and I chose from Synaptic "completely remove" eric4 and all of its configuration files,
eric4 keeps referencing /home/zbog/.eric4.

*For one thing, I believe user names should not be hardcoded in configuration files, therefore I believe this is a bug.*

Unfortunately I could not find where exactly the setting /home/zbog/.eric4 is stored. Could you help?

---

### Post by SadaraX on 2008-08-25
I am not sure exactly what your problem is, but I had a problem with using the Eric4 in the repos and then using the latest stable version.

The configuration files conflicted and it took me a while to track down where the config files were.

There are some in /home/user/.eric4 AND there are additional config files in /home/user/.config/Eric4.

Try deleting both of those directories and restarting Eric. Hope that helps.

---

### Post by bogdanbiv on 2008-09-02
I'll look into it tonight.

---

