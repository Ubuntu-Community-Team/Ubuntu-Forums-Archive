---
title: "Printing a thread  forum from FireFox: Missing right edge"
date: 2008-10-29
forum: Forum Feedback &amp; Help
---

### Post by LarryJ2 on 2008-10-29
When ever I tried to print a forum thread from FireFox3, the printed page's right edge would be cut off (cropped).  I finally stumbled on a solution in one of the mozilla help forums.  Since it took several hours to find this tip,  I'm repeating it here.

In the url window, enter
```
about:config
```

Ignore the silliness about the warranty. 

In the Filter window, enter 
```
print.whileInPrintPreview
```

After this item appears, right click on this item then select toggle to change its value from false to true.

Restart Firefox.  Now when you print preview you'll have a scale drop down which you can select, say 80%, inorder to avoid cropping the right margin.  As usual, what you see in print preview, is what is printed, just smaller.

Another irritation: Windoze versions of Firefox have a place where you can set the printer margins.   But not apparently  FireFox under Linux Ubuntu

---

