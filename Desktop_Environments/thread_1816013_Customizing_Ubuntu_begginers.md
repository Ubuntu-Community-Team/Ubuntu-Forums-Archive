---
title: "Customizing Ubuntu begginers"
date: 2011-08-01
forum: Desktop Environments
---

### Post by JsCoolDart on 2011-08-01
I want to tweak my desktop to the max :D, but Im a newbie who has never used terminal and used codes without assistance :(. after reading all the steps on this website, 

[http://lifehacker.com/5556316/set-a-rotating-picture-of-the-earth-as-your-ubuntu-wallpaper](http://lifehacker.com/5556316/set-a-rotating-picture-of-the-earth-as-your-ubuntu-wallpaper), 

I get this error for the picture... 
(lets hope it came, if not, ill type what came- 
Could not load image '1600.jpg'. Error interpreting JPEG image file (Not a JPEG file: starts with 0x47 0 ) 

:confused: any ideas how to make it come correctly? ill add my next question after this one is solved :)

---

### Post by hakermania on 2011-08-01
Hello, instead of 
```

wget -r -N http://static.die.net/earth/mercator/1600.jpg

```
use
```

GET http://static.die.net/earth/mercator/1600.jpg > 1600.jpg

```

---

### Post by JsCoolDart on 2011-08-01
thanks for the tip of not running scripts blindly :) 
the code however did'nt work
any ideas?

---

### Post by JsCoolDart on 2011-08-01
if you cant read it, 
Could not load image '1600.jpg'.
Error interpreting JPEG image file (Improper call to JPEG library in state 200)

---

### Post by hakermania on 2011-08-01
Well I think that you read again the previous image...
Remove any directories used in previous tries, like 'static.die.net' and then run the following commands one line per time in a terminal:
```

cd ~/Desktop/
GET http://static.die.net/earth/mercator/1600.jpg > 1600.jpg

```
This should create on your Desktop a file called 1600.jpg.
Post back if it does or not.

---

### Post by JsCoolDart on 2011-08-01
Hmm, I think you did'nt understand what I wanted to do. I want to schedule a task to download the latest image from that website every 1 hour (as it is updated), so it looks like the Earth is rotating in my desktop. It works when I tried in terminal, but is there a code to make it run every one hour. thanks...

---

### Post by JsCoolDart on 2011-08-01
anyways, let that be, does anyone know how to change icons of libre office, google chrome, etc. thanks

---

### Post by xdominex on 2011-08-02
I found that I have the same problem when doing what you are trying to do with downloading the picture (I figured the first step to helping you solve it is to reproduce it, so that's what I did). Wget is a very complex and powerful program that is difficult to master, leaving it as a poor choice for simple tasks like downloading this picture. To download the picture, use the aria2c command from the package aria2. Code to copy-and-paste is below; it will install aria2 and download the picture to the directory into which the failed downloads were going (~/static.die.net/earth/mercator/).
```

sudo apt-get install aria2
aria2c --dir=$HOME/static.die.net/earth/mercator http://static.die.net/earth/mercator/1600.jpg

```

That should do the trick! If the directory doesn't exist, aria2 creates it for you.

Now, about your icon question.. which version of Ubuntu are you running, and which desktop environment do you use (i.e. Unity, Gnome 3, or Gnome2)? LibreOffice icons should change when you change the system icon theme, but I can't help you do that without knowing which desktop you use. We can also get Chrome to use the gtk theme native to the desktop environment. Open Chrome, click the wrench on the right, and select "preferences" from the drop-menu. From here, click on "Personal Stuff" on the left. Now, just click the button that says "Use GTK+ Theme."

Hope I've helped!

With regards,
XSpiritusX

---

### Post by JsCoolDart on 2011-08-02
trying that right now :D Ubuntu 11.04, Im inserting screenshot of my screen, hopefully, that will help as I dont know... :(

---

### Post by JsCoolDart on 2011-08-02
stupid question- will this update on its own, or do I have to do it manually?

---

### Post by xdominex on 2011-08-02
Yep, that would be the Unity desktop in Ubuntu 11.04. 

Will what update on its own? If you are referring to your desktop wallpaper, then I do not know. I figured that that part was covered in the article you were reading about it. If you are referring to something else, I will try to help you out on that one when I know what it is lol

---

