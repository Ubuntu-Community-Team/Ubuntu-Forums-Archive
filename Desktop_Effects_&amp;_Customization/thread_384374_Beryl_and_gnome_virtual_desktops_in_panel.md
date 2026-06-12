---
title: "Beryl and gnome virtual desktops in panel"
date: 2007-03-14
forum: Desktop Effects &amp; Customization
---

### Post by svenole on 2007-03-14
I've been using Fedora for a long time and have just converted to ubuntu. Using beryl on ubuntu 6.10 (NVIDIA laptop) is working, but I have a problem: 

beryl does not automatically integrate with the gnome virtual desktop applet in the panel. When installing beryl or compiz on fedora, the cube feature integrated nicely with my four virtual desktops in gnome so that switching desktops on the panel made the cube roll to that desktop. Same thing with the windows list in the panel. 

This does not work out of the box when installing beryl on ubuntu and I'm stuck. Any clues?
:( 

Thanks, 

- Sven

---

### Post by old_geekster on 2007-03-17
Do you have Beryl Manager icon in the panel?  If not, go to System/Preferences/Sessions.  In Sessions, click on "Startup Programs".  Then, click on "+Add".  In the box type Beryl Manager and save.  Next, repeat the steps, only this time type "Emerald".

Now, when you boot, "Beryl Manager" icon will appear in the lower right panel.  "Emerald Theme Manger" is in System/Preferences.  You can right click on it and Add this launcher to Panel.

This should do what you want.  It should allow the virtual desktop to rotate.

I hope that I understood your question correctly.

---

### Post by svenole on 2007-03-17
Thank you for your tips. I had "beryl-manager" in the startup and changed to "beryl manager". At least now beryl starts as it should. 
 
A couple of things is not as it should be however. First thing is that the beryl icon is gone i the panel. Sometime during my hunt for problem-fixes, this icon disappeared and I can not find a way to get it back. It's not in the add-to-panel list. 

Second is that I have got the svitsjer between desktops to work, but not totally integrated with the panel switcher. The panel switcher is set to one desktop. Inside that desktop, the four beryl dektops are spread out.

---

### Post by old_geekster on 2007-03-17
> **svenole said:**
> Thank you for your tips. I had "beryl-manager" in the startup and changed to "beryl manager". At least now beryl starts as it should. 
 
A couple of things is not as it should be however. First thing is that the beryl icon is gone i the panel. Sometime during my hunt for problem-fixes, this icon disappeared and I can not find a way to get it back. It's not in the add-to-panel list. 

Second is that I have got the svitsjer between desktops to work, but not totally integrated with the panel switcher. The panel switcher is set to one desktop. Inside that desktop, the four beryl dektops are spread out.
Having you put Beryl Manager in the Startup Programs was a typo.  It should have been beryl-manager.  If it works, I guess this is not a problem.

I will give your other two questions some thought.

However, you may want to use Automatix Bleeder to reinstall Beryl.  I didn't even know that it existed until last night.  I used it to install Beryl and it worked great.  Everything was setup correctly.

---

### Post by old_geekster on 2007-03-17
> **svenole said:**
> A couple of things is not as it should be however. First thing is that the beryl icon is gone i the panel. Sometime during my hunt for problem-fixes, this icon disappeared and I can not find a way to get it back. It's not in the add-to-panel list. 
If you are talking about the red rubby icon, go to Applications/System Tools, right click on Beryl Manager and select "Add this launcher to panel".  This will add the red ruby in the panel.

> Second is that I have got the svitsjer between desktops to work, but not totally integrated with the panel switcher. The panel switcher is set to one desktop. Inside that desktop, the four beryl dektops are spread out.
I am assuming that you mean switcher, not "svitsjer".

Only one desktop shows in the switcher area in the panel on my desktop, also.  However, if I click on the blank spaces, it changes desktops.  Also, when I rotate the desktops, it shows a desktop in the appropriate space.

If I misconstrued your questions, please fire back and let me know.:lolflag:

---

