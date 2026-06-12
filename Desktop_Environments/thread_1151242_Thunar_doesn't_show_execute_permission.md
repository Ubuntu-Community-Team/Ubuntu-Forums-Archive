---
title: "Thunar doesn't show execute permission?"
date: 2009-05-06
forum: Desktop Environments
---

### Post by peyre on 2009-05-06
When I get properties of something in Thunar, it shows the owner, group, and other permissions: read and write--but it doesn't show execute permissions or let you change them.  Is this by design (and if so, why)?  Or is this a bug or something easily fixable or something I can work around easily?

Yes, of course I can open Terminal and [font="Courier New"]ls[/font] and [font="Courier New"]chmod[/font] the file/folder in question, but I could do that with the read and write permissions too.  Why display only some of the permissions in the GUI?

---

### Post by gnawingonfoot on 2011-03-13
I'm having the same problem, except I don't know how to 'ls and chmode' to actually change the permissions.  I've got a file called minecraft.jar that I would like to run, but I'm unable to do so at the moment.  Any help with explaining the procedures for changing permissions would be much appreciated.  Thanks!

---

### Post by nhtrader on 2011-03-13
xfce 4.8.1
Thunar File Manager 1.2.1

Select View Menu
Configure Columns  (setup columns as you like.)

Also you can click Help Menu:

Under table of contents: select "The File Manager Window" sub-category "Customizing the Appearance"

---

### Post by nhtrader on 2011-03-13
> **gnawingonfoot said:**
> I'm having the same problem, except I don't know how to 'ls and chmode' to actually change the permissions.  I've got a file called minecraft.jar that I would like to run, but I'm unable to do so at the moment.  Any help with explaining the procedures for changing permissions would be much appreciated.  Thanks!


enter terminal mode: select Applications|Accessories|Terminal
use this command to change directories/folders:  cd /home/user/stuff <E>
use this command to change permissions:  chmod 0755 minecraft.jar <E>
use this command to view permissions:  ls -l <E>

---

### Post by nhtrader on 2011-03-13
I just experimented with two files one a *.txt and *.pl

I have the same problem with *.txt but with *.pl it shows a checkbox that allows me to enable this file to run as a program.

So it appears that Thunar has some smarts. It knows the most commonly used extensions and provides you executable access when it thinks it should. But in terminal mode you can override these built-in rules.

I don't know how to change the inherent rules.

---

### Post by Morbius1 on 2011-03-13
> **gnawingonfoot said:**
> I'm having the same problem, except I don't know how to 'ls and chmode' to actually change the permissions.  I've got a file called minecraft.jar that I would like to run, but I'm unable to do so at the moment.  Any help with explaining the procedures for changing permissions would be much appreciated.  Thanks!
A jar file is not an "executable" entity. Try running it directly:
```
java -jar /path/to/minecraft.jar
```

---

### Post by gnawingonfoot on 2011-03-13
Problem solved for me!  Thanks!

EDIT: both solutions worked for me!  Thanks to the both of you!

---

### Post by Jose Catre-Vandis on 2011-03-13
You could add a custom action into Thunar that would chmod a file or files you have selected. You'll need gksudo too to allow the change. Something like:

```
gksu chmod 0755 %F
```
Set to work for any file/files you choose. Fiddle with the code to get the right set of permissions for you - e.g. 0777 instead of 0755.

---

