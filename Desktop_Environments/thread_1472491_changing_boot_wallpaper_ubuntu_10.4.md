---
title: "changing boot wallpaper ubuntu 10.4"
date: 2010-05-04
forum: Desktop Environments
---

### Post by Don Bowen on 2010-05-04
Dear Friends,
   I recently went looking for a way to change the boot-time wallpaper.  There seem to be many approaches, and some of them specific to different Ubuntu versions.  I wanted to change the wallpaper that shows up when you boot Ubuntu BEFORE you log in.  It defaults to the purple thing, and I wanted something else.

so... here's how to change it for Ubuntu 10.4

Broad steps:
1) locate default wallpaper (/usr/share/backgrounds/warty-final-ubuntu.png)
2) rename that to something else
3) copy your wallpaper to the same location
4) rename your wallpaper to "warty-final-ubuntu.png"

notes:  
-you will need to be in privileged mode for this. [COLOR=Red]Caution[/COLOR]:  you can damage your system in this mode, so
  you should use it carefully.  "sudo -i" is the command that will prompt you for your password, as shown 
  below.  (I hope it's OK to include that.  Learning that command, and its dangers, made working in Ubuntu 
  a lot easier!)
-I made sure the wallpaper I used was the same file type as the default: .PNG.  It might not matter, but it 
   seems a good idea to stay with the same file type. (use GIMP to re-save a .JPG in the .PNG format)
-renaming a file seemed odd... there seems to be a "rename" command, but I couldn't make sense of it.  the "move" command accomplished the same thing.  Here's what I did:  (your mileage may vary!)

<username>@<computer>:~$ [COLOR=Blue]sudo -i[/COLOR]
[sudo] password for <username>:
root@<computer>:~#[COLOR=Blue]cd /usr/share/backgrounds[/COLOR]
#[COLOR=Blue]mv warty-final-ubuntu.png boot-wallpaper.png[/COLOR]
[COLOR=Lime](the above line renames the default wall paper, then you can move in your own)[/COLOR]
#[COLOR=Blue]mv /home/<username>/Pictures/my-wallpaper.png /usr/share/backgrounds/warty-final-ubuntu.png[/COLOR]

(items shown in <> are specific to your system and not literal.)

That's it. You're done.  It worked well for me, and I hope it will for you as well. I've made every effort to be accurate and hope you'll find it useful.

Is there another way to do this?  Probably.  Want to post how you accomplished the same?
cheers,
-Don Bowen

---

