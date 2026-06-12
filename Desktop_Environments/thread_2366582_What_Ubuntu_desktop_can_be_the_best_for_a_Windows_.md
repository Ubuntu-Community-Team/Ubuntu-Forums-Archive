---
title: "What Ubuntu desktop can be the best for a Windows user?"
date: 2017-07-19
forum: Desktop Environments
---

### Post by dmitriano on 2017-07-19
I worked with MS Visual Studio on Windows for a long time, but now I have KUbuntu 14.04 + KDE Plasma with QT Creator and the most annoying thing for me is that I cannot select a text with Ctrl+Shift+(numpad arrows), for example. (probably this KDE bug can relate to this key combination somehow: [https://bugs.kde.org/show_bug.cgi?id=183458](https://bugs.kde.org/show_bug.cgi?id=183458)).
The other shortcuts I need are:
Ctrl + Shift + (numpad arrow or end/home) = text selection
Ctrl + Ins = copy to clipboard
Shift + Ins = paste from clipboard
etc...
I wonder if anyone knows how to make these shortcuts work everywhere (text editor, browser address bar, Qt Creator, etc...). Probably there is some Ubuntu desktop that can be configured in that way?

---

### Post by vocx on 2017-07-19
> **dmitriano said:**
> I worked with MS Visual Studio on Windows for a long time, but now I have KUbuntu 14.04 + KDE Plasma with QT Creator and the most annoying thing for me is that I cannot select a text with Ctrl+Shift+(numpad arrows), for example. (probably this KDE bug can relate to this key combination somehow: [https://bugs.kde.org/show_bug.cgi?id=183458](https://bugs.kde.org/show_bug.cgi?id=183458)).
The other shortcuts I need are:
Ctrl + Shift + (numpad arrow or end/home) = text selection
Ctrl + Ins = copy to clipboard
Shift + Ins = paste from clipboard
etc...
I wonder if anyone knows how to make these shortcuts work everywhere (text editor, browser address bar, Qt Creator, etc...). Probably there is some Ubuntu desktop that can be configured in that way?
I am using Ubuntu 16.04 and Unity. Those shortcuts that you mention seem to more or less work in my system.

Ctrl+Shift+PageUp selects to the beginning of the line, and PageDown selects to the end of the line. I tried with +LeftArrow and +RightArrow and they work as well, but not on the numerical pad. Using +Home, and +End selects to the beginning and end of the file.

Ctrl+Ins to copy I didn't know, but it does copy. Shift+Ins to insert works. Nice.

Unfortunately I don't think you can make the changes global as I think some programs trap the key combinations and use them for something else. For example, it seems that in Firefox and Gnome-terminal, Ctrl+Shift+PageUp moves the positions of the tabs.

I wouldn't know what exactly controls this, whether it's the X window system, the particular graphical library (GTK+, Qt), or some other part (system wide configuration?).

---

### Post by dmitriano on 2017-07-20
Yes, in Ubuntu 14.04 + ubuntu.desktop, Ctrl+Ins and Shift+Ins do copy/paste, and this is really cool! The only disappointing thing is that I cannot configure KDE plasma to do copy/paste with these keys. GNOME desktop also does copy/paster in its terminal with Ctrl+Ins, Shift+Ins, but not in FireFox or a text editor.

---

### Post by dmitriano on 2017-07-28
Found the solution for KDE, see [How to make Ctrl/Shift+NumPad keys select/copy/paste text in KDE (like as in MS Windows)]("https://developernote.com/2017/07/how-to-make-shift-numpad-keys-select-text-in-kde-like-as-in-ms-windows/")

---

### Post by oldrocker99 on 2017-07-28
As as Windows user 9 years ago, I found the GNOME 2.3 interface as easy to learn as could be. That desktop lives on in Ubuntu MATE.

---

### Post by xinuzi on 2017-08-03
I find the simplicity and the speeed of Lubuntu (LTS) very satisfactory.

Whether as a full clean install or as a xsession over Ubuntu Unity.
On older and newer machines.

Combine it with Opera for browsing and you will fly through the internet!

---

### Post by ClickXT on 2017-08-03
Most of those work without issue for me in Ubuntu 16.04 Unity.

---

