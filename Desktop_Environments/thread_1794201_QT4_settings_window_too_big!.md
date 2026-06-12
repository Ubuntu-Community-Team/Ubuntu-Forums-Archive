---
title: "QT4 settings window too big!"
date: 2011-06-30
forum: Desktop Environments
---

### Post by wgw on 2011-06-30
When I go to System > Preferences > QT 4 Settings

I get a window that can't be resized and is too big for the screen; I can never see what is at the bottom of the screen. 

I want to make sure QT is set to utf-8 encoding. I'm not even sure it will be in that window, but right now I need to figure out how to see the window!

(A bit ironic that QT settings window doesn't work...)

Any idea how to fix this? (or simply check what character encoding QT is set at?)

Thanks!

---

### Post by mourt on 2011-06-30
> **wgw said:**
> ....
Any idea how to fix this? (or simply check what character encoding QT is set at?)

Thanks!

There is no general "Qt character encoding". Qt can basically handle "anything", if you refer to "non-fixed" things like QString::toLocal8Bit(), that uses the system enviroment (see 'locale'), which of course can be overridden in any shell or before an application is started.

---

### Post by jerrrys on 2011-06-30
until you get a fix you can hold down the "Alt" key and drag the screen with the mouse.  do not drag from top of window

---

### Post by wgw on 2011-07-01
Thank you both for your suggestions -- I used the alt-move to see the whole window, and as you predicted, there is no encoding setting. 

I will keep an eye out for ways to resize the window, but for the encoding, I'm guessing it is a dead-end. Encoding is always tricky!

Thanks!

---

