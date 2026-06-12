---
title: "A few items don’t show up in Nautilus context menu"
date: 2016-09-14
forum: Desktop Environments
---

### Post by arnauldd on 2016-09-14
Hello,

when logged as user "arnauld" and when I do a right click on a file, a few items I installed, like "nautilus image tools" [https://www.atareao.es/ubuntu-apps/](https://www.atareao.es/ubuntu-apps/), and others, don't appear in the context menu, I am using Ubuntu Mate.

[IMG]https://ubuntu-mate.community/uploads/default/original/2X/0/073ed1dfa2ce499682aa296292fa383f6ffc70fc.jpg[/IMG]

And, if I do a right click on a file, from "file browser as root", new items appear in the context menu, see below the red arrows...

[IMG]https://ubuntu-mate.community/uploads/default/original/2X/2/23fe427a00ba1c52df82d41ebd17270f1f4274ac.jpg[/IMG]


I installed "image tools" through the terminal :
 

sudo add-apt-repository ppa:atareao/nautilus-extensions
sudo apt-get update
sudo apt-get install nautilus-image-tools


I also installed, [http://www.howtogeek.com/116807/how-to-easily-add-custom-right-click-options-to-ubuntus-file-manager/](http://www.howtogeek.com/116807/how-to-easily-add-custom-right-click-options-to-ubuntus-file-manager/) : 
sudo apt-add-repository ppa:nae-team/ppa
sudo apt-get update
sudo apt-get install nautilus-actions nautilus-actions-extra
but they don't show up in the right click menu when I am logged as "arnauld".

As you can see in the following screencast, when I browse files as "root", they do appear in the right click menu when I right click on an image...


[https://youtu.be/J4yDXiM2aUM](https://youtu.be/J4yDXiM2aUM)


How can I get all the items in the context menu, as logged as user "arnauld" ?
Thanks for any help,

---

