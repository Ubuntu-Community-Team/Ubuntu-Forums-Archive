---
title: "KDE Autologin"
date: 2005-05-17
forum: Desktop Environments
---

### Post by giosico on 2005-05-17
I have searched and search for a way to set kubuntu to autologin to a specific user.  Is it possible? Thank you.

I found this but it talks of compilation which scares me ;-)
[http://ubuntuforums.org/showthread.php?t=31310](http://ubuntuforums.org/showthread.php?t=31310)

---

### Post by Xian on 2005-05-17
You need to open the following path with admin priviledges:

KDE Control Center > System Admin > Login Manager

[img]http://img.photobucket.com/albums/v469/camplear/forums/login.jpg[/img]

---

### Post by giosico on 2005-05-17
I guess I did not do enough searching ... I had read the work convenience before but didnt understand it but (complain) it should be names auto login 

I couldnt find the login manager from the control center but found it by searching for it after reading this post
[https://www.redhat.com/archives/fedora-test-list/2003-October/msg03036.html](https://www.redhat.com/archives/fedora-test-list/2003-October/msg03036.html)

Now I just have to figure out how to get the fields not greyed out after [COLOR=Red]Attention! Read Help![/COLOR] ;-)

---

### Post by Xian on 2005-05-17
[QUOTE=giosico]Now I just have to figure out how to get the fields not greyed out after [COLOR=Red]Attention! Read Help![/COLOR] ;-)[/QUOTE]
KDE start menu > Run Command > kdesu kcontrol

---

### Post by giosico on 2005-05-17
Thank you all for taking the time to reply.  Most helpful.

I initially tried to sudo kdesu kcontrol from a terminal but couldnt connect to ":0.0" at root and eventually ended up runing at you stated --> start run command using the root user under options.

And it worked.

---

### Post by wwwolf on 2005-05-17
[QUOTE=giosico]Thank you all for taking the time to reply.  Most helpful.

I initially tried to sudo kdesu kcontrol from a terminal but couldnt connect to ":0.0" at root and eventually ended up runing at you stated --> start run command using the root user under options.

And it worked.[/QUOTE]

'sudo kcontrol' will work.
'kdesu kcontrol' will also work.
Both 'sudo and kdesu' together will not work AFAIK.

HTH,

---

### Post by giosico on 2005-05-17
Thank you for taking the time to reply.

Got it [http://www.afaik.com/](http://www.afaik.com/) :)

This is off topic but related to the command ... Here is what I got while running the command after I su to root

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specifed

kdesu: cannon to connect to X server :0.0

get the same message trying to run kcmshell

Now I rem from years ago about window and X but dont even know if KDE is an X window env or not ...

Thoughts?

Cheers

John

---

### Post by giosico on 2005-05-17
I assume sudo and su to root are different

---

### Post by Terracotta on 2005-05-17
In KDE center there is an option to become super user for that session, it asks for a password and then you can change it to autlogin, it's the way  I just changed it

---

### Post by govert on 2005-05-17
[QUOTE=giosico]Thank you for taking the time to reply.

Got it [http://www.afaik.com/](http://www.afaik.com/) :)

This is off topic but related to the command ... Here is what I got while running the command after I su to root

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specifed

kdesu: cannon to connect to X server :0.0

get the same message trying to run kcmshell

Now I rem from years ago about window and X but dont even know if KDE is an X window env or not ...

Thoughts?

Cheers

John[/QUOTE]

I think it works something like this:

The following will run the command as user "root"
% su
 password: ***
% [command]

The following will run the command as normal user but with _root_priviliges_:
%sudo [command]


The reason that you get "Xlib: connection to ":0.0" refused by server" is because
you are running as the root user, and the root user is not allowed to
display windows on your screen (your x-server).

Do this before logging in as root:

% xhost +
This will allow any user to display widows on your screen.-

Does it work?

---

### Post by giosico on 2005-05-17
[QUOTE=govert]
Do this before logging in as root:

% xhost +
This will allow any user to display widows on your screen.-

Does it work?[/QUOTE]

Aaah good one ... yes it works ...

Thanks ...

Good to know!

---

