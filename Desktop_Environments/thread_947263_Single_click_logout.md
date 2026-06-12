---
title: "Single click logout"
date: 2008-10-14
forum: Desktop Environments
---

### Post by ypout on 2008-10-14
Is there anyway to logout from a GUI session with a single click of an Icon. i.e I don't want to click the shutdown button and then click logout - I just want to click an icon and have the session logged out.

Any ideas?

---

### Post by Pelham123 on 2008-10-14
Well...

I guess if I was doing it I would create a Desktop launcher with the command

```
sudo shutdown -h now
```

But then you would still have to enter sudo password. but you could get around this by editing the sudoers file, so the command 'shutdown' was a non-sudo command for a group or user...

Take a look at the 'man' pages for 'shutdown' and 'sudoers' although google might be a better friend for sudoers. 

NB: Please be careful and make a backup of the sudoers file before editing please...

---

### Post by JaspSoft on 2008-10-14
My Solution:

```
echo gnome-session-save --logout > ~/Desktop/LOGOUT.sh
chmod +x ~/Desktop/LOGOUT.sh
```

Then drag the LOGOUT.sh file from your desktop to the panel... and call it 'logout'.

---

### Post by forger on 2008-10-14
> **ypout said:**
> Is there anyway to logout from a GUI session with a single click of an Icon. i.e I don't want to click the shutdown button and then click logout - I just want to click an icon and have the session logged out.

Any ideas?

You can add an application launcher in desktop or in the panel, I suggest the gnome panel since you want a single-click execution of the icon.
Right-click on the panel > add to panel

You have a panel applet "Logout" if you're interested, but it still asks you whether you want to log out or switch user :) However, it logs you out automatically in 60 seconds if you don't reply with logout or switch user

Similar with the shutdown dialog, it shuts down automatically in 60 seconds, you can add a gnome panel application launcher with this:
```
gnome-session-save --shutdown-dialog
```

---

### Post by tstiv1 on 2008-10-14
topic:  a good handbook of library ejournal list  with stanford jhu university!!
content : Dear friends:  Do you know how to find out database quickly without entering so many university libraries and search the web again and again? Do you know what databases does a library have? You will recommend google search engine, but does it provide you enough and prcise information? No!So we made up this handbook for you guys as an index of library resource menu, for you to get to any database or journal without entering lots of university librares.

here is the handbook!  
You can download the hand book here
[http://www.zshare.net/download/200017001447007d/](http://www.zshare.net/download/200017001447007d/)
or  link:  
[http://rapidshare.com/files/151117220/passfans.chm.html](http://rapidshare.com/files/151117220/passfans.chm.html)

you can go to  [http://www.passfans.com/forum](http://www.passfans.com/forum) userid=your userid get more information

---

### Post by ypout on 2008-10-17
Thanks for your suggestions I'll have a little play and see what works best...

I'll let you know.

Cheers

Update - Here what I've done...

Create a Gnome panel Launcher with the following command

```
gnome-session-save --kill --silent
```

This seems to do what I wanted.... Can anyone see any issues with this solution?

---

