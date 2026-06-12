---
title: "Proper installation of programmes"
date: 2006-08-14
forum: Desktop Environments
---

### Post by khaledaboualfa on 2006-08-14
I'm trying to get a couple of programmes installed properly. I've installed Gimp 2.3 from a .deb file, it's installed this properly which is great and it works however I need to go to the following folder 

usr/local/bin/

and then click on the executable file in order to run it. For some reason it hasn't put this as part of the actual program set in my main menu file along with the icons etc. Is there a way to implement this properly? 

Also I've downloaded Celtx and the only way to run that particular programme is running the script everytime. Once again not sure how to make an application launcher as it states in the instructions on the site. 
[http://celtx.com/download.html](http://celtx.com/download.html)

Any help would be really appreciated.

---

### Post by ardchoille on 2006-08-14
First of all, you should not be using .deb packages unless you know they were built for Ubuntu. Using debian .deb packages can cause problems. It's better to use a previous version of an app from the Ubuntu repos rather than using an unknown .deb to get a more recent version of the app.

Secondly, to make a launcher for celtx, use this line in the "command" section when you create the launcher. You can also use this command from a terminal.

```

/usr/local/celtx/celtx

```

If that doesn't work, try making sure the script is executable with "sudo chmod +x /usr/local/celtx/celtx" and then try running it again.

---

### Post by gunksta on 2006-08-14
Try

```
which gimp
```

To see where all this .deb file put the executable, even though it sounds like you know where it is.

You can use the Alacarte menu editor to make a shortcut in your menu.

Applications -> Accessories -> Alacarte

Go to the section you want to have the shortcut in. I would probably stick it in graphics. And make a new shortcut. You will have to hardwire the evecutable path and the icon image, but it shouldn't be too hard. If there aren't any gimp icons in /usr/share/pixmaps for some reason, you can get slocate and grep to help you.

```
slocate gimp | grep icon
```

The icon ususally has the word wilber in it.

If you are trying to install this on a multiuser system, you will need to make a new .desktop entry in /usr/share/applications. A quick and dirty way to do this is to find a similar .desktop file....say ANYTHING in already in the Graphics section of your menu. Open up the selected .desktop file with your favorite editor (remember, use sudo) and change the values to fit your needs. Change the name to gimp.desktop and all should be happy day.

Where did you get this .deb file? It doesn't sound like it was made very well because it should have handled the creation of a shortcut for you by placing a gimp.dekstop into the applications folder as part of it's post-install stuff. This .deb file sounds kinda flaky to me...but I use several apps that did the same thing to me.


--andy

---

### Post by khaledaboualfa on 2006-08-15
I got the .deb file from the official debian repository. I thought .deb files were fine as ubuntu is built on top of debian no?

I was using SLED for Ubuntu and that's why the gimp and icons etc were not showing up. Once I'd put the normal menu back in there it all worked fine. It's still kinda buggy but it looks BRILLIANT, and I generally hate GImp, so it's definitely going in the right direction, the new icons seriously elevate it.

As for CELTX, I'll give the way you describe it above a try and post what I found. THanks guys.

---

### Post by ardchoille on 2006-08-15
> **khaledaboualfa said:**
> I got the .deb file from the official debian repository. I thought .deb files were fine as ubuntu is built on top of debian no?

I was using SLED for Ubuntu and that's why the gimp and icons etc were not showing up. Once I'd put the normal menu back in there it all worked fine. It's still kinda buggy but it looks BRILLIANT, and I generally hate GImp, so it's definitely going in the right direction, the new icons seriously elevate it.

As for CELTX, I'll give the way you describe it above a try and post what I found. THanks guys.

It's not a good idea to use debian .deb's (or any .deb's that weren't specifically  made for Ubuntu) on an Ubuntu system.

---

### Post by gunksta on 2006-08-15
> **ardchoille said:**
> It's not a good idea to use debian .deb's (or any .deb's that weren't specifically  made for Ubuntu) on an Ubuntu system.

I'll second this statement. 

Ubuntu *is *built on top of Debia but it is *NOT *debian, it's Ubuntu. The version of many lower level libraries are different and there is no reason to believe a .deb from debian ______ will work on Ubuntu. Of course, a .deb from Debian Sarge might not work on Debian Sid and a .deb from Dapper probably won't work on Warty. So, it's all a tangled mess.

---

