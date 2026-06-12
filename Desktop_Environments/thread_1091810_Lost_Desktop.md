---
title: "Lost Desktop"
date: 2009-03-09
forum: Desktop Environments
---

### Post by Pablo W on 2009-03-09
Hello everyone. I'm a newbie and I guess I've made a silly mistake, but I don't know how to fix it.

The problem: I have lost the Ubuntu Desktop. That is, I don't have the upper bar wich gives acces to all applications. I don't know how to run the package manager to download the lost desktop package. Any ideas as to how to do it?

Background information: I uninstalled it unintentionally. I was getting lots of "update" suggestions, including recommended updates for Evolution. Since I don't use Evolution and I am not interested in getting its updates, I went to the package manager and uninstalled all what had "evolución" in the package name, but it seems I've gone too far (because I lost my desktop).

Thanks for your help.

---

### Post by UbuntuNerd on 2009-03-09
you probably removed your desktop, hit (Ctrl+Alt+f1) to go to the terminal. log in and enter your password, then enter this code at the prompt:
```
sudo apt-get install ubuntu-desktop
```
this code will reinstall your desktop, after is done hit (alt f7) to get back to your desktop to see if it work

---

### Post by Mud.Knee.Havoc on 2009-03-09
I can't answer your question related to Evolution.

I can, however, help you out with getting the upper bar back.  Basically, the gnome desktop is pretty easy to customize.  You can create a new bar by following these steps:

1. Put your mouse over the bar on the bottom of the screen
2. Right click, choose "New Panel".  This will make a new panel (bar) appear somewhere on the screen.  I just tried it and it put it on the right side.  It doesn't matter where it is, you can move it.
3. Move the bar to the top of the screen if it isn't there already.
4. Add stuff to the bar that you feel should be there.  To do this, right click and select "Add to panel". Select:
- Menu Bar (don't confuse with Main Menu, which is similar, but has everything in one little button)
- Clock
- Shutdown (not there by default, I don't think, but I like it)
- Notification area
- Volume control.

Play around with other addons, too... if you use more than one language, the keyboard indicator is good.  You might like Weather, as well.

Once you've got stuff on the bar, you can drag them to different spots on the bar so it's all laid out as you prefer.  You can also drag icons onto the bar for little application launcher buttons.  

It's pretty intuitive... I think you'll be surprised when you see how easy it is. :)

---

### Post by Pablo W on 2009-03-09
> **UbuntuNerd said:**
> you probably removed your desktop, hit (Ctrl+Alt+f1) to go to the terminal. log in and enter your password, then enter this code at the prompt:
```
sudo apt-get install ubuntu-desktop
```
this code will reinstall your desktop, after is done hit (alt f7) to get back to your desktop to see if it work

Thanks UbuntuNerd for your quick reply.
For some reason unknown to me, nothing happens when I hit (Ctrl+Alt+f1). I could solve the problem, though, through a more complicated procedure. I describe it here, in case someone has the same problem and cannot do (Ctrl+Alt+f1): I created a folder in the desktop, I open it (so the files browser opened). In the files browser I went to search and typed "synaptic". From the many options shown as search results, I clicked on different "Synaptic packages manager" files until I got one which asked for my password. After entering my password, I got access to Synaptic, where I typed ubuntu desktop and got it back.


I wonder:
 why I cannot open the terminal hitting (Ctrl+Alt+f1) (maybe I won't be so lucky to have another option next time)
I also wonder if there is any way to stop the evolution updates from pouring in, without preventing other suggested updates that I might be interested in.

Anyhow, thanks again for a very useful post.

---

### Post by UbuntuNerd on 2009-03-09
you have to be careful when unistalling some applications because some of them are closely integrate with your desktop, some of them are Gimp and Evolution

---

### Post by Bölvaður on 2009-03-09
try alt+f2 instead of ctrl+alt+f1 or ctrl+alt+f3 (you can go back with ctrl+alt+f7 if you manage to get that to work)

---

### Post by UbuntuNerd on 2009-03-09
@ PABLO W
to stop evolution from updating just go into Synaptic and use the "Lock version" feature on a package.
To lock the version of an application do this:

 Go to System > Administration > Synaptic Package Manager
enter your password
Search for the package you want to lock and select it, then click "Package" > "Lock Version"

It will now remain the same, even when a new release is available.

---

