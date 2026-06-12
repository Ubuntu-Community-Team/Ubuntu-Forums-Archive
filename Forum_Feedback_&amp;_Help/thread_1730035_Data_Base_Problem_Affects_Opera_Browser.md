---
title: "Data Base Problem Affects Opera Browser"
date: 2011-04-15
forum: Forum Feedback &amp; Help
---

### Post by Frogs Hair on 2011-04-15
Hello,

Since some forum database warnings earlier the Ubuntu forum page appears with red lines under everything . I don't know if you are having on going problems or not , I'm just looking for some input as to why . I have tested many web pages and this only appears on the Ubuntu forums . I have included a screen shot and any feedback would be great.

---

### Post by Frogs Hair on 2011-04-15
Removed Opera and all profile folders and reinstalled with no change . I wanted to be sure I did not activate a hot key for the Ubuntu Forums page.

---

### Post by lovinglinux on 2011-04-15
It is rendering correctly on Opera 11.10 2092.

Perhaps you are using some style sheet that underlines all text.

Right-click on the page, select "Edit site preferences", then click the display tab and check what is in "My style sheet".

---

### Post by Frogs Hair on 2011-04-15
I have the same build and have never made any modifications to those settings. This is what appears in the box ./usr/share/opera/styles/user.css

---

### Post by lovinglinux on 2011-04-15
Try the attached css.

---

### Post by Frogs Hair on 2011-04-15
You will have to instruct me how to use it. I figured it out , it looks nice except the red lines . The lines only appear on the main page , once I enter a sub forum all is normal . This happened during the data base errors.

---

### Post by lovinglinux on 2011-04-15
> **Frogs Hair said:**
> You will have to instruct me how to use it. I figured it out , it looks nice except the red lines . The lines only appear on the main page , once I enter a sub forum all is normal . This happened during the data base errors.

Now that you have mentioned it, the front page also appear with underlines here. When I hover the tab preview with the mouse they disappear. They only appear when the mouse is over the page :confused:

---

### Post by Frogs Hair on 2011-04-15
> **lovinglinux said:**
> Now that you have mentioned it, the front page also appear with underlines here. When I hover the tab preview with the mouse they disappear. They only appear when the mouse is over the page :confused:

I turned on open console on errors tab under site preferences > scripting and the page fills up.

---

### Post by Frogs Hair on 2011-04-15
Same problem with Opera on Win 7

---

### Post by lovinglinux on 2011-04-15
> **Frogs Hair said:**
> Same problem with Opera on Win 7

Have you tried an old version of Opera?

Perhaps you should report the problem to a forum admin.

---

### Post by wojox on 2011-04-15
It kind of acts funny on Firefox 4. When I hover over the blue section about the archives and spam it all turns red. Looked at the code and found this:

```
<b>Spammer Ban List</b><br />The Ubuntu Forum will be applying a new spammer IP ban list today. More info <a href="http://ubuntuforums.org/showthread.php?t=1729768">here<a>
```

There is no closing tag on the hyper-link </a>. Could be that. It's been a while since my HTML/php days. :p

---

### Post by Frogs Hair on 2011-04-15
> **lovinglinux said:**
> Have you tried an old version of Opera?
 
Perhaps you should report the problem to a forum admin.
 
No , I have been on the forum all day , no work or school and the weather is crap. I will take it up again tomorow . Thanks for your input , at least I know it's not just me . Being on this forum on IE 9 is just too weird .

---

### Post by Frogs Hair on 2011-04-16
> **wojox said:**
> It kind of acts funny on Firefox 4. When I hover over the blue section about the archives and spam it all turns red. Looked at the code and found this:

```
<b>Spammer Ban List</b><br />The Ubuntu Forum will be applying a new spammer IP ban list today. More info <a href="http://ubuntuforums.org/showthread.php?t=1729768">here<a>
```

There is no closing tag on the hyper-link </a>. Could be that. It's been a while since my HTML/php days. :p

I think you may be correct , the main page is the only page with that banner and the problem only occurs on that page . I may have just noticed it at the time of the database errors. The other banner did not cause an error when it was posted days ago. lovinglinux and I live thousands of miles apart, but we have the same problem with same browser on the same page.

---

### Post by Frogs Hair on 2011-04-16
I have emailed Technoviking in regards to what wojox pointed out about the spam announcement. I will report back when I get a response.

---

### Post by Joeb454 on 2011-04-16
> **wojox said:**
> It kind of acts funny on Firefox 4. When I hover over the blue section about the archives and spam it all turns red. Looked at the code and found this:

```
<b>Spammer Ban List</b><br />The Ubuntu Forum will be applying a new spammer IP ban list today. More info <a href="http://ubuntuforums.org/showthread.php?t=1729768">here<a>
```

There is no closing tag on the hyper-link </a>. Could be that. It's been a while since my HTML/php days. :p

Should be fixed now :)

---

### Post by Frogs Hair on 2011-04-16
> **Joeb454 said:**
> Should be fixed now :)

Thank You !

---

