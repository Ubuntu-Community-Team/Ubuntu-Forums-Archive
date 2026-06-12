---
title: "Gnome doesn't appear in the list of sessions at login!"
date: 2010-07-31
forum: Desktop Environments
---

### Post by compiz addict on 2010-07-31
My problem:

When I get to the login screen on my computer (with ubuntu-desktop, kubuntu-desktop, and xubuntu-desktop installed on Ubuntu), Gnome isn't in the list of desktop environments!


My temporary solution:

I have Openbox/Gnome. I also have an icon in my panel that opens "compiz --replace" so I can still use the regular WM with compiz.


Why my temporary solution isn't good enough:

It's annoying to have to have an extra icon in my panel, and to have to press it at login. Also, I don't get the Compiz splash screen when I login. Overall it's just not as impressive.


Is there any way to get Gnome back in the menu?

---

### Post by compiz addict on 2010-08-04
*bump*

---

### Post by cliffdodger on 2010-08-04
This may vary depending on which login manager you're using and what window manager/login options you're trying to add but the basic idea is discussed in this thread:

[http://ubuntuforums.org/showthread.php?t=18626](http://ubuntuforums.org/showthread.php?t=18626)

Hope that helps!

---

### Post by compiz addict on 2010-08-05
Thanks for your reply, I found out that I can create my own session by making a .desktop file and putting it in "/usr/share/xsessions", with the .desktop file containing the following syntax:

```

[Desktop Entry]
Name=NameOfEnvironment
Comment=Short discription thing
Exec=/directory/of/executableFile
TryExec=/directory/of/executableFile
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=csession-1.0

[Window Manager]
SessionManaged=true

```

And of course the executable file can be a regular file with #!/bin/bash at the beginning.

All this info was found here:
[http://ubuntuforums.org/showthread.php?t=1494457](http://ubuntuforums.org/showthread.php?t=1494457)

---

### Post by cliffdodger on 2010-08-12
Hmmm, nice find. :) I'm bookmarking that.

---

