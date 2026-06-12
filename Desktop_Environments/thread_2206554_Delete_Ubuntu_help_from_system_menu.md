---
title: "Delete Ubuntu help from system menu"
date: 2014-02-19
forum: Desktop Environments
---

### Post by marc0tjevp on 2014-02-19
Hi!

I´ve had a little question: How do I remove the Yelp starter from the system menu? Can´t make a screenshot because menu´s close when making one. :(

Sorry for my bad English :P

Thanks!

---

### Post by deadflowr on 2014-02-19
You can take a screenshot with menu by using a delay.
Open the program "Screenshot" and set a delay time for 5 seconds.

This should be enough time for you to set up the menu.
Otherwise, don't know what you mean by yelp.

---

### Post by grahammechanical on 2014-02-19
I think that you are referring to the power/cog menu option of "Ubuntu Help." Is that correct? What version of Ubuntu are you using? Sometimes there are changes from one version to another and that means that instructions that work in Ubuntu 12.04 may not work in Ubuntu 13.10.

I cannot answer your question. You will need to search through a large number of system folders to find the script that controls what is written in that menu. Someone asked a similar question here more than 18 months ago. They did not receive any answer.

[http://askubuntu.com/questions/158423/how-can-i-modify-unity-12-04s-power-cog-menu](http://askubuntu.com/questions/158423/how-can-i-modify-unity-12-04s-power-cog-menu)

Regards.

---

### Post by Dennis N on 2014-02-21
Try this:

Add the line **NoDisplay=true** to **yelp.desktop** in **/usr/share/applications**

Save, log out and log in.

---

