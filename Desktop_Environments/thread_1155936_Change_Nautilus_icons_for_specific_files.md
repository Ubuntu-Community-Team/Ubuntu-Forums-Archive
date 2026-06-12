---
title: "Change Nautilus icons for specific files"
date: 2009-05-11
forum: Desktop Environments
---

### Post by Soepstengel on 2009-05-11
Hello all,


I have Office 2007 running in Wine. The Gnome menu shows the Office 2007 applications under "Applications -> Wine -> Programs -> Office 2007". I want those Icons, the official Office 2007 icons, also in Nautilus for .doc, .docx, .xls, .xlsx, etc. files. I figured out how to change the Icon of a single file in Nautilus (right mouse -> properties), but how can I change the Icons for all Word Document files, Excel Document files, etc.?

I am running Ubuntu 8.10.


Soepstengel

---

### Post by Minsky on 2009-05-17
If you have a custom desktop theme installed, check if it has created a **.icons** folder in your home folder by enabling **Show Hidden Files (CTRL-H)**. If it has then:

Go to **~/.icons/"custom theme"/scalable/mimetypes** and select an icon that corresponds with your application. Right click. select **Properties** and you can replace the icon with one of your choice.

If you wish to preserve the existing icon, then rename it by appending **.old** to the very end of the filename, copy and paste your icon into the folder and rename it with the existing icon's original filename.

If you do not have a **.icons** folder in your home folder, then go to **/usr/share/icons/gnome/scalable/mimetypes** and follow the same procedure there.

And that hopefully should work. Sorry if the explanation is a bit long winded

---

### Post by Soepstengel on 2009-05-18
That worked great :D

Thanks for your help.

---

### Post by Minsky on 2009-05-20
Just an update, I've found this -

[http://onlyubuntu.blogspot.com/2008/10/how-to-change-file-type-mimetype-icons.html](http://onlyubuntu.blogspot.com/2008/10/how-to-change-file-type-mimetype-icons.html)

- which features a bit more info

---

### Post by Soepstengel on 2009-05-20
I noticed yesterday that if I change the icon size in Nautilus my own placed icons remain the same size. When I placed the icon file in all the "SizexSize" folders I figured out this would happen, but I am okay with that.

Thanks for the more information.

---

