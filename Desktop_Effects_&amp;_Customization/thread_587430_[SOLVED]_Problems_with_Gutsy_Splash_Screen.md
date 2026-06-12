---
title: "[SOLVED] Problems with Gutsy Splash Screen"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by scorziello on 2007-10-22
I have seen some other posts on the issue but so far I haven't found a way around changing the brown that comes up behind the splash screen. I have tried changing the color of the the background with no picture, I have changed the background color of the login screen. If any one has any ideas I would appreciate it. Thanks

---

### Post by Mr Greencastle on 2007-10-22
When you say splash screen, you do mean the picture you see when logging in right?

If so, I'm pretty sure you just right click the desktop, then click appearance. Under the background tab, there is a colour thing at the bottom - change that to the colour of your choice.

Hope that helped.

Mr Green

---

### Post by moto89 on 2007-10-23
This is what I have found on the subject, but when I open the default file it is blank.

> 
1) Open /etc/gdm/PreSession/Default with your favorite text editor using sudo:

sudo gedit /etc/gdm/PreSession/Default

2) Find the line that says BACKCOLOR="#DAB082" and change it to the HEX color of your choice. I wanted mine black so mine says BACKCOLOR="#000000". You can find your color's hex code here: (Color Hex Code).

3) Save the file and reboot!


---

### Post by moto89 on 2007-10-23
Ok, what I posted above is indeed the solution. I used a gksudo nautilus launcher to open up that default presession file in open office and it was just as described. Save the file and reboot, the brown is gone.

---

### Post by scorziello on 2007-10-23
Thanks Moto 89 for the post but unfortunately I see no hex code#'s in the code. Mr. Greencastle, the splash screen I am talking about it the screen you see after you enter your name and password. I can change the the splash it self but I cannot change the color of the screen behind it, it is still the same old boring brown. Thanks


Sorry Moto89, you were absolutely correct. I just overlooked the line, it is 0230 here where I am, but I must say it worked like a charm. Thanks

---

### Post by chuckyp on 2007-10-23
Under System > Administration > Login Window there is an option for the background color.  That should change the brown that is displayed directly after you log in.  Atleast until your wallpaper loads.  If you are experiencing another brown screen come up you need to right click on your desktop and there is also another option for background color.

---

### Post by scorziello on 2007-10-23
Yes I am aware of both of those, but for some reason on my system it will not change the color through either one of those methods. What moto89 described worked though.

---

### Post by bigboy_pdb on 2007-10-23
It sounds as though you want a splash screen, but splash screens have been disabled in Gutsy.

To view the splash screen open configuration editor using the command "gconf-editor" and check the box for "app/gnome-session/options/show_splash_screen". The splash screen will now show up when you log in. Edit "app/gnome-session/options/splash_image" so that it contains a path to and including the splash screen that you want.

---

### Post by Witte1985 on 2007-10-23
What scorziello was describing was neither the gdm background color nor the wallpaper background color. its the background color after you login on the gdm login screen, wich you cannot alter in any screen (not that i found) and is brown by default. Thnx moto89 for the solution.

---

### Post by groggyboy on 2007-10-23
moto89's quote has a typo.  the file in question is located at "/etc/gdm/PreSession/Default", not "/etc/gdm/Pre**s**Session/Default"

---

### Post by moto89 on 2007-10-23
> **groggyboy said:**
> moto89's quote has a typo.  the file in question is located at "/etc/gdm/PreSession/Default", not "/etc/gdm/Pre**s**Session/Default"

Good catch, fixed.

---

### Post by eldipablo on 2007-10-27
Here is the link to Moto89's original source I think:[http://www.bauer-power.net/2007/10/get-rid-of-ubuntu-brown-in-gutsy.html]("http://www.bauer-power.net/2007/10/get-rid-of-ubuntu-brown-in-gutsy.html")


I read the same thing, and hey..It worked for me. i think the trick is to change the desktop background, change the GDM background and edit the file mentioned in the article.

All 3 equals no more brown!

---

### Post by scorziello on 2007-10-27
Yeah IF PEOPLE WOULD PAY ATTENTION THE POST IS LABELED AS SOLVED. WOW MAYBE THAT MEANS THAT IT IS AN ISSUE THAT NO LONGER NEEDS TO BE ADDRESSED.

---

### Post by Joe Momma on 2007-10-31
Excuse me, but it doesn't really seem solved to me.  It's more of a work-around.  The problem still remains that setting the background color through the GUI does not work correctly.

In previous versions of Ubuntu you could get rid of the brown screen by setting your splash background and your desktop background.

---

