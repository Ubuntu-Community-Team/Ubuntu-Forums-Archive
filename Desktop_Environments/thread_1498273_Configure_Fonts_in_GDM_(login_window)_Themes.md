---
title: "Configure Fonts in GDM (login window) Themes"
date: 2010-05-31
forum: Desktop Environments
---

### Post by harrismh777 on 2010-05-31
Use the following procedure carefully to change the default color 
and font used by one of the gdm (greeter, login window) themes on 9.04
Jaunty. In this example I am changing the color and font of the username 
password entry fields on the gdm greeter login window "Human" theme in 
jaunty, 9.04. 

   Each theme is maintained in a separate folder under /usr/share/gdm/themes/.

   The themes are owned by root, so you will need to be logged in with 
an administration userid that has authorization to sudo, or gksudo.

   Open a terminal window with Applications -> Accessories -> Terminal

   Change to the themes directory with:

       cd /usr/share/gdm/themes/Human/

   If you plan to edit the Human.xml theme file with gedit (or other gui
editor) then you will want to use a command like:

       gksudo gedit Human.xml

   Otherwise if you are planning to edit the Human.xml file with vi or 
vim then use the command:

       sudo vi Human.xml 

   Warning: It is assumed here that you know what you are doing with an
editor. Also, that you understand that care should be taken to not break
the file being edited. Make a backup copy of the file before you begin 
tweaking it: words to the wise.

   Search down through the Human.xml file for the "password box" coding.
The snippet below shows the comment header and the section of code we are
interested in. We will be changing the line of code directly below the 
following line:

        <item type="entry" id="user-pw-entry">

   See below:

  <!-- password box -->

     <<< snipped >>>

          <item type="pixmap">
            <normal file="userentry.png"/>
            <pos width="240" height="32"/>
            <fixed>
              <item type="entry" id="user-pw-entry">
                <normal color="#FF00FF" font="Sans Bold 12"/>
                <pos y="5" x="5" width="-10" height="-10" anchor="nw"/>
              </item>

   I have changed the default color="#000000" font="Sans 11" to a bold font in magenta:
       <normal color="#FF00FF" font="Sans Bold 12"/>

   The colors are specified in RedGreenBlue format. See the following link
for a discussion of color codes:
       [http://www.w3schools.com/html/html_colors.asp](http://www.w3schools.com/html/html_colors.asp)

   To make the font larger just make the pitch number larger for example,
font="Sans Bold 14".

   Save the file and logout. When the greeter panel restarts the change will take effect.

:)

Regards,

---

