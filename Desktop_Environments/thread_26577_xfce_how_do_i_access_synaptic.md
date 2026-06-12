---
title: "xfce: how do i access synaptic?"
date: 2005-04-13
forum: Desktop Environments
---

### Post by Datchew on 2005-04-13
I'm in a fresh install of hoary and running both stock gnome and xfce. 

I prefer to use xfce but when i need to open synaptic package manager and find/install something, i can't seem to locate it within XFCE so i have to logout and go into gnome to do it. 

Also, as a recent example, I went into gnome to use synaptic to install Gftp. 
restarted, can access it in gnome, but when i go into xfce again, i cannot find it. 

Any ideas?

---

### Post by jordanau on 2005-04-13
debian > apps > system

or sudo synaptic in terminal

---

### Post by localzuk on 2005-04-13
or type alt-f2 and use 'gksudo synaptic'

---

### Post by Glanz on 2005-04-13
You may also add Synaptic to your panel, either as an entry in a roll-up already there or by adding a new launcher. The path is /usr/sbin/synaptic. The 'command' entry will therefore be: sudo /usr/sbin/synaptic.  You may also use the terminal to install applications via "apt-get"... using, of course, the 'sudo' also:  terminal >  $ sudo apt-get install gftp...

---

### Post by Trevor Bramble on 2005-04-13
[QUOTE=jordanau]debian > apps > system

or sudo synaptic in terminal[/QUOTE]

I do the second one because the first one does not work.  That portion of the menu is curiously off-limits to the XFCE Menu Editor, and I haven't uncovered whatever other mysterious and minimally-documented method should be used in its stead.

---

### Post by Datchew on 2005-04-13
i'm about moved to tears. 

so many times i've posted questions and gotten NOTHING... [COLOR=Red][SIZE=6]***NOTHING***[/SIZE][/COLOR]

and now, i have not only how to do it, but how to add it to menus in a couple different ways and also how to (from console) install the app that i was speaking about.  

you guys are the greatest.  heck, i'm gonna start posting xfce questions more often!

one more question.  
when i right click the xfce desktop, i get the little menu of things to run. 
how can i add things into that little menu?  what is that menu called?
can't find how to edit it anywhere!

---

### Post by Glanz on 2005-04-13
[QUOTE=Datchew]
one more question.  
when i right click the xfce desktop, i get the little menu of things to run. 
how can i add things into that little menu?  what is that menu called?
can't find how to edit it anywhere![/QUOTE]

We are NOT the greatest! We are just afraid of your dino avatar.!!!
Yes, you can edit that menu! Check /home/x/.config/xfce4/desktop.menu.xml (don't touch the other 'menudefs.hook' thingy.). Replace the "x" in the above location with the name of the user. That xml file is easy to edit... just make a backup in case you screw up in your first try. I have many personalized entries in my root menu.

---

### Post by Datchew on 2005-04-13
[QUOTE=Glanz]We are NOT the greatest! We are just afraid of your dino avatar.!!![/QUOTE]


sorry man... that thing scares everyone.  what can i say?  (shrug) 
 :grin:

I browsed as sudo through the file manager to 

/home/x/.config/xfce4/  

but under the "desktop" folder there, there is NOTHING!.  I have it set to show all hidden files, etc.  
Am i missing something?

---

### Post by Glanz on 2005-04-13
[QUOTE=Datchew]sorry man... that thing scares everyone.  what can i say?  (shrug) 
 :grin:

I browsed as sudo through the file manager to 

/home/x/.config/xfce4/  

but under the "desktop" folder there, there is NOTHING!.  I have it set to show all hidden files, etc.  
Am i missing something?[/QUOTE]
 Yes, you have to show hidden files to see "dot files and folders" (those beginning with a dot).

You do NOT have to be sudo to edit the menu.xml file contained in the ".config" FOLDER using the path I gave you. In fact, you do NOT want to be sudo. (yet). The "x" should be changed with your home user's name.....

So, if you are using gedit > open file, right-click in the choices of folders in your home directory that are presented, and choose "Show Hidden Files".... 

Here is how a 'virgin' 'menu.xml' file looks::
=======================================
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE xfdesktop-menu>

<!-- 
     Explanantion of Xfce 4 menu file: 
     =================================
     Here we will try to explain the format of the menu file.  Look at the
     actual menu below for the real examples.  You shouldn't really need to
     edit this manually; check out xfce4-menueditor instead.
-->

<!-- Obviously, this is how you make a comment ;-) -->

<!-- 

  + Everything is between exactly one pair of 
    <xfdesktop-menu></xfdesktop-menu> tags.

  + Applications:
    <app name="Name in menu" cmd="Command to run" term="false"
         icon="iconfile"  snotify="false" visible="true" />
    The 'term' attribute determines if the program needs a terminal to run,
    and 'snotify' sets whether or not the program supports startup
    notification.  You can set an icon to be displayed next to the item with
    the 'icon' attribute.  Only 'name' and 'cmd' are required.

  + Separators:
    <separator visible="true" />
    Creates a horizontal separator.  The 'visible' attribute is optional.

  + Submenus:
    <menu name="Name in menu" icon="iconfile" visible="true"></menu>
    Only 'name' is required, but you can also set an icon to be displayed using
    the 'icon' attribute.  Between the menu tags you can define more
    applications, separators and menus.

  + Including other files:
    <include type="file" src="menu2.xml" visible="true" />
    Includes the file menu2.xml.  A relative path is assumed to be rooted at
    ~/.xfce4/ or $XDG_CONFIG_DIRS/xfce4/. An absolute path will be treated
    as such.
    
  + Including an autogenerated system menu:
    <include type="system" />
    Includes a system menu.
-->

<xfdesktop-menu>

    <app name="Run Program..." cmd="xfrun4" icon="gnome-fs-executable"/>

    <separator/>

    <app name="Terminal" cmd="xfterm4" tip="Terminal emulator" icon="gnome-terminal"/>
    <app name="File Manager" cmd="rox" icon="file-manager"/>
    <app name="Web Browser" cmd="sensible-browser" icon="gnome-globe"/>

    <separator/>

    <!--
      The next line includes the autogenerated menu at the current level.  If
      you want, you can put this in its own submenu.
    -->
    <include type="system" />

  <menu name="Debian" icon="debian">
      <include type="file" src="menudefs.hook" />
  </menu>

    <!--
      Uncomment the following line (and comment the above) if you would rather
      include a separate menu file instead of using the auogenerated menu.
    -->
    <!-- <include type="file" src="menu2.xml"/> -->

    <separator/>

    <app name="Help" cmd="xfhelp4" tip="Display help about Xfce" icon="gnome-help" />
    <app name="About..." cmd="xfce4-about" tip="Display information about Xfld and Xfce" icon="xfce-system-info" />

    <!--
      This will cause xfce4-session to quit, after first displaying a log-out
      dialog box.  If xfce4-session isn't running, it will quit xfdesktop.
    -->
    <builtin name="Quit" cmd="quit" tip="Quit Xfce desktop session" icon="gnome-logout"/>

</xfdesktop-menu>

---

