---
title: "Text beside icons on the desktop"
date: 2009-08-03
forum: Desktop Environments
---

### Post by dullo on 2009-08-03
I'm using Ubuntu 9.04 and I'm trying to get the text that normally appears under the the icon to appear beside it instead. I know you can change this option in the "Views" tab of nautilus preferences' but this does not work for the icons on the desktop. 
Can anyone help me out with this, it would be much appreciated.

---

### Post by dullo on 2009-08-04
buuuuumppp

---

### Post by dullo on 2009-08-04
I thought linux was supposed to have this great helpful community? No replies? This is my second bump..

---

### Post by gettinoriginal on 2009-08-05
I am sorry you are not getting a response, but sometimes with a question like yours, many of us don't know the solution.  I did search google and googlubuntu both, and cannot find any posts that solve your problem.  
This is an extremely helpful forum, it is just a matter of waiting for someone with the knowledge to see your request.  Also, please try to wait 24 hours before bumping, there are those of us that mostly look for "unanswered posts", and once you bump it it removes it from that selection.  :D

---

### Post by dullo on 2009-08-05
Ah, sorry i just bumped once the topic reached the second page. Next time I'll be sure to wait. Anyone have any information on getting desktop icon text to appear beside the icons?

---

### Post by dullo on 2009-08-06
bump

---

### Post by davbren on 2009-08-07
I also wanted to know this a while back. It's just not in the OS at the moment mate. Maybe if you make a request for future releases...?

---

### Post by dullo on 2009-08-10
There is no way at all?

---

### Post by davbren on 2009-08-10
dont think so mate sorry. Well, theres always a way, you'll just have to program it yourself...

---

### Post by ArmenianLeader4 on 2009-08-10
I think theres something you can do, like resetting your appearance settings or something like that. A friend of mine had the same problem and he fixed it by somehow resetting something.

---

### Post by dullo on 2009-08-10
Well can you ask your friend?

---

### Post by dullo on 2009-08-12
bump..

---

### Post by dullo on 2009-08-13
two bumps in a row

---

### Post by gettinoriginal on 2009-08-14
Try this

F2 and enter:
```
gconf-editor
```
run > apps > nautilus > icon view > labels beside icons
[ATTACH]124823[/ATTACH]

---

### Post by dullo on 2009-08-14
that will only work inside a nautilus window, the text still stays below the icons on the desktop

---

### Post by steveneddy on 2009-08-14
Have you tried Google or actually searching yourself for these issues?

UF isn't the only place that you can ask for help.

If no one knows then you can bump a thousand times and still no one will know the answer.

---

### Post by Joeb454 on 2009-08-14
> **gettinoriginal said:**
> Try this

F2 and enter:
```
gconf-editor
```
run > apps > nautilus > icon view > labels beside icons
[ATTACH]124823[/ATTACH]

> **dullo said:**
> that will only work inside a nautilus window, the text still stays below the icons on the desktop

Have you tried it? It looks like it would work (I'm not at an Ubuntu machine, so can't verify it)

---

### Post by dullo on 2009-08-14
> **steveneddy said:**
> Have you tried Google or actually searching yourself for these issues?

UF isn't the only place that you can ask for help.

If no one knows then you can bump a thousand times and still no one will know the answer.

Yes I did plenty of searching here and on other results from google before I made this thread.

> Have you tried it? It looks like it would work (I'm not at an Ubuntu machine, so can't verify it)

Yes I tried it in the nautilus preferences and using gconf-editor as well.

---

### Post by dullo on 2009-08-18
bumppppp

---

### Post by davbren on 2009-08-20
Dude, I told you it can't be done just yet... try and find the nautilus ideas thing so you can launch the idea.

---

### Post by r5r4y on 2009-10-02
Sorry about the BIG BUMP, But I've found a solution...

[http://oi3prnnx.deviantart.com/art/The-New-Nautilus-Desktop-138405468](http://oi3prnnx.deviantart.com/art/The-New-Nautilus-Desktop-138405468)

---

### Post by syn4k on 2009-10-20
Thank you! I was able to help some others with this information:
[http://ubuntuforums.org/showthread.php?p=8134062#post8134062](http://ubuntuforums.org/showthread.php?p=8134062#post8134062)
You get a gold star :KS

---

### Post by Donalb on 2009-10-20
Thanks to r5r4y & syn4k for his link.

I'd opened a thread on this about a year ago. It quickly seemed it wasn't possible so I put in a Brainstorm request for it.

```
http://brainstorm.ubuntu.com/idea/17683/

```
However it was my first request/idea and I didn't label it well enough and also I didn't realise someone else could come in and add something that seemed to me to have nothing to do with the original idea.

Anyway Option 1 in the brainstorm link is for this request, allow the user to use small icons, with the text beside the icon, on the desktop, and also allow a "snap-to-Grid" option.
If you think we should be able to do this without modding code, please vote it up.

It seemed such an obvious lack that I hoped it might make the "100 Papercuts" project, but I'm afraid not the last time I looked. 
Also, I guess, "obvious" is subjective.

---

### Post by ssouthparkk on 2009-10-20
I am trying this and am stuck on:


[LIST=1]
[*]2) Copy the patch into the folder ~/nautilus-(version)/src/file-manager
[*]open terminal go to ~/nautilus-(version)/src/file-manager that where you put the patch and when you in there, write:
[/LIST]
I cannot find that folder.  There are no Nautilus folders with a version number after it.

---

### Post by Donalb on 2009-10-20
I found that folder in my /home dir, but I got:

```
/nautilus-2.24.1/src/file-manager$ patch -p0 < file-manager.patch
patch: **** Only garbage was found in the patch input.
```

The file-manager.patch file was just a copy & paste of the original instructions. 
Ideas?

---

### Post by syn4k on 2009-10-22
This is exactly what I referring to in my post when I said, I did not use the patch because it complained so I instead manually modified the code myself and then cd to src to compile it.

---

### Post by syn4k on 2009-11-01
Do this...
[http://nettekk.com/index.php?action=content_view&id=218](http://nettekk.com/index.php?action=content_view&id=218)
:popcorn:

---

### Post by jdorenbush on 2009-11-10
> **ssouthparkk said:**
> I am trying this and am stuck on:


[LIST=1]
[*]2) Copy the patch into the folder ~/nautilus-(version)/src/file-manager
[*]open terminal go to ~/nautilus-(version)/src/file-manager that where you put the patch and when you in there, write:
[/LIST]
I cannot find that folder.  There are no Nautilus folders with a version number after it.

> **Donalb said:**
> I found that folder in my /home dir, but I got:

```
/nautilus-2.24.1/src/file-manager$ patch -p0 < file-manager.patch
patch: **** Only garbage was found in the patch input.
```

The file-manager.patch file was just a copy & paste of the original instructions. 
Ideas?

The ~ is your home directory. If you put ~ in the Nautilus location bar it will take you to /home/yourusername

I was having problems with permissions on the patch file and was unable to use the patch file in the tutorial. But if you look in the patch file it really isn't changing much -- you could just as easily do it manually.

1. In ~/nautilus-xxxx/src/file-manager there is a file "**fm-desktop-icon-view.c**". That is the one you need to patch. Open it in text editor.

2. Find the line of code that says "**real_supports_labels_beside_icons (FMIconView *view)**".

3. Below it, it should say "**return FALSE;**". Change to "**TRUE**".

Continue with step 3 on [http://pastebin.com/f3f29fcec]("http://pastebin.com/f3f29fcec") and you should be good to go.

Worked for me. [http://img5.imageshack.us/i/screenshothyh.png/]("http://img5.imageshack.us/i/screenshothyh.png/")

**UPDATE:**
It seems this is a little buggy. If you turn off the 'Text Beside Icon' view on the desktop the rename option for folder/file names act as though they are still in the 'Text Beside Icon' view, but they switch back to normal once done renaming.

I also noticed I couldn't edit folder/file names when I first turned off 'Text Beside Icon' view. I had to go and turn it back on, and then off again. That seemed to resolve the problem. Not exactly sure why.

---

### Post by andrek on 2009-12-05
Thanks guys, been looking for this for a long time.

---

### Post by Donalb on 2009-12-13
Fantastic.
Something that's been annoying me for years, almost there...

Any idea though how to reduce the Icon size while retaining the text size?

I reduced Icon Zoom Size to Smallest in gconf >apps>nautilus>icon view,  but the text disappeared. At Smaller setting instead, the icons are still a bit too big, with 23 items on the desktop, to  have them all in one list on the left.

Appreciate all the work on this.

---

