---
title: "autostart a konsole command that uses sudo in KDE- HELP?!"
date: 2007-05-28
forum: Desktop Environments
---

### Post by KevinAlaska on 2007-05-28
Hello and first off thank you for reading my posting here.

I have had difficulty on an issue that I am sure is pretty simple.  

First off let me post a web link to a page on ubuntuforums.org that helped me get my logitech g15 keyboard up and running except for the bottom part of the page which would help me if I had gnome installed and not KDE.

[http://ubuntuforums.org/showpost.php?p=2461304&postcount=285]("http://ubuntuforums.org/showpost.php?p=2461304&postcount=285")

halfway down this small page it reads:
"If you want to have the daemon autorun on startup try running (BE CAREFUL)"

I first am not sure where exactly this is supposed to installed at in the file /etc/sudoers using the command "sudo visudo".  Bellow is the files internal view.

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


```

Then I am supposed to insert this command "somewhere" in the file:
user ALL= NOPASSWD: /usr/sbin/g15daemon

that is the first half of my question... Last part is how do I get it to autostart sense I can't do that gnome thing of System->Preferences->Sessions and add sudo g15daemon to the list. :(  I heard /.kde/Autostart and right click then 'create new' --> 'link to application' but is that correct and what in there in the link to I have to give it besides giving it a name, a working path like and the command (ie work path=/usr/bin and Command=/usr/sbin/g15daemon)?  I am just to lost and to much of a noob to really get this fixed by my self... hay I have an idea.. Maybe I should get someone to hold my hand while I get walked through it? Joking of course.

Well thank you for your time again.

Sincerely,

Kevin in Alasak

---

### Post by KevinAlaska on 2007-05-29
No body had a thing to post on this in a 24 hour time frame? heh.. It was probably my fault with this.  If I am missing something int his post please let me know.  I am not sure but I was really guessing that this was an easy post to help on.  I at least thought the part with the /.kde/Autostart might have been easy.  :) 

Oh well thank you none the less.  I will give it a we bit more time.  Cheers! :)

---

