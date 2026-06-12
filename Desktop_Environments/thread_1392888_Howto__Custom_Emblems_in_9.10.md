---
title: "Howto:  Custom Emblems in 9.10"
date: 2010-01-28
forum: Desktop Environments
---

### Post by lexen on 2010-01-28
Hello everyone.  I wanted to add some custom emblems so I could label my folders more effectively and after a little bit of work, I figured out how to do it and I thought I should share that info with the group.

   The first thing to note is that the emblems are stored in the folder /usr/share/icons/gnome/32x32/emblems.  The first problem you are going to run into is that you don't have permission to add files to this folder.  The way I got around this was by changing the owner of the folder to myself.  I am using a computer for recording, so my user name is "band."  Change that to your user name.

```
sudo chown band "/usr/share/icons/gnome/32x32/emblems"

```

   After you do that, you can paste your icons (I would use the .png format) into the folder.

   Next, you have to resize your icons so they are 32x32.  You can do this by right clicking on the image then Open With > Gimp Image Editor.  When Gimp starts up, go to Image > Scale Image.  Change the width to 32.  If your image is square, it will automaticly change the hight to 32.  If it isn't then you can either force it to be 32 by unchecking the chain icon between the width and height, or you can resize the layer so it fits within 32x32.  Then File > Save.  If it is not a .png file, I would use Save As and save it as a .png by replacing the current format (.jpg, ect.) to .png.  The Gimp will automaticly change the settings so it save it to the right format.

   I know for some of you these steps were obvious, but I thought I should help people out who aren't too familiar with the terminal or with the Gimp.

   If there are any mistakes in this tutorial, let me know and I will fix them.  Any advise is welcome.


Thanks,
Lexen

---

### Post by magicfab on 2010-03-06
It's not a good idea to change a system's folder permissions like that.

Instead, create your icons in your own folder, then copy them to the system folder using sudo...

sudo cp FILE /destination/path/FILE

---

### Post by sagarsiddhpura on 2010-04-17
LOL it doesnt work in Ubuntu 10.04. After adding png to said folder, It does'nt show up in emblems tab.

---

### Post by Ufogos on 2010-05-29
This may help, [Adding emblems manually]("http://www.go2linux.org/How-Customize-Ubuntu-with-Backgrounds-and-Emblems")

---

### Post by Zol666taN on 2012-04-18
Thanks to you all -- reading this thread saved me some time and research.

This widget for emblems is a sweetie. Ain't Linux great ? And Ubuntu ?

---

### Post by oldos2er on 2012-04-18
Closed, necromancy.

---

