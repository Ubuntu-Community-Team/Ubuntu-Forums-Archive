---
title: "Copying Folders in Ubuntu"
date: 2012-09-17
forum: Desktop Environments
---

### Post by syam2202 on 2012-09-17
Hi there ... I am new to Ubuntu. I have just installed Ubuntu and I am  facing with several problems... 1. some printers could not be installed  (eg Canon LBP 2900),  2. How can I copy folder from Home to localhost  (/var/www). Using Windows, I can open several windows and just drag the  folder into another folder in the windows. In Ubuntu... Can I? (open  several folders and copy one directory into the /var/www directory -  localhost). 3. In windows, i usually use Dreamweaver to create a  homepage visually, in ubuntu ...Komposer is not as user friendly as  Dreamweaver ... Can someone help me ... or would you recommend me to  switch back to Windows? Plsssssss....;)

---

### Post by GeForce 9500GT on 2012-09-17
> **syam2202 said:**
> 1. some printers could not be installed (eg Canon LBP 2900)
[Check this site for Canon drivers.]("https://sites.google.com/site/tipsandtricksforubuntu/printer-info/canon-drivers")
 
[/QUOTE]3. In windows, i usually use Dreamweaver to create a homepage visually, in ubuntu ...Komposer is not as user friendly as Dreamweaver ... Can someone help me ... or would you recommend me to switch back to Windows?[/QUOTE]
[Here you can find all sort of website editors]("http://linuxappfinder.com/development/web/websiteeditors"). Maybe you could make Dreamweaver run using Wine. Else check these pages:
 
[http://ubuntuforums.org/showthread.php?t=1685203&highlight=dreamweaver](http://ubuntuforums.org/showthread.php?t=1685203&highlight=dreamweaver)
[http://ubuntuforums.org/showthread.php?t=2055200&highlight=dreamweaver](http://ubuntuforums.org/showthread.php?t=2055200&highlight=dreamweaver)
[http://ubuntuforums.org/showthread.php?t=2056681&highlight=dreamweaver](http://ubuntuforums.org/showthread.php?t=2056681&highlight=dreamweaver)
[http://ubuntuforums.org/showthread.php?t=1982237&highlight=dreamweaver](http://ubuntuforums.org/showthread.php?t=1982237&highlight=dreamweaver)
[http://ubuntuforums.org/showthread.php?t=1983296&highlight=dreamweaver](http://ubuntuforums.org/showthread.php?t=1983296&highlight=dreamweaver)
[http://ubuntuforums.org/showthread.php?t=2042572&highlight=dreamweaver](http://ubuntuforums.org/showthread.php?t=2042572&highlight=dreamweaver)
[http://ubuntuforums.org/showthread.php?t=2052484&highlight=dreamweaver](http://ubuntuforums.org/showthread.php?t=2052484&highlight=dreamweaver)
 
If you need more info, just do a search on this forum. There's more than enough info to be found here! Good luck!

---

### Post by kaytrance on 2012-09-17
> **syam2202 said:**
> Hi there ... I am new to Ubuntu. I have just installed Ubuntu and I am  facing with several problems... 1. some printers could not be installed  (eg Canon LBP 2900),  2. How can I copy folder from Home to localhost  (/var/www). Using Windows, I can open several windows and just drag the  folder into another folder in the windows. In Ubuntu... Can I? (open  several folders and copy one directory into the /var/www directory -  localhost). 3. In windows, i usually use Dreamweaver to create a  homepage visually, in ubuntu ...Komposer is not as user friendly as  Dreamweaver ... Can someone help me ... or would you recommend me to  switch back to Windows? Plsssssss....;)
1. Very dependent. Google shows many results, you might want to try some.
2. use sudo [cp ]("http://www.computerhope.com/unix/ucp.htm")command. The reason you cannot copy it because you do not have sufficient permissions to write to  /var/www/. Either chown it (not recommended), or launch nautilus as root (sudo nautilus) to drag-n-drop.
3. Cannot directly answer, but I can suggest not to use ones at all since making a page is very easy by writing its code.

---

### Post by newb85 on 2012-09-17
I wouldn't go running back to Windows just yet.

1.  Sorry, I don't know about Canon Printers.  My old faithful Brother takes a bit of a rigmarole, while I've had several HP printers work with almost no effort.

2.  As kaytrance said, your copying issue is a matter of permissions.  By default, you only have basic user permissions, which means you can only alter the contents of your /home directory and its sub-directory.  Beyond that you need superuser privileges.

If you want to drag-and-drop,

```
gksudo nautilus & gksudo nautilus & exit
```

will open 2 file browser windows with said privileges.

You can also simply copy or move from the command line

```
sudo cp ~/file_to_copy /var/www/.
sudo mv ~/file_to_move /var/www/.

```

3. I'm guessing kaytrance's advice won't sit so well with you on this one.  I have little experience in this area.  I don't know if you've realized it yet, being new to Ubuntu, but there are options.  If you're unsatisfied with Komposer, try a few alternatives and see which one you like.  [Here]("http://ubuntuforums.org/showthread.php?t=2055200&highlight=dreamweaver")'s another recent thread where alternatives to Dreamweaver are discussed.


By the way, when posting in the forums, please create a separate thread for each of your issues.  It makes life easier for everyone.

---

### Post by syam2202 on 2012-09-17
Waaaa... You all are very helpful. Thanks again. By the way, Sorry coz' I posted three different issue in one post.  I wont do it next time...

I will try all the suggestions... thanks again!

---

### Post by newb85 on 2012-09-17
By the way, in case no one has said it yet, welcome to Ubuntu.  Hope your experience is as enjoyable as mine has been.  You will have more questions along the way, so when you post, please keep in mind the suggestions in [this sticky]("http://ubuntuforums.org/showthread.php?t=1422475").

Also, please leave feedback about how others' suggestions work (or don't as the case may be).  It's helpful for others with the same questions who find your thread.

---

