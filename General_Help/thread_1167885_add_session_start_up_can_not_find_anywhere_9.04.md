---
title: "add session start up: can not find anywhere: 9.04"
date: 2009-05-23
forum: General Help
---

### Post by equiplist on 2009-05-23
Hello, 

I want to add something to session start up, and I can not find it anywhere.  It is not in System/Preferences or System/Admin, and I can not find it in Synpatics Package Manager or Add/Remove Programs.  I am using Ubuntu v9.04 on an Acer Laptop that originally had Vista on it, the Ubuntu installation is relatively new.  Advice on this matter would be greatly appreciated.  

All the best, Barry, 
Equipment Recyclers "equiplist"

---

### Post by Legace on 2009-05-23
Do you mean **System/Preferences/Startup Applications**?
If you can't find it, right-click on "System", select Edit Menu and make sure the entry is selected.

Or execute the following in Terminal:
```
gnome-session-properties
```

---

### Post by equiplist on 2009-05-23
Hello Legace, thanks, very much, for the reply.  --> Is there a way to 'pre-start' Terminal with a specific command?

Legace: > Do you mean System/Preferences/Startup Applications?

Perhaps so, but I am not sure this is accomplishing the task at hand.  

Using Linux on this laptop has been cumbersome when I am portable and using the touchpad.  Personally, I do not like a touchpad.  I carry a 'mini-mouse', and use it whenever possible.  

When using the touchpad, the cursor would do funky things.  Online research pointed to 'syndaemon', which works correctly, it shuts down the touchpad during keystrokes, for a brief moment.  The default is 2 secs, I prefer 1 sec.  .

I just tried to find the online reference where I found syndaemon, but could not easily find it, did not want to run the search all over again.  As I recall, the info I found the first time, commented something to the effect of:

     'if you do not want to run this every time you boot up, use 'sessionstartup',  
     or something like that (System/Preferences or System/Admin ?).  

That is what prompted this posting.  When I try 'Startup Applications', and click 'Add', am then asked for a 'Command'.  I am not sure what that should be.  

Is there a way to pre-start Terminal with a specific command?  
Terminal:~$ syndaemon -d -i 1

All the best, Barry, 
Equipment Recyclers 'equiplist'

---

### Post by Legace on 2009-05-24
Just type **syndaemon -d -i 1** into the command box and you should be fine :)

---

### Post by equiplist on 2009-05-24
Hello Legace, 

> Just type syndaemon -d -i 1 into the command box and you should be fine

What I want is for it to load *automatically*, every time, at start-up.  

All the best, Barry

---

### Post by Legace on 2009-05-24
> **equiplist said:**
> Hello Legace, 

> Just type syndaemon -d -i 1 into the command box and you should be fine

What I want is for it to load *automatically*, every time, at start-up.  

All the best, Barry

Adding it to the startup applications and making sure that its checked should automatically start it every time.

-- ONLY DO FOLLOWING IF ABOVE DOESN'T WORK --

Remove the entry you put above from Startup Applcations.
Then open Terminal.
Type in:
```
sudo gedit /etc/gdm/PreSession/Default
```

and add the **syndaemon -d -i 1** following just before **exit 0** at the end..
So the END of the Default file should look like:
```
syndaemon -d -i 1
exit 0
```

Finally save and reboot.

---

### Post by equiplist on 2009-05-25
Hello Legace, 

> Just type syndaemon -d -i 1 into the command box and you should be fine

I misunderstood this instruction.  Perhaps I was reading it too fast.  I took it to mean type it into the terminal.  I just tried it, entering the command into the startup applications command box, and it works perfectly.  Thanks for the help.  

All the best, Barry, 
Equipment Recyclers, 'equiplist'

---

