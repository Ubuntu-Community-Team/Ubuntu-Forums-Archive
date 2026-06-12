---
title: "How to remove Global Menu?"
date: 2012-07-18
forum: Desktop Environments
---

### Post by michaelbr on 2012-07-18
Greetings All:
I just installed Ubuntu 12.04 and the Desktop is quite different from previous version, I'm not used to Global Menu so I tried to remove it, I followed following instructions, but it's still there, what I'm missing?
```
sudo apt-get autoremove appmenu-gtk appmenu-gtk3 appmenu-qt
```
and I also disabled the Global Menu showing by using Unsetting, then selected Windows tab, set Global Menu to OFF, but the Global Menu still is there!!!

---

### Post by Paddy Landau on 2012-07-19
Do you mean that you are trying to uninstall the Dash and Launcher? Ubuntu 12.04 comes with Unity. If you just get rid of it, you'll have nothing.

You have a few options.
[LIST]
[*]At the login screen, choose Gnome Classic. It does not use the Dash and Lancher, but instead the classical menu.
[*]Use one of the different Ubuntu flavours, such as Kubuntu, Xubuntu or Lubuntu. You can install their desktops on top of Ubuntu, and then choose your preference at the login screen.
[*]Use a different distribution, such as Mint.
[/LIST]

---

### Post by michaelbr on 2012-07-19
> **Paddy Landau said:**
> Do you mean that you are trying to uninstall the Dash and Launcher? Ubuntu 12.04 comes with Unity. If you just get rid of it, you'll have nothing.

You have a few options.
[LIST]
[*]At the login screen, choose Gnome Classic. It does not use the Dash and Lancher, but instead the classical menu.
[*]Use one of the different Ubuntu flavours, such as Kubuntu, Xubuntu or Lubuntu. You can install their desktops on top of Ubuntu, and then choose your preference at the login screen.
[*]Use a different distribution, such as Mint.
[/LIST]
Thanks Paddy, no, I'm not trying to remove the Unity, just the Global Menu, the top most menu, where shows the menu options of the apps you're running, according to what I read, you can remove it, but it seems not working. Maybe I should just forget it and use the classical one instead.

Thanks

---

### Post by NikTh on 2012-07-19
> **michaelbr said:**
> Greetings All:
I just installed Ubuntu 12.04 and the Desktop is quite different from previous version, I'm not used to Global Menu so I tried to remove it, I followed following instructions, but it's still there, what I'm missing?
```
sudo apt-get autoremove appmenu-gtk appmenu-gtk3 appmenu-qt
```and I also disabled the Global Menu showing by using Unsetting, then selected Windows tab, set Global Menu to OFF, but the Global Menu still is there!!!
Hi ,
I really don't know what could happen . I had disable successfully global menu with the command you provide.

Maybe CCSM has something to do with your problem ? Check it out. 
Thanks

---

### Post by michaelbr on 2012-07-19
> **NikTh said:**
> Hi ,
I really don't know what could happen . I had disable successfully global menu with the command you provide.

Maybe CCSM has something to do with your problem ? Check it out. 
Thanks
Thanks NikTh, you mean you used the above code then CCSM? Which steps you took to remove it?

Thanks

---

### Post by Paddy Landau on 2012-07-20
> **michaelbr said:**
> ... no, I'm not trying to remove the Unity, just the Global Menu, the top most menu...
Sorry, I completely misunderstood.

May I suggest that you re-install those items:
```
 sudo apt-get install appmenu-gtk appmenu-gtk3 appmenu-qt
```Log out and in again.
Then try using [Unsettings]("http://www.webupd8.org/2012/03/unsettings-tool-to-disable-global-menu.html"). I have not tried it myself, but Web Upd8 is usually reliable.

---

### Post by NikTh on 2012-07-20
> **michaelbr said:**
> Thanks NikTh, you mean you used the above code then CCSM? Which steps you took to remove it?

Thanks

No i didn't use CCSM , i just wonder , if CCSM has something to do with your problem. 
CCSM its just a thought of mine. I am not sure
I just ran the commands you ran. Global menu disappeared after a reboot.

---

### Post by michaelbr on 2012-07-21
> **NikTh said:**
> No i didn't use CCSM , i just wonder , if CCSM has something to do with your problem. 
CCSM its just a thought of mine. I am not sure
I just ran the commands you ran. Global menu disappeared after a reboot.
Thanks NikTh, but I'm not using CCSM. I'll try again without Unsetting and see what happens, you're talking about the global menu, right? The top most menu bar.

Thanks

---

### Post by michaelbr on 2012-07-21
> **Paddy Landau said:**
> Sorry, I completely misunderstood.

May I suggest that you re-install those items:
```
 sudo apt-get install appmenu-gtk appmenu-gtk3 appmenu-qt
```Log out and in again.
Then try using [Unsettings]("http://www.webupd8.org/2012/03/unsettings-tool-to-disable-global-menu.html"). I have not tried it myself, but Web Upd8 is usually reliable.
I'll give it a try and let you know. Sorry, did not work.

---

### Post by bobsan on 2012-07-21
I think it is "sudo apt-get remove indicator-appmenu"

---

### Post by michaelbr on 2012-07-22
> **bobsan said:**
> I think it is "sudo apt-get remove indicator-appmenu"
Nope, still there.

---

### Post by Paddy Landau on 2012-07-22
> **michaelbr said:**
> Sorry, did not work.
Is this a standard installation of 12.04? Are you using Unity (not Unity 2D or Gnome Classic)? I feel a bit lost now, not knowing what you can do next.

---

### Post by vasa1 on 2012-07-22
> **michaelbr said:**
> Greetings All:
I just installed Ubuntu 12.04 and the Desktop is quite different from previous version, I'm not used to Global Menu so I tried to remove it, ...
Why don't you put up (as an attachment) a screenshot of what you see and what you want to get rid of?
Perhaps you could also mention why you want to get rid of it. Maybe someone may have some idea to help make it less objectionable.

---

### Post by bobsan on 2012-07-22
This may be a stupid question, did you reboot or at least log out from Unity? You need rebooting/logging out for the removal to complete.

---

### Post by vasa1 on 2012-07-22
> **bobsan said:**
> This may be a **stupid** question, did you reboot or at least log out from Unity? You need rebooting/logging out for the removal to complete.
Not stupid at all, IMO. 
The thing I don't understand is that some things take effect immediately, others need just a change of theme, yet others need a log out and log in, and the real tough guys need a reboot to take effect.
(Come to think of it, someone explained it nicely, but I didn't keep note :) )

---

### Post by michaelbr on 2012-07-22
> **bobsan said:**
> This may be a stupid question, did you reboot or at least log out from Unity? You need rebooting/logging out for the removal to complete.
Thanks bobsan, yes I did log out, but I did not reboot.

---

### Post by michaelbr on 2012-07-22
> **Paddy Landau said:**
> Is this a standard installation of 12.04? Are you using Unity (not Unity 2D or Gnome Classic)? I feel a bit lost now, not knowing what you can do next.
Thanks Paddy, when I used command ```
echo $DESKTOP_SESSION
```, it showed ubuntu, so I'm assuming it's Unity.

Thanks

---

### Post by michaelbr on 2012-07-22
> **vasa1 said:**
> Why don't you put up (as an attachment) a screenshot of what you see and what you want to get rid of?
Perhaps you could also mention why you want to get rid of it. Maybe someone may have some idea to help make it less objectionable.
Thanks vasa1 for your suggestion, attached is the image of my desktop, I'm trying to get rid of the top most menu, where it showed **Ubuntu Desktop**. The main reason why I'd like to get rid of it is lack of familiarity with it, besides my screen is wide and the space taken by the menu diminish the usable height of my screen. I wouldn't worry too much about it, if it's taking too much time or too much hassle, I'll just get used to it and live with it.

Thanks to every one trying to help and solve this problem.

---

### Post by vasa1 on 2012-07-22
> **michaelbr said:**
> ... I'm trying to get rid of the top most menu, where it showed **Ubuntu Desktop**. The main reason why I'd like to get rid of it is lack of familiarity with it, besides my screen is wide and the space taken by the menu diminish the usable height of my screen. I wouldn't worry too much about it, if it's taking too much time or too much hassle, I'll just get used to it and live with it.

Thanks to every one trying to help and solve this problem.
My feeling is that you won't be able to get rid of that horizontal area because on the right hand side in that same area is the notification area, not shown in the image, which is basic to Unity.

---

### Post by james12 on 2012-07-23
App Menu also known as Global menu can be removed using the following Command : 
[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] autoremove appmenu-gtk appmenu-gtk3 appmenu-qt

Try it hope it will help you.

---

### Post by vasa1 on 2012-07-23
> **james12 said:**
> App Menu also known as Global menu can be removed using the following Command : 
[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] autoremove appmenu-gtk appmenu-gtk3 appmenu-qt

Try it hope it will help you.

From what I understand, it's not just the menu. OP wants which ever program currently running and even the desktop to occupy the full vertical area of the screen. The App Menu or Global menu is **one component** in that area. Merely removing the App Menu or Global Menu does not free up more vertical area because the indicators (on the far right) also occupy part of that horizontal area.

Also, in a lighter vein, OP seems to prefer filling the desktop with icons of stuff deemed to be of use. "Modern developers" seem to **not** like this approach.

---

### Post by michaelbr on 2012-07-23
> **vasa1 said:**
> From what I understand, it's not just the menu. OP wants which ever program currently running and even the desktop to occupy the full vertical area of the screen. The App Menu or Global menu is **one component** in that area. Merely removing the App Menu or Global Menu does not free up more vertical area because the indicators (on the far right) also occupy part of that horizontal area.

Also, in a lighter vein, OP seems to prefer filling the desktop with icons of stuff deemed to be of use. "Modern developers" seem to **not** like this approach.
Thanks vasa1, that's exactly what I'd like to have, I prefer to have apps that I use frequently on the desktop, instead of keeping hovering mouse over menu to look for it. It seems to me that Windows desktop is more efficient, they have task/quick launch/tray etc. all located at the same "bar", which for me is better usage of the spaces/desktop.

---

### Post by vasa1 on 2012-07-23
> **michaelbr said:**
> Thanks vasa1, that's exactly what I'd like to have, I prefer to have apps that I use frequently on the desktop, instead of keeping hovering mouse over menu to look for it. It seems to me that Windows desktop is more efficient, they have task/quick launch/tray etc. all located at the same "bar", which for me is better usage of the spaces/desktop.
One of the problems with Unity is how it's been "sold" to the users. It's such a different way of working that there should have been a whole bunch of videos to illustrate its novelties.

I found one and if you don't mind spending ~27 min of your life, you may find it (Unity) easier to use: [http://www.youtube.com/watch?v=xA9EHaNc2VI](http://www.youtube.com/watch?v=xA9EHaNc2VI)

---

### Post by michaelbr on 2012-07-23
> **vasa1 said:**
> One of the problems with Unity is how it's been "sold" to the users. It's such a different way of working that there should have been a whole bunch of videos to illustrate its novelties.

I found one and if you don't mind spending ~27 min of your life, you may find it (Unity) easier to use: [http://www.youtube.com/watch?v=xA9EHaNc2VI](http://www.youtube.com/watch?v=xA9EHaNc2VI)
Thanks vasa1 for sharing, I'll take a look.

---

### Post by Paddy Landau on 2012-07-23
> **michaelbr said:**
> It seems to me that Windows desktop is more efficient, they have task/quick launch/tray etc. all located at the same "bar", which for me is better usage of the spaces/desktop.
Some people want to get rid of the Global Menu because they prefer to have the menu at the top of the application window (the classical method). I had assumed that that was your reason.

However, your reason is to save vertical space. But that won't work. Removing the Global Menu will do the opposite, and reduce your vertical space. The Global Menu was in fact created as a vertical-space-saver.

You see, when you get rid of the Global Menu, the  menu will instead appear within the application, taking up the space  anyway.

If you want to see how life would be with and without the Global Menu, do the following. (I use Libre Office, as its Global Menu is disabled by default because of some bugs in its implementation.)


[LIST=1]
[*]Put back the items that you removed (if you haven't already done so): ```
sudo apt-get install appmenu-gtk appmenu-gtk3 appmenu-qt
```
[*]Start Libre Office Writer. Note the location of its menu, and how much space is available. Example:
[attach]221669[/attach]
[*]Now close Libre Office completely (including Quickstarter if it is running). Install Global Menu for Libre Office:```
sudo apt-get install lo-menubar
```
[*]Restart Libre Office Writer to exactly the same window size. This time, the menu is now in the top bar. Note how much space more is available. Example:
[attach]221670[/attach]
[/LIST]

You can remove the Libre Office Global Menu again:```
sudo apt-get purge lo-menubar
```

---

### Post by hako1 on 2012-07-26
> **Paddy Landau said:**
> Some people want to get rid of the Global Menu because they prefer to have the menu at the top of the application window (the classical method). 

 ... 

  You can remove the Libre Office Global Menu again:```
sudo apt-get purge lo-menubar
```

Thank you!  This is what I was looking for. 

 Unfortunately, for me, the Global Menu was enabled by default in Libre Office, but quite buggy.
For applications with tabs the global menu is a nice space saver. But, if you have several windows of the same app, it gets more difficult.
In case of Libre Office the only way was to cycle through alt+tab.

---

### Post by vasa1 on 2012-07-26
> **hako1 said:**
> ...
 Unfortunately, for me, the Global Menu was enabled by default in Libre Office, but quite buggy...
Hmmm ... I thought that one had to install lo-menubar to get the Global Menu to kick in for LibreOffice. Maybe things have changed. I'm now using LibreOffice direct and not via a ppa so I don't know the latest situation.

---

### Post by Paddy Landau on 2012-07-26
> **vasa1 said:**
> I thought that one had to install  lo-menubar to get the Global Menu to kick in for LibreOffice.
Yes. It is curious that hako had it installed; it should not have been. Even 12.10 does not have lo-menubar installed by default. I think, hako, you might have installed it without realising or without remembering.

> **hako1 said:**
> ... if you have several windows of the same app, it gets more difficult.Well, that's a personal preference. But I'm glad you have managed to solve it. Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help others.

> **hako1 said:**
> In case of Libre Office the only way was to cycle through alt+tab.
You may find [FONT=Lucida Console]Alt[/FONT]+**[FONT=Lucida Console]`[/FONT]** more useful; it cycles through windows only of the same application. You can also use the Libre Office menu > Window.

---

### Post by monkiki on 2012-11-21
Run this:

$ sudo apt-get remove indicator-appmenu

After that close current session and login again.

---

### Post by Cavsfan on 2013-02-02
> **michaelbr said:**
> Greetings All:
I just installed Ubuntu 12.04 and the Desktop is quite different from previous version, I'm not used to Global Menu so I tried to remove it, I followed following instructions, but it's still there, what I'm missing?
```
sudo apt-get autoremove appmenu-gtk appmenu-gtk3 appmenu-qt
```and I also disabled the Global Menu showing by using Unsetting, then selected Windows tab, set Global Menu to OFF, but the Global Menu still is there!!!

That command still worked beautifully in Ubuntu 13.04. 
I also had to disable Firefox addon Global Menu Bar Integration for it to work.

I just had to logout and back in for it to take effect. :popcorn:

---

