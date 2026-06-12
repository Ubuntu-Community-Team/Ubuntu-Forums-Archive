---
title: "Cannot Login"
date: 2012-08-04
forum: Desktop Environments
---

### Post by cosmarchy on 2012-08-04
Great....I cannot log in.
 
Until about an hour ago, I was using kubuntu desktop but then the problems started. I rebooted and tried to log in. I typed the correct password and then I got a black screen and then it returned me to the login screen again. Ummmm, I thought. So I tried again, and again, and again.....
 
Every time I get the same thing - a black screen and then it returns me to the login screen.
 
Can anyone please point me in the right direction to solving this?
 
Thanks

---

### Post by steeldriver on 2012-08-04
can you log in at one of the virtual terminals (Ctrl-Alt-F1 etc.)? if so, do that then check the ownership of your .Xauthority / .ICEauthority files:

```
ls -l ~/.{X,ICE}authority
```

---

### Post by cosmarchy on 2012-08-04
> **steeldriver said:**
> can you log in at one of the virtual terminals (Ctrl-Alt-F1 etc.)? if so, do that then check the ownership of your .Xauthority / .ICEauthority files:
 
```
ls -l ~/.{X,ICE}authority
```
 
The result is 
 
> 
ls:cannot access /home/user/_Xauthority: No such file or directory
ls:cannot access /home/user/_ICEauthority: No such file or directory

 
Thanks

---

### Post by cosmarchy on 2012-08-04
Interestingly enough it lets me login as a guest but not as the usual account I was using.

---

### Post by steeldriver on 2012-08-04
the first character should be a dot not an underscore

twiddle slash DOT Xauthority

---

### Post by cosmarchy on 2012-08-05
> **steeldriver said:**
> the first character should be a dot not an underscore
 
twiddle slash DOT Xauthority
 
 
Oh dear :( What do I do now then? :confused:

---

### Post by steeldriver on 2012-08-05
if your .Xauthority file has become root-owned you can just delete it 

```
sudo rm /home/*yourusername*/.Xauthority
```once you've done that, try again logging in at the GUI

---

### Post by cosmarchy on 2012-08-06
> **steeldriver said:**
> if your .Xauthority file has become root-owned you can just delete it 
 
```
sudo rm /home/*yourusername*/.Xauthority
```once you've done that, try again logging in at the GUI
 
this didn't do anything as I still had the same problem when I tried to log in.  So I thought what the hell and tried ```
sudo rm /home/*yourusername*/.ICEauthority
``` instead; now i'm back in :D
 
I am curious however, being a linux numpty and all, but when I do a ls on the ```
/home/*yourusername*/
``` directory, I cannot see .Xauthority or .ICEauthority...why?
 
thanks for your help

---

### Post by steeldriver on 2012-08-06
files starting with a '.' character are hidden - you need to use 'ls -a' ('all') or 'ls -al' ("all, long") to see them using 'ls'

---

