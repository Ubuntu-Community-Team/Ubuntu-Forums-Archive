---
title: "Tabs in Nautilus"
date: 2009-08-03
forum: Desktop Environments
---

### Post by JarekMk on 2009-08-03
Hello,

How configure Nautilus to open new folder in tab like in Firefox? Not in new window.
Any ideas?

---

### Post by realzippy on 2009-08-03
???????
It is the same as in firefox: CTRL + T.

---

### Post by JarekMk on 2009-08-03
Nop. When I open first folder on desktop and then open second, it's opening in new windows - not in new tab, do you follow? 
I want to make double click on folder and open it in new tab.

---

### Post by wojox on 2009-08-03
Closes you'll get is to press the toggle button under the back button and switch view from buttons and text.

---

### Post by JarekMk on 2009-08-03
Yeah, but this not working as I told ;/

---

### Post by asmoore82 on 2009-08-03
I was so excited when I first heard Nautilus was adding tabs.

I was a little surprised that they tread so lightly with them.

I say Let's go Whole Hog with tabs!!!
Here's hopin' for the next release :KS

---

### Post by realzippy on 2009-08-03
????
..what happens,if you press mouse3 (mousewheel)?

my nautilus ;-) opens folder in new tab.Also ctrl +T...

(Nautilus 2.24.1)

---

### Post by JarekMk on 2009-08-03
Yep, open in new tab if u click on folder in current location, but if u want to open folder eg. from desktop it's opening in new window...

---

### Post by Subban on 2009-08-05
While not answering the OP's oringal query I do think this is relevant and brings better tab functionality to Nautilus in a manner.

Some of Nautilus's layout options are in plain old XML files, its possible to add a New Tab button to Nautilus toolbar, I have also added a New Folder button to mine as its something I constantly use and ctrl+shift+n is a two hand job.

```
sudo gedit /usr/share/nautilus/ui/nautilus-navigation-window-ui.xml
```

There is a section that starts with:
```
<toolbar name="Toolbar">
```

Below that it doesn't take a rocket scientist to notice a bunch of the Nautilus buttons are defined, by popping in a :
```
	<toolitem name="New Tab" action="New Tab"/>
```

add any separators you want and you shall have a nice New Tab button.

I have also added :
```
	<toolitem name="New Folder" action="New Folder"/>
```

It is also possible to add cut, copy and paste buttons and possibly more, I have tried discovering a create document button but couldn't find the command, I was unable to find a list of possibilities.

Regardless, its very easy and a useful addtion to the toolbar when you do not use the breadcrumb style location bar (its much too useful being able to quickly type a path in to change to breadcrumb imo)

edit: Credit to greeleaf for his information that was helpful @ [http://ubuntuforums.org/showthread.php?t=659294](http://ubuntuforums.org/showthread.php?t=659294)

---

