---
title: "Gui login issue"
date: 2013-06-20
forum: Desktop Environments
---

### Post by kkhosa on 2013-06-20
Hi 
I have been using ubuntu for quite sometime. My system can login using commandline (alt +clt+f1) can update anything. But when I am trying login using normal desktop gui it does not go further (not sure what's wrong with it ) but it works when I am using guest session ( here can not run command but it shows it's own desktop ) . Tried recovering it but no scuess (I can not find startx)

---

### Post by dino99 on 2013-06-20
well, wich system is it (Precise/Quantal/Raring) ? wich DE ? (gnome/kde/else)  how do you log with ? (ubuntu (aka unity)/gnome (aka gnome-shell)/else)

as you does tell us how that system has been installed, here is my way to get a standard one:
[http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

---

### Post by Bashing-om on 2013-06-20
[COLOR=#000000]kkhosa; Hi ! Welcome to the forum .

Maybe you have lost the authority to access your home directory in the GUI environment; to check:
[/COLOR]

1. At the login screen, press Ctrl+Alt+F1 to get to the console.
2. Log in there.
3. Check if ".ICEauthority" is owned by you:
```

ls -al .ICEauthority
```
4. If it isn't (but possibly by root), change it to you:
```

sudo chown USERNAME:USERNAME .ICEauthority
```where "USERNAME" is your actual user name.
5. Switch back to the login screen by pressing Ctrl+Alt+F7 or F8
6. Try again to log in.
7. Repeat this procedure for the file ".Xauthority".
If it worked, see here about a possible cause:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)[INDENT=2]
just try'n to help

[/INDENT]

---

