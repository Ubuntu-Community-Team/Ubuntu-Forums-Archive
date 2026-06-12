---
title: "SSH X11VNC login screen problems"
date: 2009-02-19
forum: General Help
---

### Post by excbuntu on 2009-02-19
far-pc has the ssh and x11vnc servers.
near-pc is what i'm using to log into far-pc.

i'm trying to login to far-pc from near-pc via ssh and x11vnc server. i am able to remotely view far-pcs login screen and enter the login/pw, but after pressing enter, it seems that far-pc attempts to login, then shuts down x11vnc server, and then continues to to display the login screen. (these are actually computers on my network so i actually see what's going on).

this is after i followed the instructions in the  "Connecting to your login screen" ubuntu vnc documentation [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC).

my step by step process is as follows:

on far-pc i
1. edited /etc/gdm/gdm.conf-custom by adding "KillInitClients=false" under the [daemon] heading.
2. restarted gdm to pick up the change with "sudo /etc/init.d/gdm restart". this command attempted to restart the pc, but it hung on "checking battery state" so i did an alt-ctrl-del to restart that way. **maybe this is the problem?**
3. i added to $PATH an executable script named "vnc" containing the following:
```
sudo x11vnc -safer -noxdamage -scale 1/1 -localhost -once -auth /var/lib/gdm/:0.Xauth -display :0
```
4. restart far-pc so it displayed the ubuntu login screen.

on near-pc i
1. ran "ssh -L 5900:localhost:5900 far-pc@192.168.1.100" and logged into far-pc.
2. ran far-pc's newly created vnc script described above.
3. opened my vnc client and connected to localhost. afterwards, near-pc is able to show far-pcs ubuntu login screen. entering the the login/pw on far-pc from near-pc flickers far-pc's display and closes far-pc's x11vnc server. far-pc would continue to display the ubuntu login screen.

*sigh* please help.. thanks guys.

---

### Post by krunge on 2009-02-19
Please look through this entire thread: [http://ubuntuforums.org/showthread.php?t=965695&highlight=x11vnc+intrepid](http://ubuntuforums.org/showthread.php?t=965695&highlight=x11vnc+intrepid)

The relavant stuff involves the discussion of the X server crashes (not at the beginning of the thread.)

---

### Post by excbuntu on 2009-02-19
;) thanks again!

---

