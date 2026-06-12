---
title: "Facebook graphic component malfunction"
date: 2012-04-10
forum: Desktop Environments
---

### Post by gabidospi on 2012-04-10
Hi all, 
I have installed graphyc composant Facebook on my toolbar and facebook window is appear in the bottom of my screen (I can seen only the blue bar where is written Facebook) and nothing else. And I can't close this window, nor moove it.

Somebody can tell how can I remove this sh..t? Thanks

Kubuntu 11.10 KDE

---

### Post by kiirokurisu on 2012-04-11
If you mean the Facebook plasmoid, you can get rid of it by hovering your mouse over it so the plasmoid button bar slides out, and then click the X to close it. You may have to experiment a bit to find the right place to hover the mouse cursor for the button bar to slide out.

---

### Post by gabidospi on 2012-04-11
Actually no. I don't mean the plasmoid. In fact the FB plasmoid I get rid of, but the FB window opened by, I can't. That window is located in the bottom of the screen, and the only action I can get is right click on the mouse who show me a little thumbnail   on the blue bar of the window: "Recharger F5". No way to close it, no way to move it!!

Does kubuntu have a sort of task manager like windows?

---

### Post by kiirokurisu on 2012-04-11
Yes, Kubuntu has a task manager, it's called KSysGuard. You can start it by searching for "task" in the K menu.

---

### Post by gabidospi on 2012-04-12
Actually I've found it. It's called  System Guard (surveillance du système) but I can't figure it out what is the process that correspond to my facebook window. 

I paste here an image that show you how it looks my facebook window on my screen:

[[IMG]http://img37.imageshack.us/img37/6973/fbbug1.th.jpg[/IMG]](http://imageshack.us/photo/my-images/37/fbbug1.jpg/)

You can see that I cans scoll in this very thin rectangle my facebook page, and that's interesting that all the facebook scrolls inside (even the blue bar).

Any ideeas? Thank's

---

### Post by gabidospi on 2012-04-12
And the window without any scroll:

[[IMG]http://img713.imageshack.us/img713/2699/fbbugj.th.jpg[/IMG]](http://imageshack.us/photo/my-images/713/fbbugj.jpg/)

---

### Post by kiirokurisu on 2012-04-12
It's quite possible there is no separate process and the window is being controlled by Plasma Desktop. If you don't mind having your Plasma widgets reset to default, have a look at this post how to reset the config:
[http://ubuntuforums.org/showpost.php?p=9249676&postcount=3](http://ubuntuforums.org/showpost.php?p=9249676&postcount=3)

---

### Post by gabidospi on 2012-04-12
Wow, it's worked, but now I hawe 2 task bars!!!! The last one is visible and basic, and the ancient one is faded back of newer one. 

And the most important thing is that I lost 2 buttons: (and theirs options in K menu) shutdown and restart!!!!

I have a message error in the terminal:


unnamed app(4369): "Application plasma-desktop could not be found using service org.kde.plasma-desktop and path /MainApplication." 
root@ubuntu:~#

---

### Post by gabidospi on 2012-04-12
Ok I closed the task bar and I found the older one! 

Good, but now I need to put back my scrolling fast louncher (you know the one is in the middle of the screen) and the search bar and the favorites icons on the top of the screen. 

I don't know their real name, so... I stop searching and trying like a blind man or else I could have a similar situation like with the FB.

(sorry again for my poor english)

---

### Post by gabidospi on 2012-04-12
I've found their names: it's called docks. So I need to activate the central screen dock and the top screen dock.

[IMG]http://img692.imageshack.us/img692/5384/hybrydekubuntu04490x306.jpg[/IMG]


Like on this picture.


Thank you

---

### Post by kiirokurisu on 2012-04-12
Have a look at this article: [http://www.linuxbsdos.com/2010/10/22/exploring-the-kde-plasma-netbook-interface/](http://www.linuxbsdos.com/2010/10/22/exploring-the-kde-plasma-netbook-interface/)

It shows you how to switch to the Plasma Netbook interface, which is what your screenshot depicts.

---

### Post by gabidospi on 2012-04-13
Thank's for your link. It's almost what I've searcing for, but unfortunately, in notebook mode the pannel is hidding. 

Before my reinitialisation tip, I have the same thin (all those panels) in desktop mode. 

So, I found it!!!

It's simple, but not obvious!

On the search and launch thumbnail (it's disposed on the upper right corner of the screen) you choose "Search and launch settings" after you make a click on it.

And then, on the new opened window, Screen/Disposition choose Search and Launch.

[IMG]http://img823.imageshack.us/img823/6025/dockping1.jpg[/IMG]

Thank's.

---

### Post by kiirokurisu on 2012-04-13
I vaguely remembered there was some other way to achieve it - well done for finding it :)

---

### Post by gabidospi on 2012-05-05
Finalement je reviens avec mes soucis...

Le réset de l'interface KDE m'a donné d'autres soucis: les docks disparaissent après chaque reboot. Et en plus j'ai une fenêtre Visualisation du dossier, vide, qui apparaît au milieu de l'écran.

Si vous avez d'autres solutions, je suis preneur.

MErci.

---

### Post by gabidospi on 2012-05-06
Sorry for my previous post (I was tired and I forgot that is an english forum).

So, I was telling that my KDE plasma problem was not resolved (after rebooting, all my modifications was reset).

I find a solution yet:

Going into home (with dolphin) and tape Atl+. for revealing hidden folders, rename .kde to .kde.old and reboot
A new kde is created like new installing kubuntu.

Note: It's possible that your kde plasma crashed into reboot, you can boot in safe mode and then reboot normally.

---

