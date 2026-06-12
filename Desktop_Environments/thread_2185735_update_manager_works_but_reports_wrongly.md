---
title: "update manager works but reports wrongly"
date: 2013-11-04
forum: Desktop Environments
---

### Post by wijit on 2013-11-04
Here is the hardware info:
Acer Travelmate p243, Intel Core i3, 2Gb RAM
and software:
Windows 7 Pro and Ubuntu 12.04 on different partitions (of course)
One of annoying behaviours of this computer is the report that Update Manager makes when its session finished. Above the update lists box it says "Software updates may be available for your computer. The update information was last updated nnn days ago. Press the 'Check' button below to check for new software updates.". However, just under the box there is another line that says "There are no updates to install.". If the button is pressed the software shows it is running and reports the mentioned results again. The "nnn" is the number of days which keeps increasing. The day zero can be worked out by counting back, for example, today is Nov4th,2013 and the nnn is reported 140 thus the day zero is Jun17th,2013. Please guide me out of this. Thanks.

---

### Post by grahammechanical on 2013-11-04
It is not giving you any error messages? And the number of days does not zero when you run Check for Updates? Try this and note any error messages and post them in your post.```
sudo apt-get update
``````
sudo apt-get upgrade
```The Update Manager is a front end for the apt-get command but by running those commands in the terminal we may get error messages that can help us determine what is wrong and how to fix things. Regards

---

### Post by ian-weisser on 2013-11-04
The confused phrasing on Update Manager, and the need to click to update, was long ago reported...and fixed in more recent versions of Ubuntu).
You should see the improvement when you update to 14.04 and Software Updater replaces Update Manager.

Meanwhile, [[COLOR=#000000]grahammechanical[/COLOR]]("http://ubuntuforums.org/member.php?u=1087323") is quite right trying to help you solve the more immediate problem of your system not updating properly.

---

### Post by wijit on 2013-12-06
Hi! Sorry for late update. The problem was solved. Here is a solution:
1. run a command:
sudo apt-get update
in Terminal.
2. note every line beginning with Err.
3. open the Software Source and remove the associated repo.
4. re-run sudo apt-get update and see if the result changes.
5. do it one by one and put the repo back if no change occures and re-do it on the next Err line.
Thanks for all conversation.

---

### Post by claracc on 2013-12-06
As you fixed your problem and explained how, please mark the thread as solved with "thread tools" in order to find easily the information by other users. Thanks.

---

