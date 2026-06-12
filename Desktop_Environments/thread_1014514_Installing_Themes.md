---
title: "Installing Themes"
date: 2008-12-17
forum: Desktop Environments
---

### Post by DannyP87 on 2008-12-17
Sorry to be a pain and noob but I haven't got the slightest idea how to install themes, never mind get the right one.

I've seen plenty on Gnome Art etc but I haven't a clue which one to install or how to. I'm new to linux, just recently installed Ubuntu 8.10.

If I right click on my desktop I can change the themes that are already there no problem, I'm just struggling in finding the right one and how to install it so if anyone can help I'd truly appreciate it.

Thanks

---

### Post by tuxxy on 2008-12-17
DOwnload the theme you want to desktop, open up system > prefs > appearance and drag the .tar file into the theme window.

---

### Post by Yanz on 2008-12-27
Where would I go to find .tar files?

---

### Post by rudihawk on 2008-12-27
> **Yanz said:**
> Where would I go to find .tar files?

On your local computer? To wherever you saved them. Then just go and drag them into the appearance dialog. 

Otherwise you would have to download them first :D

---

### Post by steveneddy on 2008-12-27
Go to:

art.gnome.com

or

gnome-look.org

and find a theme that YOU like.

Download it to your desktop.

Go to your desktop (minimize everything) , right click the desktop. when themenu opens up, select Change Desktop Background.

New window, select the Themes tab, then the install button.

Navigate to the desktop and find the theme that you just downloaded.

Easy peasy.

---

### Post by arepaking on 2008-12-27
> **steveneddy said:**
> Go to:

art.gnome.com

or

gnome-look.org

and find a theme that YOU like.

Download it to your desktop.

Go to your desktop (minimize everything) , right click the desktop. when themenu opens up, select Change Desktop Background.

New window, select the Themes tab, then the install button.

Navigate to the desktop and find the theme that you just downloaded.

Easy peasy.



Hi,
I followed your steps and I downloaded a theme from 
gnome-look.org. Then when I did drag-and-drop in the theme window, then I got the following message:

"eGDM" does not appear to be a valid theme"

Am I missing something?

Thanks,
AK

---

### Post by Yanz on 2008-12-28
I keep getting "This is not a valid theme"
And the one that did work, said "The icon pack is missing" or whatever >.> or the colour pack >.>

---

### Post by cylux on 2008-12-28
The following works for me.

Get a gtk theme that you like.

A good place to start is here

[http://gnome-look.org/index.php?xcontentmode=100&PHPSESSID=57cf56124843553fe2edce7796a3c50a](http://gnome-look.org/index.php?xcontentmode=100&PHPSESSID=57cf56124843553fe2edce7796a3c50a)

Download the file and it should be a tar achrive, that just means it has the .tgz extension.

A tarball archive works kindof the same way a .zip file works. When Firefox prompts you for if you want to open or save the file, open it.

This will bring up the gnome archiver dialogue, go to the "File" dropdown menu at the top left corner of the dialogue and select "Extract"

Extract the contents of the file to  
```

~/.themes/
```

NOTE: You can make that directory if it isn't already there with running the following command within a terminal.
```

mkdir ~/.themes
```



Now you need a GTK theme switching application, I like to use gtk-theme-switcher, you can install this application by running the following command from the terminal
```

sudo apt-get install gtk-theme-switch
```

Now open up any terminal window and run the command

```
switch2
```

Select your theme from the drop-down menu and voila, you have your theme installed.

Let me know if you encounter any issues.

---

### Post by 3pinner on 2008-12-31
I just tried this myself in Intrepid.
I dowloaded the tar file to my desktop.
right clicked on the desktop to open Change Desktop Background,
Clicked on the Themes tab,
 then Install.
I navigate to the tar file, click open and I get a message that the file has been installed, do I want to use it? I clicked Yes.
But I didn't see it listed in the Themes window; but noticed that Custom was highlighted.
So I renamed Custom to the name of the tar file, and there it is.

Easy!

---

### Post by spinstartshere on 2008-12-31
eGDM is a GDM theme, not a GTK theme.  It gets used when you log in to the computer.  I downloaded it the other day, but changed it a bit to better suit me...

To install it, go to System -> Administration -> Login Window, and type in your password.  Click the tab that says Local, and then drag the .tar or .tar.gz file into the bit of the window with the various different pictures.  If I recall, when you download the theme it is in a .zip file so you have to extract the .tar first.  You can do that by right-clicking on it (once you've downloaded it) and clicking Extract Here.

Hope this helps.

---

