---
title: "No icons in Avant Window Navigator"
date: 2007-06-16
forum: Desktop Effects &amp; Customization
---

### Post by akshayas1986 on 2007-06-16
Hi people

I have been using AWN (Avant Window Navigator) for over 3 weeks now. Yesterday My OS (Ubuntu Fawn)said there is an update on my AWN and I updated it. But as soon as i restarted xwindows, AWN had lost all its icons..

Could no longer add icons. When I went to Configure launchers, all launchers were there and yet none were appearing.. Drag and drop also did not work. Then I realized that AWN did not do something that I should be doing -- The bounce effect, Then I opened it in terminal

Everytime I moved the mouse AWN, I got this message  

> (avant-window-navigator:6470): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed


Please help me out :(

Thanks and regards

Akshaya Srivatsa

EDIT: 

Well is there a bug in the new version of Avant window Navigator?? I forced the older version on my computer which is saved in /var/

> sudo dpkg -i --force-all <avant older version>

Now its fine again but my package manager says there is a newer version of Avant and I need to install it..

I have Beryl-manager 0.2.1 while we have beryl 0.3 now right?? Is it because of that??? Though its working now, I would want to always keep a newer version of Avant or Beryl.

---

### Post by alial on 2007-06-17
When you open the updated AWN go to it and right click and then click configure applets, add Launcher/taskmanager and that will bring up all your icons.

---

### Post by joep on 2007-06-17
Hi I had a problem like this one. I got help off of this thread.

[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

I reinstalled Avant and it runs OK now.

---

### Post by burritod on 2007-06-17
> **alial said:**
> When you open the updated AWN go to it and right click and then click configure applets, add Launcher/taskmanager and that will bring up all your icons.

This worked perfectly for me.  Thanks!

---

### Post by loopeando on 2007-06-17
Worked for me too!

But I had to execute the command "avant-applets" because I couldn't right click on the dock.

Thx!

---

### Post by theonlykman on 2007-06-17
ok, just updated, got the same problem...but very happy to see that the above solution worked for me. suffice it to say, its not that intuitive...

---

### Post by akshayas1986 on 2007-06-19
> **alial said:**
> When you open the updated AWN go to it and right click and then click configure applets, add Launcher/taskmanager and that will bring up all your icons.

Works damn well for me too.. Thanks buddy :popcorn:

Akshaya Srivatsa

---

