---
title: "python file qutestion"
date: 2009-06-03
forum: General Help
---

### Post by The-ITu on 2009-06-03
how do make so that instead of having to open the terminal CD to where the file then type "python filename.py" I want to know how to make it open python file aromaticity after i double click on them. 

Thanks
The-ITu

---

### Post by The-ITu on 2009-06-03
I can't deleted this post so I wont.
il just edit it.

---

### Post by ad_267 on 2009-06-03
Haha geez patient much?

Is this a graphical application? Or a command line application?

Add this as the first line of your python script:
#!/usr/bin/env python

Then make your python script executable with "chmod a+x filename.py" or by right clicking in the file browser and editing its properties. Then you can just double click to execute it.

---

### Post by NFblaze on 2009-06-03
Here check this thread out... I asked something similar yesterday

[http://ubuntuforums.org/showthread.php?t=1175466](http://ubuntuforums.org/showthread.php?t=1175466)

aight, peace.

---

### Post by The-ITu on 2009-06-03
> **NFblaze said:**
> Here check this thread out... I asked something similar yesterday

[http://ubuntuforums.org/showthread.php?t=1175466](http://ubuntuforums.org/showthread.php?t=1175466)

aight, peace.
not exactly.
i want it to execute it when I double click on it rather than having to type in that command every time i qant to execute a python file.
thanks for trying tho.

---

### Post by The-ITu on 2009-06-03
> **ad_267 said:**
> Haha geez patient much?

Is this a graphical application? Or a command line application?

Add this as the first line of your python script:
#!/usr/bin/env python

Then make your python script executable with "chmod a+x filename.py" or by right clicking in the file browser and editing its properties. Then you can just double click to execute it.
dietn help anything.
im not having troubles with permissions, I am the superuser.
read my post above.
thanks anyway.

---

### Post by ad_267 on 2009-06-03
> **The-ITu said:**
> dietn help anything.
im not having troubles with permissions, I am the superuser.
read my post above.
thanks anyway.

It doesn't matter if you're the superuser. Root can't execute a file that isn't executable. 

Help us help you or we won't bother, how did it not help? Why didn't it work?

---

### Post by sehe on 2009-06-03
Also, don't forget you can create launchers to include just about any startup option you require. From then it's just a single or double click (epending on your settings) to launch from the icon.

In gnome: right-click on desktop (or panels) and 'Create Launcher...'

---

### Post by NFblaze on 2009-06-03
Yes, my scripts are executable by double-clicking. 

Did you read in the thread where you have to make the script executable by using "chmod a+x" (or opening the file permission via GUI and editing it).

Also, like ad_267 stated **#!/usr/bin/env/python** must be the first thing in the script.

Can you maybe show us your script, output of the permissions on the script.

---

### Post by The-ITu on 2009-06-04
> **ad_267 said:**
> It doesn't matter if you're the superuser. Root can't execute a file that isn't executable. 

Help us help you or we won't bother, how did it not help? Why didn't it work?
sorry its just I thought I made my self clear. 
what chmod a+x filename.py did was:
when I clickon the file it gave me some optopn of what i wanted to do and I pressed run in terminal.
then the mouse pointer tuned into a cross and then I draged a square around an aria and a new file in that folder can up named OS and it was a picture of what I had selected in that square. this was extremely weird because that's absolutely not what the file was supposed to do. 
then: after i added **#!/usr/bin/env/python** to the top of my script, it did nothing after I pressed run in terminal.

and P.S I don;t mind if no one helps me.
no one here ows me anything nor I you guys.
im just a school boy who is tired of seeing "(not responding)" on my screen.

---

### Post by benj1 on 2009-06-04
open up a nautilus window, go edit-->preferences-->behaviour

and make sure 'run executable files when they are opened' is selected.

---

### Post by ad_267 on 2009-06-04
> #!/usr/bin/env/python
That should be "#!/usr/bin/env python"

---

### Post by The-ITu on 2009-06-04
> **ad_267 said:**
> That should be "#!/usr/bin/env python"
works.
that you very much!!

---

