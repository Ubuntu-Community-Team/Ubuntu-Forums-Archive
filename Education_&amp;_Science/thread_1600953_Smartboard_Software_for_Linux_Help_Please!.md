---
title: "Smartboard Software for Linux Help Please!"
date: 2010-10-19
forum: Education &amp; Science
---

### Post by sarsar on 2010-10-19
Hello,

Im an absolute beginner at Ubuntu so i will probably need a lot of help doing something that is probably very simple. I am currently training to be a teacher and so i have downloaded some SMART Board Software. SMART (the company who produce the software) have sent me the Linux version of their software complete with the drivers. However, when i went to open the download the message came up with: 

Could not open the file /home/[my name]/.cache/.fr-…e With Drivers 10.package using the Unicode (UTF-8) character encoding.

I have selected both options in the menu but it keeps coming up with this message. 

Please could somebody help me? Is there another way of opening this package and a kind of coding that i don't know about? or do i have to open it in the terminal? if so please could someone tell me how. 

Btw: Im using Ubuntu 10.04 LTS. If you need any more info i will try and give you it. 

Many Thanks 

Sarsar

---

### Post by tonyyarusso on 2010-12-26
For whatever reason Ubuntu is incorrectly guessing the type of file this is, and attempting to open it in GEdit (a text editor).  What you want to be doing is actually running this installer as a program, which is disabled on filed you download by default for obvious security reasons.  So, you need to tell Ubuntu that this file is okay to "execute".

To do this, right-click on the file, select "Properties", and within the dialog that pops up go to the "Permissions" tab and check the box for "Allow executing file as program".  Then you'll be able to just double-click the file or run it from a terminal.  I've also attached a (zipped) copy of a video demonstrating this.

---

