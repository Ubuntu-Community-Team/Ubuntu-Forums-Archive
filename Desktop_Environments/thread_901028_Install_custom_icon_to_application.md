---
title: "Install custom icon to application"
date: 2008-08-26
forum: Desktop Environments
---

### Post by apche93 on 2008-08-26
hi all,

i have a .docx document on my desktop.  Now, i already have a set of icons installed, but the problem is that the Microsoft .docx icon isnt showing up.  Instead the Text Editor icon is showing.  So, i downloaded a custom icon for the Microsoft Word.  When i right click the file to go to properties and replace the icon with the one i downloaded it changes but here is my problem:  I dont want to have to change every single documents icon to suit that of my preference.  Is there a way where i can set all .docx files to use a certain icon?

---

### Post by apche93 on 2008-08-27
Um, so can anyone help me with this?

---

### Post by bornakke on 2009-03-08
Hi Apche93.

It seems like a very simple qustion - but the answear have always seemed very complex. Have had the problem ever since Docx were introduced and have tried several times to fix it (however without luck). Today I however finally found a way and to my suprice, the solution is quite simpel. 

How to:
1) Right click on a docx document and click properties (assuming you are using gnome). On the 'basic' check out the type name. For me it was Microsoft Word Document (application/vnd.openxmlformats-officedocument.wordprocessingml.document) - because i'm using crossover office. 

2) Now go to folder containing your current icon theme. I believe it to be /usr/share/icons if you are using the standart icon themes or /home/[username]/.icons/[current-icon-theme-name]/ if you have installed your own icon themes. In here go to 'scalable' -> 'mimetype'

3) Place your new icon in here and rename it to [type].png - in my case: application-vnd.openxmlformats-officedocument.wordprocessingml.document.png

Log out and log in and it worked for me. Please feel free to write again if it doens't work and I will try to help you out :)

---

