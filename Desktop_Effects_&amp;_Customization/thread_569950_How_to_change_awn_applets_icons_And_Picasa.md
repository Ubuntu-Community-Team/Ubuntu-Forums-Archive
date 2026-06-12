---
title: "How to change awn applets icons? And Picasa"
date: 2007-10-07
forum: Desktop Effects &amp; Customization
---

### Post by olavjunior on 2007-10-07
Is there any way of changing the ugly icons for the applets in awn? 

Alos, Picasa is the only launcher I can't change the icon. Any ideas why?

---

### Post by Ninjaraffe on 2007-11-05
Ya, I noticed the Picasa thing too. Actually none of the icons for apps running under wine can be changed. I can't even add awn launchers for some wine apps . Anyone know why?

---

### Post by hihihi on 2007-11-09
yes, that is really complicated.
i think it has something to do with gtk-pixbuf but i dont know how to and it is quite a query to get appliable info about this.
it has also effect on compiz...
somehow you have all this nice eye-candies but nobody seems to be irritated by this super-mega-ultra-UGLY .xpm icons
the same icons in .svg look already acceptable for 2007 standards...
huhuhu

---

### Post by ibbi on 2008-04-02
YES! My first chance at giving back to the community! Whenever I'm on Ubuntu, I always find myself accessing these forums, but I've never signed up till now -- now that I have something to share :).

After a couple of days of hard noobish efforts lol, I finally got the AWN icons for Wine applications to work! Here's how:

1. We have to make the Wine application executable with a simpler terminal command, i.e. typing "dreamweaver" in the terminal will launch Dreamweaver instead of typing "wine blah blah blah" to launch it. We do this by adding the following to your ~/.bashrc
[INDENT]alias *your_application_name*='wine *your_application_location* *your_application_name*.exe' [/INDENT]

2. Open AWN Manager and add a launcher to AWN and simply type *your_application_name* for the command field.

3. Right-click the default icon that appears in AWN and change the icon.

4. Restart AWN.

I hope that helps!

---

### Post by ibbi on 2008-04-03
My bad, I just turned my computer on and the shortcut doesn't work anymore. This should work though. (Note: wherever you see the word "dreamweaver" below, replace it with the name of the Wine application you're adding to the AWN dock.)

1. Create an empty file in your home folder or whatever (doesn't matter, we'll move it later) and name it ***dreamweaver*** or whatever the name of your Wine application is. You can do this by right-clicking in your home folder or wherever, and mousing over to *Create Document > Empty File*).

2. Open the file in a text editor and type the Wine command that executes Dreamweaver (see previous post for an example). Save and close the document.

3. Open a terminal and ***cd*** to the directory where you created the file.

4. Make the file executable by typing ***chmod +x dreamweaver***

5. Copy the file to your /usr/bin/ directory by typing ***sudo cp dreamweaver /usr/bin/***

Now you should be able to launch Dreamweaver by simply typing *dreamweaver* in the Run Program (Alt+F2) dialog box.

6. Open AWN Manager and go to Launchers. Add a launcher named Dreamweaver and for the command, type ***dreamweaver***

7. Restart AWN.

You should be able to change the icon in AWN now and the launcher should work perfectly. Phew!

---

### Post by toorima on 2008-04-04
> **ibbi said:**
> YES! My first chance at giving back to the community! Whenever I'm on Ubuntu, I always find myself accessing these forums, but I've never signed up till now -- now that I have something to share :).

After a couple of days of hard noobish efforts lol, I finally got the AWN icons for Wine applications to work! Here's how:

1. We have to make the Wine application executable with a simpler terminal command, i.e. typing "dreamweaver" in the terminal will launch Dreamweaver instead of typing "wine blah blah blah" to launch it. We do this by adding the following to your ~/.bashrc
[INDENT]alias *your_application_name*='wine *your_application_location* *your_application_name*.exe' [/INDENT]

2. Open AWN Manager and add a launcher to AWN and simply type *your_application_name* for the command field.

3. Right-click the default icon that appears in AWN and change the icon.

4. Restart AWN.

I hope that helps!

To make this survive a reboot you can add it to your .bash_aliases (if you don't have that file in your home dir, just create it)

---

