---
title: "best DE (or lack thereof) for taking notes without battery drainage"
date: 2012-08-05
forum: Desktop Environments
---

### Post by haplorrhine on 2012-08-05
I would enjoy learning to program, but I'm not a programmer, and I just learned about alternative Desktop Environments.

I could make a custom DE just for creating, opening, and altering documents in LibreOffice.  However, I read that OpenBox is more lightweight than Compiz-Fusion, and I keep reading that custom DEs require Compiz in some form.  Would my battery be better off with Openbox?> Many people use Compiz-Fusion in Gnome or KDE, but it is also possible  to use it as a standalone window manager like Openbox. It is a very  light environment, compared to Gnome or KDE (but still heavier than  Openbox)
[https://help.ubuntu.com/community/CompizStandalone](https://help.ubuntu.com/community/CompizStandalone)I found this too.  Would this be my best option?
[http://askubuntu.com/questions/23932/how-do-i-replace-the-desktop-by-an-application](http://askubuntu.com/questions/23932/how-do-i-replace-the-desktop-by-an-application)> Sometimes it may be needed that a user only has access to a certain  application. Running the desktop environment then may be unwanted...


This guide has "lightweight" in its title, but it's still relying on compiz.
[http://maketecheasier.com/easily-create-a-custom-lightweight-desktop-environment/2010/08/10](http://maketecheasier.com/easily-create-a-custom-lightweight-desktop-environment/2010/08/10)

---

### Post by Whovian on 2012-08-05
Well Openbox is a good choice or even lxde both use very little battery power an well if you are set on using openbox I believe #!crunchbang linux uses it as its standalone DE.

---

### Post by haplorrhine on 2012-08-05
I've read that LXDE (Lubuntu's desktop environment) doesn't extend battery life very much.  Anyway, would it be an option to create a custom DE from LXDE programs and run it from the Ubuntu login screen?  Is AbiWord more efficient than LibreOffice when it's running alongside LXDE programs?

I just discovered that my new netbook's battery light doesn't do anything to warn me of low battery, so I'll need to include a program for that.

---

### Post by Whovian on 2012-08-05
Abiword is a standalone word-processor so it would use less than the entire libreoffice sweet. Having them run next to LXDE i'm not sure.

If I am understanding this right you want to have some lxde programs run on your custom DE an have a the lubuntu log-in as well?

If that is the case personally I just keep the login in screen an remove the desktop environment an install the openbox.

---

### Post by Simian Man on 2012-08-05
It doesn't really matter that much.  The DE will normally use very little of your CPU and thus not increase battery drain that much.  Things like turning down the screen brightness and turning off WiFi and Bluetooth will make more difference.  If you really want to maximize battery life, boot into a text console and take your notes with vim :).

---

### Post by vexorian on 2012-08-05
> **Simian Man said:**
> It doesn't really matter that much.  The DE will normally use very little of your CPU and thus not increase battery drain that much.  Things like turning down the screen brightness and turning off WiFi and Bluetooth will make more difference.  If you really want to maximize battery life, boot into a text console and take your notes with vim :).
Compositing probably has an effect. It needs the video card and that stuff.

I found compiz and mutter to be both resource drains. In my weak CPU netbook, the best balance was to use metacity with compositing. Although I disabled compositing altogether because **maximus** (yeah, I still use maximus) kind of causes metacity crashes when metacity has compositing. hmnn, I should probably report this bug.

Replacing the desktop with an application is as light weight as you can do.

I actually do that, but replace it with a single terminal window. Then the terminal window becomes my DE. This is great for things like running heavy games in WINE. After doing it with a terminal just type "libreoffice".

---

### Post by haplorrhine on 2012-08-06
Hey! Another Primate! :)

> **vexorian said:**
> I actually do that, but replace it with a single terminal window. Then the terminal window becomes my DE. This is great for things like running heavy games in WINE. After doing it with a terminal just type "libreoffice".
Can I run DE programs from the terminal?  That might be a good way to figure out what programs I have to run to get this DE doing what I want it to do.

[QUOTE=Whovian]Abiword is a standalone word-processor so it would use less than the  entire libreoffice sweet. Having them run next to LXDE i'm not sure.

If I am understanding this right you want to have some lxde programs run on your custom DE an have a the lubuntu log-in as well?

If that is the case personally I just keep the login in screen an remove the desktop environment an install the openbox.     [/QUOTE]
No, I was asking about running an LXDE based DE from within Ubuntu, but I didn't phrase the question well.
I compared the battery rate during LibreOffice Writer usage and Abiword usage.  Not only did AbiWord use more battery, it lagged! Since AbiWord is recommended during Lubuntu installation, I wondered if it runs better in its natural LXDHabitat.

---

### Post by vexorian on 2012-08-06
You can try. From a terminal window type:

sudo gedit /usr/share/xsessions/terminal.desktop


Add this text and save:
```

[Desktop Entry]
Name=Terminal
Comment=This session logs you into Terminal
Exec=gnome-terminal
TryExec=gnome-terminal
Icon=
Type=Application
```

Make the file executable:

sudo chmod 755 /usr/share/xsessions/terminal.desktop

log out to lightdm, in the sesion chooser there should be a terminal option. When you enter it, you will find a terminal mixed with your desktop. You can try typing libreoffice from there, or gedit , or whatever program. I really think it should run, but it will lack the usual interface and you won't be able to switch to the terminal without closing it...

---

### Post by Simian Man on 2012-08-06
> **vexorian said:**
> Compositing probably has an effect. It needs the video card and that stuff.

You're right there, you can always turn that off though.

---

### Post by haplorrhine on 2012-08-14
Long time no talk.  I didn't crash my computer trying to make a new DE, I just went on a family vacation into the middle of nowhere.


I want to thank Vexorian for showing me that script.  Other pages told me to make a .desktop file, but I didn't know how to do that until Vexorian gave me that. While following Vexorian's instructions, I was so caffeinated that I found out how to make the file executable before noticing Vexorian's code for that. This is my code.```
cd /usr/share/xsessions
sudo chmod +x terminal.desktop
```I was able to open LibreOffice in the terminal session.  I was even able to open and save files.
Also, in Vexorian's gedit code, I replaced "gnome-terminal" with "libreoffice" to make a session that only runs LibreOffice.   Using Power Statistics, I compared the battery discharge rate for running LibreOffice within Unity and running the LibreOffice session.  Everything else was the same.  With wifi off, the LibreOffice session was only slightly more battery efficient than LibreOffice running within Unity.
The second one is LibreOffice with Unity.  Those sudden drops are from my screen turning off.  With both, screen on=barely over 6 watts, screen off=barely over 4 watts.  I was surprised that the screen still turned off automatically in the custom session.
[IMG]http://i1160.photobucket.com/albums/q485/haplorrhine/batteryLOvsLOUbuntu.jpg[/IMG]



I've been less fortunate with running  DE programs from the terminal session.  I looked online for a command to run compiz.  I tried
```
compiz
```and```
compiz --replace
```, but neither did anything.

---

