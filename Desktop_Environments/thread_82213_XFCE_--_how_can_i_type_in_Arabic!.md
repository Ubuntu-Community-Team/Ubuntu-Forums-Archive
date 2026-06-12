---
title: "XFCE -- how can i type in Arabic?!"
date: 2005-10-26
forum: Desktop Environments
---

### Post by majed on 2005-10-26
Hi guys..

I thought i'll give XFCE a try since my dear laptop is only running with 256mb ram.. and i have to say that i was AMAZED by how slick and fast XFCE is!!! Unfortunately, I can't figure out how to type Arabic?! It was easy to install a keyboard layout and use it in GNOME, but I can't figure a way to do this in XFCE :(

I can read Arabic, fonts are there and all.. but I can't "input"...

Did a little research and found about this SCIM project.. however, it did't work will for me.. i don't know what I'm doing wrong.. I installed it and installed the Arabic table but when I click on the little keyboard to change the language, nothing appears to be there.. so frustrating..

Now seeing how fast XFCE is on my laptop, i want to use it.. but i also need to type in Arabic.. Any idea?

I am also open to any other suggestion of a fast and good enough alternative window/desktop manager that would support Arabic input more easily if it would be so hard in XFCE..

*fingers crossed*

---

### Post by majed on 2005-10-26
For all who might get in the same situation i was in, here is the solution i found and worked just fine :)

i found it @ [http://www.linuxquestions.org/questions/showthread.php?threadid=370857]("http://www.linuxquestions.org/questions/showthread.php?threadid=370857")

Summary:
-------------

just run this line and then you can switch input language by pressing both shift keys:

```
setxkbmap -option grp:switch,grp:shift_toggle,grp_led:scroll us,ar
```

PS: this can be used to switch between any two languages (after the word "scroll") in this case, us (English) and ar (Arabic).

Now i can enjoy fast and slick XFCE and use my native language too :)

Enjoy!

---

### Post by matthew on 2005-10-26
shokran!

That was very helpful.

---

### Post by majed on 2005-10-26
Aafwan, Mat :)

And if this might also help, to make sure the language switching will work everytime you login without running the command manually everytime, just add it to a script in ~/Desktop/Autostart/

Here you go:

```
mkdir -p ~/Desktop/Autostar

gedit startup
```

Then paste the following:

```
#!/bin/bash
setxkbmap -option grp:switch,grp:shift_toggle,grp_led:scroll us,ar &
```

save, and close the editor.. then make the script executable:

```
chmod a+x startup
```

Done!

Any executable scripts in ~/Desktop/Autostart/ will be run automatically everytime you start an XFCE session.. *hint: i also start firestarter here*

---

### Post by Mankdim on 2006-01-09
[B]Thank you very much Majed.
I was looking for this problem, when I have seen your subject.
thank you Again.[/B]

:smile:

---

### Post by Mankdim on 2006-01-09
[B]Thank you very much Majed.
I was looking for this problem, when I have seen your subject.
thank you again.
:smile: 

/Abdellah Fayea/[/B]

---

### Post by mcman42 on 2006-06-21
```
setxkbmap -option grp:switch,grp:shift_toggle,grp_led:scroll us,ar
```

Good job, mate! What if I want to use ctrl+ shift instead of double shift? Should I type "grp:shift, ctrl" instead of "grp:shift_toggle" :confused: ? And if I get you right this will also work for 3 languages, I only have to put another comma in the end (f.e.: us,ru,ee)?

Thank you.

---

### Post by majed on 2006-06-22
[QUOTE=mcman42]```
setxkbmap -option grp:switch,grp:shift_toggle,grp_led:scroll us,ar
```

Good job, mate! What if I want to use ctrl+ shift instead of double shift? Should I type "grp:shift, ctrl" instead of "grp:shift_toggle" :confused: ? And if I get you right this will also work for 3 languages, I only have to put another comma in the end (f.e.: us,ru,ee)?

Thank you.[/QUOTE]

hi,

I'm glad you find this useful for you :)

You can use ctrl_shift_toggle or alt_shift_toggle for CTRL+SHIFT or ALT+SHIFT to toggle between languages..

For having more than 2 languages, I believe it should work, however, it doesn't work with me when I add a 3rd language but that could be something with my setup..

According to the links below, more than 2 languages should work as well. Good luck!

[http://ubuntuforums.org/showthread.php?t=98233](http://ubuntuforums.org/showthread.php?t=98233)
[http://www.knowprose.com/node/2394](http://www.knowprose.com/node/2394)

majed

---

### Post by mcman42 on 2006-06-24
Thanks, Majed.
The "ctrl_shift_toggle" thing works wonderfully. By the way the instructions you posted DO work with more than 2 languages. To get this to work right you just have to add the languages first, to do this follow the guide posted [HERE]("http://ubuntuforums.org/showthread.php?t=66115").

---

### Post by basilwatson on 2006-08-01
Hi folks 
Well it sort of changes languages, I cut and pasted the command line as per arabic and changed the ar to jp, and the little flag up on the tool bar is Japanese 

As of yet. I cant find the key combination to swap between languages  shift shift  ctrl,space etc,   I can swap if I click on the icon and go properties ( there are 2 in the text dialogue box jp and jp one is english the other is Japanese ) 

Sooo Nearly there ! 

Any ideas 

Stephen
Sorry wrong forum , Ill repost in beginners Sorry #-o

---

