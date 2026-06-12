---
title: "Mouse cursor appearance in desktop screenshots"
date: 2012-05-09
forum: Desktop Environments
---

### Post by Tornikee on 2012-05-09
Hello; since upgrading to Ubuntu 12.04/GNOME 3.4, I've been experiencing a minor but annoying issue with the appearance of mouse cursor in screenshots I take - the cursor is accompanied with a small black background rectangle, which I then have to correct in image editing apps. Here's the screenshot of the mentioned issue: [http://bit.ly/Jsg1HD](http://bit.ly/Jsg1HD)

Is there a way this can be resolved?

---

### Post by Tornikee on 2012-05-09
And there's another issue as well: the message tray notification messages tend to break periodically, showing only a scrollbar on click: [http://bit.ly/IUoowy](http://bit.ly/IUoowy)

---

### Post by vikxmc on 2012-05-10
I am also using Ubuntu 12.04, gnone 3.4.1 and have same issues... Plus i want to know how can i change the screenshot folder from pictures to desktop. In 11.10 it always opened up the box asking to save the picture and i could choose the location, but in 12.04, it just saves it in pictures.

---

### Post by Tornikee on 2012-05-10
I bypassed the cursor issue, as well as the folder issue in your post, by installing Shutter: [http://shutter-project.org/](http://shutter-project.org/) , although the problem described in my second post still persists.

---

### Post by vikxmc on 2012-05-10
> **Tornikee said:**
> I bypassed the cursor issue, as well as the folder issue in your post, by installing Shutter: [http://shutter-project.org/](http://shutter-project.org/) , although the problem described in my second post still persists.
Okay, i installed Shutter but its still saving in pictures, even though i have defined to save on desktop.
My concern is why in ubuntu 11.10 it by default asked for location and in 12.04 it just assumed that i want it saved in the pictures...

---

### Post by Tornikee on 2012-05-10
It might still be saving it using system service, due to PrtScr being default key for that. Try removing that key mapping in system settings and taking screen again. That's what I did.

---

### Post by vikxmc on 2012-05-11
Nope, Still saving in pictures...:(

---

### Post by Tornikee on 2012-07-15
I would really like to hear if there's any solution to the appearance of mouse cursor in screenshots, as I would like to remove Shutter - I can't make it take screenshots by simply pressing PrtScr (I have to select the screenshot type from Shutter menu and then select the window using the cursor).

---

### Post by stinkeye on 2012-07-16
What session are you logging in to?

---

### Post by Tornikee on 2012-07-16
Gnome. There's no such issue on gnome classic session.

---

### Post by stinkeye on 2012-07-16
> **Tornikee said:**
> Gnome. There's no such issue on gnome classic session.
Ok, I was looking for a solution to make shutter the default 
screenshot tool but there appears to be a bug.
[**_[COLOR="DarkRed"]https://bugs.launchpad.net/shutter/+bug/1005473[/COLOR]_**]("https://bugs.launchpad.net/shutter/+bug/1005473")

---

### Post by Tornikee on 2012-07-16
Thanks for that info. At least now I know it's not my fault.

---

