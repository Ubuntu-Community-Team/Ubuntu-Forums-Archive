---
title: "Launching Maple 11"
date: 2008-09-03
forum: Education &amp; Science
---

### Post by takkuso on 2008-09-03
I got maple 11 installed and running, but at the moment, I can only launch it using the terminal ->
export AWT_TOOLKIT=MToolkit && /home/tuck/maple11/bin/xmaple
 
Is there any way for me to create a shortcut in the pull down application menu? Or a shortcut on the desktop? (I'd rather have it in the menu, really)

P.S. I have only been using linux for a couple days, so please don't flame me, and I'd really appreciate a detailed answer if possible. Thank you very much.

---

### Post by kjohansen on 2008-09-03
you can make a desktop launcher.

right click on the desktop->create launcher.

then give the launcher a name, and paste the command that you listed in the command box. then click ok.

---

### Post by takkuso on 2008-09-03
"There was an error launching the appication.
Details:failed to execute child process "execute" (No such file or directory)"

Any tips?

---

### Post by takkuso on 2008-09-04
update:
When I put
alias xmaple='export AWT_TOOLKIT=MToolkit &&  /your_maple_install_location/maple11/bin/xmaple &'
into the terminal, I can merely type "xmaple" and maple 11 will run perfectly. However, only until I close the terminal. When I reopen it and try to execute xmaple, it responds with "bash: xmaple:command not found"

I'm wondering if I can make that alias stick, so I could at least have an easy way to run it. Best scenario would be for me to make a shortcut on desktop or in menu.

Thanks

---

### Post by stumbleUpon on 2008-09-04
> **takkuso said:**
> update:
When I put
alias xmaple='export AWT_TOOLKIT=MToolkit &&  /your_maple_install_location/maple11/bin/xmaple &'
into the terminal, I can merely type "xmaple" and maple 11 will run perfectly. However, only until I close the terminal. When I reopen it and try to execute xmaple, it responds with "bash: xmaple:command not found"

I'm wondering if I can make that alias stick, so I could at least have an easy way to run it. Best scenario would be for me to make a shortcut on desktop or in menu.

Thanks
Open in any editor the .bashrc file present in your home directory. Add the alias you want. The command will be recognized when you open a new terminal.

To make a desktop shortcut, see the earlier post by kjohansen.

To add an item an the menu, right click on Applications --> Edit menus --> Choose a submenu you want --> New item --> Paste the path to the executable you want in the command box --> Close.
This will give you a new item in the menu.

---

### Post by takkuso on 2008-09-04
Again, I appologize for my lack of basic knowledge.
I got the alias working perfectly, Thank you!
However, what would I type in the shortcuts to get them to launch properly? Just having "xmaple" in the command line doesn't work.

---

### Post by stumbleUpon on 2008-09-04
> **takkuso said:**
> Again, I appologize for my lack of basic knowledge.
I got the alias working perfectly, Thank you!
However, what would I type in the shortcuts to get them to launch properly? Just having "xmaple" in the command line doesn't work.
I would suggest splitting the earlier .bashrc entry in to two lines as
> 
export AWT_TOOLKIT=MToolkit 

alias xmaple='/your_maple_install_location/maple11/bin/xmaple'

This allows you to set the AWN_TOOLKIT separately from the alias to the xmaple executable.

To create a shortcut on your desktop
Right click on desktop --> Create Launcher --> Type Maple in the name box --> /your_maple_install_location/maple11/bin/xmaple in the comand box --> Choose an icon if you have/want --> Close

---

### Post by takkuso on 2008-09-04
This is really wierd. I did as you said, Stumble, and it launched from the desktop, but now gives a blank screen; even when running xmaple from the terminal.
[http://ubuntuforums.org/showthread.php?t=617730](http://ubuntuforums.org/showthread.php?t=617730)
Is basicly now what I'm ending up with.

---

### Post by stumbleUpon on 2008-09-04
I dont know about this. Try with the full thing in the comannd box and see

export AWT_TOOLKIT=MToolkit && /your_maple_install_location/maple11/bin/xmaple &

Are you using compiz...? If yes, try disabling that and see it maple works.
If this fails, then i dont know the reason. Sorry.

---

### Post by takkuso on 2008-09-04
"There was an error launching the application.
Details: Failed to execute child process "Export" (No such file or directory)"

I don't know what compiz is.. How would I check to see if I have it and disable it?

---

### Post by stumbleUpon on 2008-09-05
Are you getting a blank screen even when you have 

alias xmaple='export AWT_TOOLKIT=MToolkit && /your_maple_install_location/maple11/bin/xmaple &'

in the .bashrc file...?

You said earlier that it was working from the command line. Is that not fine enough?

Compiz is a compositing window manager [http://freedesktop.org/wiki/Software/Compiz](http://freedesktop.org/wiki/Software/Compiz).

To disable compiz, right click on desktop --> change desktop background --> go to visual effects tab --> see if either the normal or extra visual effects are enabled --> choose none to disable compiz --> close

---

### Post by baggins on 2008-09-09
> **takkuso said:**
> "There was an error launching the application.
Details: Failed to execute child process "Export" (No such file or directory)"
You use Export (starting with a capital) you need to use export (in all lowercase)
> 
I don't know what compiz is.. How would I check to see if I have it and disable it?
It's the nice desktop effects you get if you mark Extras in System -> Preferences -> Appearance -- Visual effects tab

-- Jon

---

### Post by relaxartwork on 2008-09-10
the problem with maple follows from the Java runtime environment wich is installd with maple.

you should delete it an install the JRE of sun again.> 

sudo mv /opt/maple/jre.IBM_INTEL_LINUX/bin/java /opt/maple/jre.IBM_INTEL_LINUX/bin/java.old
sudo ln -s  /usr/bin/java /opt/maple/jre.IBM_INTEL_LINUX/bin/java 

(replace 'opt' with the path, where maple is installes)

---

### Post by chnhonker on 2008-09-12
when you add the launch choose [COLOR="Red"]type[/COLOR] "application in terminal" instead of the default "application"

---

### Post by srekkas on 2009-11-12
I now that it is old post :)    
With  maple 12 you only need cretae launcher to "/home/yourname/maple12/bin/xmaple".
Maybe it be usefull for sameone.

---

