---
title: "Transparent ScreenSaver - Lock ScreenSaver"
date: 2024-06-24
forum: Desktop Environments
---

### Post by adewit on 2024-06-24
Prupose:
    I want to display the status page of a monitoring system (like Nagios) but still protect the system with a password.
    
Oldies:
    In the past I used an Transparent Screen Saver running under Windows (example from [https://www.e-motional.com/TScreenLock.html](https://www.e-motional.com/TScreenLock.html) so you have at least a working solution for Windows) but it is not OpenSource and not for Linux
Test:
    I test, among others, XTRLOCK on Ubuntu (version  22.04) with Wayland Gnome version 42.69) standard installation ; but get "WARNING: Wayland X server detected: xtrlock cannot intercept all user input. See xtrlock(1). xtrlock (version 2.15): cannot grab keyboard "
    
Request:
    Does onyone know an OpenSource solution as Trasparent ScreenSaver - LockScreen ? on Linux / Windows ; and even eter if I can start it at boot time.
    
    
Thanks

---

### Post by Holger_Gehrke on 2024-06-24
On X11 this is basically a solved problem. Just use xscreensaver and set up conky as the display-hack (conky can be made to display it's output in a specific window and xscreensaver can pass the window-id of the (undecorated) window it puts on top of the desktop to the hack it runs.

On Wayland screensavers are not really a thing (yet ?). Since the compositor is basically window manager and display server in one and each DE has it's own compositor, getting anything to the point were everyone agrees to some standard way of doing things is a long and protracted process.

Holger

---

### Post by adewit on 2024-06-28
Thank Holger for your answer.

I have to confest I didn't understand much !

Could you please explain it and be more descriptive (a procedure would be the best)

Thank in advance

Regards
ADEWIT

---

### Post by Holger_Gehrke on 2024-06-28
There are two graphic stacks on Ubuntu. You can choose which one to use using the cog icon on the login screen. The older stack uses the X11 protocol with xorg as the display server. The newer stack uses Wayland as the protocol and various compositors - a separate one for each desktop environment - as both display server and window manager. Wayland has been in development for a long time now, but there are still areas where the protocol and the implementations have problems. Screensavers are one of these areas, so to the best of my knowledge what you want to do can't currently be done on wayland (I wouldn't mind being proven wrong on that, I'm using Xubuntu (XFCE-desktop) which doesn't yet support Wayland, so my knowledge of Wayland is mostly theoretical).

On X11 one of the best known screensavers is 'xscreensaver'. It's modular with a background process that takes care of when to blank or un-blank the screen and reacting to hot-keys, a program to make settings to the screensaver ('xscreensaver-demo'), and a lot of small programs called display hacks that have no purpose but to show some graphics on the blanked screen. You can write your own display hack or use a program as a display hack that can be told to make it's output into a specific window. To do so you edit the configuration file for xscreensaver ('~/.xscreensaver') and add the new program to the line that starts with 'programs:' (yes, it's all one line with lots of escaped line-endings ...). For example, I added 'mpv' (a video-player controlled from the command line) to the programs like so:
```

...
programs:                                      \
                mpv --really-quiet --no-stop-screensaver      \
                  --loop=inf --fs --no-audio              \
                  --wid=$XSCREENSAVER_WINDOW              \
                  $HOME/Videos/'TSV.mkv'            \n\
                maze -root                    \n\
...

```
As you can see one program can be spread over multiple lines by putting escaped line-ending to split up long commands; the part describing one program ends with '\n\'+line-end (so 'maze -root' is the command for the next program in the list).
The important thing here is '--wid=$XSCREENSAVER_WINDOW'. The option '--wid=' tells mpv to write to the window with the id given after the option and '$XSCREENSAVER_WINDOW' is a variable passed from xscreensaver to a hack that contains the id of the undecorated window xscreensaver puts over the display to hide it's content.

The other half of my solution is conky. conky is a very configurable status display program. It has an option '-w' or '--window-id=' that does the same thing as the '--wid=' of mpv. Configuring conky is ... complex ... to say the least, so look for tutorials and examples on the net - there are lots of them.

Holger

---

### Post by adewit on 2024-07-01
Thank Holger

Your answer give me some clue.

The solution seems to be to use Xorg  you can chose it on the login screen: (see attachment : I don't find how to insert it another way)

Install xtrlock (sudo apt install xtrlock)

And when you want to lock the screen ; in a terminal type xtrlock.

By the way if you have some "good" internet site or book to learn more about Xorg and Wyland ; please be free to post it.

Regards
ADEWIT

---

