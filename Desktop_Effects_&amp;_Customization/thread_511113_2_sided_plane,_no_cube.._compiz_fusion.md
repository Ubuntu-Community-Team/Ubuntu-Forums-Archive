---
title: "2 sided plane, no cube.. compiz fusion"
date: 2007-07-27
forum: Desktop Effects &amp; Customization
---

### Post by JZeFF on 2007-07-27
just got compiz fusion installed, when i press alt+ctrl+mouse1 i can rotate between my desktops but there is only 2, it is a 2 sided plane, not even a cube.  However in the bottom right of my screen there is 4 desktops, but they dont have a cube either.

In the compizconfig settings manger i went to general options and set number of desktops to 4, and horizontal and vertical to 2, made sure that cube effects were enabled, made sure rotate cube was enabled... now im just kind of confused

What do i need to do?

EDIT: I got the cube working when pressing alt+ctrl+mouse1, (i set horizontal to 4, and vertical to one) but when i actually click on the desktops in the bottom right, i see no cube effects.

---

### Post by synthaxx on 2007-07-27
You probably have the wrong setting ("number of desktops" instead of "Horizontal Virtual Size")

Go to the CompizConfig Settings Manager, Go to "General" and check the tab "Desktop size".
Set the "Number of Desktops" to 1 and the "Horizontal Virtual Size" to 4.

Hope that helps.

---

### Post by era86 on 2007-07-27
I was having the same issue.  The above solution fixed it. Thanks!

---

### Post by mooter on 2007-08-02
My problem is that the Horizontal Desktop text is in blue instead of black and it always reverts to 2....I though removing Emerald would help but nope....

Ok...well...right after I posted it's working....strange....let's see if it works with Emerald....

---

### Post by thinsoldier on 2007-10-24
> **synthaxx said:**
> You probably have the wrong setting ("number of desktops" instead of "Horizontal Virtual Size")

Go to the CompizConfig Settings Manager, Go to "General" and check the tab "Desktop size".
Set the "Number of Desktops" to 1 and the "Horizontal Virtual Size" to 4.

Hope that helps.

lol!
What I'd like to know is how in the hell they expected anyone to ever figure that out?
Why isn't it just called 'cube sides' or something easy to find. And no, it's tooltip doesn't help.

Vertical virtual size seems to have no effect. What is that supposed to do?

I want to change a shortcut to Super+something but i get a system beep when I press the Super(windows) key. How do you assign a key combo using super?

---

### Post by Tanker Bob on 2007-10-25
I still have the same problem in gutsy with emerald. I have # desktops in General set to 4, but I'm showing 8 desktops on the taakbar, but they are all duplicated of just 2 virtual desktops! If I go to 1 desktop, I still have two showing on the taskbar and the second one is a duplicate. Any ideas?

---

### Post by Lolo Uila on 2007-10-29
The Desktop Pager in the lower tool bar (task bar) is for switching Workspaces. Compiz doesn't use Workspaces, it uses Viewports.

You need to set the number of desktops to 1, vertical size to 1, and horizontal size to 4. That will give you 1 desktop with 4 viewports (the Compiz Cube).

Aloha, Tim

---

