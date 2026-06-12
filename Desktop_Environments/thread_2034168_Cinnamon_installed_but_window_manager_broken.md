---
title: "Cinnamon installed but window manager broken"
date: 2012-07-28
forum: Desktop Environments
---

### Post by uzumakifahim on 2012-07-28
Hi everybody,
I have installed Cinnamon on my Ubuntu 12.04. I have got all the necessary .deb files from here 

[https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable/+packages]("https://launchpad.net/%7Egwendal-lebihan-dev/+archive/cinnamon-stable/+packages")

Actually, I wanted to install Cinnamon desktop by installing one by one .deb packages for a specific reason. Whatever, I have successfully installed Cinnamon in that way, but the problem is when I am opening a new window in Cinnamon, it is opening with a very old fashioned theme (Close, minimize and maximize buttons). It's not with the default Cinnamon theme. I have tried by changing the theme, theme has been changed successfully, but the buttons is looking same. 

I don't know why this is happening. Please help anyone with this issue. Sorry for poor English. Thanks in advance to everyone.

---

### Post by kurt18947 on 2012-07-28
> **uzumakifahim said:**
> Hi everybody,
I have installed Cinnamon on my Ubuntu 12.04. I have got all the necessary .deb files from here 

[https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable/+packages]("https://launchpad.net/%7Egwendal-lebihan-dev/+archive/cinnamon-stable/+packages")

Actually, I wanted to install Cinnamon desktop by installing one by one .deb packages for a specific reason. Whatever, I have successfully installed Cinnamon in that way, but the problem is when I am opening a new window in Cinnamon, it is opening with a very old fashioned theme (Close, minimize and maximize buttons). It's not with the default Cinnamon theme. I have tried by changing the theme, theme has been changed successfully, but the buttons is looking same. 

I don't know why this is happening. Please help anyone with this issue. Sorry for poor English. Thanks in advance to everyone.

I am far from an expert.  I installed Cinnamon but did not install muffin. My logic was that muffin and compiz seem to perform similar functions.  Compiz is pretty integral to Ubuntu AFAIK and I thought they might not like one another.  The little bit I've used Cinnamon without muffin seems okay.

---

### Post by uzumakifahim on 2012-07-28
That's good to hear. But as  far as I know muffin is one of the dependencies of Cinnamon. How could you install Cinnamon without muffin? Please share the procedure here.

Moreover, do you understand why I am facing this problem (mentioned above)? If you can, please give me a solution.

Thanks.

---

### Post by kurt18947 on 2012-07-28
> **uzumakifahim said:**
> That's good to hear. But as  far as I know muffin is one of the dependencies of Cinnamon. How could you install Cinnamon without muffin? Please share the procedure here.

Moreover, do you understand why I am facing this problem (mentioned above)? If you can, please give me a solution.

Thanks.

I don't recall exactly how I installed Cinnamon.  I used the gwendal-lebihan ppa and I recall being able to choose to install muffin or not.  Here is what I have when I search for muffin in Synaptic:

Installed:

[LIST]
[*]muffin-common
[*]gir1.2-muffin-3.0
[*]libmuffin0
[/LIST]
not installed:

[LIST]
[*]libmuffin-dev
[*]muffin
[/LIST]
so some muffin components are installed, but not all.




As far as the buttons, I didn't do anything special.  I believe Cinnamon sits on top of Gnome sort of like Unity.  I installed gnome-shell before Cinnamon and used Gnome-shell's 'advanced settings' applet to change the shell to display all 3 buttons.  I also set the following in gnome -shell:


cursor theme:   Adwaita
Icon theme:       Tango
GTK+ theme:     Adwaita


I hope this is of some help to you.

---

### Post by rewyllys on 2012-07-28
You need to open the "Cinnamon Settings" window, and then click on the Window icon.  When you do this, you will see a new window, entitled "Cinnamon Settings - Windows".  It includes a place for you to choose what "Left side title bar buttons" you want, and a place for you to choose what "Right side title bar buttons" you want.  Make your choices.

Note that after making your choices, you will need to log out and then log back in, in order to restart Cinnamon.

---

### Post by uzumakifahim on 2012-07-29
Thanks kurt18947, for your brief description. May be I need to clear more on this. 

I have a desktop and a netbook. I have installed Cinnamon on my desktop successfully by using ppa, but for my netbook, I wanted to install Cinnamon by collecting all .deb files associated with this. To do that I have collected all the .deb files from

[https://launchpad.net/%7Egwendal-lebihan-dev/+archive/cinnamon-stable/+packages](https://launchpad.net/%7Egwendal-lebihan-dev/+archive/cinnamon-stable/+packages).

Now Cinnamon is installed on my netbook. But it's window manager seems broken. Please check the attached screenshot. It's not an issue with theme.

By the way, Cinnamon on my desktop is working perfectly. When I have searched for muffin in Synaptic. It showing the follwing

**Installed**
1. gir1.2-muffin-3.0
2. libmuffin0
3. muffin
4. muffin-common

**Not Installed**
1. libmuffin-dev

Problem is just with my netbook. I have no problem with ppa install, but I have problem with dpkg install. Hope this explanation will help everyone to understand my problem easily. Waiting for help. Thanks to all.

---

### Post by kurt18947 on 2012-07-29
> **uzumakifahim said:**
> Thanks kurt18947, for your brief description. May be I need to clear more on this. 

I have a desktop and a netbook. I have installed Cinnamon on my desktop successfully by using ppa, but for my netbook, I wanted to install Cinnamon by collecting all .deb files associated with this. To do that I have collected all the .deb files from

[https://launchpad.net/%7Egwendal-lebihan-dev/+archive/cinnamon-stable/+packages]("https://launchpad.net/%7Egwendal-lebihan-dev/+archive/cinnamon-stable/+packages").

Now Cinnamon is installed on my netbook. But it's window manager seems broken. Please check the attached screenshot. It's not an issue with theme.

By the way, Cinnamon on my desktop is working perfectly. When I have searched for muffin in Synaptic. It showing the follwing

**Installed**
1. gir1.2-muffin-3.0
2. libmuffin0
3. muffin
4. muffin-common

**Not Installed**
1. libmuffin-dev

Problem is just with my netbook. I have no problem with ppa install, but I have problem with dpkg install. Hope this explanation will help everyone to understand my problem easily. Waiting for help. Thanks to all.

Does your network work with Unity 3D or one of the other more graphically demanding environments?  Netbooks don't have the most capable video systems.  I wonder if that's all or part of your problem?  I've never used a netbook so I'm just guessing.

---

### Post by uzumakifahim on 2012-07-30
Yes, my netbook works perfectly with Unity. Moreover, I have customized an Ubuntu ISO with Cinnamon Desktop, when I have tried that customized Ubuntu on that netbook, Cinnamon Desktop is working perfect. Problem is when I am trying to use the Cinnamon Desktop installed on that netbook, window manager seems broken.

---

### Post by uzumakifahim on 2012-08-02
Is there anybody who can give me any solution for this issue ? :confused:

---

