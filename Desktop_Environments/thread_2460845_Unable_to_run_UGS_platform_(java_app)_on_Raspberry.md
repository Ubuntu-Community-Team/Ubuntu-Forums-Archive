---
title: "Unable to run UGS platform (java app) on Raspberry Pi 4"
date: 2021-04-20
forum: Desktop Environments
---

### Post by jonas852 on 2021-04-20
Hey.
I'm new to the Linux environment. I'm working on a CNC controller project based on Raspberry Pi 4 and a 7" touch screen.
I was first running Raspberry Pi OS and UGS Platform (Linux ARM version with bundled Java) [URL="https://winder.github.io/ugs_website/download/"]https://winder.github.io/ugs_website/download/ 
[/URL]That worked fine out of the box, just click the app and it runs.

I didn't really like RPi OS, didn't work well with the touchscreen so I wanted to try Ubuntu desktop 20.10 which looks a lot better and worked really well with the touchscreen.
But I can't make it run UGS Platform for some reason. If i just click the app like in RPi OS, it just opens in the text editor.

If i run it from the terminal i get:
[COLOR=#00ff00]jonas@jonas-ubuntu[/COLOR]:[COLOR=#0000ff]~/Downloads/1/ugsplatform-pi/bin[/COLOR]$ java ugsplatform 
Error: Could not find or load main class ugsplatform
Caused by: java.lang.ClassNotFoundException: ugsplatform

Java version:
[COLOR=#00ff00]jonas@jonas-ubuntu[/COLOR]:[COLOR=#0000ff]~/Downloads/1/ugsplatform-pi/bin[/COLOR]$ java -version 
openjdk version "11.0.10" 2021-01-19
OpenJDK Runtime Environment (build 11.0.10+9-Ubuntu-0ubuntu1.20.10)
OpenJDK 64-Bit Server VM (build 11.0.10+9-Ubuntu-0ubuntu1.20.10, mixed mode)

Does anyone have any ideas of why it's not working? 

Thanks in advance /Jonas

---

### Post by Holger_Gehrke on 2021-04-20
'~/Downloads/1/ugsplatform-pi/bin/ugsplatform' is a shell script, so it's no wonder Java isn't able to execute it. Try './ugsplatform' with '~/Downloads/1/ugsplatform-pi/bin/' as your working directory.

If you want to start it graphically you should create a .desktop file for it, something like
```

[Desktop Entry]
Type=Application
Name=UGS
Comment=Universal G-Code Sender
Exec=/home/jonas/Downloads/1/ugsplatform-pi/bin/ugsplatform
Icon=[COLOR=#ff0000]Put Path and Name to an image to use as the icon here[/COLOR]
Terminal=false
Categories=Utility;
Keywords=CNC;GCode
Path=/home/jonas/Downloads/1/ugsplatform-pi/bin/
StartupNotify=true

```
Put this in a file ~/.local/share/applications/UGS.desktop and UGS should show up in the Applications overview.

Holger

---

### Post by jonas852 on 2021-04-20
Thanks for the reply.

it doesn't work ether:
[COLOR=#00ff00]jonas@jonas-ubuntu[/COLOR]:[COLOR=#0000ff]~/Downloads/1/ugsplatform-pi/bin[/COLOR]$ ./ugsplatform
./../platform/lib/nbexec: line 421: /home/jonas/Downloads/1/ugsplatform-pi/jdk/jdk-13.0.1+9/bin/java: No such file or directory

/Jonas

---

### Post by ActionParsnip on 2021-04-20
What is the output of:
```

sudo apt install pastebinit
cat -n ~/Downloads/1/ugsplatform-pi/bin/ugsplatform | pastebinit

```
Thanks

---

### Post by jonas852 on 2021-04-21
[https://paste.ubuntu.com/p/GDj9sxwgy3/](https://paste.ubuntu.com/p/GDj9sxwgy3/)

---

### Post by jonas852 on 2021-04-21
[https://paste.ubuntu.com/p/GDj9sxwgy3/](https://paste.ubuntu.com/p/GDj9sxwgy3/)

---

