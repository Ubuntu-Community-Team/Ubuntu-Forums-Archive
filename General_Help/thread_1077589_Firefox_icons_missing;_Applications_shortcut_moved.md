---
title: "Firefox icons missing; Applications shortcut moved"
date: 2009-02-22
forum: General Help
---

### Post by canjecricketer on 2009-02-22
First, let me say that I'm not entirely sure if this is the right place to post this- if not, please direct me. 

Let me first describe what I did that caused the problem. I'm running Ubuntu Intrepid. I wanted to try out Kubuntu and knew that I could achieve that by adding the proper packages. That all went fine- I just used the core package because I generally like my gnome apps. The one thing I missed at first was the Firefox panel icon I have in gnome. Not sure of the best way to do this in Kubuntu (I'm primarily a Windows user...), I just tried making a shortcut from the icon in the launcher. I got the shortcut onto the desktop, but then decided I wanted to rename it just Firefox instead of Firefox Web Browser. Here is where things went awry. After I changed the name and hit enter, it said something about updating the system, like it was applying this change elsewhere. I thought I was just renaming a shortcut, like I would in Windows, but it was clear that I had done something else. Right away the icon changed from the usual Firefox one to the "default" app icon. I decided to go back into gnome and see if things had changed there. Sure enough, the panel icon had changed to the little "spring board" (at least that's what it looks like), and Firefox was no longer in the "Internet" category in the Applications menu. I found it in Other now, with the default application icon. 

Note- all of these icons work fine and launch the web browser. But they don't look right and I'd like to have the real ones back. Any thoughts? I did a search for files with "firefox" in the name, but I don't think I found the right ones. It looks like the panel icon at least is an svg file, and I couldn't find any Firefox svg files.

So, how can I get these icons back, and what did I do wrong in Kubuntu that messed things up?  

Also, what is the best way in Kubuntu to add shortcuts to the bottom bar (I don't even know the proper name for it...)?

Thanks

---

### Post by canjecricketer on 2009-02-25
Any ideas at all? Am I even in the right area? This was my first post ever on these forums...

---

### Post by canjecricketer on 2009-02-26
Well, I tried what I would call the "windows" solution, which was to "reinstall" the program. I'm not sure if that was the right thing to do, or if I did it the right way, but whatever the case, it doesn't seem to have worked anyway. I went into the Package manager and marked all of the current firefox packages for reinstallation. But it doesn't seem to have changed anything or brought back the icons. What am I missing here?

---

### Post by jdorenbush on 2010-01-23
If Firefox is installed but you don't see an icon in your Applications menu do this:

1. Right Click on "Applications" menu

2. Click "Edit Menus"

3. Click on "Internet" in the "Menus" section

4. Click "+ New Item"

5. Use the following information:
Type: Application
Name: Firefox
Command: firefox

6. Click "Ok"

This worked for me in the past when the icon disappeared and even after a fresh install of Firefox it still doesn't seem to come back. Hope this works for you.

---

### Post by Mrs Twaddle on 2010-04-29
thanks that fixed my firefox problem too!

---

