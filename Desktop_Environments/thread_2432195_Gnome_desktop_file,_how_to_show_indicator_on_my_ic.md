---
title: "Gnome desktop file, how to show indicator on my icon"
date: 2019-11-28
forum: Desktop Environments
---

### Post by aeronutt on 2019-11-28
I've created a .desktop file to run firefox with a different profile. (eg "firefox -p myownproflle.profile").

When I click on the icon, it executes and runs fine, but I want the 'indicator' button to show up on my icon, not the system firefox icon.

As shown below, when I click on the lower icon, it runs fine, but the indicator (red button) shows on the installed version of firefox.  I'd really like the indicator to show on my icon.
I've tried a bazillion things, but no change.  
Can this be done?
[IMG]https://i.imgur.com/TmJPXYf.png[/IMG]

---

### Post by CatKiller on 2019-11-28
The task manager uses the WM_CLASS attribute to identify which launcher to give the dot to. I believe you can specify the WM_CLASS in your .desktop file. That needs to match the filename of your .desktop file.

---

### Post by aeronutt on 2019-11-28
Awesome, I was just looking at the desktop files descriptions on the freedesktop site. Was wondering what WM_CLASS might do!!
I'll give it a try and report back.

Thanks!

---

### Post by aeronutt on 2019-11-29
Ok, got this working!!  My first mistake was trying to create my own "wm_class" for my script (which runs firefox).  But all that's needed, is to set the wm_class to the same class that the installed firefox has. And that's easy to find out. So, for later reference:

In a terminal, run "xprop WM_CLASS" and then click on any window that you want to know what wm_class it has.
Then, simply put that result in your desktop file.  

For firefox it's "Firefox". Duh! lol. Worked for thunderbird also.

So now, when I start "my" versions of firefox and thunderbird via the desktop, the little notification button is shown next to the correct icon!!!!

Simple. For completeness, here are the lines I added to my firefox and my thunderbird .desktop files

myfirefox.desktop:
StartupWMClass=Firefox

mythunderbird.desktop:
StartupWMClass=Thunderbird

Thanks again, thread marked solved.

---

### Post by Dennis N on 2019-11-29
Thanks for supplying the details here. This solved a similar problem between LibreOffice and LibreOffice AppImage icons in the dock that I couldn't figure out.

---

### Post by aeronutt on 2019-11-29
Cool! Glad I could contribute.

---

### Post by aeronutt on 2019-11-29
Well, I celebrated too early. 

Now, the indicator button associates with myfirefox icon and never the default version, even when I start the default version of firefox.

Ug.

I need this indicator to "attach" itself to the icon from which I started the program (ie to my version with my icon, or the system version, depending on which I clicked on to start firefox).

Ideas would be appreciated.

---

### Post by aeronutt on 2019-11-30
I think I found it!

This thread got me there.
[https://askubuntu.com/questions/653702/startupwmclass-will-not-change-wm-class-of-eclipse-ide](https://askubuntu.com/questions/653702/startupwmclass-will-not-change-wm-class-of-eclipse-ide)

Using "StartupWMClass=<class>  simply tells the window which class to put this particular window in.
However, there's a way to define a unique class a .desktop application should be in.  
Simply add "--class=<class> to the end of the Exec command! And <class> can be a unique string just for this .desktop file.

So for "myfirefox.desktop", I have the following:

> [Desktop Entry]
...
Exec=firefox -p profile2 --class=a_unique_classname
...
StartupWMClass=a_unique_classname

Yea!!  And now, each firefox icon in my dock gets an identifier button depending on which icon I used to start firefox!!
I've wondered how to fix this for years. lol.

---

### Post by Dennis N on 2019-11-30
When I read your post #7, I tested and find LibreOffice Writer and it's AppImage have the same problem. When launching the regular LO Writer, the little indicator now shows that the AppImage is running instead. 

I tried your last idea (post #8) of defining and using a unique class name in the .desktop file to see what that might do. I added "--class=loappimage" to the Exec= line, and made StartupWMClass=loappimage, but this made things worse, as clicking the AppImage Icon in the Dock now wouldn't open it. Neither would it open from the Applications Overview. So something is missing to make it work.


I reverted to using "StartupWMClass=libreoffice". This is better than doing nothing, as the icon for the AppImage now shows on the Dock, and I can pin it to the Dock to keep it there. Before, an icon would not appear at all.

---

