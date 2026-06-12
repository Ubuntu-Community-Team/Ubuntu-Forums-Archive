---
title: "Digital camera not showing up on Dolphin, but it does on Nautilus..."
date: 2010-05-19
forum: Desktop Environments
---

### Post by eks on 2010-05-19
Hello

I'm using Kubuntu, but installed Nautilus so I could use Dropbox. Yesterday I plugged my camera and it popped up a window asking what to do, but it didn't list any application, and the only option available was Cancel. Then I couldn't find it anywhere on the system, neither where it was mounted.

Today I've turned on an USB hard disk and Nautilus popped up (why? shouldn't be dolphin...?), then afterwards plugged in the camera, and there it was on Nautilus. But in it's interface I also couldn't find the mount point... :confused:

I've seen I can add an entry on Dolphin's "Places", but I need the mount point... Where should I look?

Is there a way to make Dolphin add the entry automatically?

Device Actions under System Settings is a bit confusing... And Digital Camera (also under System Settings) gives "Unable to initialize camera, check your port settings and camera connectivity and try again. Could not lock the device", and indeed, I can't unmount it on Nautilus....

---

### Post by bailout on 2010-05-19
Nautilus will take over the system and is best avoided unless you run gnome. I did see some kde frnot ends for dropbox a while ago, maybe on kde-apps, but I haven't used them myself. I would try and get rid of nautilus, although that might not be easy, and search for a kde alternative for dropbox.

---

### Post by ajgreeny on 2010-05-19
I don't use KDE at all, so can't help with that but the camera is probably mounted in /media, particularly if it is seen as a usb mass storage device.

---

### Post by manvvip on 2012-03-29
12.10

I cannot mount my camera, (canon ixus 100) It's not in media,

so cannot find it in Dolphin.

When I open nautilus, I can see it mounted.

I also installed nautilus via dropbox.

---

### Post by SeijiSensei on 2012-03-29
Try installing digikam ("sudo apt-get install digikam") and see if it detects your camera.

---

### Post by manvvip on 2012-03-29
Thanks, Digikam is fine. (Detects the camera) (Also removed Dropbox and Nautilus, will do it through KDE).

Was wanting access via Dolphin though.

Does anyone know how to do that?

---

