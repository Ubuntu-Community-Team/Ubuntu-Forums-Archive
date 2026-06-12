---
title: "Trying an Xfce-session has ruined my Xubuntu-session!"
date: 2011-05-20
forum: Desktop Environments
---

### Post by Dáire Fagan on 2011-05-20
On logging in I decided to try try an Xfce-session instead of my usual Xubuntu-session.

When I opened up Firefox in Xfce-session I was asked if  I would like to make it my default browser, which I thought strange as it was already my default browser in Xubuntu-session and I had thought Xfce-sessions would use the same .mozilla dir and settings etc.

I then logged back into Xubuntu-session, and everything now looks a bit blurry, text looks different, Firefox asked me again if I wanted it to be my default browser although it still has my bookmarks etc, I have 4 virtual workspaces instead of 2, the icons for all different types of files are different, and my windows look different than I left them: the title-bar looks different than the default, and I didn't have an option to minimize the window to the title-bar etc. please see screenshot.

[IMG]http://oi56.tinypic.com/w0hu1z.jpg[/IMG]

If all these things have changed, more possibly has. I didn't even go near any options in the Xfce-session. What happened, and how can I fix it without a fresh install of Xubuntu 11.04?

Fixed by logging out, ctrl+alt+f6 to bring up a TTY, logged in and executed:

```
sudo rm -rf .config/xfce 

sudo shutdown -g now
```

When I booted back up and logged in everything Xfce was back to Xubuntu 11.04 defaults.

*I think you can probably just log back in but I chose to reboot.

---

### Post by Janiporo on 2012-07-24
Exactly same happened to me after xfce-session visit.

Here is Xubuntu 12.04 "screenshot" (upper)
And Ubuntu 10.04 "Screenshot" (lower)

[IMG]http://kuvaton.com/k/Ym7B.jpg[/IMG]

Going to try your fix :shock:

---

### Post by Janiporo on 2012-07-24
Did not solve my problem :(

Started a new thread --> [http://ubuntuforums.org/showthread.php?p=12126320#post12126320](http://ubuntuforums.org/showthread.php?p=12126320#post12126320)

---

### Post by coffeecat on 2012-07-24
Old thread closed.

---

