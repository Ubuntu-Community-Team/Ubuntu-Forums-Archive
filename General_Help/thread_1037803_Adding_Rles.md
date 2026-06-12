---
title: "Adding Rles?"
date: 2009-01-12
forum: General Help
---

### Post by Lukehluke on 2009-01-12
Hi,

my first question is that do I need to ask for help in this board or the Ubuntu board?

Also, I want to do something on my Wubi (Ubuntu) install but it says that I need to do the following.

```
   1. Login as root and create this file: /etc/udev/rules.d/50-android.rules.

      For Gusty/Hardy, edit the file to read:
      SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666"

      For Dapper, edit the file to read:
      SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0bb4", MODE="0666"
   2. Now execute:
      chmod a+rx /etc/udev/rules.d/50-android.rules 
```

How do I do this?

---

### Post by brandon88tube on 2009-01-12
For your first question, you would probably be better off asking in other sections of the forums as this is not necessarily wubi related.

Now the second part I am willing to help on if I can. What exactly is it you are trying to do? Something with Android?

---

### Post by Lukehluke on 2009-01-12
I am using my phone (G1) as a modem.

Tethering on XP :D (Until I get my internet online soon).

I want to do the same on my newly installed Linux.

It's just that bit that I am stuck on.

---

### Post by brandon88tube on 2009-01-12
I'll tell you how I would go about doing this.
```
sudo gedit /etc/udev/rules.d/50-android.rules

#Copy and paste the line below this and save the file.

SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666"

#Then open the terminal and do this

sudo chmod a+rx /etc/udev/rules.d/50-android.rules
```

EDIT: The above is for the Hardy one

---

### Post by Lukehluke on 2009-01-12
sudo gedit?

Sorry real new to Linux.

Also when I installed Wubi, it took 15 GB space.

I thought its only meant to take 5 GB.

Does it matter? (If so I can install it again but select the 5GB option).

---

### Post by brandon88tube on 2009-01-12
> **Lukehluke said:**
> sudo gedit?

Sorry real new to Linux.

Also when I installed Wubi, it took 15 GB space.

I thought its only meant to take 5 GB.

Does it matter? (If so I can install it again but select the 5GB option).

1. Do you know how to open a terminal? If not go to Applications > Accessories > Terminal. Once that is open type in this command ```
sudo gedit /etc/udev/rules.d/50-android.rules
``` It will ask for your password, type it in and hit enter. That will bring up a text editor with a blank file. Just paste this in for Gutsy/Hardy version of Ubuntu```
SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666"

``` or this for Dapper version ```
      SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0bb4", MODE="0666"

``` When you are done with that click the save button. Go back to the terminal that you had open or you could always open a new one, its up to you. When you have the terminal up type this command in ```
sudo chmod a+rx /etc/udev/rules.d/50-android.rules
```

Now I am not sure if those commands you supplied me with are correct. All I am doing is telling you how to do what you asked.

Secondly, when you installed using wubi it defaulted to 15gb of space to use for the install. If you had wanted a smaller amount or larger you would have had to change that in the installer where it asked the size you wanted. Now I wouldn't suggest going to 5gb because if you needed to install any other programs or save files etc. on that install, you wouldn't be able to or you would have very little space. It doesn't really matter what size you have as long as its not taking up more space then what you want.

---

### Post by Lukehluke on 2009-01-12
I get a writing error I think when I close the blank file which I put the line of code into.

Also how do I know which version I am using out of Gutsy/Hardy or Dapper?

---

### Post by brandon88tube on 2009-01-12
Could you list the error and to tell what version you have you can go to System Monitor and under System it should tell you (can't think of other ways right because I am tired). You might have Intrepid installed.

---

### Post by 60hbe16es52 on 2009-01-12
there are four kinds of jewelry,[wholesale jewelry](http://www.jewelryol.com/),[fashion jewelry](http://www.jewelryol.com/),[handmade jewelry](http://www.jewelryol.com/) and [costume jewelry](http://www.jewelryol.com/) ,which one do you like ?

---

### Post by Lukehluke on 2009-01-12
> **brandon88tube said:**
> Could you list the error and to tell what version you have you can go to System Monitor and under System it should tell you (can't think of other ways right because I am tired). You might have Intrepid installed.

I do have Intrepid installed.

Error is as follows.

```
lukehluke@ubuntu:~$ sudo gedit /etc/udev/rules.d/50-android.rules
[sudo] password for lukehluke: 

** (gedit:5985): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.6C18MU': No such file or directory
```

After I close the file the Warning comes up.

---

### Post by brandon88tube on 2009-01-12
Hmm, are you sure you typed it in correctly? You can copy the command I gave you and paste it into the terminal by doing ctrl+shift+v or file paste at the top. Also, did you just save the file as is without renaming it in gedit? All you need to do is hit the save button or ctrl+s

---

### Post by Lukehluke on 2009-01-12
Which code do I put in?

Gutsy/Hardy or Dapper?

Also I am sure I put it in correctly but I will try again after your next reply.

When I save it, I just click save button then close as it should already be named properly right? (As the line code to open it, creates it?

---

### Post by brandon88tube on 2009-01-12
> **Lukehluke said:**
> Which code do I put in?

Gutsy/Hardy or Dapper?

Also I am sure I put it in correctly but I will try again after your next reply.

When I save it, I just click save button then close as it should already be named properly right? (As the line code to open it, creates it?

You should try the Hardy one because thats the closest one to Intrepid. Also it should be named properly from the code. The code is: ```
sudo gedit /etc/udev/rules.d/50-android.rules
``` I gave this a test shot and it worked for me. If you are still having problems, let me know and I'll try and come up with another way for you to get this working.

---

### Post by Lukehluke on 2009-01-12
How do I know when the drivers are installed properly ?

---

### Post by brandon88tube on 2009-01-12
Well for one, did making the file work this time for you? Two, I'm not sure, I told you that I was just telling you how to make the files and insert the given info because I wasn't sure if the info you provided was correct.

---

### Post by Lukehluke on 2009-01-12
I think I sorted the driver.
Not 100% sure though.

I tried running the .exe file and this is what happened:

```
lukehluke@ubuntu:~$ \home\lukehluke\Desktop\ADB\ADB.exe forward tcp:1080 tcp:1080
bash: homelukehlukeDesktopADBADB.exe: command not found
```

Do I have to put something before it to get it to execute properly ?

---

### Post by brandon88tube on 2009-01-12
I'm not entirely sure on this subject, but at a quick glance I see that you have \ instead of /. Try this instead ```
/home/lukehluke/Desktop/ADB/ADB.exe forward tcp:1080 tcp:1080

```

---

