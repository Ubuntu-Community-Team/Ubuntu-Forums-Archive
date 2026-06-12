---
title: "desktop configuration"
date: 2009-08-26
forum: Desktop Environments
---

### Post by Dr. Md. Manirul Ali on 2009-08-26
:confused:  I have got my new hp mini 110 with readymade installed ubuntu (genome) desktop. I am not able to open a terminal. How do I configure my desktop so that I can have the terminal icon shown whenever I login to the system ?

---

### Post by sumeshgupta on 2009-08-26
Did you try Applications > Accessoies > Terminal?
To see the terminal icon everytime you log in and not to go through the above process go to Applications > Accessories >Terminal, then right click on terminal submenu and click add to panel in the popped up sub-sub menu. The Terminal icon will permanently show on the top panel. You can then click on it to access the terminal.
I hope I got your question right and this helps.

---

### Post by Dr. Md. Manirul Ali on 2009-08-27
> **sumeshgupta said:**
> Did you try Applications > Accessoies > Terminal?
To see the terminal icon everytime you log in and not to go through the above process go to Applications > Accessories >Terminal, then right click on terminal submenu and click add to panel in the popped up sub-sub menu. The Terminal icon will permanently show on the top panel. You can then click on it to access the terminal.
I hope I got your question right and this helps.


Dear sumeshgupta, thanks for your reply. But I do not see the terminal submenu when I try  Applications > Accessoies > ........Can you suggest me how to bring the terminal submenu in Applications > Accessoies > ? yours manirul

---

### Post by Dr. Md. Manirul Ali on 2009-08-27
> **sumeshgupta said:**
> Did you try Applications > Accessoies > Terminal?
To see the terminal icon everytime you log in and not to go through the above process go to Applications > Accessories >Terminal, then right click on terminal submenu and click add to panel in the popped up sub-sub menu. The Terminal icon will permanently show on the top panel. You can then click on it to access the terminal.
I hope I got your question right and this helps.


Dear sumeshgupta, thanks for your reply. But I do not see the terminal submenu when I try Applications > Accessoies > ........Can you suggest me how to bring the terminal submenu in Applications > Accessoies > ? yours manirul

---

### Post by abhilash82 on 2009-08-27
> **Dr. Md. Manirul Ali said:**
> :confused:  I have got my new hp mini 110 with readymade installed ubuntu (genome) desktop. I am not able to open a terminal. How do I configure my desktop so that I can have the terminal icon shown whenever I login to the system ?

You can right click on your panel and select "add to panel". Here you can select the terminal application (gnome-terminal) and place it wherever you want in the panel. This is like the Quick Launch option in XP.

[http://library.gnome.org/users/user-guide/stable/gospanel-34.html.en](http://library.gnome.org/users/user-guide/stable/gospanel-34.html.en)

---

### Post by orsenthil on 2009-08-27
> **Dr. Md. Manirul Ali said:**
> Dear sumeshgupta, thanks for your reply. But I do not see the terminal submenu when I try Applications > Accessoies > ........Can you suggest me how to bring the terminal submenu in Applications > Accessoies > ? yours manirul

It is not Terminal Sub-Menu. There should be an item with the Terminal Symbol on that.
Alternatively, you can do 
> ALT + F2 

And in the dialog box that comes up, type the following exactly and press enter.
> gnome-terminal


---

### Post by sumeshgupta on 2009-08-27
My mistake. Its not terminal submenu but program called terminal. If you cant see terminal under Applications > Accessories > then try the method given in the post above. If that also fails then I think terminal is not installed on your laptop (:confused:). Then follow the following if you have internet connection :
[PHP] 
Goto System > Administration > synaptic package manager.
Enter your login password when asked for.
click on search.
Type gnome-terminal in the search window.
click OK
You will see the package in the package manager window.
Select the package by clicking on the box on left side of the package entry.
Select "mark for installation" in the menu that pops up.
click on "Apply changes" button on top.
Click OK on new window that pops up.
Sit and watch.
The gnome-terminal package will be downloaded and installed.
Click on close window and then close synaptic.
[/PHP]you will now see terminal application under Applications > Accessories >

---

### Post by Dr. Md. Manirul Ali on 2009-08-28
> **sumeshgupta said:**
> My mistake. Its not terminal submenu but program called terminal. If you cant see terminal under Applications > Accessories > then try the method given in the post above. If that also fails then I think terminal is not installed on your laptop (:confused:). Then follow the following if you have internet connection :
[php] 
Goto System > Administration > synaptic package manager.
Enter your login password when asked for.
click on search.
Type gnome-terminal in the search window.
click OK
You will see the package in the package manager window.
Select the package by clicking on the box on left side of the package entry.
Select "mark for installation" in the menu that pops up.
click on "Apply changes" button on top.
Click OK on new window that pops up.
Sit and watch.
The gnome-terminal package will be downloaded and installed.
Click on close window and then close synaptic.
[/php]you will now see terminal application under Applications > Accessories >
 
 
:confused: ???????
Dear Friends, Thanks for your helpful responses. I have been able to open the
terminal by using "Alt+f2" and then writing "gnome-terminal". But I do not see the
panel where I can make an icon for the terminal, so that everytime I don't need 
to do "Alt+f2"......Actually the readymade installed Ubuntu (gnome) desktop looks
very strange to me, I have never encountered with this kind of Ubuntu Desktop. 
You may have a look to this Desktop: please link to this website: [http://www.hp.com/united-states/campaigns/mini1000/?jumpid=ex_r602_hpmini-com/hpmini_mihome#/MiHome/](http://www.hp.com/united-states/campaigns/mini1000/?jumpid=ex_r602_hpmini-com/hpmini_mihome#/MiHome/)
 
I do not see the panel in the desktop, where I can keep icons of various applications.
If I "write click" at any place in this strange desktop, nothing happens.
 
Generally (in Ubuntu) we see an icon for the terminal in the "Accessories". 
But in my laptop, "Accessories" contain only 2 applications: "calculator" and "gEdit". 
 
PS: I have checked using synaptic package manager that "gnome-terminal" is already
installed in my laptop.

---

### Post by Dr. Md. Manirul Ali on 2009-08-29
> **orsenthil said:**
> It is not Terminal Sub-Menu. There should be an item with the Terminal Symbol on that.
Alternatively, you can do 
 
And in the dialog box that comes up, type the following exactly and press enter.
 
 
:confused: ???????????
Dear Friends, Thanks for your helpful responses. I have been able to open the
terminal by using "Alt+f2" and then writing "gnome-terminal". But I do not see the
panel where I can make an icon for the terminal, so that everytime I don't need 
to do "Alt+f2"......Actually the readymade installed Ubuntu (gnome) desktop looks
very strange to me, I have never encountered with this kind of Ubuntu Desktop. 
You may have a look to this Desktop: please link to this website: [[COLOR=#444444]http://www.hp.com/united-states/camp...ihome#/MiHome/[/COLOR]]("http://www.hp.com/united-states/campaigns/mini1000/?jumpid=ex_r602_hpmini-com/hpmini_mihome#/MiHome/")
 
I do not see the panel in the desktop, where I can keep icons of various applications.
If I "write click" at any place in this strange desktop, nothing happens.
 
Generally (in Ubuntu) we see an icon for the terminal in the "Accessories". 
But in my laptop, "Accessories" contain only 2 applications: "calculator" and "gEdit". 
 
PS: I have checked using synaptic package manager that "gnome-terminal" is already
installed in my laptop.

---

### Post by Dr. Md. Manirul Ali on 2009-09-01
> **abhilash82 said:**
> You can right click on your panel and select "add to panel". Here you can select the terminal application (gnome-terminal) and place it wherever you want in the panel. This is like the Quick Launch option in XP.

[http://library.gnome.org/users/user-guide/stable/gospanel-34.html.en](http://library.gnome.org/users/user-guide/stable/gospanel-34.html.en)
:confused: ???????
Dear Friends, Thanks for your helpful responses. I have been able to open the
terminal by using "Alt+f2" and then writing "gnome-terminal". But I do not see the
panel where I can make an icon for the terminal, so that everytime I don't need 
to do "Alt+f2"......Actually the readymade installed Ubuntu (gnome) desktop looks
very strange to me, I have never encountered with this kind of Ubuntu Desktop. 
You may have a look to this Desktop: please link to this website: [http://www.hp.com/united-states/camp...ihome#/MiHome/]("http://www.hp.com/united-states/campaigns/mini1000/?jumpid=ex_r602_hpmini-com/hpmini_mihome#/MiHome/")
 
I do not see the panel in the desktop, where I can keep icons of various applications.
If I "write click" at any place in this strange desktop, nothing happens.
 
Generally (in Ubuntu) we see an icon for the terminal in the "Accessories". 
But in my laptop, "Accessories" contain only 2 applications: "calculator" and "gEdit". 
 
PS: I have checked using synaptic package manager that "gnome-terminal" is already
installed in my laptop.

---

### Post by Dr. Md. Manirul Ali on 2009-09-01
:confused: ???????

---

### Post by Dr. Md. Manirul Ali on 2009-09-01
> **sumeshgupta said:**
> My mistake. Its not terminal submenu but program called terminal. If you cant see terminal under Applications > Accessories > then try the method given in the post above. If that also fails then I think terminal is not installed on your laptop (:confused:). Then follow the following if you have internet connection :
[php] 
Goto System > Administration > synaptic package manager.
Enter your login password when asked for.
click on search.
Type gnome-terminal in the search window.
click OK
You will see the package in the package manager window.
Select the package by clicking on the box on left side of the package entry.
Select "mark for installation" in the menu that pops up.
click on "Apply changes" button on top.
Click OK on new window that pops up.
Sit and watch.
The gnome-terminal package will be downloaded and installed.
Click on close window and then close synaptic.
[/php]you will now see terminal application under Applications > Accessories >

:confused: ???????
Dear Friends, Thanks for your helpful responses. I have been able to open the
terminal by using "Alt+f2" and then writing "gnome-terminal". But I do not see the
panel where I can make an icon for the terminal, so that everytime I don't need 
to do "Alt+f2"......Actually the readymade installed Ubuntu (gnome) desktop looks
very strange to me, I have never encountered with this kind of Ubuntu Desktop. 
You may have a look to this Desktop: please link to this website: [http://www.hp.com/united-states/camp...ihome#/MiHome/]("http://www.hp.com/united-states/campaigns/mini1000/?jumpid=ex_r602_hpmini-com/hpmini_mihome#/MiHome/")
 
I do not see the panel in the desktop, where I can keep icons of various applications.
If I "write click" at any place in this strange desktop, nothing happens.
 
Generally (in Ubuntu) we see an icon for the terminal in the "Accessories". 
But in my laptop, "Accessories" contain only 2 applications: "calculator" and "gEdit". 
 
PS: I have checked using synaptic package manager that "gnome-terminal" is already
installed in my laptop.

---

### Post by Dr. Md. Manirul Ali on 2009-09-01
> **abhilash82 said:**
> You can right click on your panel and select "add to panel". Here you can select the terminal application (gnome-terminal) and place it wherever you want in the panel. This is like the Quick Launch option in XP.

[http://library.gnome.org/users/user-guide/stable/gospanel-34.html.en](http://library.gnome.org/users/user-guide/stable/gospanel-34.html.en)
:confused: ???????
Dear Friends, Thanks for your helpful responses. I have been able to open the
terminal by using "Alt+f2" and then writing "gnome-terminal". But I do not see the
panel where I can make an icon for the terminal, so that everytime I don't need 
to do "Alt+f2"......Actually the readymade installed Ubuntu (gnome) desktop looks
very strange to me, I have never encountered with this kind of Ubuntu Desktop. 
You may have a look to this Desktop: please link to this website: [http://www.hp.com/united-states/camp...ihome#/MiHome/]("http://www.hp.com/united-states/campaigns/mini1000/?jumpid=ex_r602_hpmini-com/hpmini_mihome#/MiHome/")
 
I do not see the panel in the desktop, where I can keep icons of various applications.
If I "write click" at any place in this strange desktop, nothing happens.
 
Generally (in Ubuntu) we see an icon for the terminal in the "Accessories". 
But in my laptop, "Accessories" contain only 2 applications: "calculator" and "gEdit". 
 
PS: I have checked using synaptic package manager that "gnome-terminal" is already
installed in my laptop.

---

### Post by sumeshgupta on 2009-09-03
Please check out the following page. Since terminal is installed you can add it to Applications > Accessories menu. Where it shows firefox(in the Howto) change it to Terminal and in command, change it to gnome-terminal. Hope this helps.
[URL="http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html"][php] 
http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html
[/php][/URL]

---

