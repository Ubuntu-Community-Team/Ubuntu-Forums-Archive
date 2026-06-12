---
title: "How do i run WINE?"
date: 2006-07-20
forum: Desktop Environments
---

### Post by trojanlinux on 2006-07-20
Hello, today is my first day using ubuntu. I installed WINE and it even appears in my add/remove programs but I can't figure out how to run it. What am I missing?

Thanks!

---

### Post by jonnymccullagh on 2006-07-20
Have you tried opening a terminal and typing:
```
winecfg
```
I think you have to do that to configure Wine for each user account. This sets up special hidden folders(~/.wine) and menu entries etc. and you should then be able to install win32 software.

---

### Post by JerMe on 2006-07-20
Applications > Accessories > Terminal

To run something in Wine, you'd type
```
wine *name_of_program_to_run.exe*
```

For example, I installed Firefox under Wine so that I could browse Flash 8+ websites (like MySpace and YouTube):

```
wget http://releases.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.4/win32/en-US/Firefox%20Setup%201.5.0.4.exe
wine  Firefox\ Setup\ 1.5.0.4.exe
```

Then to run Firefox:
```
wine /home/jerme/.wine/drive_c/Program\ Files/Mozilla\ Firefox/firefox.exe
```

---

### Post by mister_p_1998 on 2006-07-20
> **JerMe said:**
> Applications > Accessories > Terminal

To run something in Wine, you'd type
```
wine *name_of_program_to_run.exe*
```

For example, I installed Firefox under Wine so that I could browse Flash 8+ websites (like MySpace and YouTube):

```
wget http://releases.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.4/win32/en-US/Firefox%20Setup%201.5.0.4.exe
wine  Firefox\ Setup\ 1.5.0.4.exe
```

Then to run Firefox:
```
wine /home/jerme/.wine/drive_c/Program\ Files/Mozilla\ Firefox/firefox.exe
```

Could I run IRfanview in wine and have it as the default picture viewer?

---

### Post by JerMe on 2006-07-20
You should be fine.  Seems like there were a couple of success stories with the install:

[http://appdb.winehq.org/appview.php?iAppId=163](http://appdb.winehq.org/appview.php?iAppId=163)

I know digikam is a good photo viewing app, but it's for KDE (as opposed to Gnome) so if you're running Ubuntu, you'll have to download a lot of the KDE libraries to run digikam.  There are a number of other native linux photo viewing applications that you can try.

---

