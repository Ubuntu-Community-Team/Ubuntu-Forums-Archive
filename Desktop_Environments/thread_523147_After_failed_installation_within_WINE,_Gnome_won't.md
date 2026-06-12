---
title: "After failed installation within WINE, Gnome won't load"
date: 2007-08-11
forum: Desktop Environments
---

### Post by Mr. Farlops on 2007-08-11
Hello, and apologies in advance for covering old ground.

A few days ago I purchased a Darter Ultra--my first new hardware in seven (?!) years--and have been very pleased with it. Everything (With the exception of the fingerprint reader--no big deal.) just worked right out of the box or with a little minor tweaking. Apt-get works just fine, everything just goes as smooth as silk. Very happy!

Now, I've never tried my hand at WINE before since I felt that none of my other machines were powerful enough to run it. But now that I've got the iron, I decided to give it a try.

WINE installed just fine. I stuck with default configuration--Windows 2000 emulation (I know, WINE Is Not an Emulator.).

Then I tried to install an eight year old Windows game within it. This went mostly smoothly--except for brief error message towards the end of the install process. Something like "Win95 direct [something but not Direct X] failed" I figured with was some little weird, undocumented video hook thing and, daring lad that I am, I just blew by it.

I tried to start the game. My screen flickers a few times and then flips into a weird resolution where I can't see the whole desktop. I assume this was a failed attempt to go  into full screen mode.

The Gnome spinner just sits there and spins and spins and spins. My mouse can shake it around but I can't switch back to Gnome desktop or to other tasks. My system appears to be hung in trying to start this ol' Windows game. Not remembering the command to flip into the shell to kill X, I force a reboot.

The system boots and it appears to start X but then it won't bring me to the Gnome log in. The spinner is visible but it just sits there and spins and spins and spins.

I assume that this Windows game, via WINE, wrote some weird, bogus command to my   Gnome config files and if I were to delete that line Gnome would load fully like it's supposed to.

I can boot from GRUB into kernal recovery mode but when I try "startx" it loads this incomplete version of Gnome. (Which I assume is the expected behavior?)

The thing is where in my user account filepath can I find the Gnome config files so I can look at them and paste them here so you kind folks can tell me what lines to delete and edit?

---

### Post by ajgreeny on 2007-08-11
Try renaming .gconf in your home directory .gconf.bak?  I suspect a new .gconf folder will be made automatically, then perhaps you can bring all the separate bits of the original into the new folder one by one, until something goes wrong again.  Its a bit long winded, I know, unless you can look carefully into the contents of all the parts of the original folder until you come up with a likely offending configuration entry.

Good luck.  Let us know the problem when you find it.

---

### Post by Mr. Farlops on 2007-08-11
AJ,

In kernal recovery mode, from the shell, I tried renaming .gconf and .gconfd to .gconf.bak and .gconfd.bak respectively. I also started X to remove WINE with synaptic, just to be on the safe side. I then rebooted.

The problem remains. 

Ubunutu's boot process starts normally enough but when X starts the screen flickers a bit, trying to find the right resolution and driving rate I guess, but it remains black. There is disk activity while it's doing this, like it's loading and trying things. The mouse spinner appears, spinning, but it never brings me into the color, user log in form. It just sits there spinning. It will stay there spinning uselessly if I let it.

So I rebooted into kernal recovery mode and looked at my home directory. New .gcon* directories were not created. It's odd.

Should I review the log files, if any, within .xsession-errors? Should I try the rename trick on the .gnom* directories? 

Should I mess with .nautilus, .Xauthority or .config? I don't know what settings these directories effect, even though they seem suggestively related to my problem. I don't want to mess with them until I know what they do.

The fact that X gets so close to loading everything fully suggests to me that the problem is simple to fix if I only knew where it was.

Might it be possible that gnome was damaged outside of my home directory?

---

### Post by Mr. Farlops on 2007-08-12
So I'm doing a little research on this thing and, perversity in the universe tending to a maximum, I pick one of the ***few*** old games that WINE 9.16 and higher doesn't run:

[http://appdb.winehq.org/appview.php?iVersionId=3058](http://appdb.winehq.org/appview.php?iVersionId=3058)

I don't know if this helps others troubleshoot my problem but I'd figure add this data.

---

### Post by Mr. Farlops on 2007-08-12
If it helps, here is edited output of my .xsession-errors file:

```
Window manager warning: Window 0x3204536 () sets an MWM hint indicating it isn't resizable, but sets min size 486 x 278 and max size 2147483647 x 2147483647; this doesn't make much sense.
Window manager warning: Window 0x3204536 () sets an MWM hint indicating it isn't resizable, but sets min size 486 x 278 and max size 2147483647 x 2147483647; this doesn't make much sense.
wine: creating configuration directory '/home/pace/.wine'...
wine: '/home/pace/.wine' created successfully.
evolution-alarm-notify-Message: Alarm callback!
evolution-alarm-notify-Message: Process alarm with trigger 1186815600
check_midnight_refresh)
alarm-queue.c:1837 (check_midnight_refresh)
alarm-queue.c:1837 (check_midnight_refresh)
alarm-queue.c:1837 (check_midnight_refresh)
alarm-queue.c:279 (midnight_refresh_cb) - Invoking task for midnight refresh
alarm-notify.c:349 (alarm_msg_received) - 0x80cff80: Received at thread b33fab90
alarm-queue.c:249 (midnight_refresh_async) 
alarm-queue.c:233 (add_client_alarms_cb) - Adding (nil)
alarm-queue.c:560 (load_alarms_for_today) - From Sat Aug 11 00:00:01 2007
 to Sat Aug 11 00:00:01 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:516 (load_alarms) - Disconnecting old queries 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-queue.c:233 (add_client_alarms_cb) - Adding (nil)
alarm-queue.c:560 (load_alarms_for_today) - From Sat Aug 11 00:00:01 2007
 to Sat Aug 11 00:00:01 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:516 (load_alarms) - Disconnecting old queries 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-queue.c:233 (add_client_alarms_cb) - Adding evolution-alarm-notify-Message: alarm.c:235: Requested removal of nonexistent alarm!
evolution-alarm-notify-Message: Setting timeout for 86400 1186902000 1186815600
evolution-alarm-notify-Message:  Sun Aug 12 00:00:00 2007

evolution-alarm-notify-Message:  Sat Aug 11 00:00:00 2007

fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
Window manager warning: Treating resize request of legacy application 0x5a00001 (Win95 Inte) as a fullscreen request
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:font:WineEngCreateFontInstance Untranslated charset 228
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x5400001 specified for 0x5400002 (Electronic).
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x5400001 specified for 0x5400009 (Electronic).
Window manager warning: Treating resize request of legacy application 0x5000001 (Planescape) as a fullscreen request
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x181bf0) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x16e6e8)->(0xb00d6,00000011)
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
The application 'gnome-session' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
gnome-panel: Fatal IO error 104 (Connection reset by peer) on X server :0.0.

(gaim:21224): libgnomevfs-WARNING **: Failed to re-activate daemon: Connection is closed
Window manager warning: Fatal IO error 104 (Connection reset by peer) on display ':0.0'.
nautilus: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
The application 'gnome-cups-icon' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'evolution-2.10' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
X connection to :0.0 broken (explicit kill or server shutdown).
```

Of particular note is the line that says, "Window manager warning: Treating resize request of legacy application 0x5000001 (Planescape) as a fullscreen request"

---

