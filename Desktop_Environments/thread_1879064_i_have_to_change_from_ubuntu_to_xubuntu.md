---
title: "i have to change from ubuntu to xubuntu"
date: 2011-11-10
forum: Desktop Environments
---

### Post by iamkanoot on 2011-11-10
I think there is some problem with my computer because i can not set my computer to be xfe interface.i have to login in to a unity mode them logoff then change the mode again every time i want to use xubuntu.

can you tell me how can i permanently cahnge from ubuntu to xubuntu.

thank you very much

---

### Post by hhh on 2011-11-10
See the psychocats tutorial for getting rid of Ubuntu and Keeping Xubuntu...

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Note the first paragraph since (I assume) you started with Ubuntu, not Xubuntu, and note the first line about which version you're running.

I'd also recommend backing up any personal files (photos, music, etc...) before doing this.

---

### Post by iamkanoot on 2011-11-11
thank you very much i am going to try

---

### Post by iamkanoot on 2011-11-11
Now i my computer can not use Ubuntu. Luckily i still have windows in my laptop :D

I think the computer still try to boot from Ubuntu,which we already deleted.

When i boot my computer there are a list of OS shown up i select Ubuntu
then my com went to Xfc loading page ,after that the screen turn dark and flashy for a while.At that moment i was be able to move my cursor but can type anything.then my laptop turn dark and the light that indicate hard-disk operating is stop blinking.

Do you have any advised for me to do next.If i could i dont want to re-install my linux again

Thank you verymuch

---

### Post by Elfy on 2011-11-11
Try going to recovery mode - then root shell

```
sudo apt-get install lightdm-gtk-greeter
```

Then open the conf file for editing

sudo nano -B /etc/lightdm/lightdm.conf

change the greeter session to 

```
greeter-session=lightdm-gtk-greeter
```

and session to 
```
user-session=xubuntu
```

Ctrl+X - Y - Enter

```
exit
```

then resume.

---

### Post by iamkanoot on 2011-11-11
This is the result after i ran "sudo apt-get install lightdm-gtk-greeter"

[IMG]https://lh4.googleusercontent.com/-w7_Violg7Qo/Trzfjw2YvUI/AAAAAAAAR3o/3dBOLS7evBI/s640/photo%2525201.JPG[/IMG]

[IMG]https://lh6.googleusercontent.com/-rlf8zXWAqqc/Trzfj-1iHpI/AAAAAAAAR3k/CNsdD1YM3CY/s640/photo%2525202.JPG[/IMG]

Thank you very much for all of your answer i am very new to linux

---

### Post by Elfy on 2011-11-11
ok - do the same thing again - but before you try and install the greeter run the remount option from the menu - it'll do it and then say ENTER - do that and you should be back at the root prompt

Then do what I gave you in post#5

Then try and resume.

---

### Post by scottbomb on 2011-11-11
Or you could just delete the partition(s) and do a fresh install of Xubuntu from CD/DVD.

---

### Post by OrangeCrate on 2011-11-11
> **scottbomb said:**
> Or you could just delete the partition(s) and do a fresh install of Xubuntu from CD/DVD.

Best option, in my opinion.

---

### Post by iamkanoot on 2011-11-11
thank you very much

---

