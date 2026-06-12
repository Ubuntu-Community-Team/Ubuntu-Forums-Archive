---
title: "Code Tags"
date: 2011-07-30
forum: Forum Feedback &amp; Help
---

### Post by Frogs Hair on 2011-07-30
Hello ,

I have been having a problem with code tags , when ever try to insert content between the tags the content jumps to the right of the last bracket when I select paste .

    ] paste content

I was wondering if this is my browser causing this because I am using the FF Nightly build or is it some setting on the forum that I have unknowingly activated ?

---

### Post by PCaddicted on 2011-07-30
Are you sure you really pasted the content in the area between the brackets that are in bold here:
[CODE**] ****[**/CODE]
?
Maybe you accidentally pasted it in the wrong place. I can't see other explanation.

---

### Post by Frogs Hair on 2011-07-30
It works fine when I type the command , when I try to paste the command the type indicator  jumps to the right side of the bracket as  indicated in my first post . I use this feature often and that is why I was trying to figure out what's happening .

---

### Post by Frogs Hair on 2011-07-30
```
It works fine with opera . 
```

It has to be a Firefox Nightly problem , which will update tomorrow or Monday .

---

### Post by Frogs Hair on 2011-07-30
Code tags do not work properly after Firefox Nightly  update . It is an alpha so I will have to live with it . I will mark as solved because I know origin of the problem is not the forum .

---

### Post by AlphaLexman on 2011-07-31
I can confirm this. Firefox 5.0 (not nightly builds) will put the cursor outside of the Code Tags...

Chrome 12.0.742.124 keeps the cursor in between the tags.

---

### Post by lisati on 2011-07-31
A quick question. What happens if you type up the "code", highlight it, and then press [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG]?

---

### Post by AlphaLexman on 2011-08-01
```
It works
``` except the cursor is still outside when I want to type more...

**EDIT:** I agree with Frogs Hair, this is not a forum issue, but a browser difference. However thank you lisati for your concern.

---

### Post by lovinglinux on 2011-08-03
I have experienced some weird bbcode tag issues like that on a Java based forum, but never here.

How are you pasting the text, through context menu, CTRL+V or middle-mouse button?

---

### Post by Frogs Hair on 2011-08-03
Thanks for responding , I am using the context menu .

---

### Post by AlphaLexman on 2011-08-03
> **lovinglinux said:**
> I have experienced some weird bbcode tag issues like that on a Java based forum, but never here.

How are you pasting the text, through context menu, CTRL+V or middle-mouse button?
Well I typed my text, then selected with the mouse, then clicked the 'code tags button' the cursor was on the outside of the tags.

I also just tested code tags with firefox at [www.unix.com](www.unix.com) forums and got the same thing,

With firefox 5.0 the cursor is outside the tags and with google chrome it is inside! Weird!!

EDIT: Just tested with epiphany and the cursor is in between the code tags. It must be a firefox issue.

---

### Post by lovinglinux on 2011-08-04
> **Frogs Hair said:**
> Thanks for responding , I am using the context menu .

> **AlphaLexman said:**
> Well I typed my text, then selected with the mouse, then clicked the 'code tags button' the cursor was on the outside of the tags.

I also just tested code tags with firefox at [www.unix.com](www.unix.com) forums and got the same thing,

With firefox 5.0 the cursor is outside the tags and with google chrome it is inside! Weird!!

EDIT: Just tested with epiphany and the cursor is in between the code tags. It must be a firefox issue.

I had a problem with my VM drive, but I will install Ubuntu again (I am suing KDE instead of Unity) and check if I can reproduce the problem.

Meanwhile, check if the problem persists with Compiz disabled. Also try to disable Global Menu Bar Integration add-on.

---

### Post by Frogs Hair on 2011-08-04
Nightly just updated  and no change .  I have had the global menu integration  disabled since unity was installed . I am logged in to E17 at the moment and that made no difference , the problem began long before that was installed .  There has been no change in my Compiz settings since installation in April .

---

### Post by lovinglinux on 2011-08-04
> **Frogs Hair said:**
> Nightly just updated  and no change .  I have had the global menu integration  disabled since unity was installed . I am logged in to E17 at the moment and that made no difference , the problem began long before that was installed .  There has been no change in my Compiz settings since installation in April .

Don't know what else could be. I would test if other versions have the same issue on your system.

---

### Post by Elfy on 2011-08-04
While I might be clutching at straws here - have you checked the hardware? 

Have you disabled all add-ons?

Like I said - clutching ... 

I find that the only time it goes a bit wrong is when whatever I expect to be within the tags is not highlighted.

Tried pasting and middle click with either the # or code tags - which I tend to get by using a bbcode addon anyway.

---

### Post by AlphaLexman on 2011-08-04
I am running 10.04.3 LTS, so the repos only give me Firefox 3.6.16 in /usr/bin/ 

However I downloaded firefox 5.0 and installed it to /home/AlphaLexman/bin/firefox/ so that I can use either one...

3.6.18 **and** 5.0 still put the cursor outside the code tags!!

---

### Post by lovinglinux on 2011-08-04
> **AlphaLexman said:**
> I am running 10.04.3 LTS, so the repos only give me Firefox 3.6.16 in /usr/bin/ 

However I downloaded firefox 5.0 and installed it to /home/AlphaLexman/bin/firefox/ so that I can use either one...

3.6.18 **and** 5.0 still put the cursor outside the code tags!!

So, is not the new Firefox fault. Please try a new Ubuntu user account, so we can discard user settings as culprit.

---

### Post by Frogs Hair on 2011-08-07
```
code tag test
```Problem solved with update , it began with an update and this one on 8/7 has fixed it , for now .

---

