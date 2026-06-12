---
title: "Run in background"
date: 2009-12-02
forum: Desktop Environments
---

### Post by camrant on 2009-12-02
Is it possible to change properties for any program to run in the background and show an icon in with the other apps running on the tool bar in kde? 
Certain apps like ktorrent when you click the x do not actually close but go to the toolbar, not as the currently open windows but more as a background process.  

Can this be achieved with any app of my choosing?

---

### Post by Zorael on 2009-12-03
You can start an app with '**ksystraycmd**', but it doesn't seem to work with all apps. Konsole seems to end up in the task manager no matter what I do.
```
$ ksystraycmd firefox &
```
So if you just edit your shortcuts and add **ksystraycmd** to the start of them, it should (hopefully work).
```
$ ksystraycmd --help
Usage: ksystraycmd [Qt-options] [KDE-options] [options] command 

Allows any application to be kept in the system tray

Generic options:
  --help                    Show help about options
  --help-qt                 Show Qt specific options
  --help-kde                Show KDE specific options
  --help-all                Show all options         
  --author                  Show author information
  -v, --version             Show version information
  --license                 Show license information
  --                        End of options

Arguments:
  command                   Command to execute

Options:
  --window <regexp>         A regular expression matching the window title
                            If you do not specify one, then the very first window
                            to appear will be taken - not recommended.
  --wid <int>               The window id of the target window
                            Specifies the id of the window to use. If the id starts with 0x
                            it is assumed to be in hex.
  --hidden                  Hide the window to the tray on startup
  --startonshow             Wait until we are told to show the window before
                            executing the command
  --tooltip <text>          Sets the initial tooltip for the tray icon
  --keeprunning             Keep the tray icon even if the client exits. This option
                            has no effect unless startonshow is specified.
  --ownicon                 Use ksystraycmd's icon instead of the window's icon in the systray
                            (should be used with --icon to specify ksystraycmd icon)
  --ontop                   Try to keep the window above other windows
  --quitonhide              Quit the client when we are told to hide the window.
                            This has no effect unless startonshow is specified and implies keeprunning.
```
Maybe konsole just needs to be supplemented with a --window option.

---

