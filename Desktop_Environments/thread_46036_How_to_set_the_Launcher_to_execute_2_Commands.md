---
title: "How to set the Launcher to execute 2 Commands"
date: 2005-07-02
forum: Desktop Environments
---

### Post by Prudentissimus on 2005-07-02
How do I create a launcher so that It will execute 2 or 3 or 4 (Multi) commands in the Terminal?

---

### Post by Omnios on 2005-07-02
Make a shell script  " .sh " and run the shell script.
 for example my Never Winter Nights Launcher because if would only run properly in terminal after changing to directory was

cd /your/directory/here/nwn
./nwn

saved as nwn.sh

YOu could also probably do sudo but would have to edit another file which I dont recall off hand.

---

### Post by Prudentissimus on 2005-07-03
[QUOTE=Omnios]Make a shell script  " .sh " and run the shell script.
 for example my Never Winter Nights Launcher because if would only run properly in terminal after changing to directory was

cd /your/directory/here/nwn
./nwn

saved as nwn.sh

YOu could also probably do sudo but would have to edit another file which I dont recall off hand.[/QUOTE]
 what if say I need to do the following:

```

sudo penggy<ENTER>
mypassword<ENTER>

```

---

### Post by khc on 2005-07-03
You cannot do that. If you really want the command "penggy" to always be executed as root without entering a password, you can setuid it.

---

### Post by Morimando on 2005-07-03
Sure you can.
In Gnome set the starter to use:
```
gksudo penggy
```
and it will open a window, asking to give your password and then run "penggy" as Super-User.

---

### Post by Prudentissimus on 2005-07-03
[QUOTE=khc]You cannot do that. If you really want the command "penggy" to always be executed as root without entering a password, you can setuid it.[/QUOTE]
 How do you do "setuid"?

---

### Post by khc on 2005-07-09
sudo chmod u+s /path/to/binary

Note that this should only be done to a binary executable, not to a shell script.

---

### Post by bdamon on 2005-07-09
Another option would be to modify your sudoers file so your user is not prompted for a password for that script or app

username ALL= NOPASSWD: /pathtoscript/scriptname

---

### Post by Prudentissimus on 2005-07-10
[QUOTE=bdamon]Another option would be to modify your sudoers file so your user is not prompted for a password for that script or app

username ALL= NOPASSWD: /pathtoscript/scriptname[/QUOTE]
 where is the sudoer's file?

---

### Post by bdamon on 2005-07-10
sudo visudo will put into the sudoers file.

---

