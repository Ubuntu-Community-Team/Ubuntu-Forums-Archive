---
title: "Gnome-Panel Missing"
date: 2007-08-31
forum: Desktop Effects &amp; Customization
---

### Post by oneadvent on 2007-08-31
I am not sure where to post this because it could be anything, but I think it is more related to Compiz than anything.  

Here is my story:

My hard drive fried, and when I got a new one in the mail, I reinstalled Ubuntu 7.04 on the laptop. I then installed all the optional packages that I like, and decided to experiment with Compiz and Emerald. I got my desktop looking pretty awesome (I changed the color and the button for the menu) and installed wine. I put Counter Strike on, and it failed to work, so I rebooted. 

When I did I noticed that the gnome panel was missing. (Tool tips kept coming from where it was, ie: "You are now connected to the XYZ wireless network.") I could not click on it, and there was no icons either. I made a link on the desktop and go to the terminal, and started firefox.
I found the manual command to start the menu, gnome-panel and tried it. It said that it was already running. So I did a ps -A and found the command and killed it. The menu then popped right up.

Every time I reboot it does this, but it doesn't when I hibernate and come back.

It is extremely annoying, but on the bottom of importance, since I have a workaround.

If anyone knows what could be causing this, I would appreciate the help! 

Thanks!

---

### Post by hyperair on 2007-08-31
I reckon it's to do with hibernating, yeah. My system screws up every time I try to hibernate, so I don't =P

---

### Post by Inxsible on 2007-08-31
I have never had much use for hibernate either, now suspend/stand-by is a different issue.

I wish my suspend worked :(

---

### Post by oneadvent on 2007-08-31
No I mean that it works fine with Hibernate.

it doesn't if I reboot or log out and in.

Its really odd...

Maybe I should just add to my pop up a command to kill gnome-panel

(I do not know how to do that without the psid.)

---

### Post by hyperair on 2007-08-31
```
killall gnome-panel
```

or 

```
kill `pidof gnome-panel`
```

---

### Post by oneadvent on 2007-09-01
I was waiting to be sure, but since I used that, it has worked great!

Thanks for the help!

BTW: If anyone is reading this sometime in the future, notice the ` not the '

Thanks again!

Josh

---

