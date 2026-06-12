---
title: "Unity to Gnome howto"
date: 2011-04-30
forum: Desktop Environments
---

### Post by otherethe on 2011-04-30
For people like me who dont like Unity and dont f***kin say give it a shoot because i have been for 2 days now after someone told me to and i have learned it and it's annoying and i also dont care what none of you say it's alot slower befor i could click and go now i have to take the time to take my hand off the mouse to start typing in the box to get my apps up faster befor it was mouse over click loaded, now it's mouse over hand off mouse onto keybored type in some letters handd back on mouse click loaded Befor firefox loaded move 2 inc mouse on bookmarks website loaded now it's 45 inc bookmarks = loaded dont get me wrong it looks very nice for people who are into buggy unstable I like for things to look like a mac because i enjoy icandy linux is all about being stable and getting things done I just hope they stop going down the wrong road anyways back on topic here

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell
Open the terminal and run the following commands


or u could follow this  [http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3](http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3)

---

### Post by ratcheer on 2011-04-30
I installed Gnome3 on Natty, just last weekend. Your instructions are pretty close.

You should not have to install gnome-shell after the dist-upgrade. It should come along with the upgrade.

After Gnome3 is up, you need to remove gnome-themes-accessibility and install gnome-themes-standard. Then you should run the gnome-tweak-tool and change your theme to adwaita. This should give you a good gnome-shell experience to start with.

After that, customization is up to you.

Tim

---

