---
title: "How to move window buttons on to the top?"
date: 2013-08-26
forum: Desktop Environments
---

### Post by serg2 on 2013-08-26
Hi, I am using ubuntu 12.04 default Unity theme, I would like to disable the window title completely and instead move all buttons in title (minimize,maximize,close) onto the top, the same way as it became when you maximize the window, but it I want buttons to be forever there, how to achieve that? please help.

PS. I found out how to remove window titles, just need now to move buttons on the top.

---

### Post by Frogs Hair on 2013-08-26
That is not something that can be done with a gui or command . it would entail re-writing some Ubuntu code and though probably not impossible it would be an ambitious project.   [https://launchpad.net/ubuntu/precise/+source/unity](https://launchpad.net/ubuntu/precise/+source/unity)

[http://askubuntu.com/questions/28470/how-do-i-build-unity-from-source](http://askubuntu.com/questions/28470/how-do-i-build-unity-from-source)

---

### Post by serg2 on 2013-08-27
really?!
 I dont think it needs additional hardcode changes, there should a possibility to leave "min,max,close" buttons on the top as when you maximize the window.

---

### Post by SweetAurora on 2013-08-27
Sorry, but when it comes to the user end, Ubuntu is designed to be fixed and uncustomizable. So to do a simple "button replacement" will in fact entail a rewrite of some, if not most of Unity's code.

---

### Post by serg2 on 2013-08-27
Do you mean that when I restore original window size from Maximized size - Unity completely changes window objects behavior? 

BTW, I thought that it could be customized through skin theme files  /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml

---

### Post by SweetAurora on 2013-08-27
Yes. In fact, the maximized window aspect of Unity uses it's own seperate theme and code to manage a window in maximized mode as opposed to a standard window that sits on the desktop with it's window border around it. Yet despite being different pieces of code, they are inherently tied together and share some code as they after all manage the window borders.

---

### Post by serg2 on 2013-08-27
ok got you, thanks.

---

