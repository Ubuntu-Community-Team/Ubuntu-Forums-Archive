---
title: "Splash screen changes"
date: 2011-03-15
forum: Desktop Environments
---

### Post by Canime on 2011-03-15
I have tried fooling around to change my splash screen, and have downloaded splash manager to try and change all that. It wont work and in this instance, I am afraid I am stuck on how to fix it. Can anybody please tell me how to change the Ubuntu splash screen from the horrible purple to something better?

---

### Post by stinkeye on 2011-03-15
Do you mean the login screen or  plymouth screen with the Ubuntu logo?

For the background image at the login screen...
Open the terminal and run the following commands

```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```

Then logout, and you’ll see an Appearance window pop up. Change it to how you prefer it, then close it and login as usual.

When you have logged in after finishing the customizing, run this command to prevent the Appearance window from opening at the GDM screen every time.

```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```


If you want to change the background color of the plymouth screen let me know.
eg the attached pic shows my plymouth background changed to black.

---

### Post by Canime on 2011-03-15
Great that is awesome, I modified the splash screen at login, and yes, the plymouth screen is exactly what I want to change. 

Here is the splash screen at the moment:

[[IMG]http://img340.imageshack.us/img340/80/modifiedsyringa.th.jpg[/IMG]](http://img340.imageshack.us/i/modifiedsyringa.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by stinkeye on 2011-03-15
You can change the look of the default plymouth theme colors using
this guide [**_[COLOR="DarkRed"]http://www.khattam.info/howto-change-ubuntu-pinkpurple-plymouth-boot-screen-to-any-color-you-like-2010-11-09.html[/COLOR]_**]("http://www.khattam.info/howto-change-ubuntu-pinkpurple-plymouth-boot-screen-to-any-color-you-like-2010-11-09.html")
It basically copies the default plymouth to create a new plymouth theme 
and shows you how to change the background colors and/or the logo colors.
I just used it to change the background color.

You can also change your plymouth theme by searching for **plymouth-theme** in synaptic and installing the one you want.
After installation you need to change plymouth with
```
sudo update-alternatives --config default.plymouth
```
select your theme and then run
```
sudo update-initramfs -u
```

---

### Post by Canime on 2011-03-15
Thanks for your help, for now I will just keep the splash screen changes and not bother with the plymouth theme script hacking. It seems all a little bit too complicated for me. I have installed another theme however and will use that to change the boot screen color.

---

### Post by stinkeye on 2011-03-15
Just changing the default plymouth background to black is fairly simple and looks a lot
better than the purple.

Make a backup of **ubuntu-logo.script**...
```
sudo cp  /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script.bak
```


Then edit **ubuntu-logo.script**...
```
gksudo gedit /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script
```
When gedit opens go to **edit > preferences > view** and tick **Display line numbers**.


Now go to line 166 and 167
```
Window.SetBackgroundTopColor (0.16, 0.00, 0.12);     # Nice colour on top of the screen fading to
Window.SetBackgroundBottomColor (0.16, 0.00, 0.12);  # an equally nice colour on the bottom
```

and change to...
```
Window.SetBackgroundTopColor (0.00, 0.00, 0.00);     # Nice colour on top of the screen fading to
Window.SetBackgroundBottomColor (0.00, 0.00, 0.00);  # an equally nice colour on the bottom
```

---

### Post by Canime on 2011-03-15
It hasn't worked. I have backed-up the splash script as needed and added the changes to the background color bar. 

I tried several different colors. 

I've also tried to update the package through package manager so that when I run the command,

```
sudo update-alternatives --config default.plymouth
```

I choose the available option for the splash package... 

I then run 

```
sudo update-initramfs -u
```

No change at all on several restarts. I'm exhausted trying this, I am just going to say that it is fixed and leave it at that.

---

### Post by stinkeye on 2011-03-15
Ok, is your brain bleeding? :P
Have a panadol and a lie down and you might want to try later. #-o
It get's easier. It's just copy and paste, and yeah if somethings not working
don't do your head in, just put it on the back burner until things make more sense. 

That edit works with ubuntu-logo theme so you would have to select 
"**0            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       auto mode**"
when you run ```
sudo update-alternatives --config default.plymouth
```


and then ```
sudo update-initramfs -u
```

---

### Post by Krytarik on 2011-03-15
Thanks for the detailed guide, stinkeye! I'll try it, when I get fed up with this one:
[http://gnome-look.org/content/show.php/Ubuntu+sunrise+plymouth?content=129696](http://gnome-look.org/content/show.php/Ubuntu+sunrise+plymouth?content=129696)
I just recently replaced the default one with it, and yeah, it's still a bit purple, but nice enough. :)

---

### Post by Kri5 on 2011-05-16
I found i could edit the background colour easily by using 'alt+F2' and 'gksu nautilus'.
 
From there i just copied and pasted the ubuntu-logo.script and renamed it, then right clicked on the original and selected 'open in text editor'.
 
I changed the background colour as Stinkeye stated and then re-selected the Plymouth theme, i use the 'Zorin Splash Screen Manager'.
 
 [http://zorin-os.webs.com/splashscreenmanager.htm](http://zorin-os.webs.com/splashscreenmanager.htm)
 
The black screen is a big improvement over the purple one, however i would like to change the colour of the dots underneath the word 'Ubuntu'.
 
Does anyone know what line you need to edit?

---

### Post by stinkeye on 2011-05-16
This tutorial shows how he changed the progress dots as well.
[**_[COLOR="DarkRed"]http://www.khattam.info/howto-change-ubuntu-pinkpurple-plymouth-boot-screen-to-any-color-you-like-2010-11-09.html[/COLOR]_**]("http://www.khattam.info/howto-change-ubuntu-pinkpurple-plymouth-boot-screen-to-any-color-you-like-2010-11-09.html")

---

### Post by Kri5 on 2011-05-16
Thanks for that, I think I was originally put off by having to use the Terminal. It's not that I don't like using it, It's more a case that I don't understand what I'm typing lol.

Saying that I followed the instructions and everything worked out fine. I may try and tweak it a little as I'd like to reverse the colours, i.e. black screen and white Ubuntu logo. This leaves rather ugly 'PNG off' buttons, black with a white box. I shall have to experiment some more with those.

Thanks again for the pointer Stinkeye.

---

### Post by MrMat on 2013-04-25
Thanks! I had run across this in 12.10 and it's one of the first things I change.
BTW works in 13.04 too.

---

