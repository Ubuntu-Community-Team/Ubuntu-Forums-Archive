---
title: "configuring toolbars, workspaces, and compiz"
date: 2014-01-25
forum: Desktop Environments
---

### Post by ClientAlive on 2014-01-25
_Running Ubuntu 13.10 Desktop_  <--  and it's not broken yet  :o

I hope I'm in the right area and that I'm not including tooo much in this post. I have 3 things I'm hoping to get some help on. If anyone can help I would sure appreciate it...

They are :

 1) I want to have this one thing I think you can get with compiz but I don't know what it's called

  --> It makes a wall in the desktop that shows the lanuchers in it
  --> Looks just like macintosh where the wall is curved away from you and there's a reflection beneath it
  --> You can click on the launchers and that's what launches your applications

 2)  I want "1)" to replace the unity launcher bar altogether ( or, better  yet, just not show the unity launcher and use that instead )

 3) I have 4 workspaces now but I want to make things so certain launchers only appear in certain workspaces and the apps thereof only launch within that workspace. I've named my workspaces "Office Administration", "Research and Development","Multimedia and Entertainment", and "System Administration" ( workspaces 1, 2, 3, and 4 respectively )

  --> For the Office Administration workspace I want only the following to appear on its wall and to only launch within that workspace...

     - Thunderbird email
     - Skype
     - Konversation
     - Okular
     - Gnome terminal
     - Firefox
     - and so on ( you get the idea )

  --> For the Research and Development workspace I want only the  following to appear on its wall and to only launch within that  workspace...

     - eclipse
     - Visual Paradigm
     - Redmine
     - phpPgAdmin
     - Gnome terminal ( so some overlap )
     - Firefox ( so some overlap )
     - and so on ( you get the idea )

  --> For the Multimedia and Entertainment workspace I want only the  following to appear on its wall and to only launch within that  workspace...

     - Gimp
     - VLC
     - Deluge
     - Netflix
     - Gnome terminal ( ...some overlap )
     - Firefox ( ...some overlap )
     - and so on ( you get the idea )

  --> For the System Administration workspace I want only the  following to appear on its wall and to only launch within that  workspace...

     - Webmin
     - Gedit
     - Software center
     - System settings ( launcher )
     - Gnome terminal ( ...overlap )
     - Firefox ( ...overlap )
     - and so on ( you get the idea )

---

### Post by grahammechanical on 2014-01-25
You should first install Compiz Configuration Settings Manager (CCSM) and/or Unity Tweak Tool. Other people will suggest other options but first make sure that they are compliant with the Ubuntu 13.10 and Unity 7, which is in 13.10. And then experiment with the settings. But keep a record of the changes you make because you may have to revert those changes.

The Launcher can be set to autohide. you will find that in System Settings>Appearance>Behaviour tab. What do you want to replace the Launcher with?

Regards.

---

### Post by deadflowr on 2014-01-25
Yep, use ccsm, and go to the section "place windows"
Then go to the section fixed window placement
And set it as you would like.
add the entries to the fixed windows viewport.
viewport = workspace.

I think when using the grab I change it to title, as opposed to the class setting or something.

Anyway, that's where you can set various apps in the various workspaces.

---

### Post by ClientAlive on 2014-01-25
> **grahammechanical said:**
> You should first install Compiz  Configuration Settings Manager (CCSM) and/or Unity Tweak Tool. Other  people will suggest other options but first make sure that they are  compliant with the Ubuntu 13.10 and Unity 7, which is in 13.10. And then  experiment with the settings. But keep a record of the changes you make  because you may have to revert those changes.

The Launcher can be set to autohide. you will find that in System  Settings>Appearance>Behaviour tab. What do you want to replace the  Launcher with?

Regards.

Thank you. I do have ccsm installed and did spend a couple hrs  messing around with it yesterday, just that I haven't been finding what I  need.

-------------------------------------------------------------------------------


> **deadflowr said:**
> Yep, use ccsm, and go to the section "place windows"
Then go to the section fixed window placement
And set it as you would like.
add the entries to the fixed windows viewport.
viewport = workspace.

I think when using the grab I change it to title, as opposed to the class setting or something.

Anyway, that's where you can set various apps in the various workspaces.

Thanks. That takes care of placing windows where I want them, and grahammechanical gave me the way to hide unity launcher, any ideas on how to get that wall thingy? 

):P

---

### Post by deadflowr on 2014-01-25
> **ClientAlive said:**
> 
Thanks. That takes care of placing windows where I want them, and grahammechanical gave me the way to hide unity launcher, any ideas on how to get that wall thingy? 

):P

No clue, and I don't understand the idea you want to achieve, but probably look at the ccsm sections "desktop wall" and "expo".

---

### Post by desconocido on 2014-01-27
> **ClientAlive said:**
> ..... any ideas on how to get that wall thingy? 

):P

No, but I have seen a thread somewhere here talking about it. If you can find the codename Apple uses for that dock, it might turn up searching the forums?

---

