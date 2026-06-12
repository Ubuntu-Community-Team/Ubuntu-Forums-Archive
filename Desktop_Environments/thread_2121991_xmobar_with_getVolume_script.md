---
title: "xmobar with getVolume script"
date: 2013-03-03
forum: Desktop Environments
---

### Post by iamnoahc on 2013-03-03
I'm trying to display the sound level in my xmobar configuration. I'm using the script from [https://github.com/davidbrewer/xmonad-ubuntu-conf](https://github.com/davidbrewer/xmonad-ubuntu-conf) and have configured xmobar as described on github. However, I get "Could not execute command ~/.xmonad/get-volume" in xmobar.

However, when I run it at the command line it appears to be working:

```
~ $ ~/.xmonad/get-volume
62%

```

I've also given execute rights to everyone:

```
~ $ ll ~/.xmonad/get-volume 
-rwxrwxr-x 1 noahc noahc 1061 Mar  3 16:52 /home/noahc/.xmonad/get-volume*

```

Here is my xmobar config:

```
Config { font = "-misc-fixed-*-*-*-*-12-*-*-*-*-*-*-*"
       , bgColor = "black"
       , fgColor = "grey"
       , position = Top
       , border = FullB
       , borderColor = "#3579a8"
       , lowerOnStart = True
       , commands = [ Run Weather "KAMW" ["-t","<tempF>","-L","32","-H","65","--normal","green","--high","red","--low","lightblue"] 36000
                    , Run Network "eth0" ["-L","0","-H","32","--normal","green","--high","red"] 10
                    , Run Cpu ["-L","3","-H","50","--normal","green","--high","red"] 10
                    , Run Wireless "wlan0" ["-L", "33", "-H", "66", "--low", "red", "--high", "green"] 500
                    , Run Memory ["-t","Mem: <usedratio>%"] 10
                    , Run Date "%b %_d %H:%M" "date" 10
                    , Run BatteryP ["BAT0"] ["-t", "<acstatus>: <left>","-L", "10", "-H", "80", "-l", "red", "-h", "green", "-n", "yellow","--", "-c", "energy_full", "-O", "A", "-o", "B"] 10
                    , Run StdinReader
                    , Run MultiCpu ["-t", "<autototal>%", "-L","15","-H","50","--normal","green","--high","red"] 10
                    , Run Com "~/.xmonad/get-volume" [] "myvolume" 10
                    ]
       , sepChar = "%"
       , alignSep = "}{"
       , template = " %StdinReader% }{ <fc=#ee9a00>%date%</fc>| %KAMW% | %battery% | %wlan0wi% | %multicpu% | %memory% | %myvolume% "
       }

```

Any thoughts or suggestions on how I could get this to work?

---

### Post by finnreservedmail on 2013-12-30
Run your "get-volume" script, replace your current line with:
Run Com "bash" ["~/.xmonad/get-volume"] "myvolume" 10

I don't know why the interpreter has to be specified when running scripts(in eg home directory), but my guess is that xmobar looks only in "global" directories specified by the PATH variable for executables. Bash exists in one or several of those paths, and bash can execute programs anywhere. So i think that is why.

---

### Post by finnreservedmail on 2013-12-30
Run your "get-volume" script, replace your current line with:
Run Com "bash" ["~/.xmonad/get-volume"] "myvolume" 10

I don't know why the interpreter has to be specified when running scripts(in eg home directory), but my guess is that xmobar looks only in "global" directories specified by the PATH variable for executables. Bash exists in one or several of those paths, and bash can execute programs anywhere. So i think that is why.

If this is correct, then another way to run your script is to copy it over to eg /usr/bin. 
Then you can execute is with your original statement.

---

