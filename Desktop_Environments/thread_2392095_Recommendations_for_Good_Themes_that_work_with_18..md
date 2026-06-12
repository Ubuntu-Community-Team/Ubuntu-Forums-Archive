---
title: "Recommendations for Good Themes that work with 18.04"
date: 2018-05-15
forum: Desktop Environments
---

### Post by galacticstone on 2018-05-15
Hi Folks,

I need a recommendation for a good dark theme for 18.04 (Gnome). I want something that shows dark fields in the browsers and apps. I had one (DeLorean) on 16.04 before I upgraded to 18.04, but I lost it during the upgrade (I did a total wipe and clean install). I am having trouble now finding one that will work and now I am not sure how to even install a new theme. 

So, I guess I need two things - a good dark theme and how do I install it?

EDIT : I now know how to install themes. But I am still having trouble finding good ones that work with 18.04.

Thanks!

MikeG

---

### Post by RobGoss on 2018-05-15
Hello you can take a look here for some good dark themes [https://www.gnome-look.org/search?projectSearchText=DeLorean](https://www.gnome-look.org/search?projectSearchText=DeLorean) I do believe they have instructions on installations as well

---

### Post by Frogs Hair on 2018-05-15
If you don't mind flat design look [here]("https://www.opendesktop.org/s/Gnome/p/1182169/").

---

### Post by galacticstone on 2018-05-15
I saw that Equilux theme and was interested in it, but didn't know which (or all) of the files to download. There are 10 files in there. Do I download them all and put them in the ".themes" folder?

Thanks!

MikeG

---

### Post by Frogs Hair on 2018-05-15
The first two listed are the newest and one is labeled compact which has thinner title bars. Yes, you can extract and install in the .themes folder for a single user.

---

### Post by kazakore on 2018-05-16
Check this thread for tips getting your chosen dark theme working across all apps, whether gtk2, gtk3 and qt5.

[https://ubuntuforums.org/showthread.php?t=2391601](https://ubuntuforums.org/showthread.php?t=2391601)

---

### Post by pythagorean1804 on 2018-05-16
Thanks for the suggestion.  I like the flat design.  Is it possible that there is a Canonical/Ubuntu version that implements the same concepts and that is certain to work with any app's menus/icons/title bars?  I like trying out new themes in Ubuntu but I have found that they can be a little rough around the edges once you really use them every day.

---

### Post by galacticstone on 2018-05-16
I tried looking at that thread, but it's mostly Greek to me.

Is there a difference between a Gnome Shell Theme and a "regular" Theme?

I extracted some theme files into the .theme folder, but most of them don't seem to work. The Equilux theme is working, but none of the others I tried will work - they don't even show up in the drop-down list of themes in the Gnome Tweaks menu.

---

### Post by Frogs Hair on 2018-05-16
Many themes @ Gnome Look are dated and for earlier versions of Gnome. An example would be that a Gnome 3.6 theme is not likely to work on Gnome 3.26 or 28 .

 Edit: The shell theme includes the top panel and launcher and the GTK themes are for applications.

---

### Post by Dennis N on 2018-05-16
> Is there a difference between a Gnome Shell Theme and a "regular" Theme?
Gnome Shell Theme is in the main theme's folder. Open the Equilux folder and you will see a folder for 'gnome-shell'. It themes the top bar and activities overview. Tweaks has a selector for Shell theme if you want to use the one provided in Equilux (or other theme). It is not automatically used.

---

### Post by kazakore on 2018-05-16
I always had issues of themes not seeming to work from the ~/.themes folder and always copy them into the system folder after extracting.

I'm afraid I'm an XFCE (Ubuntu Studio) user and can't answer your other questions. One of the key points in my above linked thread was that many downloadable themes only contain gtk2 files though, but with gtk3 you can select variants (eg Greybird has a Light and a Dark variant for GTK+3 applications.) Hence follow the instructions for forcing it to always use the Dark variant for gtk3, then edit or copy over the gtk2 folder. Then there is the final step with qt5ct to get any Qt apps you are using also following the theme.

But you're right, it's really  not simple!! ;)

---

### Post by galacticstone on 2018-05-16
I have been trying out some new themes for 18.04 and most of them do not work. It appears that many themes that worked with 16.04, do not work any more.

I know about the new community theme and I tried it - it's nice, but I want something darker. 

On 16.04, I used Delorean Dark. Now I am using Equilux. But, I want something darker - something that applies those changes to my apps (mostly Chrome).

Can anyone recommend a website or repository where I can find themes that are compatible with 18.04?

Best regards,

MikeG

---

### Post by galacticstone on 2018-05-16
Thanks Kazakore - even though I did not follow all of it, I did learn a couple of things about themes. Now I know the difference between gtk2 and gtk3.  :)

---

### Post by QIII on 2018-05-16
Threads merged.

---

### Post by Frogs Hair on 2018-05-16
A couple of options here.

```
sudo apt install arc-theme 
``` There are dark versions with different colors of the linked themes. Just install the dark ones if you want.

[https://www.gnome-look.org/p/1187179/](https://www.gnome-look.org/p/1187179/)


[https://www.gnome-look.org/p/1190851/](https://www.gnome-look.org/p/1190851/)

---

### Post by galacticstone on 2018-05-16
> **Dennis N said:**
> Gnome Shell Theme is in the main theme's folder. Open the Equilux folder and you will see a folder for 'gnome-shell'. It themes the top bar and activities overview. Tweaks has a selector for Shell theme if you want to use the one provided in Equilux (or other theme). It is not automatically used.
Thanks Dennis.  :)

---

