---
title: "nVidia driver issue?"
date: 2009-03-16
forum: General Help
---

### Post by spamjam on 2009-03-16
Hi, I'm new to Ubuntu and Linux and just barely started using it. I installed the recommend nVidia drivers (177) and i love the little effects, but something seems wrong with my windows. Here is a pic:

[IMG]http://i42.tinypic.com/160aolk.jpg[/IMG]

This seems to happen whenever I move the cursor over to the close, maximize and minimize buttons, whenever I open up a new app or sometimes it just happens. What could the problem and how can I fix this? I really like Ubuntu and want to keep using it, but this kind of makes me want to go back to Vista :P

not really, just kidding. But this is a nuisance.

Also, my video card is GeForce 7600 GT.

---

### Post by mb_webguy on 2009-03-17
That's a problem with your window decorator, and doesn't really have anything to do with your video card (other than the fact that you probably couldn't use the nicer desktop effects when you were using the generic driver).  I've seen other people reporting that their title bar disappears entirely and I know how to fix that problem, but I've never seen anyone say that just the buttons were missing.

You could try using a different window decorator like Emerald.  Use the command "sudo apt-get install emerald" to get Emerald.  If that doesn't work by itself, install the compizconfig-settings-manager package, open it with the command "ccsm" (or by the menu option in System->Preferences), click on Window Decoration, and put the line "emerald --replace" in the Command line.

---

### Post by spamjam on 2009-03-17
Thank you.

I went ahead shortly after I posted the topic and reverted the driver back to version 96 and the problem hasn't happened.

Is it safe to update the drivers to 177 and try Emerald?

Also, what exactly is Emerald? Will it change the appearance of the OS at all? Sorry, I just barely got Ubuntu:P

---

### Post by mb_webguy on 2009-03-17
Ok, here's a quick info dump about the graphical interface in Linux.

An operating system handles low-level operations like allocating memory and interfacing with the hardware.  A program called a window manager controls the placement of windows in a graphical environment.  A window manager may use a separate program called a window decorator to provide the visual elements of a window (e.g. the titlebar, buttons, and border) or it may do this on its own.  A graphical desktop environment incorporates a window manager and other programs like toolbars, a desktop with icons and wallpaper, etc., to provide a complete graphical user interface for the computer.

In the Windows world, you don't have to be worried about these distinctions since if you use the Windows operating system you're stuck using the Windows window manager and desktop environment.  But the philosophy of Linux is to do one thing and do it well, and so each of these different concepts are handled by a separate program.  And in general, numerous programs exist of each type.  Gnome, KDE, and Xfce, for example, are all different desktop environments (used by Ubuntu, Kubuntu, and Xubuntu, respectively).

The Ubuntu distribution of the Linux operating system uses the Gnome desktop environment, which by default uses the Metacity window manager and decorator.  However, if the computer's video card will handle it, Ubuntu will instead use the Compiz window manager.  (This is why things looked and acted a bit different after you installed the proprietary driver for your video card.)  Since Compiz doesn't have an integrated window decorator, it will by default use the Metacity window decorator.  However, you can replace Metacity with another window decorator like Emerald instead.

Since the window decorator only provides window decoration, the only thing that will change by using Emerald instead of Metacity is the appearance of the titlebar, titlebar buttons, and border of windows.  An advantage of using Emerald is that you can use a number of different attractive themes, which can utilize transparency.  You can get these themes at various websites, most notably [Gnome-Look.org]("http://www.gnome-look.org").  The [UbuntuStudio Emerald]("http://www.gnome-look.org/content/show.php/UbuntuStudio+Emerald?content=59198") theme is rather nice.

Btw, many window managers can be used independently of a desktop environment.  I personally like using the Openbox window manager in conjunction with the PyPanel taskbar program and the feh image viewer (for the desktop wallpaper).  This combination provides the same basic appearance and functionality as a full desktop environment, but uses far fewer system resources.

---

### Post by Volt9000 on 2009-03-17
> **mb_webguy said:**
> Ok, here's a quick info dump about the graphical interface in Linux.

An operating system handles low-level operations like allocating memory and interfacing with the hardware.  A program called a window manager controls the placement of windows in a graphical environment.  A window manager may use a separate program called a window decorator to provide the visual elements of a window (e.g. the titlebar, buttons, and border) or it may do this on its own.  A graphical desktop environment incorporates a window manager and other programs like toolbars, a desktop with icons and wallpaper, etc., to provide a complete graphical user interface for the computer.

In the Windows world, you don't have to be worried about these distinctions since if you use the Windows operating system you're stuck using the Windows window manager and desktop environment.  But the philosophy of Linux is to do one thing and do it well, and so each of these different concepts are handled by a separate program.  And in general, numerous programs exist of each type.  Gnome, KDE, and Xfce, for example, are all different desktop environments (used by Ubuntu, Kubuntu, and Xubuntu, respectively).

The Ubuntu distribution of the Linux operating system uses the Gnome desktop environment, which by default uses the Metacity window manager and decorator.  However, if the computer's video card will handle it, Ubuntu will instead use the Compiz window manager.  (This is why things looked and acted a bit different after you installed the proprietary driver for your video card.)  Since Compiz doesn't have an integrated window decorator, it will by default use the Metacity window decorator.  However, you can replace Metacity with another window decorator like Emerald instead.

Since the window decorator only provides window decoration, the only thing that will change by using Emerald instead of Metacity is the appearance of the titlebar, titlebar buttons, and border of windows.  An advantage of using Emerald is that you can use a number of different attractive themes, which can utilize transparency.  You can get these themes at various websites, most notably [Gnome-Look.org]("http://www.gnome-look.org").  The [UbuntuStudio Emerald]("http://www.gnome-look.org/content/show.php/UbuntuStudio+Emerald?content=59198") theme is rather nice.

Btw, many window managers can be used independently of a desktop environment.  I personally like using the Openbox window manager in conjunction with the PyPanel taskbar program and the feh image viewer (for the desktop wallpaper).  This combination provides the same basic appearance and functionality as a full desktop environment, but uses far fewer system resources.

What a thorough and informative post.
Thanks for that, mb_webguy! :D

---

### Post by spamjam on 2009-03-18
> **Volt9000 said:**
> What a thorough and informative post.
Thanks for that, mb_webguy! :D

Very informative, thank you a lot sir.

I will try Emerald and see what happens.

---

### Post by spamjam on 2009-03-18
I did what you said and it work perfectly!

On the downside, I'm not too fond of the colors of the default Emerald haha. Is there anyway to use Emerald so I can use the recommended drivers, but have the default Ubuntu look?

---

### Post by mb_webguy on 2009-03-18
Well... I have no idea if it will work, since I'm not sure what exactly is causing your problem in the first place, but you could try reinstalling Metacity.  

Open Synaptic and type "metacity" in the search box.  Mark the metacity, metacity-common, and libmetacity0 packages for reinstallation and click Apply.  Now open the terminal and type "metacity --replace".  If that works, then open Compiz, go to the Window decoration, and put "metacity --replace" in the Command box.

---

### Post by spamjam on 2009-03-18
I'm actually really liking Emerald. I love the effects it has. After looking further into it, it looks as if I can change the colors to emulate the default Metacity(?).

Is there a source out there that has the default colors for Metacity so I can put them into Emerald? Or can anybody do me that favor? I'll buy you a beer ;)

I'm using vrunner btw.

---

### Post by mb_webguy on 2009-03-18
Have you looked at Gnome-Look.org?  There are quite a few different themes available, and many of them allow you to select from a variety of colors.  I'm not sure that there's one that will look exactly like Metacity, but you can probably get close.

---

### Post by spamjam on 2009-03-18
I decided to just revert back to 96. I like the look of metacity better. Thank you for the help. This helped me learn more about Linux.

---

### Post by tom4jean on 2009-03-19
Greetings, I just happened across this thread and realized it may fix a problem I have had. I use the NVIDIA 96 driver and everything works fine in xubutu when I install and start the driver, but if I try to use Ubuntu with the NVIDIA 96 driver I loose the title bar and frames of all the windows. Also when I run the terminal it is just a white box that I cannot enter anything into, so any suggestions to enter commands in the terminal don't work for me and using the VC does not work ether.
   So, I am assuming from this thread, it has something to do with Metacity? From what I am getting from this thread it has to do with Ubuntu automatically switching to Compiz and using Metacity once I install the NVIDIA driver, is this correct?

The title bars etc..work with Ubuntu running the generic driver, and the NVIDIA 96 driver works fine with xubuntu that I am using now.

As a noob could someone tell me how to fix this so I can use Ubuntu instead of xubuntu, in simple terms. 
Is it as simple as switching to emerald?
This only happens under Ubuntu when I use the NVIDIA 96 driver.
I don't currently have the Ubuntu desktop installed, but I will reinstall it if I can get it fixed.:D


Thanks,
Tom

**EDIT****
Never mind, I tried installing the Ubuntu desktop along with emerald and it did not fix the problem. I did some searching on other threads, tried a few tweeks and gave up and just used [http://psychocats.net/ubuntu/purexfce](http://psychocats.net/ubuntu/purexfce) to return to a pure xfce4 desktop. 
It works well for me on my older computer anyway, and I have not had any problems with xubuntu and my NVIDIA driver so I am going to leave well enough alone and stick with what works! ;-)
I just don't have the time or will to mess around doing all the system tweeks to get Ubuntu working right. Thanks anyway. Tom

---

