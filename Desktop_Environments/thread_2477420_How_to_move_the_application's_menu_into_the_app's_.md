---
title: "How to move the application's menu into the app's window?"
date: 2022-07-24
forum: Desktop Environments
---

### Post by dwater on 2022-07-24
I am getting tired of moving my mouse pointer all the way over to the top left of the left most screen just to get to the app's menu.

Is there a way to put the app's menu back into the top of the app's window?

Ubuntu 22.04 LTS

---

### Post by #&amp;thj^% on 2022-07-24
See if this is what your after, and please read it all: [https://www.makeuseof.com/add-application-shortcuts-ubuntu-desktop/](https://www.makeuseof.com/add-application-shortcuts-ubuntu-desktop/)

---

### Post by dwater on 2022-07-24
Hi,

I had a quick look at that, all the way through in case it had something relevant slipped in, but it doesn't look like it is about the question I've asked. Did I miss it in there somewhere?

---

### Post by #&amp;thj^% on 2022-07-24
No it's just an alternative method, and perhaps an open mind.
Gnome has been talking about moving  the application's menu back, but so far it's just Lip Service.
And I may have misunderstood your request here, apologizes.

---

### Post by deadflowr on 2022-07-24
I guess is would depend on the app.
Some apps, like gedit (text editor) or files, no longer even build with the traditional app menu.
Those apps now have a funky icon in the top bar area that has the app menu functions; if functions is even the right word.

(I do see terminal can have it if you right click in the main textarea and select the option Show menu bar.
But that seems to be an outlier of gnome apps, as most simply have that odd icon in the top of the app for all app menu settings)

On the other hand, apps like firefox or thunderbird should have a setting to allow showing the menu bar, somewhere.
That show go for any non-gnome app. That is if the app had a traditional app menu in the first place.

> Gnome has been talking about moving the application's menu back, but so far it's just Lip Service.
I think you something like what is referred here:
[https://www.omgubuntu.co.uk/2018/06/gnome-app-menu-migration]("https://www.omgubuntu.co.uk/2018/06/gnome-app-menu-migration")
While the link is old(ish) it's basically what's been done.

---

### Post by #&amp;thj^% on 2022-07-24
That's about the gist of it deadflowr , It was around 2021 when the talk was going on again, but I can't find the link ATM and during the 21.10 release, and most of it was a mixed reaction nearly split down the middle, For and Against.

---

### Post by Dennis N on 2022-07-24
Most of those top bar application menus which appear for the focused application have just a few options now (screenshot attached). I think what you see there (and more) can also be done from the two menu icons in the application header bar, or a menu bar if the application has one. For Firefox, it has a menu bar which shows if you press the Alt key.

---

### Post by ajgreeny on 2022-07-24
In Firefox I just use left-Alt to show the menubar which then hides again after first use rather than use up screen space all the time with the menubar.

---

### Post by mIk3_08 on 2022-07-25
> **dwater said:**
> I am getting tired of moving my mouse pointer all the way over to the top left of the left most screen just to get to the app's menu.

Is there a way to put the app's menu back into the top of the app's window?

Ubuntu 22.04 LTS

If you need to create a desktop icon here is something that can help you inside your desktop text icon. Regards and cheers

[Desktop Entry]
Name=Desktop Icon Name
Comment=Aplication comment
GenericName=Gen Name
Exec=/location/address/ofthe.app
Icon=/home/username/Pictures/iconfolder/icon.png
Type=Application
Categories=Network;WebBrowser;
MimeType=application
Actions=;
Keywords=;

---

