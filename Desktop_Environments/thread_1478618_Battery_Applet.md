---
title: "Battery Applet"
date: 2010-05-09
forum: Desktop Environments
---

### Post by perky on 2010-05-09
**Latest version:**   1.05 - 28/Jul/2010

**Rationale:** [Missing functionality]("https://bugs.launchpad.net/indicator-application/+bug/527458") in default Ubuntu power manager icon.  

**Features:** Displays battery status in the GNOME panel (more stats in tooltip).  Plays a sound & blinks when the battery is low.  Additional options are in gconf-editor under /apps/battery-status-applet

**To install:**  Save and extract BattStatus.zip to a temporary directory, then cd to where you extracted the files and type:

```
sudo sh install.sh
```

GNOME Panel will reload and the applet should now appear in the '**Add to Panel**' list as '**Battery Status Applet**'.

**Known bugs:**

Most bugs are caused by conflicting gconf settings from older versions and can be fixed by:
[LIST=1]
[*]Removing the applet
[*]Running as regular user: gconftool-2 --recursive-unset '/apps/battery-status-applet'
[*]Re-adding the applet
[/LIST]

The error: ...OAFIID:GNOME_PythonPanelApplet... means that the OAFIID in the .server file does not match the last line in the .py file.
Installing the latest version fixes this.

Other distros display a default icon unless Humanity icon theme is installed (will be fixed when I get around to making my own icons)

Thanks to all that have helped identify bugs :)

**Uninstall instructions:**
```
sudo rm /usr/lib/bonobo/servers/battery_status.server
sudo rm /usr/local/bin/batteryStatus.py
```

---

### Post by Konrad Ansehelm on 2010-05-14
This looks great, if only I could place it in my Netbook Edition, but there does not seem to be a way to add icons to the panel.

---

### Post by perky on 2010-05-14
> **Konrad Ansehelm said:**
> This looks great, if only I could place it in my Netbook Edition, but there does not seem to be a way to add icons to the panel.

Thanks :)

I've read somewhere that the Indicator Applet takes up the entire panel in the Netbook edition.

Try removing the Indicator Applet, add the Battery Applet, then put back the Indicator Applet.

---

### Post by Clancy_s on 2010-05-17
It works beautifully, thank you.

---

### Post by bennie88 on 2010-05-23
Great applet. Thanks!

---

### Post by sumedh.bhogle on 2010-05-24
cool, it works!! thanks!!

---

### Post by bornagainpenguin on 2010-05-26
Thank you for this!

--bornagainpenguin

---

### Post by perky on 2010-05-30
Thanks for the feedback, and glad to hear it works :)

New version available today, please let me know if something doesn't work so I can fix!

---

### Post by mehsme on 2010-06-03
Sticky?

---

### Post by auxbuss on 2010-06-06
Doesn't work on my clean Lucid install. Install script works fine, but adding the applet doesn't result in any change to the panel. i.e. the applet doesn't appear.

Let me know what debug info you require.

---

### Post by perky on 2010-06-06
> **auxbuss said:**
> Doesn't work on my clean Lucid install. Install script works fine, but adding the applet doesn't result in any change to the panel. i.e. the applet doesn't appear.

Let me know what debug info you require.

Could you please run this in a terminal and paste the results here?
```
python /usr/local/bin/batteryStatus.py 1
```

Passing a parameter will open the applet as a window and should output any debugging info.

Cheers!

---

### Post by auxbuss on 2010-06-07
```

$ python /usr/local/bin/batteryStatus.py 1
settings loaded
Traceback (most recent call last):
  File "/usr/local/bin/batteryStatus.py", line 601, in <module>
    sample_factory(app, None)
  File "/usr/local/bin/batteryStatus.py", line 592, in sample_factory
    BattStatus(applet)
  File "/usr/local/bin/batteryStatus.py", line 112, in __init__
    self.loadSettings()
  File "/usr/local/bin/batteryStatus.py", line 435, in loadSettings
    self.saveSettings()
  File "/usr/local/bin/batteryStatus.py", line 381, in saveSettings
    g.set_string(gP + "panel.separator", self.sep)
TypeError: GConfClient.set_string() argument 2 must be string, not None
```

Running this again, I noticed that adding the applet adds a single white pixel in the middle of the panel.

---

### Post by perky on 2010-06-07
> **auxbuss said:**
> 
Running this again, I noticed that adding the applet adds a single white pixel in the middle of the panel.

Thanks!  Found the little critter, new version is up, or you can just run: sudo gedit /usr/local/bin/batteryStatus.py
Search for: if self.sep == None:
and change that line to: if self.sep == None: **self.**sep = "<span foreground='#777777'>|</span>"

Once saved you can do a killall gnome-panel to reload the applet (there may be more than one on the panel when this happens).

Cheers :)

---

### Post by codethief on 2010-06-07
Still doesn't work. Adding it to the panel results in an error message.

```

codethief@philosoph:~$ python /usr/local/bin/batteryStatus.py 1
Traceback (most recent call last):
  File "/usr/local/bin/batteryStatus.py", line 56, in <module>
    dev_obj = bus.get_object ('org.freedesktop.Hal', udis[0])
IndexError: list index out of range
```

---

### Post by perky on 2010-06-08
> **codethief said:**
> Still doesn't work. Adding it to the panel results in an error message.

```

codethief@philosoph:~$ python /usr/local/bin/batteryStatus.py 1
Traceback (most recent call last):
  File "/usr/local/bin/batteryStatus.py", line 56, in <module>
    dev_obj = bus.get_object ('org.freedesktop.Hal', udis[0])
IndexError: list index out of range
```


It may be possible that HAL is not detecting your battery, or the battery is classified as something other than 'battery'.  Could you please report the output of this command?  lshal | grep battery

Other than that, not too sure :/ Stats will come from DeviceKit in the near future (instead of HAL), so maybe that will help.

Thanks for the pick-up, added some error checking for unsupported batteries or for when there is no battery present.

---

### Post by auxbuss on 2010-06-08
Yup, all fixed. Thanks v.much for the app.

---

### Post by codethief on 2010-06-08
HAL seems to recognize my battery. (Otherwise, there wouldn't be any info about it in the default battery applet, either, right?)
Here's the result:
```
codethief@philosoph:~$ lshal | grep battery
udi = '/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0'
  battery.charge_level.current = 59018  (0xe68a)  (int)
  battery.charge_level.design = 103896  (0x195d8)  (int)
  battery.charge_level.last_full = 103884  (0x195cc)  (int)
  battery.charge_level.percentage = 56  (0x38)  (int)
  battery.charge_level.rate = 37662  (0x931e)  (int)
  battery.is_rechargeable = true  (bool)
  battery.model = '42T4803'  (string)
  battery.present = true  (bool)
  battery.rechargeable.is_charging = true  (bool)
  battery.rechargeable.is_discharging = false  (bool)
  battery.remaining_time = 4288  (0x10c0)  (int)
  battery.reporting.current = 5317  (0x14c5)  (int)
  battery.reporting.design = 9360  (0x2490)  (int)
  battery.reporting.last_full = 9359  (0x248f)  (int)
  battery.reporting.rate = 3393  (0xd41)  (int)
  battery.reporting.technology = 'Li-ion'  (string)
  battery.reporting.unit = 'mAh'  (string)
  battery.serial = ' 1187'  (string)
  battery.technology = 'lithium-ion'  (string)
  battery.type = 'primary'  (string)
  battery.vendor = 'LGC 11'  (string)
  battery.voltage.current = 11980  (0x2ecc)  (int)
  battery.voltage.design = 11100  (0x2b5c)  (int)
  battery.voltage.unit = 'mV'  (string)
  info.capabilities = {'battery'} (string list)
  info.category = 'battery'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0'  (string)
  input.keymap.data = {'0x01:screenlock', '0x02:battery', '0x03:sleep', '0x04:wlan', '0x06:switchvideomode', '0x07:f22', '0x08:f24', '0x0b:suspend', '0x0f:brightnessup', '0x10:brightnessdown', '0x11:kbdillumtoggle', '0x13:zoom', '0x14:volumeup', '0x15:volumedown', '0x16:mute', '0x17:prog1'} (string list)

```

---

### Post by qweabab1 on 2010-06-08
I have the same problem

---

### Post by perky on 2010-06-14
> **codethief said:**
> Still doesn't work. Adding it to the panel results in an error message.

> **qweabab1 said:**
> I have the s[am]("http://www.ibm.com/")e problem

Looking closer at the error you reported (array index out of range), it seems likely that either the dbus, hal or hal manager objects are not being created properly.

The array is supposed to hold all devices found with the capability of 'battery', but this is dependant on previous statements working.

I've added some extra debugging info in today's version, if you could install it and post the output that would be great.

---

### Post by codethief on 2010-06-15
```
codethief@philosoph:~/Desktop/BattStatus$ python /usr/local/bin/batteryStatus.py 1
battery found: /org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0
settings loaded
settings saved
updating theme
theme changed
theme changed
theme changed
^CTraceback (most recent call last):
  File "/usr/local/bin/batteryStatus.py", line 158, in update
    self.hbox.set_tooltip_markup(self.tooltipText())
  File "/usr/local/bin/batteryStatus.py", line 383, in tooltipText
    if not self.full(): result += "%s %s:\t%s\n" %("Approx time to", destFullOrEmpty, strTimeLeft)
  File "/usr/local/bin/batteryStatus.py", line 212, in full
    return not (self.charging() or self.discharging())
  File "/usr/local/bin/batteryStatus.py", line 203, in charging
    return (dev.GetProperty('battery.rechargeable.is_charging') or
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
KeyboardInterrupt

(batteryStatus.py:8129): Bonobo-WARNING **: Never got frame, control died - abnormal exit condition
^CTraceback (most recent call last):
  File "/usr/local/bin/batteryStatus.py", line 630, in <module>
    gtk.main()
KeyboardInterrupt
codethief@philosoph:~/Desktop/BattStatus$
```

As you can see, I hit Ctrl+C twice to exit the script (which had stopped after 'theme changed') . Meanwhile, a small (empty) window appeared whose contents were drawn the second I pressed Ctrl+C for the first time. (See attachments)

---

### Post by nilarimogard on 2010-06-15
Try [Battery Status]("http://www.webupd8.org/2010/05/battery-status-01-released-improved.html") - it's a lot batter than the battery applet and has power management built-in.

---

### Post by codethief on 2010-06-15
@perky: I removed my battery some minutes ago and rebooted (dunno what I did first) and suddenly, the battery applet appeared (I had tried to add it to the panel again before my previous post). ;)
Now, is it a wanted behavior that the applet still shows info when the battery is no longer plugged in? (See attachment, at this time the laptop was on AC power!)

---

### Post by perky on 2010-06-17
> **codethief said:**
> @perky: I removed my battery some minutes ago and rebooted (dunno what I did first) and suddenly, the battery applet appeared (I had tried to add it to the panel again before my previous post). ;)
Now, is it a wanted behaviour that the applet still shows info when the battery is no longer plugged in? (See attachment, at this time the laptop was on AC power!)

That's good that it works, strange way of getting it working though!  The alignment of the text looks off though, forgot to cater for different font sizes (added to todo..).  [Edit: fixed]

Yep it's a wanted behaviour to still show (less) power information on AC - though I've taken away two of the fields.  I guess the logic is you wouldn't really need to mouseover to get info if you're on AC (except if you configured it to only show icon), but it's still nice to have just the information that is relevant/useful.

Also, you can enable 'Compact tooltips' to display less info.

---

### Post by trc on 2010-06-24
hey can you guys tell me how i would uninstall this battery applet so the icon no longer shows up in my add panel section???

---

### Post by perky on 2010-06-24
> **trc said:**
> hey can you guys tell me how i would uninstall this battery applet so the icon no longer shows up in my add panel section???

G'day :)

Forgot to include uninstall instructions:

```
sudo rm /usr/lib/bonobo/servers/battery_status.server
sudo rm /usr/local/bin/batteryStatus.py
```

---

### Post by trc on 2010-06-24
thank you for your help!

---

### Post by bornagainpenguin on 2010-07-20
I was happy to see someone was trying to bring this back for those of us who preferred the old battstat method of knowing where our battery life was with a glance; unfortunately every reboot requires that I delete and then add it back to the notification area.  Not my idea of a fun time.  So I went back to my "dirty hack" method of installing Debian debs with the applet still available.

[quote=bornagainpenguin]I was able to "cheat" by going to the nearest Debian mirror (in my case: [http://debian.osuosl.org/debian/pool/main/g/gnome-applets/]("http://debian.osuosl.org/debian/pool/main/g/gnome-applets/")  ) and installing the appropriate gnome-applets AND gnome-applets-data for my version of Gnome. I ignored warnings that I was installing newer versions of the software than what was in the channel and after some dependencies were installed and I did a quick logout I was able to add back the battstat icon to my panel. This way seems to be better than having to do a complete build of the package manually and works on Ubuntu Karmic.[/quote]

On Ubuntu Lucid 10.4 this still works, but you also need to install the libnotify1 from [http://debian.osuosl.org/debian/pool/main/libn/libnotify/]("http://debian.osuosl.org/debian/pool/main/libn/libnotify/") that matches the Ubuntu version of Gnome.  Do a restart and the battstat applet will be right where it used to be before developer stupidity caused Canonical to remove it from the distro.

Here's a heads up for any Canonical developers: If you want to remove or "depreciate" a piece of system software, it's usually a good idea to make sure that the replacement works just as well as what is being removed...

--bornagainpenguin

---

### Post by perky on 2010-07-20
> **bornagainpenguin said:**
> I was happy to see someone was trying to bring this back for those of us who preferred the old battstat method of knowing where our battery life was with a glance; unfortunately every reboot requires that I delete and then add it back to the notification area.  Not my idea of a fun time.  So I went back to my "dirty hack" method of installing Debian debs with the applet still available.


I probably should have done a bit more research before starting this project, there are indeed a few good alternatives out there, one mentioned in this thread already.  However, it's still interesting to explore a new language, and I'll continue to tinker.  Good to have more choice too.

Glad that you found an alternative - I did as well, Archlinux :D (My Ubuntu broke recently, could not boot or even ls in recovery mode.) Arch comes with the power meter you mentioned, but I'll continue to use/develop this one.

If you have a spare few mins it would be great if you could pm or post any error messages :)  I have a feeling that [a line in the install script]("http://ubuntuforums.org/showthread.php?t=1531216") is causing grief.  Try running this as a regular user:  gconftool --recursive-unset '/apps/battery-status-applet'
Then removing the applet and re-adding.

> 
Here's a heads up for any Canonical developers: If you want to remove or "depreciate" a piece of system software, it's usually a good idea to make sure that the replacement works just as well as what is being removed...


They won't listen, their [master has spoken]("https://bugs.launchpad.net/indicator-application/+bug/527458").. the next release is focused on getting Ubuntu to work with a ..tablet.. :rolleyes: ..so bye-bye tooltips for now..

---

### Post by bornagainpenguin on 2010-07-21
> **perky said:**
> I probably should have done a bit more research before starting this project, there are indeed a few good alternatives out there, one mentioned in this thread already.  However, it's still interesting to explore a new language, and I'll continue to tinker.  Good to have more choice too.

Please don't misunderstand me, I'm glad that you're working on your battery applet!  The dirty hack I used to get battstat to work is not guaranteed to last beyond a single update by Canonical, all I can do is hope that there is an update from Debian I can revert to and how long before some developer with a bug up his butt decides to do something that makes it impossible to fix after an update?  There's a reason why I call it a dirty hack...

Your work means there is a chance we'll see something that can be used in the future once the battstat has been completely removed from the system or its underpinnings removed completely to the point it no longer functions.

> **perky said:**
> Glad that you found an alternative - I did as well, Archlinux :D (My Ubuntu broke recently, could not boot or even ls in recovery mode.) Arch comes with the power meter you mentioned, but I'll continue to use/develop this one.

Personally I'm waiting on the next release of Debian to see if I can switch to it, or I plan to try to make Fedora 13 work for me.  Canonical is clearly hellbent on losing users for some reason, so it will be time to switch sooner or later.  It's a shame to see a once great distro do this but what can you do?

> **perky said:**
> If you have a spare few mins it would be great if you could pm or post any error messages :)  I have a feeling that [a line in the install script]("http://ubuntuforums.org/showthread.php?t=1531216") is causing grief.  Try running this as a regular user:  gconftool --recursive-unset '/apps/battery-status-applet'
Then removing the applet and re-adding.

It was just a standard message that shows up once in a while about a bad applet no longer being available and would you like to delete it.  I've seen it before on other installs, this is just the first time I'd seen it happen so consistently!  

I'm attaching the message as a screenshot, hopefully that will help.

> **perky said:**
> They won't listen, their [master has spoken]("https://bugs.launchpad.net/indicator-application/+bug/527458").. the next release is focused on getting Ubuntu to work with a ..tablet.. :rolleyes: ..so bye-bye tooltips for now..

Yeah.  So how long has Jean-Louis Gassée been running Canonical now?  This whole thing smells so much like one of his infamous "focus shifts" it ain't funny.  Of course we all remember what happened to the BeOS when they had *their* focus shift...

--bornagainpenguin

---

### Post by perky on 2010-07-21
> **bornagainpenguin said:**
> Personally I'm waiting on the next release of Debian to see if I can switch to it, or I plan to try to make Fedora 13 work for me. Canonical is clearly hellbent on losing users for some reason, so it will be time to switch sooner or later. It's a shame to see a once great distro do this but what can you do?

Hope that it gets fixed :)  It's still a great OS and one of the best, but sometimes it's nice to try a different distro.

> **bornagainpenguin said:**
> 
I'm attaching the message as a screenshot, hopefully that will help.

Definately, thanks :)

This error means the contents of the .server file does not match the last line of the .py file.

Installing the latest version should fix this error.

---

### Post by perky on 2011-03-05
yo if anyone wants to finish this off you're welcome, i dont have time sorry :(
needs to migrate to devicekit or whatever the latest interface is.  thanks!

References:
[LIST]
[*]TODO: change to DeviceKit:  [http://hal.freedesktop.org/docs/DeviceKit-power/Device.html#Device.GetStatistics]("http://hal.freedesktop.org/docs/DeviceKit-power/Device.html#Device.GetStatistics")
[*]CURRENT HAL API: [http://www.marcuscom.com/hal-spec/hal-spec.html#device-properties-battery]("http://www.marcuscom.com/hal-spec/hal-spec.html#device-properties-battery")
[/LIST]

---

