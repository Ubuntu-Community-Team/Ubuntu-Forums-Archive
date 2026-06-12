---
title: "Rule to always have application on all virtual desktops"
date: 2010-07-09
forum: Desktop Environments
---

### Post by HelloIndustries on 2010-07-09
Excuse me if this question about multiple desktops has been posted. Google didn't turn up much of relevance.

What i'm looking to do is somehow set a rule so i can have Evolution and some other apps automatically always on the visible workspace rather than have to right-click and set it every time i open an app / log-in.

Using Ubuntu 10.04/Gnome/Compiz. Pretty standard set up.
FYI: I'm quite new to Ubuntu/Linux

**[Solved] Update:**
The solution that worked for me was this:

Compiz Settings > Window rules
In 'sticky' i entered:

class=Evolution | class=Firefox | class=Exaile | class=TomBoy

The above now default to displaying on the currently visible workspace.
Thanks for the help.

---

### Post by hariks0 on 2010-07-09
Right click the Evolution Window Title bar. There should be an option to set this.

---

### Post by stinkeye on 2010-07-09
ccsm > window management > window rules (ccsm=compizconfig-settings-manager) 
Add to the sticky rule.
In my ccsm there's a bug when you grab a window it only inserts **class=**
You have to manually paste in the name.
eg **class=evolution**

---

### Post by HelloIndustries on 2010-07-09
> **hariks0 said:**
> Right click the Evolution Window Title bar. There should be an option to set this.

Indeed there is. As on all other windows. However, this is not the functionality i'm looking for. This method requires me to re-set the attribute every log-in / opening of application.

Thanks for the reply, though :)

---

### Post by HelloIndustries on 2010-07-09
> **stinkeye said:**
> ccsm > window management > window rules (ccsm=compizconfig-settings-manager) 
Add to the sticky rule.
In my ccsm there's a bug when you grab a window it only inserts **class=**
You have to manually paste in the name.
eg **class=evolution**

Thanks :)
This seems to be what i'm looking for, however, it doesn't seem to want to work :(
Also, while i'm here:

How would i enter multiple values?
Example: I want to have Evolution, Empathy, Firefox, Exaile and TomBoy notes always available.

---

### Post by stinkeye on 2010-07-09
Open up the window you want to sticky.
Then in ccsm > window rules
Click on the add button

click on the grab button

click on the window you want to sticky

change the relation to **or**

before you click on the add button copy the name in the value field
because of the bug

hit the add button

If the sticky box now looks like **class=**
paste the name after class=     (you may not have this bug, where it omits the window name)

In the end your sticky values should look similar to this
```
class=Firefox | class=Tomboy
```
You can just insert these values manually as long as the window names are correct and you separate with "|" (shift + backslash.....below the backspace key.)

---

### Post by HelloIndustries on 2010-07-09
> **stinkeye said:**
> Open up the window you want to sticky.
Then in ccsm > window rules
Click on the add button

click on the grab button

click on the window you want to sticky

change the relation to **or**

before you click on the add button copy the name in the value field
because of the bug

hit the add button

If the sticky box now looks like **class=**
paste the name after class=     (you may not have this bug, where it omits the window name)

In the end your sticky values should look similar to this
```
class=Firefox | class=Tomboy
```

You, sir or madam, are my saviour. Thank you ^_^

---

### Post by mcduck on 2010-07-09
> **HelloIndustries said:**
> Thanks :)
This seems to be what i'm looking for, however, it doesn't seem to want to work :(
Also, while i'm here:

How would i enter multiple values?
Example: I want to have Evolution, Empathy, Firefox, Exaile and TomBoy notes always available.

Use the grab button to automatically grab the exact, correct class/type/whatever for a certain window, for example it might actually be "class=Evolution" instead of "class=evolution". (It will grab the name correctly, but you still need to type it in manually afterwards becasue of the bug stinkeye mentioned).

For making more complex rules you can use basic boolean operators, like "|" for "OR", "&" for "AND" and "!" for "NOT". Also if you enable the RegExp plugin then you'll have the full power of regular expressions at your hand for making the rules..

Read here for more details: [http://wiki.compiz.org/WindowMatching]("http://wiki.compiz.org/WindowMatching")

For example to make the rule apply to all the programs you mentioned you could use something like this: "class=Evolution|Firefox|Exaile|TomBoy" (Don't just copypaste that one, though, check the correct class names yourself).

---

### Post by HelloIndustries on 2010-07-09
> **mcduck said:**
> Use the grab button to automatically grab the exact, correct class/type/whatever for a certain window, for example it might actually be "class=Evolution" instead of "class=evolution". (It will grab the name correctly, but you still need to type it in manually afterwards becasue of the bug stinkeye mentioned).

For making more complex rules you can use basic boolean operators, like "|" for "OR", "&" for "AND" and "!" for "NOT". Also if you enable the RegExp plugin then you'll have the full power of regular expressions at your hand for making the rules..

Read here for more details: [http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching)

For example to make the rule apply to all the programs you mentioned you could use something like this: "class=Evolution|Firefox|Exaile|TomBoy" (Don't just copypaste that one, though, check the correct class names yourself).

Thanks :)
I'll look into that when i'm not consuming delicious Rum :)

---

### Post by HelloIndustries on 2010-07-09
> **mcduck said:**
> "class=Evolution|Firefox|Exaile|TomBoy" (Don't just copypaste that one, though, check the correct class names yourself).

This was actually spot-on. Here's hoping it works :)

---

### Post by Jackelope King on 2010-07-09
> **stinkeye said:**
> Open up the window you want to sticky.
Then in ccsm > window rules
Click on the add button

click on the grab button

click on the window you want to sticky

change the relation to **or**

before you click on the add button copy the name in the value field
because of the bug

hit the add button

If the sticky box now looks like **class=**
paste the name after class=     (you may not have this bug, where it omits the window name)

In the end your sticky values should look similar to this
```
class=Firefox | class=Tomboy
```
You can just insert these values manually as long as the window names are correct and you separate with "|" (shift + backslash.....below the backspace key.)

A thanks from me too. I've been looking for a way to do this for months now.

---

