---
title: "How to run/execute a desktop file in terminal mode ?"
date: 2020-10-27
forum: Desktop Environments
---

### Post by oygle on 2020-10-27
I have a desktop file from a live 20.04.1 and cannot determine how to execute it from the terminal ?  See attachment

---

### Post by TheFu on 2020-10-28
.desktop files aren't executable from a shell directly.  The program on the Exec= line is.  Use that.
Also, please don't post images here, especially for text files. Linux isn't Windows.  If you'd posted the text instead, I could copy/paste the exact command you should use.

Also, if the Exec file is a script, the userid attempting to run it must have both read and execute permissions set.

---

### Post by SeijiSensei on 2020-10-28
I don't know why you would want to install 20.04 using that .desktop file. If you have the ISO, then burn it to a USB stick and boot from it.

ISO: [http://cdimage.ubuntu.com/kubuntu/focal/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/focal/daily-live/current/)

Utility to create USB:

```
sudo apt install usb-creator-kde
```

Run usb-creator-kde, point to the ISO image and the USB stick, then run the installer.

Reboot, then tell the BIOS to boot from the stick.

---

### Post by ActionParsnip on 2020-10-28
```

cat ~/Desktop/ubiquity-kdeui.desktop | grep Exec | cut -d"=" -f 2

```

Should give the command being ran in the desktop file

---

### Post by oygle on 2020-10-29
> **TheFu said:**
> .desktop files aren't executable from a shell directly.  The program on the Exec= line is.  Use that.
Also, please don't post images here, especially for text files. Linux isn't Windows.  If you'd posted the text instead, I could copy/paste the exact command you should use.

Also, if the Exec file is a script, the userid attempting to run it must have both read and execute permissions set.

Here are the file contents:

> [Desktop Entry]
Type=Application
Version=1.0
# Do not translate the word "Kubuntu 20.04.1 LTS".  It is used as a marker by casper.
Name=Install Kubuntu 20.04.1 LTS
Comment=Install this system permanently to your hard disk
Keywords=ubiquity;
Exec=ubiquity kde_ui
Icon=ubiquity-kde
Terminal=false
Categories=KDE;Qt;System;
OnlyShowIn=KDE;
X-Ubuntu-Gettext-Domain=ubiquity-desktop

The userid attempting to run it was "kubuntu" and that user had  both read and execute permissions.

> **SeijiSensei said:**
> I don't know why you would want to install 20.04 using that .desktop file. If you have the ISO, then burn it to a USB stick and boot from it.

ISO: [http://cdimage.ubuntu.com/kubuntu/focal/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/focal/daily-live/current/)

Utility to create USB:

```
sudo apt install usb-creator-kde
```

Run usb-creator-kde, point to the ISO image and the USB stick, then run the installer.

Reboot, then tell the BIOS to boot from the stick.

I was attempting to use the desktop file because that was an icon on the desktop/wallpaper. It had "install ..." and the boot from USB didn't even come up with a "Try" or "Install" option. So I only had one option, the desktop file.

I downloaded the ISO as per your instructions, then ran "usb-creator-kde" , then used that usb to boot from usb, and the same problems occured. However, thanks for your help.

> **ActionParsnip said:**
> ```

cat ~/Desktop/ubiquity-kdeui.desktop | grep Exec | cut -d"=" -f 2

```

Should give the command being ran in the desktop file

Thanks, that displayed > ubiquity kde_ui

Thanks for your help, everyone, I will have to assume the underlying cause of not being able to get to a point to install, is because the laptop screen is broken and I'm using an external monitor. See [https://ubuntuforums.org/showthread.php?t=2452691](https://ubuntuforums.org/showthread.php?t=2452691)

I've tried 2 different ISO's now, the latest and the official one from August. Plus two different tools to create the bootable usb, changed display settings I don't know how many times to try and find a way to inform the live Kubuntu in regards to the monitors, pulled my hair out a fair bit. So, the only resolve is to try and pickup an old laptop that has a working screen.

---

### Post by oygle on 2020-10-29
As the installation has now worked ( see  [https://ubuntuforums.org/showthread.php?t=2452691](https://ubuntuforums.org/showthread.php?t=2452691) ), will mark this one as solved now.  Thanks to everyone for your help.  :)

---

