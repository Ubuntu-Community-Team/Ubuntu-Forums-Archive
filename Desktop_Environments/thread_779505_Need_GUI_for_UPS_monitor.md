---
title: "Need GUI for UPS monitor"
date: 2008-05-02
forum: Desktop Environments
---

### Post by Chimmer on 2008-05-02
Ok....I finally got Ubuntu to monitor my UPS. I downloaded the PowerPanel for Linux software located [here]("http://www.cyberpowersystems.com/products/management-software/ppl.html").

I can go into a console and get the status of the UPS, looks like it's monitoring it correctly.

Now, does anyone know if there is a GUI that I can hook up to this so that I can monitor it on my desktop?

Thanks!

---

### Post by ad_267 on 2008-05-02
What do you want the gui to do?

You could create a launcher to open up the status in a command line. To add it to the panel you right click on the panel, and select add to panel then you'd select custom application launcher. Change the type to "application in terminal" and in the command box enter "pwrstate -status"
If the program requires you to be root then you would need to use "gksu pwrstate -status"
To add a launcher to your applications menu you can right click on the menu and select edit menus then select new item.

---

### Post by Chimmer on 2008-05-02
> **ad_267 said:**
> You could create a launcher to open up the status in a command line. To add it to the panel you right click on the panel, and select add to panel then you'd select custom application launcher. Change the type to "application in terminal" and in the command box enter "pwrstate -status"
If the program requires you to be root then you would need to use "gksu pwrstate -status"

I'm coming from Windows so I'm used to nice pretty GUI's!  :)

Your solution would be great if I could get it to work. The actual command is pwrstat -status. When I follow your instructions, I get a popup window for just a second and then it disappears. It happens too fast for me to read anything. 

Is there any way to get the window to stay up?

Thanks for the help.

---

### Post by ad_267 on 2008-05-02
Ok after a bit of searching it looks like it's not that easy to keep the terminal open. What you need to do is create a directory "bin" in your home folder if there isn't one already then create a new text file in here. Name it something like "upsstatus". In the text file enter this:

```
#!/bin/bash
pwrstat -status
read
```

The first line tells the script to run using bash which is the default shell used for the terminal. The second line executes the monitor. The third line reads in input from the user. This means that the script won't close until you press a key. If you want to have to press a letter like q to quit then you would do something like this:

```
#!/bin/bash
pwrstat -status
while [ "$input" != "q" ]
do
	read input
done

```

Save the file and then right click on it and select properties, go to permissions and tick the box next to exectute.
Then change the shortcut command to upsstatus instead of pwrstate -status

If you want to make a better looking gui you could look into using zenity. This allows you to write bash scripts that can create dialog boxes. So you could use grep to search through the output of pwrstat to find what you want and then zenity to output that information in a dialog box. Type "man zenity" for more info.

---

### Post by ad_267 on 2008-05-03
If you want to use Zenity then you could try using a bash script like this:

```
#!/bin/bash

status=`pwrstat -status`
zenity --title="UPS Status" --info --text="$status"
```

---

### Post by Chimmer on 2008-05-03
Thanks for all the help, I'll give it a try this weekend.

---

### Post by Chimmer on 2008-05-03
Ok....one last thing...I think we're getting close. :)

I need to use a password to be able to run the command. When I launch it, I get a "permission denied" message.

Is there any way to modify the command so that I'm either prompted for my password, or it's stored in there? (I know, probably not a good idea)

Thanks again.

Ok, I got it working, I added "sudo" before the pwrstat command and now it prompts me for my password. 

**Edited to add:** One last thing (I promise!)...

[COLOR="Blue"]Is there any way to modify the command so that it doesn't prompt me for my password (stores it in the file)? Or, would this be a bad idea? I'm the only one using the PC so it's not that big of an issue from a security standpoint.[/COLOR]

---

### Post by Chimmer on 2008-05-03
I think I figured it out....still need to test some more. I used a method for removing password prompts for sudo found [here]("https://help.ubuntu.com/community/RootSudo"). I think that will do what I want it to do.

Thanks again for all the help. Still have much to learn. :)

---

### Post by Nathan.Flow on 2010-06-30
> **Chimmer said:**
> Ok....I finally got Ubuntu to monitor my UPS. I downloaded the PowerPanel for Linux software located [here]("http://www.cyberpowersystems.com/products/management-software/ppl.html").

I can go into a console and get the status of the UPS, looks like it's monitoring it correctly.

Now, does anyone know if there is a GUI that I can hook up to this so that I can monitor it on my desktop?

Thanks!

does any one know if this will work with APC products?

---

### Post by Mike_D_P on 2010-09-20
I have used gapcmon (from the Ubuntu repos) on a Karmic server with a USB connected APC Smart-UPS 750VA.  This is a gui for apcupsd ([https://help.ubuntu.com/community/apcupsd](https://help.ubuntu.com/community/apcupsd)) which supports many APC UPS's. Documentation for this is really good (111 pages) but if you use the gui it's really easy to use.

---

