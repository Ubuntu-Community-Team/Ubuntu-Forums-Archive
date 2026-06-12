---
title: "Problems with Firefox?"
date: 2008-12-17
forum: General Help
---

### Post by amayameda on 2008-12-17
Hello all.  I have had Ubuntu for about two weeks now, and everything has been working fine.  A few days ago I started having problems.  While  in firefox, the back button is almost always grayed out, my bookmarks disappeared, it won't play java programs, and the google search engine that appears in the right-hand corner of the toolbar doesn't actually do anything anymore.  I don't know if the problem is with Firefox, Ubuntu, or my laptop.  I suddenly can't open Tomboy notes either.  All of these things were working perfectly just a few days ago, and I haven't installed anything new.


Can anyone help me?  I have no clue what I'm doing.  This guy installed linux onto my computer saying that he would teach me how to do everything.  Once it was installed, he wanted $70 an hour to teach me.  So I apologize for my ignorance in advance.

---

### Post by amayameda on 2008-12-17
I don't know if this helps, but if I open the java console by right clicking, it says:

load: class loader.class not found.
java.lang.ClassNotFoundException: loader.class
	at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:194)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:127)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at sun.applet.AppletClassLoader.loadCode(AppletClassLoader.java:640)
	at sun.applet.AppletPanel.createApplet(AppletPanel.java:786)
	at sun.plugin.AppletViewer.createApplet(AppletViewer.java:2108)
	at sun.applet.AppletPanel.runLoader(AppletPanel.java:715)
	at sun.applet.AppletPanel.run(AppletPanel.java:369)
	at java.lang.Thread.run(Thread.java:619)

---

### Post by Bakerconspiracy on 2008-12-17
I don't know what could have done this. Have you been messing around a lot on your computer? - i.e using "sudo" in directories other then your home? Can you remember anything you did before the problems started happening?

You don't need to pay some guy to teach you to learn linux. It could be understandable if he was going to teach you to program, but still, this operating system was founded on the idea of being free and easy to learn. There are enough resources for you to learn on your own. Don't give him any money.

--- Glad to see you in the community

---

### Post by amayameda on 2008-12-17
I don't know what it means to use "sudo" at all, so I'm going to say that I haven't.  The only thing I've done lately is download some episodes of House, and play Runescape.  Other than that, I've transfered my downloads to windows.  That's it.  I haven't even run updates, because he said it will break stuff, and I won't know how to fix it. 

Yeah, I'm not paying him anything more if I can help it.  He tells me its FREE FREE FREE, and then afterwards mentions that he wants a $500 "Donation" for installing it for me, and more "donations" for any tech support. So here I am, trying my best to learn by myself.

So, any ideas on how to fix this?  Or even just how to get java to work again?

---

### Post by gbc on 2008-12-17
The exact same thing has happened to me.  It started when I upgraded to the latest Firefox about a week ago.  Not sure what to do, I updated my whole system from 8.0.4 LTS to 8.1 but it still has the same problem.

---

### Post by Malcy on 2009-01-06
I have just had the same thing happen. All the bookmarks have disappeared!! The Bookmarks.html file and backups are there, it just won't display the bookmarks.

---

### Post by Jompa on 2009-02-01
I have the same problem. I can't see any of my bookmarks, when I open the browser it doesn't go to the home page, when i write an internetaddress it doesn't suggest pages i have been to earlier and when I try to serch or log in at pages it doesn't want to continue when i press search or log in. The problem just appeared, and I havn't changed any settings. I have also tried re-installing firefox, but the same problem appear again.

---

### Post by mb_webguy on 2009-02-01
Several issues here.

First, don't pay the guy any money.  Learning to use Linux isn't difficult.  You just need the willingness to learn new things and experience.

Second, you should install updates.  Unlike some other distributions of Linux, Ubuntu uses a stepped release schedule, which means that the only updates you will receive from the official repositories are security updates and bug fixes.  While there is a small chance that an update will occasionally cause some minor problem, it will generally be fixed with the next update.  Overall, you're much better off with regular updates than without.

Third, concerning Firefox, sometimes some extensions or combinations of extensions can mess up your profile.  To see if this is the problem, you can simply create a new profile.   Press Alt+F2 (or open the terminal) and type the command "firefox -ProfileManager".  Then create a new user profile for Firefox, and start Firefox with that profile.  If everything seems to work, then you can exit, run the previous command again, select your original profile, and export your bookmarks.  Then again run that command to select your new profile, and import your bookmarks.  Then install your extensions and themes as normal.

---

### Post by adamlau on 2009-02-01
Create a new profile and disable Java. See if that helps. Nothing wrong with paying for support as long as you learn a few tips and tricks from the supporter along the way.

---

### Post by Jompa on 2009-02-02
> **mb_webguy said:**
> Several issues here.

First, don't pay the guy any money.  Learning to use Linux isn't difficult.  You just need the willingness to learn new things and experience.

Second, you should install updates.  Unlike some other distributions of Linux, Ubuntu uses a stepped release schedule, which means that the only updates you will receive from the official repositories are security updates and bug fixes.  While there is a small chance that an update will occasionally cause some minor problem, it will generally be fixed with the next update.  Overall, you're much better off with regular updates than without.

Third, concerning Firefox, sometimes some extensions or combinations of extensions can mess up your profile.  To see if this is the problem, you can simply create a new profile.   Press Alt+F2 (or open the terminal) and type the command "firefox -ProfileManager".  Then create a new user profile for Firefox, and start Firefox with that profile.  If everything seems to work, then you can exit, run the previous command again, select your original profile, and export your bookmarks.  Then again run that command to select your new profile, and import your bookmarks.  Then install your extensions and themes as normal.

This worked for me, thanks :D

---

