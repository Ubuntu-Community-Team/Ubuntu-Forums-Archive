---
title: "Messed up on Repositories"
date: 2006-07-14
forum: Desktop Environments
---

### Post by Iorchova on 2006-07-14
"Cannot install 'wxvlc'

This application conflicts with other installed software. To install 'wxvlc' the conflicting software must be removed before.

Switch to advanced mode to resolve this conflict.



I got this error when installing VideoLAN Client. Prior to the installation it told me to enable a 'universe' repository. I think I did something wrong. Can anybody help?

---

### Post by oldmanstan on 2006-07-14
you were installing it using the "add/remove applications"? i think that's where that error comes from (correct me if i'm wrong)

go to "system > administration > synaptic package manager" when the add/remove dialog is not open

then click on the "search" button, a dialog pops up, make sure the drop down list says "name" then type in "wxvlc" and hit enter

right-click on the package that comes up and then hit "mark for installation"

synaptic *SHOULD* take care of it for you then, you will have to click through a dialog box but it will explain it to you

lemme know if it works ok

---

### Post by Iorchova on 2006-07-14
"The following packages have unresolvable dependencies. Make sure that all require repositories are added and enabled i the repositories.

wxvlc:
 Depends: vlc but it is not going to be installed"

---

### Post by oldmanstan on 2006-07-14
please post the contents of your /etc/apt/sources.list file and we'll get you squared away

---

