---
title: "LightDM will not let me log in."
date: 2012-06-08
forum: Desktop Environments
---

### Post by jspike397 on 2012-06-08
Hello,
I am having a problem with LightDm and Unity.  When I boot up my netbook, I get the lighdm login screen.  Then, when I enter my password and click enter, the Lightdm screen goes away, and comes back with the lightdm screen again.  When I go and log into the guest account, it works fine.  Then, I go to the terminal by clicking CTRL+ALT+F1 and kill lightdm, then type "unity" after I have logged in it gives me this error: 
```
joshn@jntbkprecise:~$ unity
WARNING: no DISPLAY variable set, setting it to :0
pkill:2311 - Operation not permitted
unity-panel-service: no process found
No protocol specified
No protocol specified
compiz (core) - Fatal: Could not open display :0
joshn@jntbkprecise:~$
```

I'm Stuck.  I have no idea if I did anything to break this.  I do not know if compiz is the problem, or if it is Unity or Lightdm.  If somebody could help it would be greatly appreciated.  I would prefer not to have to re-install.  I am using a EEE PC 1005HAB with 2gb of ram, Ubuntu 12.04 and a Intel Atom n270 cpu. Thank you for your time.

Joshua

---

### Post by LaJuan on 2012-06-08
I think the problems is Compiz? Are you running an NVIDIA as your graphics? That could be the issue as well. I'm actually, trying to get to the screen where you login under terminal so I can install the NVIDIA drivers. Their site says I need to install the drivers while x-server is not running and I shut it down but, can't seem to get terminal to pull up.

---

### Post by jspike397 on 2012-06-08
No, I have Intel graphics GMA 950, so it could be that I need their drivers, but I would not know where to get them, if that is the problem. Another problem is that I might need X to install it.  I could probably use the guest account to install it, but the driver probably very unlikely because the guest account works.  Thank you for your quick reply.
Joshua

---

### Post by jspike397 on 2012-06-12
UPDATE:

I have now tried Unity 2D and Gnome Classic.  All do not work.  Guest session still works, which I am using to type this thread, but I have no idea what to do.  I'm thinking its a problem with a compiz setting with my user, but I do not know how to reset that or anything like that.  I'm thinking maybe its crashing every time I try to log in and returning an error code that will put me back to the LightDm login screen.  I do not really know.  Thanks to anyone who tries to help.

Jspike397

---

### Post by O2Blevel on 2012-06-12
You may have a variation of the problem described here in post #3.
[http://ubuntuforums.org/showthread.php?t=1968155]("http://ubuntuforums.org/showthread.php?t=1968155")

At any rate it may give some insight as to what might work.

---

### Post by zombifier25 on 2012-06-12
I had the same problem, and it was solved by changing the ownership of the file .Xauthority in my home folder. Press Ctrl - Alt - F1, login from the trminal and type this command:
```
sudo chown yourusername:yourusername .Xauthority
```

---

### Post by jspike397 on 2012-06-15
Thank you for your help.  Zombifier's thread worked.  I am logged back into my user and everything works.  Thank you for your help.

Jspike397

---

### Post by d4m1r on 2013-02-28
> **zombifier25 said:**
> I had the same problem, and it was solved by changing the ownership of the file .Xauthority in my home folder. Press Ctrl - Alt - F1, login from the trminal and type this command:
```
sudo chown yourusername:yourusername .Xauthority
```

Thanks for this! Was having the same problem on my Ubuntu desktop (12.04 LTS x64). Basically, I'd login with the correct username/password through the LightDM login page and it switch to a black screen for a second, and then just kick me back to the LightDM login screen....This fixed my problem however without having to reinstall anything :)

On a side note, .Xauthority will NOT show up if you do a ls within your users home directly, but will if you do a ls -al (if you want to make sure it's there at all before you chown it).

---

### Post by bogan on 2013-03-01
Hi!, **LaJuan**,

To get to aTTY console or text terminal, press: 'Ctrl+Alt+F1', or from the grub menu edit the Linux /boot line - highlight & press 'e' - adding 'single' [ no quotes] where it says: " ro quiet splash ", and press 'Ctrl+x' to boot.

The first needs you to login with your username and password, the latter takes you directly to a root prompt without needing to log in - so be careful, you will not need 'sudo'.

To stop the X server enter:```
 sudo service lightdm stop
```If you need more instructions to install the nvidia driver, just ask, or refer to:

[http://ubuntuforums.org/showthread.php?t=1743535&page=5](http://ubuntuforums.org/showthread.php?t=1743535&page=5) Post # 1126

Chao!,** bogan.**

---

### Post by lptr on 2013-09-18
Helped here, too. Thanks!

Just for interest:
Do you have an idea what does cause this user change?

---

