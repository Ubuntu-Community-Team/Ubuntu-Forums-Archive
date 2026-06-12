---
title: "Unclear interaction xubuntu &lt;-&gt; compiz"
date: 2013-07-08
forum: Desktop Environments
---

### Post by r_avital on 2013-07-08
I got compiz working under xubuntu following instructions [here.]("http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html")  The long and the short of it is:

1. In terminal, I issued "compiz --replace"

2. Copied /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml to ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml

3. Edited ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml as follows:
```
[SIZE=3]<property name="Failsafe" type="empty">       
    <property name="IsFailsafe" type="bool" value="true"/>       
    <property name="Count" type="int" value="5"/>       
    <property name="Client0_Command" type="array">          [B]
          <value type="string" value="[COLOR=#ff0000]xfwm4[/COLOR]"/>[/B]       
    </property>[/SIZE]
```
Replaced xfwm4 with compiz

All is fine. But, on every reboot/logout-login, compiz starts with its window on screen.  Is that absolutely necessary?  Is it possible to have compiz as my active windows manager without it starting on screen?  I don't know if this is related, but I did install the compiz-fusion-icon (which I don't see anywhere on desktop or any panels, so that's confusing me I'm sure).

Second question:  All was fine with compiz as I said above, except the wallpaper plugin wouldn't launch, or at least I did not see my wallpapers on screen.  Digging a bit deeper, I found [this closed thread here.]("http://ubuntuforums.org/showthread.php?t=1287776")  Basically, issue "sudo xfdesktop --quit" in terminal, and edit /etc/xdg/xfce4/xinitrc to comment out the line "xfdesktop&" so it never starts to begin with.

Again, on reboot/logout-login, if I want to see the wallpaper(s) I configured in compiz, I have to re-issue that command.  Any other way to get around it?

TIA :)

---

