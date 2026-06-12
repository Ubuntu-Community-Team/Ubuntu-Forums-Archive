---
title: "Not displayed correctly"
date: 2009-11-21
forum: Desktop Environments
---

### Post by Cardale on 2009-11-21
I am using Ubuntu 9.10 and I was trying to arrange my files by type which I believed meant exstension, but ubuntu or gnome doesn't arrage it that way.  It arrages items by type as long as it knows what that type is if it doesn't then it lumps all the of unknowns together.  Even the known file types get lumped together with other ones.

My question is this.  How can I arrange my files in my directories by .*(exstension)?

---

### Post by yossell on 2009-11-21
I'm not sure what you mean - are you talking about how the file manager displays its files? If you are, and if the file manager you're running is Nautilus, then you can choose the option under View->arrange items -> `by type'

yossell

---

### Post by SonicSteve on 2009-11-21
Yossell is right,

Linux in general doesn't really use file extensions. It looks at the inner properties of a file and knows what it is. If you rename a file like a .jpg to .something else. Linux still knows its a jpeg and will still open it with the default jpeg viewer. I tried this just to test.
I had a .jpg and I renamed it to .somethingelse and it made no difference.

So then viewing the files by "type" tells ubuntu to organize them essentially extension but if you two jpegs together one is .sss and the other is .xcc it will put them together because they are both jpegs.

---

### Post by Cardale on 2009-11-21
Often times when I am working on files I need to organize them by .ext what can I do?

---

### Post by SonicSteve on 2009-11-22
I would try installing different file managers. 
Dolphin
Thunar etc...

Open up add/remove programs or the new "software center" and search for file managers. Hopefully one of them will sort by extension rather than just type.

---

### Post by yossell on 2009-11-22
It's not pretty and it requires firefox, but the firefly extension for firefox gave me a way of browsing the files on my computer by extension rather than type. I changed the extension of two pdf files, names one .aaa the other .zzz  - and they were separated on the list. They were still recognised as pdf files and opened from clicking. 

[http://firefly.mozdev.org/index.php](http://firefly.mozdev.org/index.php)

is where I found the extension.

If you can find a file manager that does the trick, SonicSteve's suggestion would probably be preferable. But this may be a workaround.

---

### Post by SonicSteve on 2009-11-22
One other way I found while doing searches was by using the command prompt / Terminal. Not quite as simple though :) In fact if you're not comfortable with the command line you likely won't want to try it at all.

---

