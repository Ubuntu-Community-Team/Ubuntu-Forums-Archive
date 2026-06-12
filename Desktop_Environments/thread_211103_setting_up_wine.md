---
title: "setting up wine"
date: 2006-07-07
forum: Desktop Environments
---

### Post by Orion2014 on 2006-07-07
Ive installed wine through the package manager, real easy, now i  need to set  it up. I tried running wine through the terminal, but it gives me this screen every time....

[IMG]http://i32.photobucket.com/albums/d31/zebcarlson/Screenshot.png[/IMG]

Can you tell me what to do, as im rather stuck and i really want to get this to work.

---

### Post by aysiu on 2006-07-07
Read this:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by Iarwain ben-adar on 2006-07-07
:D

You do know why you use Wine?

Because you just gave Wine the order to load "program.exe" :D

Normally you'd type ```
wine nameofprogram.exe
```
if you're in the dir where the exe is.

Otherwise, you'd type
```
wine /path/to/program/nameofprogram.exe
```


Iarwain

---

### Post by Orion2014 on 2006-07-07
ok, i think i got it now, thx. i will post again if i have any trouble.

---

### Post by Orion2014 on 2006-07-07
ok, i was able to get it to install my software, now what do i do to run it?

---

### Post by aysiu on 2006-07-07
Same thing.

Now that your software is installed to /home/orion/.wine/drive_c/Program Files/programname, you run it with: ```
wine "z:\home\orion\.wine\drive_c\Program Files\programname\programname.exe"
```

---

### Post by Thund3rstruck on 2006-07-07
follow the same logic as the install. Navigate to /home/yourUsername/.wine/c/progra~1/yourProgram/

and run
```

wine YourProgram.exe

```

If you use the program often then you should create a quick launch link, a symbolic link, or a simple sh script to quickly launch your application under wine

---

### Post by Orion2014 on 2006-07-07
ok, i think there is still a problem as that file dosent exist, there is no .wine folder in my zeb folder (zeb is my first name) however, it acted like it installed my software, thats wierd.

---

### Post by aysiu on 2006-07-07
.wine is a hidden folder.

---

### Post by bukwirm on 2006-07-07
Type 'ls -a' in yuo home directory and look for .wine.

Any file whose name begins with a '.' is hidden and does not show up normally.

---

### Post by Thund3rstruck on 2006-07-07
open the terminal and type
```

ls -a

```

and you should see your .wine folder. In Nautilus hit CTRL+H or view "Show Hidden Files" to expose the .wine folder. 

In Linux/Unix the period file prefix "." annotates a hidden file

---

### Post by Orion2014 on 2006-07-07
ok i found it but i cant seem to get it to run still, dosent want to run.](*,)

---

### Post by aysiu on 2006-07-08
> **Orion2014 said:**
> ok i found it but i cant seem to get it to run still, dosent want to run.](*,)
Error messages are more helpful than "doesn't want to run."

---

### Post by Orion2014 on 2006-07-08
i keep getting a could not load module, module not found error. and i can even click on the .exe and i have the .exe set up to run automatically in wine and it still dosent do anything.

---

### Post by benmoreassynt on 2006-07-08
> **Orion2014 said:**
> i keep getting a could not load module, module not found error. and i can even click on the .exe and i have the .exe set up to run automatically in wine and it still dosent do anything.

You may need to check the Wine website ([www.winehq.com](www.winehq.com)) to see if the program you want to use works with Wine - not all do, and many work badly, which is why it is usually better to try and use an alternative designed for Linux. If you are trying to run something like MS Word or Photoshop then you'd be much better off using Open Office or the Gimp (apologies in advance if that is not the case).

If the command
wine "/path/to/winprog/program.exe" is not working then it suggests the program in question may not work with wine. It sounds like a Windows module is missing (something like a .dll file maybe). Depending on how much you want to tinker you may be able to find the file in question on your Windows computer and copy it into the corresponding place in your .wine directory.

wine is really not very 'newbie friendly'. It took me ages to work this stuff out, as the wine website does not seem to mention anything as simple as 'how to run a program' or 'how to install'.

There are graphical installers you can use too, but they are almost equally confusing. Do a search in synaptic.

---

### Post by Orion2014 on 2006-07-08
yeah, the software im attempting to run DOES in fact work in wine, 

look here...

[http://appdb.winehq.org/appview.php?iVersionId=4154](http://appdb.winehq.org/appview.php?iVersionId=4154)

it even won the silver and gold award, and it installs fine, but i cant seem to get it to run once its installed. i also have copied over some of my .dlls from my windows xp partition like instructed on the wine site, but still no success.

---

### Post by benmoreassynt on 2006-07-08
> **Orion2014 said:**
>  i also have copied over some of my .dlls from my windows xp partition like instructed on the wine site, but still no success.

Did you edit the path like it mentions on that site (at the top of the page) so that wine can find the .dll files?

The only thing I can think of is that it may not be finding the ones you copied over.

Good luck!

---

