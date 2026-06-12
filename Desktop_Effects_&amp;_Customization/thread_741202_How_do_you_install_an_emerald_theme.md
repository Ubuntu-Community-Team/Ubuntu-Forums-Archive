---
title: "How do you install an emerald theme?"
date: 2008-03-31
forum: Desktop Effects &amp; Customization
---

### Post by homerm06 on 2008-03-31
I downloaded some themes I wanna add to Ubuntu 7.1 but I don't know how to install them. I'm new and I'm used to Vista so if you have instructions, please be detailed :) Thanks ^_^

---

### Post by gavintlgold on 2008-03-31
What you are dealing with are called "Window decorators". Ubuntu with the effects uses one called "gtk-window-decorator" by default. You will want to install "emerald" from the repositories, as well as "emerald-themes"
> sudo apt-get install emerald emerald-themes
Once you have that, try logging out and in. If you don't have window decorations or they are the same, add to the startup items (in the preferences menus) the following item "Emerald" with the command:
> emerald --replace
You should only do this if you see no difference after installing emerald and logging in again.

After that, you can open the Emerald themer from the menus (preferences i believe) and click "import..." and add the .emerald files. It should be quite straightforward after that.

---

### Post by homerm06 on 2008-03-31
I'm confused as hell and I'm out of cigarettes!!!
Is there a program or something easier than inputting codes? I just want to change the theme :( that's it. When I said I was a new guy, I'm a NEW guy!!! I'm like a baby trying to learn how to speak.

Ubuntu isn't for humans if I have to go through all this, it's for career coders lol. But nevertheless, I need help changing the theme into an emerald one.

---

### Post by gavintlgold on 2008-03-31
If you use Linux enough, you may find that it's easier to type in commands than to do it the long way. However, since Ubuntu is about being easier to the new user, here's the user interface way:

Open the Synaptic Package Manager from System>Administration.

Click "Search" and type in "emerald"

Click the square next to the "emerald" and "emerald-themes" items in the list and choose the option to install for both.

Choose "Apply" and confirm.

The programs will install, then continue with the instructions.

As for the second command, if the decorator doesn't load, you will have to enter that into the "Command" field in the popup window when adding the startup item. It's like making a shortcut and putting it in the "Startup" folder in  Windows really. The --replace is just to get rid of the gtk-window-decorator if it's running already.

Hope that helps.

---

### Post by homerm06 on 2008-03-31
Ok I did the steps you posted but when I double click the emerald theme I get an error: "No application suitable for automatic installation is available for handling this kind of file."

Do you know if there are themes that don't need emerald?

---

### Post by Helios1276 on 2008-04-01
Drag the theme into Emerald

---

### Post by Helios1276 on 2008-04-01
sorry, import it..its 5am here and I've had more than ubuntu beans

---

### Post by hunter_te on 2008-04-01
I dont know what theme file u have. But do this.
Since u are asking for how to install an emerald theme, i assume u already have emerald installed....
Check System>Preferences>Emerald Theme Manager..
If u have that, it will work

Go here [http://www.gnome-look.org/](http://www.gnome-look.org/)
Select Compiz from Left hand menu.

Download any theme. It will have name as xyz.emerald
Double click it. And it will open in emerald. 

Thats it....

Additionally u can do this too.  
On that same site, select GTK2x theme from left.
And download any theme on desktop. 
Right click on desktop and click "CHANGE DESKTOP BACKGROUND".
Select theme from the tabs on top.
Then drag that theme u downloaded inside the window.
It will be installed instantly.


And
Mr.Vista user, all the current ubuntu fans have used Microsoft in the past. This generation we are living in have been exposed to Microsoft already. 
Still you can see our love for ubuntu. So its just a matter of time, and u will see very soon how low maintainance, smart, efficient, professional and yet SEXY ubuntu is !!
Just stick around and be cool and patient.
We have all been through the grade or class u r going thru.

---

### Post by homerm06 on 2008-04-02
That's the thing, I don't know how to even install Emerald. I looked but the instructions that I find are for the 3D cube thingy. :(

---

### Post by homerm06 on 2008-04-02
> **hunter_te said:**
> I dont know what theme file u have. But do this.
Since u are asking for how to install an emerald theme, i assume u already have emerald installed....
Check System>Preferences>Emerald Theme Manager..
If u have that, it will work

Go here [http://www.gnome-look.org/](http://www.gnome-look.org/)
Select Compiz from Left hand menu.

Download any theme. It will have name as xyz.emerald
Double click it. And it will open in emerald. 

Thats it....

Additionally u can do this too.  
On that same site, select GTK2x theme from left.
And download any theme on desktop. 
Right click on desktop and click "CHANGE DESKTOP BACKGROUND".
Select theme from the tabs on top.
Then drag that theme u downloaded inside the window.
It will be installed instantly.


And
Mr.Vista user, all the current ubuntu fans have used Microsoft in the past. This generation we are living in have been exposed to Microsoft already. 
Still you can see our love for ubuntu. So its just a matter of time, and u will see very soon how low maintainance, smart, efficient, professional and yet SEXY ubuntu is !!
Just stick around and be cool and patient.
We have all been through the grade or class u r going thru.

AY I'm getting old lol, ok I was at the gnome site and that's where I got the theme but I don't even know how to INSTALL emerald.... And I am starting to like Ubuntu but for now I have it dual booted with Vista.. I'm even telling all my friends that once I get the hang of it then I'll install it in their computers. But the thing is that I want a Vista theme :(

---

### Post by homerm06 on 2008-04-03
Ok I found Emerald Theme Manager and I found out how to get around it. I just had to reboot to see the new themes ^_^ Thanks everyone for helping me out. I'm beginning to get used to Ubuntu, I gave Vista several chances so I'm going to do the same with Gutsy :)

---

