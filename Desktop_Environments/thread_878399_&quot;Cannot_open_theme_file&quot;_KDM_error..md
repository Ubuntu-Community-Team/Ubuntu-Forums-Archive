---
title: "&quot;Cannot open theme file&quot; KDM error."
date: 2008-08-02
forum: Desktop Environments
---

### Post by dodle on 2008-08-02
I've looked all over but haven't found an answer for this yet.  I did see some threads about it, but no resolutions.  

I installed Xubuntu 8.04, and decided to download Kde as well.  Then I wanted to try KDM because I've always used GDM.  After installing some themes for KDM, I get the error 'Cannot open theme file' at the login screen.  I hit "okay" and KDM loads up with no theme.

I've tried installing the default themes, but they don't work either.  In /usr/share/apps/kdm/themes all the folders for the themes that I have installed are there.  Can anyone help me with this?

---

### Post by K2712 on 2008-08-02
Which version of KDE did you install?

I think this may have to do with the kdmrc config line wrapping quotes around the Theme line.

---

### Post by dodle on 2008-08-03
KDE v3.5.9.  This is what my kdmrc looks like:[HTML][General]
ConfigVersion=2.3
ConsoleTTYs=tty1,tty2,tty3,tty4,tty5,tty6
PidFile=/var/run/kdm.pid
ReserveServers=:1,:2,:3
ServerVTs=-7
StaticServers=:0

[X-*-Core]
AllowNullPasswd=false
AllowRootLogin=false
AllowShutdown=Root
ClientLogFile=.xsession-errors-%s
Reset=/etc/kde3/kdm/Xreset
Session=/etc/kde3/kdm/Xsession
Setup=/etc/kde3/kdm/Xsetup
Startup=/etc/kde3/kdm/Xstartup

[X-*-Greeter]
AntiAliasing=true
LogoArea=Logo
LogoPixmap=/usr/share/apps/kdm/pics/kdelogo.png
MaxShowUID=29999
MinShowUID=1000
Preloader=/usr/bin/preloadkde
Theme="/usr/share/apps/kdm/themes/Krystal"
UseTheme=true

[X-:*-Core]
AllowNullPasswd=true
AllowShutdown=All
ServerArgsLocal=-nolisten tcp
ServerCmd=/usr/bin/X -br

[X-:*-Greeter]
AllowClose=true
FocusPasswd=true
LoginMode=DefaultLocal
PreselectUser=Previous

[X-:0-Core]
ClientLogFile=.xsession-errors

[Xdmcp]
Enable=false
Willing=/etc/kde3/kdm/Xwilling
[/HTML]

Edit:  I just found this [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg802502.html]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg802502.html") which confirms what you are telling me.

Edit: Edit:  Okay, I can use themes by deleting the quotation marks in theme line, but then I can't change themes from the theme manager, I have to edit kdmrc manually.  Hmmmm, strange.

---

### Post by AudioDef on 2008-10-25
I have the same problem and have to fix it by manually removing the quotes. 

You'd think a quick update would be in order.

---

