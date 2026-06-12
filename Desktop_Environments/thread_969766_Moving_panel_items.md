---
title: "Moving panel items"
date: 2008-11-03
forum: Desktop Environments
---

### Post by karleberts on 2008-11-03
I recently upgraded my installation, and the items that I have on the xfce panel have moved around.  I used to have a full width panel with some stuff on one side, and some stuff on the other.  Now, however, all of the items have migrated to the left side, and I can not move them to the other side for some reason.  When I click on an item and select "move" I can move it amongst the other icons (i.e. change their order) but  I can't just drag it to any position I would like.  Is there some trick I am missing, because I know I had these icons in different positions before, but I can't remember how I got them there?

---

### Post by sisco311 on 2008-11-03
add a new *Separator* to the panel and tick the *Expand* option,

then try to move the items to the right side of the separator.

---

### Post by LaneLester on 2008-11-03
> **sisco311 said:**
> add a new *Separator* to the panel and tick the *Expand* option,

then try to move the items to the right side of the separator.
I can't find the Expand option. I've been using Xubuntu for a while, but I remember the Expand option when I ran Ubuntu Hardy. Can you tell me where it is?

Lane

---

### Post by Jose Catre-Vandis on 2008-11-04
Expand is an option in the dialog that pops up when you add the Separator :)

---

### Post by LaneLester on 2008-11-04
> **Jose Catre-Vandis said:**
> Expand is an option in the dialog that pops up when you add the Separator :)
Not in Intrepid. Expand is in the Panel Properties. Regretfully, it does nothing. The icons stay where you put them, even when you move them from left to right over the separator.

This worked fine in Hardy, so I know what it's supposed to do.

But thanks for the suggestions!

Lane

---

### Post by Jose Catre-Vandis on 2008-11-07
> **LaneLester said:**
> Not in Intrepid. Expand is in the Panel Properties. Regretfully, it does nothing. The icons stay where you put them, even when you move them from left to right over the separator.

This worked fine in Hardy, so I know what it's supposed to do.

But thanks for the suggestions!

Lane

Well I am confused now, because I believe I answered your query by testing it on a fresh install of xubuntu intrepid! I will check though....

[EDIT]
have checked and the dialog with the Expand option does come up when you add a Separator in Intrepid Ibex

---

### Post by LaneLester on 2008-11-07
> **Jose Catre-Vandis said:**
> have checked and the dialog with the Expand option does come up when you add a Separator in Intrepid Ibex
Thanks for checking! The only possible explanation I have for the difference we're seeing is that I'm using Ubuntu Intrepid instead of Xubuntu. When I select Separator and click Add, the separator is added without any additional dialog being displayed.

Lane

---

### Post by Jose Catre-Vandis on 2008-11-08
Ah, the OP's issue was with xubuntu, so it must be different in the standard version!

---

### Post by ts2000 on 2010-04-18
Thanks for the tip.  The icons on the right of my panel somehow shifted to the left.  I have toddlers who are great software testers by being able to randomly bang computer key sequences.  This thread was just what I needed to restore parental control in this house.

---

### Post by drreed on 2010-04-18
Well I guess you've right-clicked on your panel and played around with the settings correct? Choose fixed, full width.

I'm in the same boat with my workspace switcher. I messed the panel up and deleted it to try to work-around my problem. When I added it back, and tried to add my workspace switcher, it put it on the left instead of the right, and it won't stay put when i drag it.

If I figure it out, I'll come back here to help you.

If more help arrives, ask them how to find how an item is launched from the menu's. I want an xterm (and a coupl other items) on my panel, and I want to see how those are launched from the menu's. They need command line options. My xterm looks like crap, and I want it to look like the one that launches from the menu - black background , same fonts, menu, etc.

*** open customiz panel and click help! LOL It takes you to the Xfce guide, and it looks like everything we need might be in there ****

*** update ***
I found some more neat stuff for our panels

```

sudo apt-get install xfce4-goodies

sudo apt-get install xfce4-cddrive-plugin


```

I still haven't fixed my problem, but now I have a little more to work with

---

### Post by koeselitz on 2010-06-20
I had this problem, and thankfully I seem to have discovered the solution.

Please note that there are big differences between how this is handled on the Gnome (standard Ubuntu) desktop and how it works on the Xfce (Xubuntu) desktop - so you won't be able to use one solution for both. This solution only works on the Xubuntu desktop. Edit: Also, I am working with **Xubuntu 10.04 LTS**, aka "**Lucid Lynx.**" (I know this thread started ages ago, but there are recent replies, so I thought I'd put this here.)

By default, the objects on a panel float left; so all of them will end up in a clump on the left corner of the screen. To cause the object at the right end of this clump to float all the way over to the right corner of the screen, do this:

1. Right-click the panel in the blank space to the right of the clump of objects, and select "Add New Items..."

2. From the menu, select "Separator or Spacing," and click the "Add" button.

3. When the "Separator or Spacing" dialog box appears, select "Expanding empty space," and press the "Close" button.

4. Right-click that object at the right end of the clump, select "Move," and then move your mouse pointer over to the right corner of the screen (where you want to place the object) and click.

If you follow these steps, any object should move over to the right end of the screen and stay there, and all objects in the new clump should float right.

I should point out that there are four or five things wrong with this process, from an interface perspective; it's really not very intuitive. For one thing, this "expanding separator" isn't a very clear concept, and that isn't helped by the fact that the separator itself is actually invisible, so people hardly know when they've added one.

Anyway - hope this helps!

---

### Post by Rabreu on 2012-10-20
Thanks!

> **koeselitz said:**
> I had this problem, and thankfully I seem to have discovered the solution.

Please note that there are big differences between how this is handled on the Gnome (standard Ubuntu) desktop and how it works on the Xfce (Xubuntu) desktop - so you won't be able to use one solution for both. This solution only works on the Xubuntu desktop. Edit: Also, I am working with **Xubuntu 10.04 LTS**, aka "**Lucid Lynx.**" (I know this thread started ages ago, but there are recent replies, so I thought I'd put this here.)

By default, the objects on a panel float left; so all of them will end up in a clump on the left corner of the screen. To cause the object at the right end of this clump to float all the way over to the right corner of the screen, do this:

1. Right-click the panel in the blank space to the right of the clump of objects, and select "Add New Items..."

2. From the menu, select "Separator or Spacing," and click the "Add" button.

3. When the "Separator or Spacing" dialog box appears, select "Expanding empty space," and press the "Close" button.

4. Right-click that object at the right end of the clump, select "Move," and then move your mouse pointer over to the right corner of the screen (where you want to place the object) and click.

If you follow these steps, any object should move over to the right end of the screen and stay there, and all objects in the new clump should float right.

I should point out that there are four or five things wrong with this process, from an interface perspective; it's really not very intuitive. For one thing, this "expanding separator" isn't a very clear concept, and that isn't helped by the fact that the separator itself is actually invisible, so people hardly know when they've added one.

Anyway - hope this helps!

---

