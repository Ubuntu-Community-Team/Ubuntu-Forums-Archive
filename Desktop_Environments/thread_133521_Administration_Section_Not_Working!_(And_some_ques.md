---
title: "Administration Section Not Working! (And some questions)"
date: 2006-02-20
forum: Desktop Environments
---

### Post by Poku on 2006-02-20
Ok, I just installed the pre-compiled version of Ubuntu 5.10, and I love it! But, there are a few problems:

1)*Whenever I enter console mode, it asks for my username, wich I enter, then it asks for my password, but none of the keys work! I am then forced to press Ctrl+Alt+F7 to get back to GNOME mode.*Solved, thank you Carlosqueso!

2) The Users and Groups administration, Network settings, and several other areas of Administration won't start. When I try to launch one it appears to be loading (appears in the bar at the bottom, Example: "Starting Networking") then, it just dissapears.

3) When I go to System Settings ---> Network Settings ---> Configure (next to network device) the new window freezes, and I have to use the force quit option.

Thank you for your help!
~~~Poku

---

### Post by carlosqueso on 2006-02-20
1)Actually, the keys are working, linux just doesn't show your password so no one looking over your shoulder can figure out how long it is.

2)Did you do an expert install with a root password?  This is probably where the problem is.  Try launching them from a terminal with sudo and the name to verify that they work.  Also make sure you are able to use sudo by using the command ```
sudo visudo
```

3)sorry, I got nothin' on this one.

---

### Post by Poku on 2006-02-20
[QUOTE=carlosqueso]1)Actually, the keys are working, linux just doesn't show your password so no one looking over your shoulder can figure out how long it is.

2)Did you do an expert install with a root password?  This is probably where the problem is.  Try launching them from a terminal with sudo and the name to verify that they work.  Also make sure you are able to use sudo by using the command ```
sudo visudo
```

3)sorry, I got nothin' on this one.[/QUOTE]

1) Awesome, thank you!

2) I think I just did a regular install, no idea what the rest of that means :neutral:

3)No problem, thanks for your help!

~~Poku

---

### Post by carlosqueso on 2006-02-20
Alright....I'm gonna try to rule some things out.  First let's see if sudo works.  Open up a terminal by going to Applications->Accessories->Terminal and type ```
sudo ls
```  this will ask you for your password.  When it does, enter your user's pasword (note you won't be able to see any response on the screen while entering your password, this is normal).  If it doesn't work it'll just kick you back to a command prompt.  If it does work, you'll see a list of everything in your home directory.  NOTE: you don't need sudo to use ls, but I'm just trying to see if it works in a way which won't damage your system.  Post back your results.

---

### Post by Poku on 2006-02-20
Ok, I did that, and it said

"Unable to get *Something* for *HOSTNAME* via *FUNCTIONNAME*"

---

### Post by jerrykenny on 2006-02-20
try 


[COLOR="Red"]sudo -l[/COLOR]

(l for list) this is what you should get

jerr@jerryspc:~$ sudo -l
User jerr may run the following commands on this host:
    (ALL) ALL
jerr@jerryspc:~$


Failing this you may not be in the sudoers group . . . .[COLOR="Red"][/COLOR]

---

