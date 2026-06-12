---
title: "Transparent panels"
date: 2009-08-02
forum: Desktop Environments
---

### Post by andrew_D14 on 2009-08-02
Hi, i downloaded this theme 
[http://gnome-look.org/content/show.php/XNTricity?content=78410](http://gnome-look.org/content/show.php/XNTricity?content=78410)

and when i apply it the panels aren't transparent 
they look like this

[http://i28.tinypic.com/9pxb3q.png](http://i28.tinypic.com/9pxb3q.png)

how do i get it to look like the first one so its transparent?
also, im aware if i go to properties it allows me to change the transparency but that doesnt work

---

### Post by Grishka on 2009-08-02
right click the panel, and check out the properties.

---

### Post by hyperAura on 2009-08-02
if this theme does not work for you, u can try out compiz-fusion.. i found it nice..:)

---

### Post by andrew_D14 on 2009-08-02
> **hyperAura said:**
> if this theme does not work for you, u can try out compiz-fusion.. i found it nice..:)

what? i am using compiz

---

### Post by Bigtime_Scrub on 2009-08-02
Right click on the panel

Properties -> Background -> Solid Color

Set style all the way over to transparent.

---

### Post by the hoplite on 2009-08-03
hi, I was trying too to have the same effect, I have everything working a part from the transparent window panels, as from the first screenshots. Been doing some googling but found nothing. Anybody?

---

### Post by the hoplite on 2009-08-03
found the solution!

Here:

[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=7724718](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=7724718)

---

### Post by hyperAura on 2009-08-03
i did it same way as Bigtime_Scrub.. works fine..

---

### Post by the hoplite on 2009-08-03
yes, it works fine for the main panel (the one with the menu and notification area), but I had trouble with transparent window borders, as from the screenshot. I solved it with the posted link...

---

### Post by andrew_D14 on 2009-08-03
> **the hoplite said:**
> found the solution!

Here:

[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=7724718](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=7724718)

what? all that does is take me to a reply to thread link

---

### Post by eamon63 on 2009-08-03
several ways to go about this.

1. if you want a plain/solid unthemed panel, do as Bigtime_Scrub, via panel properties.
2. if you want to retain themed panel but with some transparency, use compiz:
   -compizconfig settings manager> opacity, brightness and saturation (under accessibility) >opacity tab- window specific settings> click "new" button= create the following items

dock   (for panel, this is the one you want)
dropdownmenu   
popupmenu

set opacity for each (start at 85%...)

3. foe transparent window titlebars, type gconf-editor in terminal, then
apps> gwd> then play around with the settings, 1 = solid, 0.5 = 50% transparent

---

### Post by the hoplite on 2009-08-04
Yep. However the link was:

[http://ubuntuforums.org/showthread.php?t=645958&highlight=Transparency+Compiz](http://ubuntuforums.org/showthread.php?t=645958&highlight=Transparency+Compiz)

---

### Post by andrew_D14 on 2009-08-04
thanks eamon!

---

