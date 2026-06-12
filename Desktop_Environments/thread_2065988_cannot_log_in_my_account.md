---
title: "cannot log in my account"
date: 2012-10-03
forum: Desktop Environments
---

### Post by ymilev on 2012-10-03
Hallo! I'm using Ubuntu 12.04 (installation of 9.04 before 3 years, updated regularly to the current version) on laptop HP Probook 4510s. Have only 1 account "ÿordan" with administrative rights. Since this morning cannot log in - for a second appears black screen with report: Could not write bytes: broken pipe, and again the log-in screen.
Can you help me to reach my account and to save the information in it. 


PS. Already tried to create another account - successfuly, and copied part of the data, but cannot copy mail archive in /home/yordan/.thunderbird
Now the report while trying to log in is 
*Starting anac(h)ronistic cron                                       [OK]
                                                                                   [OK]  *Stopping anac(h)ronistic cron          [OK]
                                                                                          *Checking battery state...
*Stopping System V runlevel compatibility                     [OK]

---

### Post by hictio on 2012-10-03
Have you tried login in from a Virtual Console?
Type Ctrl + Alt + F1 to go to the first one and type your username and password, and see if you can login thru the CLI.
To logout type exit.
To got back to your graphical login, type: Ctrl + Alt + F7

---

### Post by ymilev on 2012-10-03
yes, i can log in by virtual console

---

### Post by hictio on 2012-10-03
Are you using EXT4?
Do you have encryption enabled on your $HOME?

---

### Post by ymilev on 2012-10-03
Yes , filesystem is ext4, but as far as I can remember, I've never enabled encription on HOME

---

### Post by ymilev on 2012-10-03
I looked to another linux forums and received some suggestions that my system disk is full. OK deleted some data and now the disk is 75% full, with 10 GB free space, but the problem persists. Another problem, that I just saw is that I cannot Close(Switch off) the computer. Every trial of closing results in going to login screen. So I can switch off the computer only by the button.
I have 1 40GB ext4 partition, and 4 NTFS partitions. (52, 107, 108, 191 GB). Have no separate /home partition, and used Ubuntu by one single account with administrative rights. Now I created new account, with which I can log on but cannot copy all the folders of the previous account (only part of them). On virtual console I can enter with both accounts

---

