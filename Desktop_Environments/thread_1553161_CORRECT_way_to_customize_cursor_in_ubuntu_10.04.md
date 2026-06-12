---
title: "CORRECT way to customize cursor in ubuntu 10.04"
date: 2010-08-14
forum: Desktop Environments
---

### Post by FireStorm102389 on 2010-08-14
There are a lot of newbies out there, I know because I am one.  This is a guide to customize your cursor in UBUNTU 10.04 since I couldn't find a good one anywhere...so here goes.

Download the Cursor that you want to install. Make sure it is a tar.gz file.

right click desktop anywhere and click change desktop background (or system>prefferences>appearance)

Click on Themes.

Open a nautilus terminal and find your tar.gz file, then drag and drop into the themes tab of your appearance window, then when prompted, click apply now.

close the prefferences window.

Even though you just installed the tar.gz file, right click and click "extract here".

right click and push cut.

go into your home directory, if you can't see hidden files click view and show hidden files. Open .icons, otherwise make it if it isn't already there.

inside .icons paste your cursor theme folder that you cutted from the other directory. Then create a folder called default.

----Here's the Tricky parts----

inside default folder, create an empty document and open it. Inside, write
```
[icon theme]
inherit="Name of the folder you pasted"
```

go to SAVE AS "index.theme"

Now close all open windows except for gedit but you can close the file you just saved. -- for the sake of organization


Open a terminal (Accessories>terminal), and open gedit text editor.

In the terminal type:
```
sudo nautilus
```

Close the terminal after your root folder browser opens.

Towards the top, you'll see an arrow pointing left, click it, and then it will change to a little icon, click it again. This is so that you are in your root folder.

Navigate to usr>share>icons>default

click and drag index.theme into the gedit window, this should open the theme file.

input your file after it says inheritance=
It should look like this:
```
[theme icon]
inherit=NaMe Of YoUr FiLe HeRe
```

Then save that file and close everything.

Log out and Log back in and it should have changed!

---

