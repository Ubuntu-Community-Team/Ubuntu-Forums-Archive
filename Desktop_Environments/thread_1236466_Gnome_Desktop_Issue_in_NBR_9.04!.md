---
title: "Gnome Desktop Issue in NBR 9.04!"
date: 2009-08-10
forum: Desktop Environments
---

### Post by saadkamal on 2009-08-10
I'm a new Ubuntu user - using Ubuntu NBR in my Asus EEEpc 1000HE.

I liked the sleek interface of NBR, but last night I felt like swreitching to the classic desktop using the desktop switcher. It worked great and I could switch to-from the netbook view to the classic view without any issues.

But after rebooting back to the classic view, No icon appeared on my desktop. I did some search and figured that its a bug with the desktop switcher. There were couple of fixes /commands that I tried and everything is fine when I'm in the netbook view.

However I believe i messed up somewhere and now when I go to the Classic view, it doesn't appear properly. The icons on my desktop appears, but the panel at the bottom (when programs shows up once minimized) doesn't appear. Moreover, there is no ubuntu start button on the top left corner, instead it just shows the ubuntu launcher logo that appears in the netbook view. But that button is not even clickable. So basically when I'm in the classic view, I cant access my programs (outside my desktop).

I have reinstalled Gnome fully, but it didn't help. Is there any way I can simply re-configure gnome to its default settings for the classic view? 

Or pls give me some other solution as this is really bugging me.

Thanks a lot in advance!

---

### Post by gjoellee on 2009-08-10
Well, you can prevent the NBR applications to start after login, then add a menu to the panel. Add a new panel, then add stuff the that panel as well....

If the desktop switcher applet does not work, there is no other way i guess...

---

### Post by saadkamal on 2009-08-10
Thanks for your reply.

How do i stop NBR stuffs from loading? Is there any command for that?

The problem now is, even when I'm in classic view ...the top bar is still like NBR...and I have a desktop with icons...and no bottom panel..

So its like a totally messed up remix of NBR view + Classic View.

But I just want the "pure classic" view. 

Isn't there a way to just get back to the pure classic view? Like a hard reset?

---

### Post by saadkamal on 2009-08-10
I have added a screen shot of my current desktop in classic view.

As you can see, there is no bottom panel, and at the top bar, the button at the top left corner doesn't do anything. So I cant access my applications. When I open a window/browser and minimize it, it goes on top panel. (Like NBR view).

When I open terminal to switch back to the NBR using the desktop-switcher command -- i get the following errors --- but it does eventually take me to NBR view and everything works fine. My only problem is with the classic view..I just dont know why i cant have the old school classic view on my netbook, i definitely screwed up something which is causing this weird remix version of classic view (check screenshot).



saad@saad-netbook:~$ desktop-switcher
In classic mode: true
** (desktop-switcher:3755): DEBUG: Enabling netbook mode
** (desktop-switcher:3755): DEBUG: Enabling launcher autostart
** (desktop-switcher:3755): DEBUG: Launching the, er, Launcher
get fences failed: -1
param: 6, val: 0
** (netbook-launcher:3761): DEBUG: CONFIG: Low graphics mode: False
** (netbook-launcher:3761): DEBUG: CONFIG: Font dpi: 96.000000
** (netbook-launcher:3761): DEBUG: CONFIG: Font changed: Sans 10

** (netbook-launcher:3761): DEBUG: CONFIG: Connecting to ConsoleKit for suspend/resume restarting
** (desktop-switcher:3755): DEBUG: Restoring panel settings
WARNING: failed to associate schema `/schemas/apps/go-home-applet/prefs/icon_name' with key `/apps/panel/applets/applet_0/prefs/icon_name': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Could not send message to gconf daemon: Message did not receive a reply (timeout by message bus))
** (desktop-switcher:3755): DEBUG: 
Restored panel configuration from: /home/saad/.config/desktop-switcher/netbook-panel-config.xml

** (desktop-switcher:3755): DEBUG: Removing nautilus from gnome session startup

** (desktop-switcher:3755): WARNING **: Failed to send buffer

** (desktop-switcher:3755): WARNING **: Failed to send buffer

** (netbook-launcher:3761): WARNING **: Failed to send buffer

** (netbook-launcher:3761): WARNING **: Failed to send buffer
saad@saad-netbook:~$ Cannot register the panel shell: there is already one running.
** (netbook-launcher:3761): DEBUG: PLACES: Volume Added: 66.4 GB Media /org/freedesktop/Hal/devices/volume_uuid_003C45DF3C45CFF8
** (netbook-launcher:3761): DEBUG: PLACES: Volume Added: 77.4 GB Media /org/freedesktop/Hal/devices/volume_uuid_A2F48F73F48F490D
** (netbook-launcher:3761): DEBUG: PLACES: Volume Added: PE /org/freedesktop/Hal/devices/volume_uuid_CCED_990E

---

### Post by saadkamal on 2009-08-11
I removed all the gnome config folder from my home directory but still its not helping. 

I'd really appreciate if anyone has a solution for this! 

Thanks

---

### Post by bubuka on 2009-09-02
I have exactly the same problem, switching works fine - until the next reboot. Then I see only the blank desktop and that's it..
Is there any workaround for this problem?


SORRY!
Since then I have found this:
[https://bugs.launchpad.net/desktop-switcher/+bug/349519?comments=all](https://bugs.launchpad.net/desktop-switcher/+bug/349519?comments=all)

it worked for me..

---

