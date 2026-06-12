---
title: "Login Screen Font Too Small"
date: 2005-12-21
forum: Desktop Environments
---

### Post by rcurley on 2005-12-21
Does anyone know how to increase the size of the font in the login screen.  I'm talking about the font for when you type in your username and password.  Please do not say to change the resolution.  I have done that and it makes no changes in the font size of the text that is entered.  I have tried a couple of other themes, but none of them has had a decent font size.

Thanks...Rich

---

### Post by zman58 on 2006-01-18
Yes, you can increase the logon user and password font on the GDM login. Here is what I did to solve the problem:

Assuming here you are using the default GDM greeeter theme which is "Human". As root you will need to edit the following file:

/usr/share/gdm/themes/Human/Human.xml

First copy original file off to the side (i.e. cp Human.xml Human.xml.original) just in case you hose it up and need to recover the original data.

Ubuntu defaults to the "Human" GDM greeter theme. If you have changed that, then you will need to edit the xml theme file that corresponds to one of the other themes. These files are located beneth the themes directory in the path above. The default file for Human theme is shown.

Find the line in the .xml file that looks like this:
  <!-- password box -->

a few lines below this line you should have an section that looks like this...

            <fixed>
              <item type="entry" id="user-pw-entry">
                <pos y="1" x="1" width="-2" height="-2" anchor="nw"/>
              </item>
            </fixed>

This is the entry that controls the input text for username and password.
It does not have a default font entry in it. You need to add a single line that provides a font and size for user entry.

Change the section to look like the following:

            <fixed>
              <item type="entry" id="user-pw-entry">
                <pos y="1" x="1" width="-2" height="-2" anchor="nw"/>
                <normal font="Bitstream Vera Sans 14" color="#523921"/>
              </item>
            </fixed>

Save the changes and exit the editor.
Log out of the system.
Now you need to restart GDM and you can do by pressing Ctrl-ALT-BkSpace
Once you see the greeter come back up, you will have a larger font to enter your user and password. If you are not happy with the size, you can adjust the <normal ....../> line above which is specified as 14 point.

Although this is not required, you might want to change all of the font sizes in the .xml file to 14. If you are running on a 1200x1024 display the greeter text looks much better.

Go UBUNTU!    :cool:

---

