---
title: "Changing OpenOffice default template"
date: 2005-11-27
forum: Desktop Environments
---

### Post by tazzik on 2005-11-27
Hi,
I want to change the OpenOffice default template (the one it loads at startup) to /home/tayo/templates/normal.ott
Cheers,
tazzik

---

### Post by Sutekh on 2005-11-28
Look at the OpenOffice help - search for Template for more info.

Basic instructions:

Load your template file normal.ott

File -> Template -> Save

Put in the desired name (descriptive) and click "My Templates" in categories.  Click OK.

File -> Template -> Organise

Double Click on "My Templates", when it expands, right-click on your template (descriptive name used above) and choose default.  Click OK.

And your done!!

---

### Post by tazzik on 2005-11-30
thanks so much
(great help)

---

### Post by pandionknight on 2006-01-26
I have downloaded the entire OpenOffice template set (a .tar file) and the instructions on their site say "These files should be placed in your %OpenOffice.org%/user/template directory." I have tried to follow this path through File System but can't seem to locate the required directory to place the templates in.

---

### Post by Sutekh on 2006-01-26
[QUOTE=pandionknight]I have downloaded the entire OpenOffice template set (a .tar file) and the instructions on their site say "These files should be placed in your %OpenOffice.org%/user/template directory." I have tried to follow this path through File System but can't seem to locate the required directory to place the templates in.[/QUOTE]

The folder should be 

/home/<your_user_name/templates/

Can you link me to the site, or the instructions?

---

### Post by pandionknight on 2006-01-27
Its here [http://documentation.openoffice.org/Samples_Templates/User/template/]("http://documentation.openoffice.org/Samples_Templates/User/template/")
OpenOffice has created a folder called My Templates for me, but I can't locate it to add the downloaded set of templates to.

---

### Post by pandionknight on 2006-01-27
OK, I have figured something out. I extract the downloaded templates to a folder in Home/PandionKnight/Office/Templates. Then I double click one of the templates .sti files to open the template in OpenOffice and select File/Templates/Save for OpenOffice to add the design to My Templates for me to use in the future. Odd way to go about it, but now I know. Cheers for the help anyway.

---

### Post by Devo66 on 2006-03-01
This does not work for me.  I am trying to change my default template in Calc.  I'm running Breezy.  I found several howtos on this and they all say what you're saying.  To save the template and then set it as default.  However, when I save the template, then go to organize, I cannot expand the My Templates folder.  My saved template does not show up (although it is being created on the disk) and there is no option to set a default template.  This is really starting to piss me off!  I've checked that my template folder is the one that OpenOffice is set to use.  What am I missing?

---

### Post by Devo66 on 2006-03-01
Never mind.  I fixed it.  I had updated to OOo 2.0.1 using the following deb source:

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

which I found somewhere on these forums.  It was suppost to run a little faster the the version that came with Breezy.  Unfortunately it's got a major bug relating to templates!  Reinstalled the Breezy version and all is well now.  Consider this a warning to others.  Don't install the above version.

---

