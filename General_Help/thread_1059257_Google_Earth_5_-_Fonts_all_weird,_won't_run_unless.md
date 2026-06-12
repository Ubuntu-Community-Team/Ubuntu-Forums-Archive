---
title: "Google Earth 5 - Fonts all weird, won't run unless SUDO"
date: 2009-02-03
forum: General Help
---

### Post by joey-elijah on 2009-02-03
I installed Google Earth 5 yesterday and, at first, it worked fine aside from a font issue: -

[IMG]http://img17.imageshack.us/img17/932/ge5ou3.jpg[/IMG]

When i run it now, the GUI pops up but is very loooooooooong and i'm unable to actually use GE because the globe or any directional controls don't show up.

I have renamed 
libcrypto.so.0.9.8but nothing has changed.

I can view the globe and use GE normally as long as i run it via terminal and with 'Sudo'. The fonts are still a mess though.

2 parts: -

[B]How do i fix running it without sudo? 
How can i fix the font issue?

[/B]*I posted this in a separate thread to the "Google Earth 5 Crashes" because mine doesn't crash.*

---

### Post by joey-elijah on 2009-02-06
*cough* bump *cough*

---

### Post by macozz on 2009-02-16
No solution yet? I have no font problems, but mine runs only as sudo. It seems that as normal user it cannot connect to server, but I think that there is another problem, becuse when sudo, even with no connection, it display the earth, as normal user it exhibit just a black screen and do not let me modify any preference.

---

### Post by cviorel on 2009-04-22
Hi!
I managed to get this working by issuing the following commands in the directory where google-earth is installed:

```

cd /opt/google-earth # this is where my google-earth 5 is installed
mv libQtCore.so.4 libQtCore.so.4_backup
mv libQtGui.so.4 libQtGui.so.4_backup
mv libQtNetwork.so.4 libQtNetwork.so.4_backup
mv libQtWebKit.so.4 libQtWebKit.so.4_backup
ln -s /usr/lib/libQtCore.so.4.4.3 libQtCore.so.4
ln -s /usr/lib/libQtGui.so.4.4.3 libQtGui.so.4
ln -s /usr/lib/libQtNetwork.so.4.4.3 libQtNetwork.so.4
ln -s /usr/lib/libQtWebKit.so.4.4.3 libQtWebKit.so.4

```

You may need to install libQtWebKit. It's in the repository.

---

### Post by joey-elijah on 2009-04-27
IN jaunty i solve all issues by just using 'googleearth -style GTK+' - which makes Google Earth use your theme, fonts etc. Flawless!

---

### Post by ad5os on 2009-05-01
Hmm that works for 4.2 googleearth  but I cant get it to work with 5.0

---

### Post by joey-elijah on 2009-05-01
> **ad5os said:**
> Hmm that works for 4.2 googleearth  but I cant get it to work with 5.0

I'm running Google Earth 5 in Jaunty and it works fine. You need to be using Jaunty or have QT4 installed in Intrepid.

---

### Post by AlanR8 on 2009-05-12
> 
IN jaunty i solve all issues by just using 'googleearth -style GTK+' - which makes Google Earth use your theme, fonts etc. Flawless!

Can you explain EXACTLY how to do that please?

---

### Post by joey-elijah on 2009-05-14
> **AlanR8 said:**
> Can you explain EXACTLY how to do that please?

Sure :) 

Either run it via a terminal by pasting 

```
googleearth -style GTK+
```and hitting return. 

**OR**

To get it running with GTK all the time just change the menu launcher: -

*System > Preferences > Main Menu*

Click '*Internet*' in the left hand bar, and then select '*Google Earth*' from the right hand side.

 Choose '*Properties*' and in the 'command' field paste the command:

```
googleearth -style GTK+
```

[I][IMG]http://img53.imageshack.us/img53/6843/screenshot001u.png[/IMG]
[/I]
Now when you launch it from the main menu, it will run with GTK!

---

### Post by aalhamer on 2009-10-06
Dear All,

I have tried every suggestion and ended up in failure, the solution to my small font problem with google earth 5 was simply to change the settings of my QT4. I know it pissed me off too.

go to your desktop
Follow to and open System> Preferences> QT 4 Settings
click on the font tab and choose the desired size. I run a 1360 resolution 18 aria was perfect.

I hope this solves the problems of many.

---

### Post by Francewhoa on 2010-03-21
Same here. Default fonts are too small in Google Earth 5. **The following worked for me.** [http://ubuntuforums.org/showthread.php?p=9004685#post9004685](http://ubuntuforums.org/showthread.php?p=9004685#post9004685)

---

