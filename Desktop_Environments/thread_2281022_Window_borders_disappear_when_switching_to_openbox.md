---
title: "Window borders disappear when switching to openbox"
date: 2015-06-03
forum: Desktop Environments
---

### Post by marinecomm on 2015-06-03
I installed Xubuntu 14.04 on an older laptop that I have. I tried using compiz but every time I ran compiz it would lock up the computer where even REISUB wouldn't restart the computer. I tried openbox but every time I run openbox the window borders disappear, there is no right-click menu on links in the web browser, no minimize/maximize/exit buttons, and it's hard to navigate around the computer because the windows that are there don't react like they should. Has anyone else experienced this with openbox?

---

### Post by vasa1 on 2015-06-03
> **marinecomm said:**
> I installed Xubuntu 14.04 on an older laptop that I have. I tried using compiz but every time I ran compiz it would lock up the computer where even REISUB wouldn't restart the computer. I tried openbox but every time I run openbox the window borders disappear, there is no right-click menu on links in the web browser, no minimize/maximize/exit buttons, and it's hard to navigate around the computer because the windows that are there don't react like they should. Has anyone else experienced this with openbox?No. I use Lubuntu 14.04 which has Openbox as the default window manager and haven't had any such problems.

1: the window borders disappear
What happens when you press alt+spacebar together?

2: no right-click menu on links in the web browser
I'm not sure this has to do with Openbox. Which browser, btw?

3: no minimize/maximize/exit buttons
Again, what happens when you press alt+spacebar together?

4: windows that are there don't react like they should
For starters, do you have a ~/.config/openbox folder? What is in it?

---

### Post by marinecomm on 2015-06-03
1. Pressing alt+space does nothing

2. Browser I am using is Firefox. When I'm not trying to use openbox I get the usual menu when I right-click on a link on a webpage. When I am trying to use openbox the menu does not appear

3. Pressing alt+space does nothing

4. Yes, i have a ~/.config/openbox folder and the only file in it is one named **rc.xml**

---

### Post by vasa1 on 2015-06-03
> **marinecomm said:**
> ...
4. Yes, i have a ~/.config/openbox folder and the only file in it is one named **rc.xml**
Could you upload that to pastebin and share the link here?

Alt+spacebar is pretty common across a variety of linux flavors. I'm surprised it does nothing for you.

Your openbox folder should also have a "menu.xml" file and your theme folder, whichever that is, should have an openbox subfolder with a .themerc file.

Do you remember how you installed openbox? How do you start openbox?

---

### Post by marinecomm on 2015-06-03
I installed openbox through git

[http://pastebin.com/n4Z5BV0j]("http://pastebin.com/n4Z5BV0j")

---

### Post by vasa1 on 2015-06-03
> **marinecomm said:**
> I installed openbox through git

[http://pastebin.com/n4Z5BV0j]("http://pastebin.com/n4Z5BV0j")

I get YOU ARE NOT AUTHORIZED TO VIEW THIS WEBPAGE AS PER THE INSTRUCTION FROM DOT. PLEASE CONTACT SYSTEM ADMINISTRATOR.

Why did you not install via the software center or via apt-get? How do you know you've got all the necessary dependencies?

---

### Post by marinecomm on 2015-06-03
I didn't think to check the repositories to see if it was in there. There was a README file that came with the install files that listed the dependencies.

---

### Post by vasa1 on 2015-06-04
Okay, I could now see your rc.xml. When I used it instead of my own, I ran **openbox --reconfigure** to check it. I'm seeing quite a few parsing errors. Fix one, another pops up :(

---

### Post by Melodie on 2015-07-15
Hello,

When you install Openbox from the repositories, it comes with the necessary depends and configuration files. Them files are located in /etc/xdg/openbox from where you can copy them to your /home/user/.config/openbox directory and there, tweak them. Once copied, if you ruin them while editing the xml files, you can still copy again from /etc/xdg/openbox to restore them to the default, and try again. In the depends, you get the themes (window borders to choose from) and you get obconf which eases the configuration process. It writes to the rc.xml file in a safe way.

---

