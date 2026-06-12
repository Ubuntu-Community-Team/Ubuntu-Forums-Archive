---
title: "Alacarte Applications can not be restored due to NULL value."
date: 2006-06-19
forum: Desktop Environments
---

### Post by I_Like_Pie on 2006-06-19
[SIZE=3][FONT=Times New Roman]**Alacarte Applications can not be restored due to NULL value**[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=2]I hope that this will be a simple fix![/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]-----------------------------------------[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]I was customizing my application menus via Alacarte and I accidentally re-named my Multimedia (Sound & Video) folder as a 'null' value...I hit escape with nothing listen in the name field and it saved a blank name there. [/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3]By doing this I can no longer access my Multimedia programs from the Applications bar. I go to Add/Remove programs and I can see the 'null' with all of my programs in it, but I can no longer select, or even see, it in the Alacarte menu or the Applications Launcher.[/SIZE][/FONT]
 
 
[SIZE=3][FONT=Times New Roman]I read where there were some menu bugs somewhere along these lines, but I am pretty sure that all I need to do it simply populate the ‘null’ with a name so that the Alacarte GUI will pick it up. It seems like it is programmed to ignore ‘null’ values.[/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3]Does anyone know where I go to replace the 'null' value with a name so that I can actually launch my multimedia files from the application bar again? -OR- How can I get back to the default menus you get after installing Ubuntu?

[IMG]http://www.geocities.com/matthew_craigge/Website_Pictures/Screenshot.png[/IMG]


[/SIZE][/FONT]

---

### Post by I_Like_Pie on 2006-08-02
I am very suprized to see that nobody has had this issue!  It still plagues me to this day.  Every now and then I see that there are python, gnome and other updates so I decided  to try and reset to default...nothing.  I tried to see if it was unique to "Sound and video" Nope...alacarte is just broken for me and reinstalling is doesn't do anything to help me return to defaule.

This is a HUGE bug that has really hurt the "synergy" that integrating and using alacarte in Ubuntu is supposed to provide.  

I don't even know where to start to fix this...try it and you will see what I mean
1 - open up alacarte
2 - Go to preferences in...say office tools.
3 - Delete the name field
4 -  Close it

Now try and find a way to bring it back NOTHING SEEMS TO WORK...stumped.  This is a problem because adding new programs automatically adds to the default menu, but now that the default menu is gone and you have to make a manual one it is considerably harder to keep all of your programs in check.

Someone please help...Please ](*,)

---

### Post by Amaranth on 2006-08-02
```
rm ~/.local/share/desktop-directories/Multimedia.directory
```

---

### Post by Tomosaur on 2006-08-02
Not sure if this will help, but have a look at the following file:

~/.gconf/apps/gnome-settings/alacarte/%gconf.xml

It seems to hold information about the menus.

---

### Post by I_Like_Pie on 2006-08-02
That actually did the trick!!!

By deleting the .local/share/desktop-directories file it flipped back to default

You made my day...I don't know how I ever would have figured that out on my own.  I know that you are quite a distance from Chattanooga, but if you deserve a free lunch.  Thank you sir.

---

