---
title: "Can't control bluetooth speaker volume from systray"
date: 2022-09-09
forum: Desktop Environments
---

### Post by TechnoJunky on 2022-09-09
I have a Dell laptop and used to have an Oontz Angle 3 Portable bluetooth speaker.  When using it, it acted as expected all the time.  Something happened to it and it wouldn't charge anymore.  My wife also had a Oontz, but it was the Angle 3 Plus Edition.  I have taken it but I can't control the volume via the system tray sound icon like I could with my old speaker.  When I mouse over it and use the scroll wheel, the volume remains the same on the speaker no matter what the volume percentage is.  150% is just as loud as 1% or vise versa.  The only setting that is accurate is 0%.  When I bring up the sound properties, under Playback Devices, the Oontz is selected, and when using the scroll wheel, you can see it going left and right, but no change in volume.  The only 2 ways I can control it are via the speaker buttons and the application's volume (Firefox, VLC, etc).  When I have my laptop plugged into my HDMI monitor, sound is controlled via the system tray just fine, as is the internal laptop speakers.  The issue is only present on this particular Oontz speaker.

There is 1 exception to this.  Due to an patching bug, I had to reinstall LInux on my laptop earlier this week.  After the reinstallation (don't remember if it was before or after updating patches) the speaker volume was controlled via the system tray.  However, today it's back to not working.

Any ideas on how to fix this?

---

### Post by #&amp;thj^% on 2022-09-09
Not sure I can help here but may we see:
```
inxi -ExAx

```
Mine looks:
```
Audio:
  Device-1: NVIDIA driver: snd_hda_intel v: kernel bus-ID: 4-1.1.1:4 pcie:
    chip-ID: 17e9:4307 speed: 2.5 GT/s lanes: 8 bus-ID: 01:00.1
    chip-ID: 10de:10fa
  Device-2: AMD ACP/ACP3X/ACP6x Audio Coprocessor vendor: Lenovo
    driver: N/A pcie: speed: 16 GT/s lanes: 16 bus-ID: 05:00.5
    chip-ID: 1022:15e2
  Device-3: AMD Family 17h/19h HD Audio vendor: Lenovo
    driver: snd_hda_intel v: kernel pcie: speed: 16 GT/s lanes: 16
    bus-ID: 05:00.6 chip-ID: 1022:15e3
  Device-4: DisplayLink UOEOS Laptop Dock type: USB
    driver: cdc_ncm,snd-usb-audio
  Sound Server-1: ALSA v: k5.19.8-hardened2-1-hardened running: yes
  Sound Server-2: JACK v: 1.9.21 running: no
  Sound Server-3: PulseAudio v: 16.1 running: yes
  Sound Server-4: PipeWire v: 0.3.57 running: yes
Bluetooth:
  Device-1: Intel AX200 Bluetooth type: USB driver: btusb v: 0.8
    bus-ID: 3-3:5 chip-ID: 8087:0029
  Report: rfkill ID: hci0 rfk-id: 3 state: up address: see --recommends


```
some times I had to point directly to play sound through that Bluetooth Speaker i was using/testing.
EDIT: I had a memory jog is this installed>>> "plasma-pa"

---

### Post by TechnoJunky on 2022-09-09
Audio:
  Device-1: Intel CM238 HD Audio vendor: Dell driver: snd_hda_intel v: kernel
    bus-ID: 00:1f.3 chip-ID: 8086:a171
  Sound Server-1: ALSA v: k5.15.0-47-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Bluetooth:
  Device-1: Intel Bluetooth wireless interface type: USB driver: btusb v: 0.8
    bus-ID: 1-5:4 chip-ID: 8087:0a2a
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: 74:E5:F9:53:D6:7F
    bt-v: 2.1 lmp-v: 4.2 sub-v: 1000

---

### Post by #&amp;thj^% on 2022-09-09
That looks Ok, but will you show this as well:
```
apt policy plasma-pa
```
And at time during the testing cycle I was able to get things prim and proper with:
```
sudo apt-get install plasma-pa
killall plasmashell
plasmashell &
```

---

### Post by TechnoJunky on 2022-09-09
plasma-pa:
  Installed: 4:5.24.5-0ubuntu0.1
  Candidate: 4:5.24.5-0ubuntu0.1
  Version table:
 *** 4:5.24.5-0ubuntu0.1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     4:5.24.4-0ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/universe amd64 Packages

---

### Post by #&amp;thj^% on 2022-09-09
And the rest of it?

---

### Post by TechnoJunky on 2022-09-09
```

~$ kf.plasma.quick: Applet preload policy set to 1
file:///usr/share/plasma/plasmoids/org.kde.plasma.systemmonitor/contents/ui/main.qml:43:5: QML MouseArea: Cannot anchor to an item that isn't a parent or sibling.
file:///usr/share/plasma/plasmoids/org.kde.plasma.systemmonitor/contents/ui/main.qml:41: TypeError: Cannot read property 'length' of undefined
file:///usr/share/plasma/plasmoids/org.kde.plasma.systemmonitor/contents/ui/main.qml:43:5: QML MouseArea: Cannot anchor to an item that isn't a parent or sibling.
file:///usr/share/plasma/plasmoids/org.kde.plasma.systemmonitor/contents/ui/main.qml:41: TypeError: Cannot read property 'length' of undefined
file:///usr/share/plasma/plasmoids/org.kde.plasma.systemmonitor/contents/ui/main.qml:43:5: QML MouseArea: Cannot anchor to an item that isn't a parent or sibling.
file:///usr/share/plasma/plasmoids/org.kde.plasma.systemmonitor/contents/ui/main.qml:41: TypeError: Cannot read property 'length' of undefined
file:///usr/share/plasma/plasmoids/org.kde.plasma.systemmonitor/contents/ui/main.qml:43:5: QML MouseArea: Cannot anchor to an item that isn't a parent or sibling.
file:///usr/share/plasma/plasmoids/org.kde.plasma.systemmonitor/contents/ui/main.qml:41: TypeError: Cannot read property 'length' of undefined
file:///usr/share/plasma/plasmoids/org.kde.plasma.systemmonitor/contents/ui/main.qml:43:5: QML MouseArea: Cannot anchor to an item that isn't a parent or sibling.
file:///usr/share/plasma/plasmoids/org.kde.plasma.systemmonitor/contents/ui/main.qml:41: TypeError: Cannot read property 'length' of undefined
file:///home/carl/.local/share/plasma/plasmoids/org.kde.userbase.plasma.luna-ii/contents/ui/main.qml:56: TypeError: Cannot read property 'subText' of undefined
file:///home/carl/.local/share/plasma/plasmoids/org.kde.userbase.plasma.luna-ii/contents/ui/main.qml:55: TypeError: Cannot read property 'text' of undefined
qml: PlasmaExtras.ScrollArea is deprecated. Use PlasmaComponents3.ScrollView instead.
file:///usr/share/ksysguard/sensorfaces/org.kde.ksysguard.linechart/contents/ui/FullRepresentation.qml:22:1: QML FullRepresentation: Binding loop detected for property "implicitHeight"
file:///usr/share/ksysguard/sensorfaces/org.kde.ksysguard.linechart/contents/ui/FullRepresentation.qml:22:1: QML FullRepresentation: Binding loop detected for property "implicitHeight"
qt.core.qabstractitemmodel.checkindex: Index QModelIndex(-1,-1,0x0,QObject(0x0)) is not valid (expected valid)
file:///usr/share/ksysguard/sensorfaces/org.kde.ksysguard.barchart/contents/ui/FullRepresentation.qml:23:1: QML FullRepresentation: Binding loop detected for property "implicitHeight"
file:///usr/share/ksysguard/sensorfaces/org.kde.ksysguard.linechart/contents/ui/FullRepresentation.qml:22:1: QML FullRepresentation: Binding loop detected for property "implicitHeight"
trying to show an empty dialog
file:///usr/share/ksysguard/sensorfaces/org.kde.ksysguard.linechart/contents/ui/LineChart.qml:57:9: Unable to assign [undefined] to int
file:///usr/share/ksysguard/sensorfaces/org.kde.ksysguard.horizontalbars/contents/ui/FullRepresentation.qml:28:9: Unable to assign [undefined] to double
file:///usr/share/ksysguard/sensorfaces/org.kde.ksysguard.barchart/contents/ui/BarChart.qml:54:9: Unable to assign [undefined] to int
file:///usr/share/ksysguard/sensorfaces/org.kde.ksysguard.linechart/contents/ui/LineChart.qml:57:9: Unable to assign [undefined] to int
file:///usr/share/ksysguard/sensorfaces/org.kde.ksysguard.linechart/contents/ui/LineChart.qml:57:9: Unable to assign [undefined] to int
trying to show an empty dialog
file:///usr/share/plasma/shells/org.kde.plasma.desktop/contents/views/Desktop.qml:118:19: QML Loader: Binding loop detected for property "height"
file:///usr/share/plasma/shells/org.kde.plasma.desktop/contents/views/Desktop.qml:118:19: QML Loader: Binding loop detected for property "height"
file:///usr/share/ksysguard/sensorfaces/org.kde.ksysguard.linechart/contents/ui/LineChart.qml:57:9: Unable to assign [undefined] to int
file:///usr/share/ksysguard/sensorfaces/org.kde.ksysguard.linechart/contents/ui/LineChart.qml:57:9: Unable to assign [undefined] to int
file:///usr/share/ksysguard/sensorfaces/org.kde.ksysguard.barchart/contents/ui/BarChart.qml:54:9: Unable to assign [undefined] to int
kf.quickcharts.deprecated: LegendDelegate::colorVisible is deprecated (since 5.82): Use an empty indicator instead
kf.quickcharts.deprecated: LegendDelegate::layoutWidth is deprecated (since 5.82): Unused
kf.quickcharts.deprecated: LegendDelegate::valueWidth is deprecated (since 5.82): Use maximumValueWidth instead
kf.quickcharts.deprecated: LegendDelegate::colorVisible is deprecated (since 5.82): Use an empty indicator instead
kf.quickcharts.deprecated: LegendDelegate::layoutWidth is deprecated (since 5.82): Unused
kf.quickcharts.deprecated: LegendDelegate::valueWidth is deprecated (since 5.82): Use maximumValueWidth instead
file:///usr/share/ksysguard/sensorfaces/org.kde.ksysguard.linechart/contents/ui/LineChart.qml:57:9: Unable to assign [undefined] to int
Plasma Shell startup completed
file:///usr/share/plasma/plasmoids/org.kde.plasma.digitalclock/contents/ui/DigitalClock.qml:530:9: QML Label: Binding loop detected for property "height"
file:///usr/share/plasma/plasmoids/org.kde.plasma.digitalclock/contents/ui/DigitalClock.qml:495:13: QML Label: Binding loop detected for property "height"
trying to show an empty dialog
Trying to use rootObject before initialization is completed, whilst using setInitializationDelayed. Forcing completion
file:///usr/share/plasma/plasmoids/org.kde.plasma.digitalclock/contents/ui/DigitalClock.qml:495:13: QML Label: Binding loop detected for property "height"
file:///usr/share/plasma/plasmoids/org.kde.plasma.digitalclock/contents/ui/DigitalClock.qml:530:9: QML Label: Binding loop detected for property "height"
file:///usr/share/plasma/plasmoids/org.kde.plasma.digitalclock/contents/ui/DigitalClock.qml:552:5: QML Label: Binding loop detected for property "height"
trying to show an empty dialog
file:///usr/share/plasma/plasmoids/org.kde.panel/contents/ui/main.qml:18:1: QML DropArea (parent or ancestor of QQuickLayoutAttached): Binding loop detected for property "minimumWidth"
libkcups: CUPS-Get-Printers last error: 0 successful-ok
libkcups: Create-Printer-Subscriptions last error: 0 successful-ok
libkcups: Get-Jobs last error: 0 successful-ok
libkcups: Get-Jobs last error: 0 successful-ok
Cyclic dependency detected between "file:///usr/share/plasma/plasmoids/org.kde.plasma.notifications/contents/ui/global/Globals.qml" and "file:///usr/share/plasma/plasmoids/org.kde.plasma.notifications/contents/ui/NotificationHeader.qml"
file:///usr/share/plasma/plasmoids/org.kde.plasma.private.systemtray/contents/ui/ExpandedRepresentation.qml:165:9: QML HiddenItemsView: Binding loop detected for property "implicitHeight"
libkcups: 3 "MX870_MissionControl"
libkcups: 0
libkcups: 0
trying to show an empty dialog
file:///usr/share/plasma/shells/org.kde.plasma.desktop/contents/views/Desktop.qml:118:19: QML Loader: Binding loop detected for property "height"
file:///usr/share/plasma/shells/org.kde.plasma.desktop/contents/views/Desktop.qml:118:19: QML Loader: Binding loop detected for property "height"
trying to show an empty dialog
trying to show an empty dialog
```

---

### Post by #&amp;thj^% on 2022-09-09
If there is still no volume control through the tray, maybe have a look at:
```
cat /etc/default/grub
```
And since kernel 5.15 upwards I've added this to "GRUB_CMDLINE_LINUX_DEFAULT="  
```
GRUB_CMDLINE_LINUX_DEFAULT="i2c-hid.polling_mode=1"
```
You may want to give that a try as well.

---

### Post by TechnoJunky on 2022-09-09
Editing grub worked.  Thank you 1fallen

---

### Post by #&amp;thj^% on 2022-09-09
Nice!
Thanks for marking as solved, I'm not sure if it will help others as well but we did our part. :D

---

