---
title: "Firefox: Remember window position"
date: 2011-07-23
forum: Desktop Environments
---

### Post by blackbird3216 on 2011-07-23
I installed Ubuntu 10.04 LTS yesterday as an upgrade to 9.10, which is no longer supported. So far, it is working very smoothly, and I love it. I have unchecked "expand" on the bottom toolbar, so that whenever I open a new window, the toolbar expands, which is great. After adding opacity, it is working excellent. Since the bottom panel is no longer maximized, I can set Scale (in compiz) to show all windows on the bottom left, and show all of window group (windows of same application) on the bottom right, without having to interfere with my "show desktop" and trash. I love this new "feature."

However, this new personal change has necessitated that I no longer use fullscreen browsing. I think non-fullscreen works just as great, and it lets me view other windows and my desktop at the same time. When I tried using Firefox, one annoying thing was that Firefox never kept the same position centered in the middle. When I tried opening nautilus, and testing the behavior there, Nautilus always remembered the last position. This is not so with Firefox. It always opens locked to the left corner, and NOT where it was last located. This is very frustrating. 

As any good forum member, I made a search (using Bing) and found this thread: 
[http://ubuntuforums.org/showthread.php?t=89627](http://ubuntuforums.org/showthread.php?t=89627)

This is exactly the problem I am facing, and it is interesting since it was dated six years ago, yet the problem is still occurring. How do I make Firefox remember its position?

---

### Post by blackbird3216 on 2011-07-23
At first, I thought it was a problem with compiz, and tried to fiddle with settings in the "put" plugin, but it didn't solve the issue.

---

### Post by lovinglinux on 2011-07-24
Use [Session Manager]("https://addons.mozilla.org/en-US/firefox/addon/session-manager/") extension. It allows to save multiple sessions, including open tabs/windows, window positions and more.

---

### Post by blackbird3216 on 2011-07-24
I viewed the page for the extension, and it seems very difficult to configure. 

Also, I thought this was inherently an issue with compiz or X, and not with Firefox. Is it simply because Firefox was not designed to save the window location?

---

### Post by lovinglinux on 2011-07-24
> **blackbird3216 said:**
> I viewed the page for the extension, and it seems very difficult to configure. 

Also, I thought this was inherently an issue with compiz or X, and not with Firefox. Is it simply because Firefox was not designed to save the window location?

I use KDE and kwin can configure Firefox windows properly. 

The extension is not complicated to configure. Give it a try.

---

### Post by blackbird3216 on 2011-07-25
Ok, I'll try it tonight when I get home, and then I'll let you know how it goes.
Thanks.

---

### Post by blackbird3216 on 2011-07-26
I tried it, and unfortunately saving the session does not remember the window location. 
I thought it was pretty clear that it was either an issue with firefox, or with compiz, but I could be wrong. 

I can't believe that there is still not a fix to a problem that is over five years old.

---

### Post by lovinglinux on 2011-07-26
> **blackbird3216 said:**
> I tried it, and unfortunately saving the session does not remember the window location. 
I thought it was pretty clear that it was either an issue with firefox, or with compiz, but I could be wrong. 

I can't believe that there is still not a fix to a problem that is over five years old.

I suppose it is a Compiz issue.

---

### Post by blackbird3216 on 2011-07-27
Yes, that's what I thought as well. I thought that someone might have a solution to the problem. 
Thanks for all your help. 

Does anyone else know a solution?

---

### Post by blackbird3216 on 2011-07-28
up

---

### Post by lovinglinux on 2011-07-28
> **blackbird3216 said:**
> up

Try this: [http://ubuntuforums.org/showpost.php?p=10568576&postcount=2](http://ubuntuforums.org/showpost.php?p=10568576&postcount=2)

---

### Post by cilo on 2012-03-20
MAKE UBUNTU REMEBER WINDOWS SIZE AND POSITION YOU LAST USED FOR EACH APPLICATION
In principle Ubuntu does this automatically, but as a default windows larger than 75%
of the desktop area are mazimized when re-opened.
Fortunately this percentage can be easily set in Ubuntu 11.10 (and we hope for later).

First you must have installed "Advanced settings", as it is called in the ubuntu software center, namely the CompizConfigSettingsManager package  (why it's not installed by default?)

Run it ---> Go to the Desktop section --->
  ---> Click Ubuntu Unity Plugin --> Go to the Experimental tab
  ---> Set the Auto-maximize value to 100% to completely disable 
   it, or just to a higher percentage if you like the behaviour
   but the default 75% is the wrong value for you.

---

### Post by Jos.vh on 2013-02-01
Hi.

When looking up Compiz in the Ubuntu software center, under reviews, you will find a couple of comments, saying that it is in-compatible with 11.10. Is this a still existing problem or is it fixed by now?
How about 12.04 compatibility? Any comments on that? Should i upgrade....

---

