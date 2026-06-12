---
title: "Windows are not in the maximum size"
date: 2014-11-02
forum: Desktop Environments
---

### Post by Nairolf2112 on 2014-11-02
Hi, 

I'm a new user of Lubuntu, and I'm trying it on a small laptop with a small resolution (10 inchs)
My problem is all my windows are smaller than the max length of my computer. I've tried to configure Openbox and its size, but for exemple, all margins are in 0 pixel... I can't have 'negative' margin obviously. 

Can you help me to have an optimized screen size ? My screen is already short, I don't need to have a reduction one more. 
Thanks 

(PS : Please, excuse-me for my english, it's not my native language)

---

### Post by Enigma12 on 2014-11-03
> My problem is all my windows are smaller than the max length of my computer.

First, I am also fairly new to Lubuntu, so I may not be giving you advice that works, but I will try. 

Does your desktop fill the screen? If not, click on the bottom left icon (LXDE?), then Preferences, then Monitor Settings. In the Resolution window, click the triangles to find the resolution that will fill your screen. 

In the program windows, either click the + in the top right to get full screen or put your mouse pointer along one edge or corner to change the pointer to the drag view, hold down the left mouse button and enlarge the window as you wish. 

If these don't work, hope for someone more knowledgeable than me to offer a solution.

---

### Post by JohnnyComeL8ly on 2014-11-05
> **Wayne_Terrebonne said:**
> ...hope for someone more knowledgeable than me to offer a solution.
I wouldn't say I am it, but I think that it would help to have a native screen resolution specification, or at least a little help in the area of which laptop he uses... and the resolution he currently has configured.

---

### Post by Nairolf2112 on 2014-11-05
Hi, 
Thank you for your help. I've tried something before seeing your message. I thought that what I saw in front was a 'panel', so after right cliking, I've deleted this panel. But unfortunately, this action has deleted also my back panel (where I could see my opened application, time, windows-like start menu, battery). 
From some doc, I've read that if I did this : 
```
rm -rf ~/.gconf/apps/nm-applet/
``` 
It will recreate a "default" panel after restart. 

I've also done this : 
```
rm -rf ~/.gnome2/
``` 

After restart, I've a strange comportement. Indeed, at the begenning I can see my panel, but after opening window (Firefox for exemple), it disapears. So, when I want to go back to desktop, I do "Super+D", and after doing "Alt+Tab", I have a "panel" application, and I can see again my panel. 
But, if you have well understood me, it's not the "default" comportement. 

I don't know what stupidity things I've done when I've written these command lines on terminal, but I think it was a ******** to delate ~/.gnome2. Indeed, now, I don't have anymore this repertory... Is it a problem ? 

Thank you :)

PS : I've tried this help :[http://askubuntu.com/questions/64631/how-to-restore-the-default-lubuntu-panel](http://askubuntu.com/questions/64631/how-to-restore-the-default-lubuntu-panel)
Do you think it could help me ?

---

### Post by Enigma12 on 2014-11-05
> I don't know what stupidity things I've done when I've written these command lines on terminal

Unfortunately, I also don't know exactly what you did, either in terminal or changing settings, so, if I had your problem, I would back up any data that I wanted to save, then use the CD or DVD to try Lubuntu. If everything works well with that, I would then have the CD or DVD erase everything and reload Lubuntu. If it works well enough then, I would reload my saved data and just use the computer as it is until I understand better what I was doing in changing settings in any way. 

Although I have used almost all versions of Windows and made them all look and act as I wanted, I am new enough to Linux to know to change things **only if I really understand what I am doing**. Other than changing both desktop pictures daily, because that is very easy, I haven't found any need to change much else. Maybe you just need to go slower in making changes at this time.

---

### Post by Nairolf2112 on 2014-11-06
I know that I shouldn't do something that I don't really understand. But, I had truth on this help. Of course, I could make a new install of Lubuntu, but, I don't really like this solution, for me it's a 'windows solution'. 

But, now, thanks to this question at stack exchange, I could solve my problem : [http://askubuntu.com/questions/64631/ho … untu-panel]("http://askubuntu.com/questions/64631/how-to-restore-the-default-lubuntu-panel") 
Indeed, I've done this : 
```
sudo cp /usr/share/lxpanel/profile/Lubuntu/panels/panel ~/.config/lxpanel/Lubuntu/panels
```

After a reboot, my panel were back to its default appareance. I don't know why there had a this 'grey block' before, but now, I've a correct panel. Thank you so much for your help.

---

### Post by JohnnyComeL8ly on 2014-11-06
I know it sounds like "a windows solution," but I think that you should look at it this way... how much time is it going to take to find how to fix it vs. just reinstalling it?  Now, I like to fix it but sometimes that isn't feasible... or impossible with your current knowledge of the problem.

---

### Post by Nairolf2112 on 2014-11-07
Yes, but as it's easy to resinstall a Linux distribution, I prefer trying to fix a problem before reinstalling. If I broke too many thing when I try to fix some 'bug', ok I will reinstall it. 
One other advantage of trying to fix problems, is that you can always learn about something. When you reinstall your system, you don't learn anything... 

But, I agree, reinstall is easy, and I always backup my personal datas, so... If I can't fix a problem, I can reinstall my system. 

Thank your for your help.

---

