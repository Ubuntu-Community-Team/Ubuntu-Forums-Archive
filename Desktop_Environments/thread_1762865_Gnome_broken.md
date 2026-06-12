---
title: "Gnome broken"
date: 2011-05-19
forum: Desktop Environments
---

### Post by guna_pmk on 2011-05-19
Hello All,

Though I am Linux user for sometime I only recently started using Ubuntu (starting from 10.10). So far so good. Last week I was suggested by the update manager to upgrade to 11.04. I went for it. After the upgrade it worked nicely; I was so happy. It provided Mac like menus and stuffs. An auto hiding side bar. With overwhelming interest, I started paying around with it. 

In that process, I turned on the Compiz cube. It warned me that it was going to disable the compiz wall; I confirmed that. And that was it. I lost everything. 

Now no keyboard shortcuts (like Ctrl+f4, Alt+f4, Alt+f1, Alt+f2, Alt+tab) work. No Window borders; no task bar. There was a blank desktop. All I could do was right click and get a context menu. With that I created a shortcut to run gnome-terminal, started the terminal, typed google-chrome and then typing this in the forum. As I said earlier, I do not have any short cut keys. I f I want to go back to the terminal, I have to close this browser. I can't move/resize windows.

Can anybody help me getting back to the Ubuntu 11.04 glory? 

Please let me know if you need more information in this regard.

Thanks

---

### Post by 3Miro on 2011-05-19
Good that you can get to a terminal. The new Unity interface (the Mac like thing) is still not fully compatible with the compiz cube. You will have to disable the cube and re-enable the wall.

If you have not yet installed CompizConfig Settings Manager:
```
gksudo synaptic
```
and then install the compizconfig package.

Once you have CCSM installed, then start it with:
```
ccsm
```

I think there is a way to get the cube working, but it is not trivial. Here is a link that I found, but I have not tested it.

[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

---

### Post by Mr. Shannon on 2011-05-19
Try typing in
```
gnome-control-center
```
this will open the control center, you may be able to access Compiz through there and change it back to the Compiz wall.

As for why changing to the Compiz cube did not work I have no idea - I don't use Compiz or Unity.

---

### Post by Copper Bezel on 2011-05-19
Cube can be enabled, but takes some tweaking. Google it if you're curious. 

Follow the link in my sig to reset Compiz and Unity to default settings and get back to a functioning desktop. = )

---

### Post by guna_pmk on 2011-05-20
Thanks very much guys for your quick replies. I now managed to get the ccsm. I disabled the compiz cube and enabled the wall. BUT there is no change. I even rebooted after trying these. No change. 

Any ideas. Please let me know if you need more information in this regard.

Thanks

---

### Post by 3Miro on 2011-05-20
Try adding a new user to see things are broken in the local user settings or for the entire system.

From the terminal, run:
```
users-admin
```
and then add a new user.

Logout (with the logout command) and then try to login with the new user to see if things are working.

---

### Post by Mr. Shannon on 2011-05-20
You might look at this thread: [http://ubuntuforums.org/showthread.php?t=1763005](http://ubuntuforums.org/showthread.php?t=1763005) the solution in post #7 worked for what looks like the same or at least a similar problem.

---

### Post by guna_pmk on 2011-05-21
Guys thanks very much for your suggestions. Its now fixed. I believe the following procedures fixed the problem:

1. Enabling wall through 'ccsm' from the command line.
2. Issuing unity --reset

Thanks again chaps.

---

