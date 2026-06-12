---
title: "removing unity and gnome session managers"
date: 2012-12-11
forum: Desktop Environments
---

### Post by bluekuma on 2012-12-11
Hi all!
I'd like to remove unity, gnome and all that, and just keep xfce4 (already installed). 
Even better, it'd be wonderful to have my computer boot into a login shell and let me run startx if and when I want a graphical session.

Now I tried with some things along the lines of "apt-get remove unity ubuntu-desktop gnome-session" but it turns out it's too naive a method. I didn't get the splash screen on boot but I still had to press CTRL-ALT-F1 to get to a login shell. 

Searched and googled here and there and couldn't find a definitive explanation.

Thank you for your kindness!

---

### Post by debodas on 2012-12-11
[http://ubuntublog.org/how-to-remove-unity-desktop-in-ubuntu-12-04.htm](http://ubuntublog.org/how-to-remove-unity-desktop-in-ubuntu-12-04.htm) Should do the trick for uninstalling unity.

---

### Post by mringer on 2012-12-22
> **kingnick42 said:**
> [http://ubuntublog.org/how-to-remove-unity-desktop-in-ubuntu-12-04.htm](http://ubuntublog.org/how-to-remove-unity-desktop-in-ubuntu-12-04.htm) Should do the trick for uninstalling unity.

When I clicked on this reference, I was redirected to 

[http://ubuntublog.org](http://ubuntublog.org)

and searching for "unity" on this site did not find anything. I tried 
copying and pasting the full address into my browser: same result.

---

### Post by grahammechanical on 2012-12-22
I think that it would have been better to install Xubuntu. You would get a more stable operating system than the one you will get by removing stuff.

You can also experiment using Recovery mode. The Resume option will get you to a log in screen.

The Root option will get you to a root shell. But the file system will only be in Read mode.

To get a file system with Read and Write capabilities, select Fail Safe mode, then press Esc to back out of fail safe mode, Now select the Root option.

You might find that startx does not do what you want. When I tried it just now I did not get to a GUI. It is possible to edit the Grub configuration file and where you see the line that says "quiet splash" add the word "recovery" and now you will always boot into Recovery mode.

Regards.

---

### Post by ibjsb4 on 2012-12-22
[http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu)

But I also prefer a fresh install like "graham" said.

---

### Post by NikTh on 2012-12-22
> **grahammechanical said:**
> I think that it would have been better to install Xubuntu. You would get a more stable operating system than the one you will get by removing stuff.

Agreed 100%

---

### Post by Cheesehead on 2012-12-22
> **bluekuma said:**
> Hi all!
I'd like to remove unity, gnome and all that, and just keep xfce4 (already installed). 
Even better, it'd be wonderful to have my computer boot into a login shell and let me run startx if and when I want a graphical session.


You have a couple issues here.

I recommend fixing your startx problem first. Do you have any idea how you broke it?

Adding/removing desktop environments is not very difficult, but it can be time-consuming. The easy way to start is to do an [FONT="Courier New"]apt-cache depends ubuntu-desktop[/FONT] , and compare that to the results of [FONT="Courier New"]apt-cache depends xubuntu-desktop[/FONT]. Anything in ubuntu-desktop that is missing from xubuntu-desktop can be safely removed. Do the same process for the metapackage you used to install Gnome desktop.

---

