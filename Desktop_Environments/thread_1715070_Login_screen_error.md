---
title: "Login screen error"
date: 2011-03-26
forum: Desktop Environments
---

### Post by ttristan on 2011-03-26
There's something wrong with the login screen of my ubuntu system.It was divided into two parts with a mittellinie,the right part is a zoomed out mirror of the left part.Both of keyboard and screen keyboard can't be used.
I take a picture of the login screen and acttached it to this message.
My english is not very good,if you don't understand ,just look at the acttached piciture and you'll know what i mean.

thanks.

---

### Post by Krytarik on 2011-03-26
When you are at the login screen
- press Ctrl+Alt+F1 to switch to a console
- login there
- run those commands:
```

sudo service gdm stop
sudo -u gdm gconftool-2 /desktop/gnome/applications/at/screen_magnifier_enabled --type bool --set false
sudo -u gdm gconftool-2 /desktop/gnome/applications/at/screen_keyboard_enabled --type bool --set false
sudo service gdm start

```

Greetings.

---

### Post by ttristan on 2011-03-26
> **Krytarik said:**
> When you are at the login screen
- press Ctrl+Alt+F1 to switch to a console
- login there
- run those commands:
```

sudo service gdm stop
sudo -u gdm gconftool-2 /desktop/gnome/applications/at/screen_magnifier_enabled --type bool --set false
sudo -u gdm gconftool-2 /desktop/gnome/applications/at/screen_keyboard_enabled --type bool --set false
sudo service gdm start

```

Greetings.

Ctrl+Alt+Fx can't be use but i can login with recorvery mode.I'll try you commands and thanks so much.

---

### Post by Krytarik on 2011-03-26
> **ttristan said:**
> Ctrl+Alt+Fx can't be use but i can login with recorvery mode.
Yeah, I didn't mind that you apparently can't use *any* keys. :P "Recovery mode" should work then.

Then you just need to run both of those commands in a terminal, and reboot:
```
sudo -u gdm gconftool-2 /desktop/gnome/applications/at/screen_magnifier_enabled --type bool --set false
sudo -u gdm gconftool-2 /desktop/gnome/applications/at/screen_keyboard_enabled --type bool --set false
```

---

### Post by ttristan on 2011-03-26
> **Krytarik said:**
> Yeah, I didn't mind that you apparently can't use *any* keys. :P "Recovery mode" should work then.

Then you just need to run both of those commands in a terminal, and reboot:
```
sudo -u gdm gconftool-2 /desktop/gnome/applications/at/screen_magnifier_enabled --type bool --set false
sudo -u gdm gconftool-2 /desktop/gnome/applications/at/screen_keyboard_enabled --type bool --set false
```

Hi Krytarik,
 Your first command has been works, the login screen looked good.But the second command only close the screen keyborad,my Keyboard still can't be use,any keys can't be use.

---

### Post by Krytarik on 2011-03-26
I'm not sure if this is because of a bug or just a misconfiguration.

1.) bug report (Fedora): [https://bugzilla.redhat.com/show_bug.cgi?id=676827](https://bugzilla.redhat.com/show_bug.cgi?id=676827)

2.) Check the file "~/.dmrc" in your home directory, I have it that way, using german keyboard layout:
```
[Desktop]
Language=en_US.utf8
Layout=de
Session=gnome
Langlist=en_US:en
LCMess=en_US.UTF-8
```

---

### Post by ttristan on 2011-03-26
> **Krytarik said:**
> I'm not sure if this is because of a bug or just a misconfiguration.

1.) bug report (Fedora): [https://bugzilla.redhat.com/show_bug.cgi?id=676827](https://bugzilla.redhat.com/show_bug.cgi?id=676827)

2.) Check the file "~/.dmrc" in your home directory, I have it that way, using german keyboard layout:
```
[Desktop]
Language=en_US.utf8
Layout=de
Session=gnome
Langlist=en_US:en
LCMess=en_US.UTF-8
```

I can't found ~/.dmrc,i've searched it under the root directory.
Still don't know how to fix my issue after readed the bug report carefully,there are no directory "/etc/sysconfig/keyboard" in my system which was mentioned in the bug report.

---

### Post by Krytarik on 2011-03-26
> **ttristan said:**
> I can't found ~/.dmrc,i've searched it under the root directory.
It's in your home directory, like I said.
> **ttristan said:**
> Still don't know how to fix my issue after readed the bug report carefully,there are no directory "/etc/sysconfig/keyboard" in my system which was mentioned in the bug report.
Because it's Fedora.

You may try re-installing "gdm":
```
sudo apt-get install --reinstall gdm
```

---

### Post by ttristan on 2011-03-27
> **Krytarik said:**
> It's in your home directory, like I said.

Because it's Fedora.

You may try re-installing "gdm":
```
sudo apt-get install --reinstall gdm
```

I know what's mean "home directory",I searched ".dmrc" in root directory use command "$find / -name *dmrc" and it return nothing.
I'll try reinstall the gdm.

---

### Post by ttristan on 2011-03-27
Well.This is not a issue,it just because im a foolish.
In login screen
   1.click the button with a little man icon in bottom bar ..
   2.click Universal Access Preferences.
And then a window which have several checkboxes on it would be shown.
Check the item "Use screen magnifier",the screen will be divided into to parts.
And the keyboard,the reason is the item "Press and hold keys to accept them (slow keys)" was checked,press and hold a key for a while then the computer will accept it.


Thanks very very much for Krytarik's help.

---

### Post by Krytarik on 2011-03-27
> **ttristan said:**
> 
And the keyboard,the reason is the item "Press and hold keys to accept them (slow keys)" was checked,press and hold a key for a while then the computer will accept it.

Ah, I didn't thought of *that* option. :p

You're welcome!

---

