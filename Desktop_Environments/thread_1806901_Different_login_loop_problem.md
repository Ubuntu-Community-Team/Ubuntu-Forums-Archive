---
title: "Different login loop problem"
date: 2011-07-18
forum: Desktop Environments
---

### Post by ubuntwho1 on 2011-07-18
Hello all,

I'm a relatively new user to ubuntu, or at least regularly using the shell, and I recently did something accidentally and now my computer is at a loop on the login screen.  My password works and then it goes blank and back to the login screen.  I know that there were other problems with this and there were suggestions to delete .ICEauthority.  This isn't the problem for me.  I looked at xsession-errors and the only error I have is 

     xhost: unable to open display "localhost:0.0"

I also already tried 

     sudo dpkg-reconfigure XServer-xorg
 
as a suggestion from a previous thread, but that also didn't work.  I'm really lost.  I can still log in using Ctrl-Alt-F2, something's just messed up with the GUI.  

Thanks for all your help,

Luke

---

### Post by wildmanne39 on 2011-07-18
Hi, see if this helps.
```
sudo apt-get install --reinstall gdm
```

---

### Post by ubuntwho1 on 2011-07-19
Ok.  Now I can't figure out how to connect to the internet through terminal, so it won't grab the packages.  I've done ```
iwlist wlan0 scan
``` to find the different networks, but because there's so many I can't see the one I actually know the key for.  Is there a way to control the output?  And is this followed by 
```
 iwconfig wlano essid <ESSID> 
iwconfig wlan0 key <key>
ifconfig wlan0 up 
```the proper way to gain access from there?  

Thanks,
Luke

---

### Post by wildmanne39 on 2011-07-19
Hi, reboot the system if you are using 11.04 keep pressing the shift key until you see the grub menu, then choose recovery at the next screen choose root with network and you will have internet access unless there is another problem.

---

### Post by ubuntwho1 on 2011-07-20
Hello,

I get > E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing? along with many > Could not resolve '<url>''.  Then when I do try and run an apt update, I get many > W: Failed to fetch http://<url>.  Any help?  Or should I just reinstall ubuntu?

Thanks.

---

### Post by wildmanne39 on 2011-07-20
Hi, were you able to get some packages downloaded?
This time go into recovery and click fix broken packages and see what that does.

---

### Post by cyfrede on 2011-07-23
Hello,

It seems I have a similar problem as you after the last update by the update manager and I didn't pay attention on what it was supposed to update I just clicked like this.
[I] I tried so many things.
My problem is that I don't know how to get a list of changes made by the Update Manager.
So no clue now.

If somebody have an idea...

Thx

Fred
[/I]

---

### Post by ubuntwho1 on 2011-07-26
Morning,

No.  Unfortunately, none of the packages were downloaded.  It just started up and then failed.  I think something may be wrong with my network card settings as well, but that's for a different forum.  Thanks for the help.  I'll use your suggestions once I figure out the network.  

-Luke

---

