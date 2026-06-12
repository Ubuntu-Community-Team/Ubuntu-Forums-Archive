---
title: "How can I use Enlightenment WM?"
date: 2004-11-28
forum: Desktop Environments
---

### Post by farmer on 2004-11-28
I want to try using Enlightenment as my WM, without removing Metacity. How can I do this?

---

### Post by jdodson on 2004-11-29
i believe you can just apt-get install it.  

```
sudo apt-get install enlightenment
```

---

### Post by farmer on 2004-11-29
OK, done that, but how do I start it when I log in?

---

### Post by siacs on 2004-11-29
I created a text file named Enlightenment.desktop with this info
and placed it in /usr/share/xsessions


[Desktop Entry]
Encoding=UTF-8
# Custom entry - YAY
Name=Enlightenment
Comment=Finally
Exec=/usr/bin/enlightenment
Icon=
Type=Application

And now it shows up under sessions at the login screen
Hope this helps

---

### Post by eventualbuddha on 2005-01-23
I tried running apt-get as described but it said 'Couldn't find package enlightenment'. I tried searching using apt-cache, but it listed nothing. I'm running Warty. Is it possible to run DR17 or is that too new too be useful?

---

### Post by shmonkey on 2005-01-23
enlightenment is in universe. Make sure you have this inluded in your sources - check /etc/apt/sources.list

---

### Post by wadcyr8_197 on 2005-01-26
Hi, 
I'm a new user of Ubuntu Hoary and I want to test Enlightenment 17 so I put [http://soulmachine.net/debian/](http://soulmachine.net/debian/) unstable/ in my source.list, then I installed it with

```
apt-get install enlightenment
``` 

after that I created the enlightenment.desktop like Siacs said.

I run it but apparently it is not the 17 but the 16.6 which run and moreover I haven't got the left-click menu so no term and no apply

can you help me ?
thanks

---

### Post by billessig on 2005-03-09
I get 
The following packages have unmet dependencies:
  enlightenment: Depends: libttf2 but it is not installable
E: Broken packages

When I try that.  I could use some help.  Thanks :D
-William

EDIT: Woops. Looks like I posted too soon. No help installing enviroments. Sorry 

 ](*,)

---

### Post by Qdlaty on 2005-03-10
Ok, 1st of all, you must decide which Enlightenment you want, E16 is quite usable and VERY comfortable and FAST while E17 is much faster and kinda eye-candy but it lacks of many features you used to use. I was using E17 for a long time and I'm back with 16. With no reason.
So, forget about official Ubuntu repository, add
[http://mirror.my-space.ath.cx/](http://mirror.my-space.ath.cx/) unstable
to your synaptic and get E16 and some other stuff you need. It's quite up-date build so you will be happy with it.

---

### Post by billessig on 2005-03-10
[QUOTE=Qdlaty]Ok, 1st of all, you must decide which Enlightenment you want, E16 is quite usable and VERY comfortable and FAST while E17 is much faster and kinda eye-candy but it lacks of many features you used to use. I was using E17 for a long time and I'm back with 16. With no reason.
So, forget about official Ubuntu repository, add
[http://mirror.my-space.ath.cx/](http://mirror.my-space.ath.cx/) unstable
to your synaptic and get E16 and some other stuff you need. It's quite up-date build so you will be happy with it.[/QUOTE]
 I keep getting a malformed sources.lst error in the gui and editing the file by hand isnt helping either...

EDIT: Kewl. It works now! Thanks!

EDIT2: Got e16, works, installed themes. YAY!, 

"If I had to procreate with a WM it would be e"
-Neil C.  from my LUG

---

### Post by flip on 2005-08-27
sorry, posted to wrong thread

---

