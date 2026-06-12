---
title: "GTK2.x/Conky Theme installation?"
date: 2009-10-10
forum: Desktop Environments
---

### Post by AnarchyCow on 2009-10-10
First, let me say that I'm decently new to Linux. I've worked with Ubuntu before, but I stopped even touching it for months.

Basically, what I want to know.
I downloaded a GTK2.x theme called Mira v2 from gnome-look.org and I figured out how to install the GTK2.x theme, I just copied the directory to the /usr/share/themes folder using "sudo mv..".
My first question is reguarding this. Is there an easier way to move this? I mean, it wasn't difficult by any stretch of the imagination, but I'm just wondering if there is some way to move files using the GUI into places that you need root access? Or am I going to have to sudo mv things to where I need them.

Secondly.
I have conky, and there is a conky theme that came along with the Mira v2 GTK2 theme.
I was wondering, it says 

```
### Install ###
Copy the fonts to your font dir (~/.fonts).
Copy the Scripts to "~/scripts".
Copy the Mira_* folders to "~/.conky".
```

I think I found the fonts directory under /usr/share/fonts and I copied the "xxx.ttf" into the /use/share/fonts/truetype directory, that is correct right?
But, I have no idea where either the "conky" directory or the "scripts" directory are located.
My biggest problem with understanding Linux is that, growing up in windows has gotten me used to all the programs files being in one of two places, the install directory, or the users appdata. I don't understand how the file structure workes at all, or where anything is located.
And, how do I then configure Conky as I want it?

Thanks for helping this Linux Newbie :]
~ Cow

---

### Post by wojox on 2009-10-11
You're not still using Dapper are you? 

The way you moved you themes is really a good way. You could also open System > Preferences > Appearance > Theme > Install and install the .tar.gz that way. 

Another option would be to extract the them and  Alt+F2 type:

```
gksudo nautilus
```

Then traverse to /usr/share/themes and drag your new theme in.

Your second question, anything that begins with a tilde (~) is referring to your home directory. So open Places >  Home Folder. Press Ctrl+H to view hidden files. Anything with a . before it, is hidden.

If you don't have any of those directories then you'll have to create them.

---

### Post by AnarchyCow on 2009-10-11
Thank you very much! :]

The reason I had to move it manually is because the theme didn't come in a format that the Apperence thing liked. It was in two folders for Mira v1 and Mira v2.

And I'll remember the ~ means the home directory.

Thanks for the help :]

---

