---
title: "Lubuntu desktop being funky after upgrade"
date: 2014-10-06
forum: Desktop Environments
---

### Post by sydneyjd on 2014-10-06
Hi all. 
I installed lubuntu a month ago,and after an upgrade a couple weeks ago, i ended up with my desktop looking like the addon pic. [ATTACH=CONFIG]256985[/ATTACH]

I can rightclick and open a terminal (openbox style menu).

What can i do to fix this?

 Also, the lubuntu-netbook option works fine.

Thanks,

Sydney

---

### Post by Rex Bouwense on 2014-10-07
It looks like you have lost your LXPanel.  Can you relaunch your LXPanel by entering
```
lxpanelctl restart
```
in the terminal.  
Ctr+Alt+t  will open your LXTerminal or at least it should.
Alternatively, can you reboot and log in as a guest?  Is your LXPanel there?  Have to tried to boot into recovery mode?  Just a few ideas to start.

Have you minimized your panel?  Move your cursor to the bottom of the screen.  If the LXPanel is minimized it will suddenly appear.  Another thing to check.

---

### Post by sydneyjd on 2014-10-09
Ok,so i tried what you said,and nothing happened. I was able to log in as guest,and it looked/worked fine. No,the lxpanel is not hidden. ;)
Thanks!!

---

### Post by vasa1 on 2014-10-09
What happens when you right-click in the lower band on your screen which seems colored slightly differently?

What do you see when you right-click there? What choices appear?

What do you see when you right-click in the center? What choices appear?

What do you see when you right-click near the top of the screen? What choices appear?

Because you can open a terminal, what do you see when you run 
**pgrep lxpanel** 
**pgrep lxsession**
**env | grep XDG_CURRENT_DESKTOP** and
**echo $DESKTOP_SESSION** ?

?

---

### Post by sydneyjd on 2014-10-09
Ok, thanks for all your attention,but i broke the lubuntu desktop somehow. I think i wil just use somthing else like xfce or enlightenment. 
Sorry for wasting your time :(

---

### Post by vasa1 on 2014-10-09
No issue. Use what you like :)

Another thing to consider is this: rename ~/.config to ~/.config-old and then logout and log in again. If that "fixes" things, just copy back folders one at time from ~/.config-old ~/.config till you break stuff again. Then undo that particular copy because contents of that folder are responsible.

Edit: the idea to rename ~/.config came from someone else @ UF in the last couple of days. I tried to find that post but couldn't.

---

### Post by sydneyjd on 2014-10-09
Ok, thanks :) That fixed it. :)

---

### Post by vasa1 on 2014-10-09
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by kaspin2 on 2014-10-24
I recently installed the alternative version of Lubuntu 14.04 on my old ASUS EEE700 (4GB SSD and 1GB RAM). Having forced pae at the start of the installation everything went well, except that it automatically put in a swap file of over 1GB, which did not leave enough room for the first update. This was easily overcome with gparted, and everything worked really well. I decided to add LibreOffice write and calc, and VLC player. I also moved the panel from the bottom to the top of the screen.

 On the next reboot, the normal login window appeared with my user name indicated and asking for my password. I subsequently got the Lubuntu desktop background, but no panel. Right clicking, or ctrl+alt+t produced nothing.  However, Ctrl+alt+F6 brought up a terminal inviting me to login. I did this, and, following advice on a forum from someone who had apparently solved a similar problem to the above, I deleted ./config/lxsession/Lubuntu/desktop.conf  
 Still the same problem on rebooting.
 Luckily I turned to this forum and tried Rex Bouwense's suggestion: lxpanelctl restart 
I then rebooted and everything was there, plus an additional &#8220;panel&#8221; with options of Internet, Work, Learn, Play, Preferences. Don't know how it got there but it looks useful.
 So, a big thank you to Rex Bouwens from me.
 Kaspin

---

