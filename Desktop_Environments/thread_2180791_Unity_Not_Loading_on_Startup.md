---
title: "Unity Not Loading on Startup"
date: 2013-10-14
forum: Desktop Environments
---

### Post by amtur_poet on 2013-10-14
I recently installed some updates on the Ubuntu install on my Toshiba X775-3DV78 laptop, but now, whenever I log into the machine, Unity refuses to load. My desktop displays, and I am able to open windows that have their borders, but the unity bar doesn't appear, nor does any other facet of its navigation menus. OI am able to boot into other desktop environments (KDE, GNOME 3, and Cinnamon, for reference). The only big addition I recently installed to my Ubuntu setup was Cairo-Dock, but it was working fine for one or two boots after installing that. Moreover, it doesn't look like I can uninstall all of Cairo's packages without completely uninstalling GNOME, so I don't think it would be wise for me to test this theory. Can anyone help?

---

### Post by JnPson on 2013-10-14
I've had a similar problem with unity after installing fglrx. I had to enable the unity plugin. I think this might apply to your problem too. 
[http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears](http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears)
Open a terminal:
```
sudo apt-get install compizconfig-settings-manager
```
and run
```
export DISPLAY=:0
``` and 
```
ccsm
```
Click on *Ubuntu Unity Plugin *and and to the left you'll find a check box to activate it.
I hope this could be of some help

---

### Post by JnPson on 2013-10-14
Another thing that came to my mind is that you might have enabled Cairo desktop from login. I installed cairo and tried to log in to cairo desktop and all I could see was the dock. Just a thought. :)

---

### Post by amtur_poet on 2013-10-15
Thanks for the idea, but I'm still getting the error when I try and log in after choosing "Ubuntu" from the session manager. I was able to remove all the leftover Cairo packages by running autoremove, but that didn't seem to help, either.

---

### Post by JnPson on 2013-10-15
Have you tested my suggestion in post #2?

---

### Post by amtur_poet on 2013-10-15
> **JnPson said:**
> Have you tested my suggestion in post #2?
Yeah, I know that I have Ubuntu selected from the session manager, as opposed to Cairo (Which is now uninstalled). I have also enabled the Unity plugin in Compiz.

---

### Post by JnPson on 2013-10-15
Sad to say I cannot be at more help. Hopefully someone else can jump in and help you with this matter.

---

### Post by amtur_poet on 2013-10-16
> **JnPson said:**
> Sad to say I cannot be at more help. Hopefully someone else can jump in and help you with this matter.
I appreciate the effort, nonetheless. :)

---

### Post by amtur_poet on 2013-10-20
I upgraded to 13.10, and it still didn't fix the issue. Please, guys, I need help!

---

### Post by stinkeye on 2013-10-20
> **amtur_poet said:**
> I upgraded to 13.10, and it still didn't fix the issue. Please, guys, I need help!
Install this small application
```
sudo apt-get install wmctrl
```

As unity is a plugin for compiz, check your in the ubuntu session and running compiz....
```
echo $DESKTOP_SESSION && wmctrl -m | head -n1
```
That will confirm the session and window manager running.

eg
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **echo $DESKTOP_SESSION && wmctrl -m | head -n1**
ubuntu
Name: Compiz
```

---

### Post by theantibob on 2013-11-30
> **amtur_poet said:**
> I upgraded to 13.10, and it still didn't fix the issue. Please, guys, I need help!

are you still experiencing issues related to nvidia drivers install and stuck in low-resolution as indicated in a previous thread?

if so:```
cat /var/log/Xorg* | grep \(EE\)
```should tell you what's wrong (EE)rror.

perhaps your monitor doesn't report the EDID properly to the nvidia xorg driver.

---

