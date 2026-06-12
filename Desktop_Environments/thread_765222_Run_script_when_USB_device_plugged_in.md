---
title: "Run script when USB device plugged in"
date: 2008-04-24
forum: Desktop Environments
---

### Post by davosmith on 2008-04-24
I have a program called 'Card Export' for my Palm which causes it to be recognised as a USB Storage Device when plugged in to my computer.

As my Palm has a DCIM folder, Gutsy used to recognise it as a Digital Camera and then offer to import the photos.

This would then run a little script that I had hacked together, spot that it was really my Palm (via an empty file in the root directory called 'this-is-palm') and then copy all the latest podcasts onto it.

I have just upgraded to Hardy and plugged my Palm in and I am not getting the 'import photos' message (nor is my script running).

Any ideas?

---

### Post by davosmith on 2008-04-26
This is getting worse.

I've just tried plugging in my digital camera. This is now mounted as a drive (with an icon on my desktop) and I am not getting an option to import my photos.

The 'removable drives and media preferences' has a tick beside 'import digital photographs when connected' and the command still says to run my script (with %m as the parameter).

What is going on?

---

### Post by sdennie on 2008-04-26
It sounds like a udev problem to me.  If you did an upgrade from Gutsy, it's possible that you have some stale udev rules lying around.  Unfortunately, I can't give you a magic command to fix the problem but, you could google for udev and also look in /etc/udev/rules.d.

---

### Post by davosmith on 2008-04-26
Thanks for your reply.

After some messing about (and nearly going down the udev route), I eventually found out what the problem was.

'Removable Drives and Media' settings are ignored in the latest version of Gnome, in favour of the Nautilus Edit->Preferences->Media tab.

Unfortunately, there is no easy way to add custom items to this, however, in case anyone else finds this thread, the answer is to:

1. Go to the folder ~/.local/share/applications
2. Create a <name of the application>.desktop file here.
3. Put something like this inside the .desktop file:

```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=<name of the application>
MimeType=x-content/image-dcf;
Exec=<command to run the application - use %f for the path to the device>
Type=Application
Terminal=false
NoDisplay=true
GenericName[en_GB]=

```

4. Edit the file defaults.list (in the same folder).
5. Add the following line:
```

x-content/image-dcf=<name of the application>.desktop

```

You should now have 'name of the application' available in the list of actions when the camera is inserted (and also when you right-click on the icon for the mounted camera).

Hope that helps someone...

---

