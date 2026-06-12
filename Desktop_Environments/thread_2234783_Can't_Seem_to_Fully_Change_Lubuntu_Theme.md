---
title: "Can't Seem to Fully Change Lubuntu Theme"
date: 2014-07-16
forum: Desktop Environments
---

### Post by redbikemaster on 2014-07-16
So, I recently decided I was sick of the default Lubuntu theme. I found a really nice looking theme that I love, and I switched the mouse cursor to one named Pulse Glass. Unfortunately, the new cursor only shows when I'm in Chrome or Steam. It shows the default system cursor on the desktop and panels. How do I fix this?

Also, I want to change the theme of the login screen, but I haven't been able to figure that out.

Pics:
[ATTACH=CONFIG]254783[/ATTACH][ATTACH=CONFIG]254784[/ATTACH]

---

### Post by Dennis N on 2014-07-16
Getting Cursor to Work Everywhere:

The cursor folder must be in **/usr/share/icons**

First, we install it to the alternatives system:
```
dmn@Roxanne:~$ sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/Pulse-Glass/cursor.theme 20
```
Then we configure alternatives to make it the default. Follow the instructions at the bottom of the output from this command.
```
dmn@Roxanne:~$ sudo update-alternatives --config x-cursor-theme
```
Then, in Preferences > Customized Look and Feel > Mouse Cursor tab > select Pulse-Glass and click the Apply Button.
Log Out and Back In.
Finished.

I tested this cursor and it is working everywhere.

---

### Post by Dennis N on 2014-07-16
I got the idea from reading the description that this thing is supposed to "pulse"? Mine doesn't, so that part doesn't work.

Edit: Yes, it does pulse. I had it over a white background and didn't see the pulsing, since the pulse color is also white.

---

### Post by vasa1 on 2014-07-16
@Dennis N, do you have any **qt** apps installed and does the method you describe work for qt apps or is it restricted to gtk apps? 

Also, even for gtk apps, is the I-bar (the cursor in text insertion mode)more or less visible than the default Lubuntu theme cursor?

And, from where do we get this Pulse Glass cursor theme? Is it from [http://gnome-look.org/content/show.php/?content=124442](http://gnome-look.org/content/show.php/?content=124442) ?

---

### Post by Dennis N on 2014-07-17
> do you have any qt apps installed and does the method you describe work for qt apps or is it restricted to gtk apps? 
All cursors are for the X window system, so as long as that is still in use it should work - qt or gtk shouldn't matter with respect to the cursor.
> is the I-bar (the cursor in text insertion mode)more or less visible than the default Lubuntu theme cursor?
the default is DMZ-white, so I think the Pulse-Glass is more visible.
> And, from where do we get this Pulse Glass cursor theme? Is it from [http://gnome-look.org/content/show.php/?content=124442](http://gnome-look.org/content/show.php/?content=124442) ? 
That's the one.

Just to be clear, it's not the cursor I have been using and I don't plan to change - I just tried it out of curiosity to test and see what it looked like. I will keep it for a while, however. It's not bad at all. The ones I use are called Flatbed Cursors of which there are several sizes and colors in the package.

---

### Post by Dennis N on 2014-07-17
> **redbikemaster said:**
>  Also, I want to change the theme of the login screen, but I haven't been able to figure that out.


What about the login screen appearance would you want to change?

---

### Post by vasa1 on 2014-07-17
> **Dennis N said:**
> All cursors are for the X window system, so as long as that is still in use it should work - qt or gtk shouldn't matter with respect to the cursor.
...
Thanks!

I tried it out and you're right about it working with both qt and gtk. Looks nice but I've switched back to the default.

---

### Post by redbikemaster on 2014-07-18
> **Dennis N said:**
> What about the login screen appearance would you want to change?

I want the default Lubuntu theme to be the ShadowPlay theme I made everything else. Why, in the app "Customize Look and Feel" is it under "Widgets"?

Working on the cursor now. Thanks for the help.

OK, cursor is fully working now. That is awesome! Thanks again. Now to get the Login screen to have the theme I want.

---

### Post by vasa1 on 2014-07-18
> **redbikemaster said:**
> .... Why, in the app "Customize Look and Feel" is it under "Widgets"?
...
That's what gtk themes are called in "Customize Look and Feel". I don't know why :)

---

### Post by redbikemaster on 2014-07-18
Just wanted to  make sure I didn't foul it up. Good.

---

### Post by JohnnyComeL8ly on 2014-07-18
*Customize Look and Feel* keeps crashing while I am removing *Pulse-Glass* (it still isn't removed).  It also crashed while installing it (Idk why).  Here's the terminal output:
 [FONT=courier new]john@OptiPlex-GX270:~$ lxappearance
Segmentation fault (core dumped)
john@OptiPlex-GX270:~$ 

[FONT=system]I don't know how to fix it, but I have a feeling that something could be found wherever the "core dumped,"[/FONT] right?

[FONT=system]P.S.   I thought this was sticking to the topic, if however it didn't, tell me, please.[/FONT]
[FONT=system]P.P.S.  In case anything would indicate otherwise, it is a mouse theme.  And I got it to work, but I want it removed.[/FONT]
[/FONT]

---

### Post by redbikemaster on 2014-07-18
Customize Look and Feel crashed for me too, but since I just wanted to install Pulse Glass, and it did that successfully, I paid it no mind.

---

### Post by JohnnyComeL8ly on 2014-07-21
@redbikemaster
I figured out how to fix it, you delete ```
/home/[FONT=courier new]*user*[/FONT]/.icons/Pulse-Glass/
```I know it could have caused problems; however, the Trash just moves the file for deleting, so I knew I could have restored it.
I found out on accident, i.e., I'm not the genuis I want to be... maybe in time. ;)

---

### Post by Dennis N on 2014-07-21
> Customize Look and Feel keeps crashing while I am removing Pulse-Glass (it still isn't removed). It also crashed while installing it (Idk why)

You encountered a long standing bug (at least 2 years old):
[https://bugs.launchpad.net/ubuntu/+source/lxappearance/+bug/952997](https://bugs.launchpad.net/ubuntu/+source/lxappearance/+bug/952997)

Although as redbikemaster said, it does "install" before crashing. I think the installer on Customized Look and Feel copies your cursor folder into ~/.icons.  You need it in /usr/share/icons to do the complete install in post #2. You don't really need it in ~/.icons

As JohnnyComeL8ly found, to remove a cursor, you can just delete its folder. Log out and back in and it won't show up anymore as a choice. But don't remove the one you have been using until you change it to another.

---

### Post by JohnnyComeL8ly on 2014-07-23
Hmm, I guess it's not that important to them (devs) to fix it.  Probably priorities are there restricting what is developed.

Thanks for the warning on removals.

---

