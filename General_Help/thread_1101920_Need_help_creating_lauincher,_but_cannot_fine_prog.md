---
title: "Need help creating lauincher, but cannot fine program!"
date: 2009-03-20
forum: General Help
---

### Post by The_Real_Anna on 2009-03-20
I installed AIM for Ubuntu but could not find the program in any part of my Applications!

Can anyone please help me (in detail please) I created a launcher for Opera, but cannot find the thread to help me! :(

I am using Ubuntu Ibex.

---

### Post by fieroboom on 2009-03-20
I know you just installed the program, but in case you aren't aware, Pidgin does a LOT of chat protocols, including AIM, and it's installed by default.
Regarding AIM, how did you install it?
:D
-Paul

EDIT:
I think I found where you got it from... Here are the instructions from [aim.com](http://www.aim.com/get_aim/linux/latest_linux.adp#deb2):
> 
Installation Instructions for Debian 3+
1. Download AIM onto your system.
2. Log in as root.
3. On the command line, type the dpkg command as shown in the example: dpkg -i aim_1.5.286-2_i386.deb where 1.5.286-2 represents the AIM version and release numbers.
4. To run AIM, log in as a regular user, and type "/usr/bin/aim" on the command line.
But you want a pretty button to click... ;)  So the question is, where do you want the button?

---

### Post by taurus on 2009-03-20
Do you know where you installed AIM?

Place a cursor on the top panel and click the right button.  Then select Add to panel -> Custom Applications Launcher -> + Add.  Now, you need to include the complete path to where you installed AIM if it's not on your path in the Command: field.

---

### Post by fieroboom on 2009-03-20
In case I wasn't clear, the last line of those instructions tells you where it is (/usr/bin/aim).
:D
-Paul

---

### Post by cariboo on 2009-03-20
To find the program you installed open an Applications-->Accessories-->Terminal and type:

```
locate aim
```

it should show up in /usr/bin

To create a launcher, right click on Applications and select Edit Menus, next select Internet. Click New Item and fill in the blanks. See the screenshots

Jim

---

