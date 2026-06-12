---
title: "kubuntu - ?howto run bash script from new media detected dialog"
date: 2006-09-08
forum: Desktop Environments
---

### Post by jetpeach on 2006-09-08
This seems like it should be so simple, i think i'm just missing some command.
When i plug my ipod in, i would like the dialog that shows up to list a choice where one is to run a script i wrote (it syncs my google calendar to my ipod).  So i go in Kcontrol and go to storage media->notifications, and add a new notification where the command is "/home/jet/myscript.sh" where my script resides.  now if I hit f2 (run command dialog in kubuntu) and type this command exactly then the script runs fine and all is good, but when i choose the option and it runs from the media load menu, I get
"Error - KIOExec
/media/ipod is a folder, but a file was expected"
and just have to hit ok.

This is so strange to me, why doesn't the script run just like when i double click it or when i run it in the terminal, or when i run it from the kde command dialog?!  arg

so, i tried adding the following before the command:
kdesu /hoem/jet/scriptname.sh
bash /home/jet/scriptname.sh
kdesu -u jet scriptname.sh
kdesu -u jet scriptname.sh

same error all the time.

anyway, if somebody can help that would be great!
thanks,
jet

PS how do i make this a kubuntu thread? i liked that option to search for kubuntu only stuff and post specifically for kde stuff.  looks like they took it away ;(

---

### Post by jetpeach on 2006-09-11
bump!  anybody?  or does anybody know if there's a way to tag this as kde related?

---

### Post by fang0654 on 2007-08-24
I came across your post on Google, and just figured out the solution.

Under the command area, put a %u at the end of your script.

ex:

/usr/bin/foo.sh %u


Then it will start up fine.

---

