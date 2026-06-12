---
title: "Icon Not Showing in Unity Launcher Bar"
date: 2012-07-19
forum: Desktop Environments
---

### Post by SamBam77 on 2012-07-19
I have created a custom application launcher for my desktop.  I did this by as described [here]("http://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity-by-hand/78968#78968").  When I double click it, it automatically launches the application, perfect...except for one tiny thing.  The icon it displays in the Unity launcher bar menu is incorrect.  Instead of displaying the correct icon for the program that I selected, it shows the generic little spring icon.

I found that this problem occurs when I create the custom launcher as an “Application.”  But when I created the launcher, instead, as an “Application in Terminal,” it displays the correct icon...but it also has a terminal window pop up with the program as well.

How can I get the correct icon, but without having to have a terminal window open too?
A big reason why I am creating this launcher icon is because I do not want to have to fuss with loading the program from a terminal window each time, and adding that clutter to my screen as well.

I am using the Unity desktop environment in Ubuntu 12.04.

---

### Post by Frogs Hair on 2012-07-19
You can create a launcher from the main menu if alacarte is installed. A recommended dependency is the Gnome Panel but you can install alacarte without it. ```
sudo apt-get install --no-install-recommends alacarte
```

Open the main menu from dash and create a launcher under the category as you want as you did with the desktop launcher. Add the icon of choice by navigating to an image from icon pictures in launcher properties. I created a Nautilus Root icon to avoid opening the terminal and typing the command every time.

---

### Post by SamBam77 on 2012-07-19
I am not sure how this helps me get the launcher on to the Desktop and/or Unity launcher bar.  I thought that the Main Menu program was more or less obsolete with the Gnome3, and Unity, replacements to the classic Gnome interface.  Is there still a way to use it?  I could not figure it out.

---

### Post by Frogs Hair on 2012-07-20
> **SamBam77 said:**
> I am not sure how this helps me get the launcher on to the Desktop and/or Unity launcher bar.  I thought that the Main Menu program was more or less obsolete with the Gnome3, and Unity, replacements to the classic Gnome interface.  Is there still a way to use it?  I could not figure it out.

The icon will appear in dash when created and can be added to the launcher. I used the Nautilus icon as and example of one I made. Alacarte is  installed by default with the Gnome Shell or the Fallback Session but not with unity. 

The main menu is a good tool for crating launcher and I would rather have an icon in dash than on the desktop when using unity. I don't know why the instruction you posted didn't work unless it is out dated.

Basically you select category you want the launcher to appear in the left pane of the main menu and select add new item from the right side .

---

### Post by SamBam77 on 2012-07-20
Oh, I see the trick now.  Add the short cut in the dash and then drag it over.  Alright, I got it to work now; now it launches the program correctly and displays the right icon.

Thanks.

---

