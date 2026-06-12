---
title: "XFCE4 Crashes/Window title Disapperas"
date: 2013-04-23
forum: Desktop Environments
---

### Post by abhayadevs on 2013-04-23
Hi,

My desktop env is XFCE and its a week now since it started causing issues like suddenly the window header/titles will be disappeared and then I wont be able to move the window.. Every time this happens i do the 'sudo xfw4 --replace'.. is there a permanent solution to this?
Regards,
abhayadev s

---

### Post by Toz on 2013-04-23
You could try to clean out the saved sessions cache in case something is corrupted in there. You don't mention the version of Xfce that you are using. Newer versions have an option in Settings Manager->Session and Startup -> Sessions tab.

To do it manually:
[LIST=1]
[*]Log out
[*]Go to the first tty (Ctrl+Alt+F1)
[*]Log in to the text console
[*]Enter the following commands:
```
cd $HOME/.cache
rm -rf sessions
exit
```
     ...be extra careful typing in the "rm -rf" statement.

[*]Go back to the gui (Ctrl+Alt+F7)
[*]Login
[/LIST]
Note: By deleting the sessions cache, you will be removing any saved session information that you have (on logout, you have the option to save the session for future logins).

Reference: [http://docs.xfce.org/xfce/xfce4-session/start]("http://docs.xfce.org/xfce/xfce4-session/start")

---

### Post by Buntu Bunny on 2013-04-23
I used to have this problem quite a bit. This is what's worked for me.

```
xfwm4 --sm-client-disable
```

That restores the desktop and workplace switcher. Then

```
xfwm4 --replace
```

That restarts xfwm4 properly. 

Log out and select "save session on exit."

Log in again and hopefully you're good to go.

---

