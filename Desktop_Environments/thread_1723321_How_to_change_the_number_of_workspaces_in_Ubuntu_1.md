---
title: "How to change the number of workspaces in Ubuntu 11.04"
date: 2011-04-06
forum: Desktop Environments
---

### Post by BlairKatu on 2011-04-06
In Unity, the default windows manager in Ubuntu 11.04, there is no obvious way to change the number of available workspaces/virtual desktops so I had to dig to find a way to do it. Here it is:
1. Go to the power icon in the top right hand corner and select it.
2. Press 'Systems Settings'
3. In the Systems Settings go to Compiz Config Settings Manager
4. In the Compiz Config Menu select 'General Options'
5. Go to the 'Desktop Size' and change your desktop settings by adjusting the number of vertical desktops.

That's it! Good luck and post if you have any questions. 
Also if any one wants to add an easier way to change the number of workspaces the time to do it is now while 11.04 is still in beta.

---

### Post by birdsarah on 2011-04-08
Hi,

I have the same problem. Thanks for your help.

In my case, when I went to System Setting CompizConfig Settings Manager wasn't there. 

I installed it. I also had to set "Horizontal Virtual Size" and "Vertical Virtual Size" to 1.

Thanks!

---

### Post by destructaball on 2011-06-15
I don't know if anyone has already suggested this but using the pop out player and pressing F11 works for me

---

### Post by klisanor on 2011-09-19
1) Hit F2 and type gconf-editor
2) Navigate to apps > compiz-1 > general > screen0 > options
3) Update the number of workspaces by changing the values of the variables hsize and vsize, which represent the horizontal and vertical number of workspaces respectively

---

### Post by gianninardoia on 2011-09-24
hello,
my problem is that it is impossible to drag the workspace icon towards the top. 
Do you have a suggestion?

gianni

---

### Post by StefanT on 2012-03-16
For Unity 2D I did the following:

1) Hit F2 and type gconf-editor
2) Navigate to apps > metacity > general > compositor_effects
3) Set the number of workspaces in num_workspaces

---

