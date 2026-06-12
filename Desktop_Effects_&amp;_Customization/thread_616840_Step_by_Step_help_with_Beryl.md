---
title: "Step by Step help with Beryl?"
date: 2007-11-18
forum: Desktop Effects &amp; Customization
---

### Post by RadiationHazard on 2007-11-18
Alright. I just go Linux to day. And i really wanna use Beryl to make my linux look like the ones you see when you look on youtube.com if you can help please private massage me with you AIM screen name. :confused:

---

### Post by schauerlich on 2007-11-18
7.10 already comes with something similar to Beryl called Compiz-Fusion. Unless you're dead set on having Beryl, you can get the eye candy you want from compiz. To download the program to set it up, go to a terminal (Applications>Accessories>Terminal) and run this command:

```
sudo apt-get install compizconfig-settings-manager
```

It will prompt you for a password. Use the same one you log in with. It won't show any stars, but it's still accepting your password.

---

### Post by overdrank on 2007-11-18
> **RadiationHazard said:**
> Alright. I just go Linux to day. And i really wanna use Beryl to make my linux look like the ones you see when you look on youtube.com if you can help please private massage me with you AIM screen name. :confused:

HI and welcome, Beryl has joined with compiz and made compiz-fusion. If you can tell us what version of ubuntu you are using ( feisty, gutsy) and the type of graphics card your system is using we maybe able to help. To find your graphics card you can use the command ```
lspci
```
and post the results here and we can help. The terminal is located under applications, accessories.

---

### Post by RadiationHazard on 2007-11-21
Ok i have the cube effect using compiz and now like i don't know i was messing with it and now the only way i can go from like the different desk tops is if i hit ctrl+alt+left mouse button. Why can't i scroll between them anymore?? :confused:

---

### Post by overdrank on 2007-11-21
> **RadiationHazard said:**
> Ok i have the cube effect using compiz and now like i don't know i was messing with it and now the only way i can go from like the different desk tops is if i hit ctrl+alt+left mouse button. Why can't i scroll between them anymore?? :confused:

HI just go back to advance desktop settings and rotate cube and along the right side you will see a little broom, click it and it will rest that command back to default. :)

---

### Post by duruttye on 2007-11-21
You probably messed up your action keys and buttons.
In ccsm go to rotate cube, then at actions you should reset it.
I will try to attach you a screenshot for you to see how it is in my setting. I didn't change too much.
Next time, in preferences make a new profile, so you can set everything back to defaults, or even make a new profile.

Hope it helps, take care!

---

### Post by RadiationHazard on 2007-11-21
that still doesn't fix it...any other ideas??

---

### Post by Inxsible on 2007-11-21
look for "Switch Viewport on Mouse" or something like that in CCSM and enable it.

I am sorry I don't remember the exact plugin name. (I am at work on a XP machine) :(

---

### Post by RadiationHazard on 2007-11-21
i searched that name...nothing came up. :confused:

---

### Post by Inxsible on 2007-11-21
> **RadiationHazard said:**
> nothing came up. :confused:you mean you used the search function? I told you I wasn't a 100 % on the name. But it definitely has Switch Viewport in the name of the plugin.

---

### Post by RadiationHazard on 2007-11-21
you sure you're a hundred percent? because there is still nothing coming up! :P

---

### Post by smartalecks on 2007-11-21
> **RadiationHazard said:**
> you sure you're a hundred percent? because there is still nothing coming up! :P

He said he _wasn't_ 100% sure, try searching keywords
have you tried simply logging out and back in, it may just be some glitch

---

### Post by Inxsible on 2007-11-21
> **RadiationHazard said:**
> you sure you're a hundred percent? because there is still nothing coming up! :PI said I ***wasn't  ***100 %. Well I will just have to look it up tonight, once I reach home.

Sorry.

---

### Post by RadiationHazard on 2007-11-21
haha. i hope you're not getting mad? i'm not upset it's fine i can deal with it til i find a solution

---

### Post by RadiationHazard on 2007-11-22
Ok attached the two special effects that i want but can't figure out how to get. I'm running compiz. Can I do those effects on compiz? (the first one is like when you close the pages and it like dissolves and the second one is where you like pull back the page for the corners)

---

### Post by Arthur Archnix on 2007-11-22
You need to install compizconfig-settings-manager. You can find it in synaptic if you search for "compiz". Or, in a terminal paste this:
```
sudo apt-get update && sudo apt-get install compizconfig-settings-manager
```
The things you want to enable can be found in the settings manager. You'll find it in one of your menus, maybe preferences, or by hitting Alt+F2 and entering compizconfig-settings-manager

---

### Post by por100pre1 on 2007-11-22
Be sure you have Compiz Config Settings Manager:

```
sudo aptitude install compizconfig-settings-manager
```


Open it and Click **Animations**.

Under the **Close Animation Tab** in the **Animation Selection** list double click **Glide 2** to edit it and change it to** Burn**.

Under the **Effect Settings** tab, change **Fire Particle Color** to white and **Fire direction** to **Up**.

---

### Post by RadiationHazard on 2007-11-22
alright thanks alot man! i'll private message you for one last question :)

---

### Post by Arthur Archnix on 2007-11-22
Post your questions in the forum so all can benefit from your experience.

---

### Post by RadiationHazard on 2007-11-22
Ok how do i do the thing where i pull the screen down for the corners and stuff? Do you know what i'm talking about?

---

### Post by santiagoward2000 on 2007-11-22
> **por100pre1 said:**
> Under the **Effect Settings** tab, change **Fire Particle Color** to white and **Fire direction** to **Up**.

That's right, except that the color is actually random. Just check the **Randomly Colored Fire** option in Animations/Effect Settings/Fire.

---

### Post by por100pre1 on 2007-11-22
> **RadiationHazard said:**
> Ok how do i do the thing where i pull the screen down for the corners and stuff? Do you know what i'm talking about?

I'm not sure what you mean there. Can you post a link to the video you saw? :-k

> **santiagoward2000 said:**
> That's right, except that the color is actually random. Jusr check the **Randomly Colored Fire** option in Animations/Effect Settings/Fire.

Can you describe how to do that other effect? I'm gonna be busy [eating a turkey]("http://en.wikipedia.org/wiki/Thanksgiving_(United_States)"). ;)

---

### Post by RadiationHazard on 2007-11-22
[http://www.youtube.com/watch?v=lawkc3jH3ws](http://www.youtube.com/watch?v=lawkc3jH3ws) (he starts doing what i'm talking about in 21 seconds.)

---

### Post by overdrank on 2007-11-22
> **RadiationHazard said:**
> [http://www.youtube.com/watch?v=lawkc3jH3ws](http://www.youtube.com/watch?v=lawkc3jH3ws) (he starts doing what i'm talking about in 21 seconds.)

Hi just maximize your window and then pull on the corner with your mouse. :)

---

### Post by RadiationHazard on 2007-11-22
oh wow. thanks for making me feel retarded!! haha but thanks buddy i'm all good now. :)

---

### Post by santiagoward2000 on 2007-11-22
> **por100pre1 said:**
> Can you describe how to do that other effect? I'm gonna be busy [eating a turkey]("http://en.wikipedia.org/wiki/Thanksgiving_(United_States)"). ;)

Sure, just open CCSM, go to **Animations**, then, under the **Effect Settings** tab, scroll down until you see a **Fire** dropdown menu and chek the box besides **Randomly Colored Fire**.

_EDIT:_
How's that turkey? :D

---

### Post by overdrank on 2007-11-22
> **RadiationHazard said:**
> oh wow. thanks for making me feel retarded!! haha but thanks buddy i'm all good now. :)

HI and the intent was not meant to make you feel anyway. Just giving you the instructions that you requested. :)

Please mark as solved under the thread tools thanks.

---

### Post by por100pre1 on 2007-11-22
> **overdrank said:**
> HI and the intent was not meant to make you feel anyway. Just giving you the instructions that you requested. :)
Please mark as solved under the thread tools thanks.

**RadiationHazard**, yes, that's **Wobbly Windows**. You may want to tweak it some more. Sorry for the delay!

> **santiagoward2000 said:**
> How's that turkey? :D

The roasted turkey stuffed with ripe [plantains]("http://en.wikipedia.org/wiki/Plantain") was good! :)

---

### Post by santiagoward2000 on 2007-11-22
> **por100pre1 said:**
> The roasted turkey stuffed with ripe [plantains]("http://en.wikipedia.org/wiki/Plantain") was good! :)

:D It's good to hear! I didn't know you could actually stuff a turkey with bananas... I just learnt something new thanks to Ubuntu! :)

---

### Post by por100pre1 on 2007-11-22
> **santiagoward2000 said:**
> :D It's good to hear! I didn't know you could actually stuff a turkey with bananas... I just learnt something new thanks to Ubuntu! :)

This year my wife prepared it that way. You got to eat turkey stuffed with [Mofongo]("http://en.wikipedia.org/wiki/Cuisine_of_Puerto_Rico"), that's second to none! :D Just be aware that plantains are not exactly bananas, even if they look alike! :)

BTW, Happy Thanksgiving Day to everybody in the US!

---

