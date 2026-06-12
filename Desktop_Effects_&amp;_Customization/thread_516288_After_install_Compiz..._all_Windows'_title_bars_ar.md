---
title: "After install Compiz... all Windows' title bars are GONE"
date: 2007-08-03
forum: Desktop Effects &amp; Customization
---

### Post by duydaniel on 2007-08-03
Any idea? :confused:

---

### Post by Sunforge on 2007-08-03
I've suffered missing title bars and this link certainly helped:

Try this for NVIDIA cards (I have an NVIDIA card so this worked for me)
[http://compiz.org/NVidia](http://compiz.org/NVidia)
NB: Ignore the installing drivers section if your NVIDIA driver is above 96.31 you can skip straight to the "Modifying your xorg.conf file" section.

Try this for ATI cards (ATI tends to be more problematic due to lack of driver support):
[http://www.compiz.org/ATI](http://www.compiz.org/ATI)

There is a link for Intel cards as well but there's not a lot of information in there.

Now for the NVIDIA stuff. **The following is the bare minimum required to get Compiz running smoothly on a GNOME desktop:**

Back up and then edit your xorg.conf file:
If you don't know where that is, open a command prompt and type
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.back (this copies your old xorg.conf)
then open it up in an editor
sudo gedit /etc/X11/xorg.conf 

and add the following commands:

In the device section add the following:
Option         "RenderAccel" "true"
Option         "AllowGLXWithComposite" "true"

At the very end of the xorg.conf file add:

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
Now save and close the file.

[B]Now to activate it the crude way:
[/B]If you hit the CTRL & ALT & Backspace you will kill your window manager and it will restart.
[B]To activate it the more gentle way:
[/B]Start a command prompt in a separate window (ALT & F2) and type:
sudo /etc/init.d/gdm stop
and then
sudo /etc/init.d/ gdm start
Or
sudo /etc/init.d/gdm restart

You should have hardware acceleration enabled and have your title bars back.

There are a host of other commands which you can add which smooth out the eye candy but the above is the bare minimum for NVIDIA. The additional commands are detailed in the Compiz.org how to link above.

If things go wrong and you end up with a blank screen **don't panic** - Ubuntu is still ticking away, you'll have been dumped at the command prompt. All you have to do is copy your old xorg.conf file back and start your window manager again:

sudo cp /etc/X11/xorg.back /etc/X11/xorg.conf 
Then start X
sudo /etc/init.d/gdm start

You should now be back where you started.

Important note: you don't *have* to edit your xorg.conf file, you can use commands to add the same thing to your config but people's mileage appear to vary with this approach so I have skipped it.

Tell us how you get on.

---

### Post by duydaniel on 2007-08-03
Thank you for the information.

But mine is intel 945GM :(
After upgrade the kernel to 2.6.22-9-generic by the link:
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)
then compiz did not work anymore.
:confused:

---

### Post by Sunforge on 2007-08-03
Well darn it I'm afraid it I don't know much about Intel graphics cards.

---

