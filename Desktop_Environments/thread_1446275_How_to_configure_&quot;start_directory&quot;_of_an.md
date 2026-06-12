---
title: "How to configure &quot;start directory&quot; of an application"
date: 2010-04-03
forum: Desktop Environments
---

### Post by dschlic1 on 2010-04-03
I have tried searching the forums for some information on this issue, but have had no luck. I want to be able to "launch" the gEDA program gschem using the menu system in Ubuntu 9.10. However gschem needs to be "launched" or run from the project directory. Is there any way to configure the menu item or the Desktop launcher to indicate to start gschem in a specified directory?

I come from a Windows enviroment, and in Windows you can specify the start directory in the shortcut. Is there anything similar in Ubuntu?

---

### Post by kblft on 2010-04-03
1. Create a desktop shortcut for your application
2. open gedit ( Application -> Accessories -> gedit Text Editor )
3. drag and drop the shortcut to gedit
4. add the following in the end of the file:
Path=/the/path/to/the/folder
replace '/the/path/to/the/folder' with the path you need

this should now start your application in the folder you want

EDIT
This will only work if you can see a Type=Application when you edit the file...

see [http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html)

---

### Post by dschlic1 on 2010-04-04
That did it, Thanks!

---

