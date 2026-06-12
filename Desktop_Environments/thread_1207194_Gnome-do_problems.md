---
title: "Gnome-do problems"
date: 2009-07-07
forum: Desktop Environments
---

### Post by ds77 on 2009-07-07
So I have been having problems getting gnome-do to work correctly with 9.04.  First, if I start it manually it will pop up for a moment and disappear.  I have no idea where it goes, it will not come back.  When I start gnome-do from terminal, I get the following: 

```
:~$ gnome-do
Could not locate Tomboy on D-Bus. Perhaps it's not running?
[Debug 22:34:58.184] Acquiring org.freedesktop.DBus session instance
[Debug 22:34:58.197] Starting org.bansheeproject.CollectionIndexer

Unhandled Exception: System.Exception: org.freedesktop.DBus.Error.ServiceUnknown: The name org.bansheeproject.CollectionIndexer was not provided by any .service files
  at IBusProxy.StartServiceByName (System.String flags, UInt32 ) [0x00000] 
  at NDesk.DBus.Bus.StartServiceByName (System.String name, UInt32 flags) [0x00000] 
  at NDesk.DBus.Bus.StartServiceByName (System.String name) [0x00000] 
  at Banshee.Collection.Indexer.RemoteHelper.IndexerClient.Start () [0x00000] 
  at Banshee.Collection.Indexer.RemoteHelper.SimpleIndexerClient.Start () [0x00000] 

```

After buying a Dell 1318 recently I have made the switch to Ubuntu on this laptop and loving it.  Now with a dedicated machine I am diving in head first, so your help is appreciated.

Also, the special-space hotkey does not work.  gnome-do will not work at all except for the times it will pop up for a minute and then its gone.

---

### Post by Ratscallion on 2009-07-08
It says it can't find TomBoy... Maybe check if it's installed.
Open up a Terminal and try this:
tomboy --version
If anything along the lines of not installed, or not found comes up, then try 
sudo apt-get install tomboy
now try running gnome-do...
Can I just ask, how did you install it?

---

### Post by ds77 on 2009-07-08
So per the version command you listed, I am running Tomboy 0.14.0.  

The install I followed for gnome-do is per the gnome-do website.  I added the source lines to my repository and also added the key (which i am not quite sure if the key is properly installed, not sure of a easy way to check this either though).  I then installed gnome-do through the add/remove under apps.

---

### Post by ds77 on 2009-07-08
small update...  I can now verify that the auth key is correctly installed. (Auth tab under Software Sources).  After installing the key correctly, gnome-do worked until reboot, and when I say 'worked'  it would come up with the special-space key, but would not give me search results at all.  Its now back to appearing for a moment and then its gone and will not come back up.

---

### Post by Ratscallion on 2009-07-08
Can you see the icon in the "tray"?

---

### Post by ds77 on 2009-07-08
The icon is not in the tray.

---

### Post by Ratscallion on 2009-07-08
Even when launched?
Then there must be a problem... Can I advise that you download the .deb package from the gnome-do site and either install, or reinstall it that way.

---

### Post by ds77 on 2009-07-08
Even when launched, it does not appear.  Im thinking the same thing. that there is a problem.  I will definitly try downloading the .deb package from the gnome-do site and give it a try.  I will let you know how it goes :)

thanks for you help.

---

### Post by Ratscallion on 2009-07-08
Just give the word, and we come running.

---

### Post by ds77 on 2009-07-08
That you do!  I was playing with opensuse before ubuntu on this laptop, but had many issues.  Switching to Ubuntu I have had no problems other then simple things like this :) Everything works out of the box with Ubuntu on a dell 1318.  (this is not true with suse!)

So I think I got it!!  I needed to install Banshee epiphany-browser.  Installing this and everything is working!

so now just to figure out how to get rid of my top and bottom panels?  I dont really want to delete them, just hide them for now to see if I like the gnome-do dock :)

Thanks for your help Ratscallion!  I removed everything I had installed and then reinstalled from the .deb package. Then installed the banshee browser.

---

### Post by Ratscallion on 2009-07-08
You're very welcome. As for your panels, you can right click, properties, and then click the show the hide buttons with the arrows. Then hit the arrow at the side and the panel slides to the left/right out of view. Glad I could help!

---

### Post by ds77 on 2009-07-08
Thanks again, looks very pretty.  Now to see about functionality.  I was never a Mac user, so this could all be for nothing, but at least I learned something :)

---

### Post by Ratscallion on 2009-07-08
I'd recommend cairo-dock over the Gnome-Do dock. But it is all about what you're going to be using it for.

---

### Post by ds77 on 2009-07-08
Im going to try Cairo as well I think.  So far gnome-do is good, but it seems a little buggy. Apps opening slowly compared to just typing firefox in terminal for example, it will pop right open.  

I have heard good things about Cairo as well, so I am going to have to try it. :)

---

### Post by fabounet on 2009-07-09
Honnestly, using a real dock with a Gnome-Do launcher inside (or another finder like Kuppfer or Deskbar) is way better, and allows you to have the best of 2.
I'd love to see Gnome-Do making some bindings so that other docks could use it natively ....

---

### Post by Ratscallion on 2009-07-09
Launch Gnome-Do with the keyboard shortcut.. I do find it's easier.

---

### Post by fabounet on 2009-07-10
you can assign a shortcut to any program in Gnome (or in Compiz ?)
so no need to have Gnome-Do visible all the time.

---

