---
title: "Google Chrome is not recognized by Preferred Applications"
date: 2012-07-27
forum: Desktop Environments
---

### Post by jonatman on 2012-07-27
I'm a ubuntu user trying to setup some old computers with xubuntu for my mom, I'm having trouble setting Google Chrome as preferred web browser with Preferred Applications in xfce 4.8 and 4.10,
I found that every time Google Chrome trys to set itself to default, two things will happen:
1. ~/.config/xfce4/helpers.rc will be modified by changing the line WebBrowser=whatever to WebBrowser=google-chrome
2. ~/.local/share/xfce4/helpers/google-chrome.desktop will be created if it is not already exist

The problem is the file google-chrome.desktop, it seems the file is copied from /opt/google/chrome/ or /usr/share/applications, and then added the following section to the end of the file.

```
Type=X XFCE-Helper
X-XFCE-Category=WebBrowser
X-XFCE-Commands=/opt/google/chrome/google-chrome
X-XFCE-CommandsWithParameter=/opt/google/chrome/google-chrome "%s"
/opt/google/chrome/google-chrome
/opt/google/chrome/google-chrome --incognito
```

While there are three sections in the original google-chrome.desktop (the ones in /opt/google/chrome and /usr/share/applications),
[Desktop Entry], [NewWindow Shortcut Group] (for unity) and [NewIncognito Shortcut Group] (also for unity), the section mentioned is added under [NewIncognito Shortcut Group], and not [Desktop Entry].
I think this causes Preferred Applications not to recognized as a valid desktop file, which is why Google Chrome is not on the Preferred Applications Web Browser list.

Onces I've move the section back to [Destop Entry], everything works, but since I'm dealing with multi-user computers, I've to do the same thing everytime I create a new user on the computer.

Is there any long term fix? and if this is a bug, where should I report it? xfce, xubuntu or google??

---

### Post by albandy on 2012-07-27
> **jonatman said:**
> 
[...]
Onces I've move the section back to [Destop Entry], everything works, but since I'm dealing with multi-user computers, I've to do the same thing everytime I create a new user on the computer.

Is there any long term fix? and if this is a bug, where should I report it? xfce, xubuntu or google??

When you create a new user, all the contents of /etc/skel are copied to the user home.

Simply add the configuration files to /etc/skel and every time you create a new user this files will be copied to the user home.

---

### Post by kc1di on 2012-07-27
Also in addition to what has already been said.  I think you'd find that if you used chromium-browser, which is in the repository you'd find you wouldn't have this problem. It's basically the same as Chrome and is maintained by ubuntu devs. 

Just a thought.

---

### Post by jonatman on 2012-07-27
> **kc1di said:**
> Also in addition to what has already been said.  I think you'd find that if you used chromium-browser, which is in the repository you'd find you wouldn't have this problem. It's basically the same as Chrome and is maintained by ubuntu devs. 

Just a thought.

I'm using chrome because some of the users has to use flash player.

---

### Post by jonatman on 2012-07-27
> **albandy said:**
> When you create a new user, all the contents of /etc/skel are copied to the user home.

Simply add the configuration files to /etc/skel and every time you create a new user this files will be copied to the user home.

I guess I can copy the desktop file and helper.rc into /etc/skel, Thanks.

---

### Post by kc1di on 2012-07-27
> **jonatman said:**
> I'm using chrome because some of the users has to use flash player.
The flash plugin works fine in chromium just install xubuntu-restricted-addons and xubuntu-restricted-extras. 

works great here :)

---

### Post by jonatman on 2012-07-27
> **kc1di said:**
> The flash plugin works fine in chromium just install xubuntu-restricted-addons and xubuntu-restricted-extras. 

works great here :)

Good to know, I'll give it a try, thanks.

---

### Post by fmcgorenc on 2012-11-30
I have the solution.

1. open ~/.local/share/xfce4/helpers/google-chrome.desktop with a text editor

2. delete this line "X-Ayatana-Desktop-Shortcuts=NewWindow;NewIncognito" and sections "[NewWindow Shortcut Group]" and "[NewIncognito Shortcut Group]" including the lines that say "TargetEnvironment=Unity".

Now save and the system setting should properly detect chrome browser as "Google Chrome".

---

